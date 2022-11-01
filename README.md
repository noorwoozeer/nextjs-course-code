<!-- @format -->

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

Skip to content
GitLab
About GitLab
Pricing
Talk to an expert
Search GitLab
/
Help
Login
Nextjs and React - The Complete Guide
Nextjs and React - The Complete Guide
Project information
Repository
Files
Commits
Branches
Tags
Contributors
Graph
Compare
Issues
0
Merge requests
0
CI/CD
Deployments
Packages and registries
Monitor
Analytics
Wiki
Snippets
Collapse sidebar
Martim Dias de Lima
Nextjs and React - The Complete GuideNextjs and React - The Complete Guide
Repository
master
nextjs-and-react-the-complete-guide
README.md
Martim Dias de Lima's avatar
Pages & File-based Routing
Martim Dias de Lima authored 1 year ago
fd102649
README.md
18.55 KiB

# Table of Contents

1.  [What is Next.js?](#org2fee060):nextjs:
2.  [Main Features](#org20d0f32)
3.  [Creating A Next.Js App](#orge86accd)
    - [Creating a Next.js project with creat-next-app](#orge07e086)
    - [Creating a Next.js project manually](#org82425cf)
4.  [Folder Structure](#org7884698)
5.  [Pages](#org22c9d82)
6.  [Custom pages](#orga415139)
7.  [File-based routing system based on pages](#org503df0c)
8.  [Routing](#org325c687)
9.  [Index Routes](#orga726681)
10. [Nested Routes](#org6889d83)
11. [Dynamic Route Segments](#orgff53802)
12. [Linking Between Pages](#org71cbdff)
13. [Styling](#orgcbc3718)
14. [Linting And Formatting](#orgddf34fe)
15. [Static Assets](#orga41a9a6)
16. [Data Fetching](#org2f59d4b)
    - [1. `getStaticProps` — used in SG when your **page content** depends on external data.](#org809906a)
    - [2. `getStaticPaths` — used in SG when your **page paths** depends on external data.](#orga43d844)
    - [3. `getServerSideProps` — used in Server-side Rendering.](#org91c0cdf)
17. [Information](#orgfb662a4)

---

<a id="org2fee060"></a>

# What is Next.js? :nextjs:

Working on a modern JavaScript application powered by React is awesome until you realize that there are a couple problems related to rendering all the content on the client-side.
First, the page takes longer to the become visible to the user, because before the content loads, all the JavaScript must load, and your application needs to run to determine what to show on the page.
Second, if you are building a publicly available website, you have a content SEO issue. Search engines are getting better at running and indexing JavaScript apps, but it’s much better if we can send them content instead of letting them figure it out.
The solution to both of those problems is server rendering, also called static pre-rendering.
Next.js is one React framework to do all of this in a very simple way, but it’s not limited to this. It’s advertised by its creators as a zero-configuration, single-command toolchain for React apps.
It provides a common structure that allows you to easily build a frontend React application, and transparently handle server-side rendering for you.
<a id="org20d0f32"></a>

# Main Features

- **Hot Code Reloading**: Next.js reloads the page when it detects any change saved to disk.
- **Automatic Routing**: any URL is mapped to the filesystem, to files put in the pages folder, and you don’t need any configuration (you have customization options of course).
- **Single File Components**: using styled-jsx, completely integrated as built by the same team, it’s trivial to add styles scoped to the component.
- **Server Rendering**: you can (optionally) render React components on the server side, before sending the HTML to the client.
- **Ecosystem Compatibility**: Next.js plays well with the rest of the JavaScript, Node and React ecosystem.
- **Automatic Code Splitting**: pages are rendered with just the libraries and JavaScript that they need, no more.
- **Prefetching**: the Link component, used to link together different pages, supports a prefetch prop which automatically prefetches page \*resources (including code missing due to code splitting) in the background.
- **Dynamic Components**: you can import JavaScript modules and React Components dynamically (<https://github.com/zeit/next.js#dynamic-import>).
- **Static Exports**: using the next export command, Next.js allows you to export a fully static site from your app.
  <a id="orge86accd"></a>

# Creating A Next.Js App

Creating a Next.js app requires Node.js, and npm (or npx) or yarn installed.
Creating a Next.js can be done in two ways, the first being the simplest:

1.  With create-next-app, or
    71
    72
    73
    74
    75
    76
    77
    78
    79
    80
    81
    82
    83
    84
    85
    86
    87
    88
    89
    90
    91
    92
    93
    94
    95
    96
    97
    98
    99
    100
    101
    102
    103
    104
    105
    106
    107
    108
    109
    110
    111
    112
    113
    114
    115
    116
    117
    118
    119
    120
    121
    122
    123
    124
    125
    126
    127
    128
    129
    130
    131
    132
    133
    134
    135
    136
    137
    138
    139
    140
2.  Manually

<a id="orge07e086"></a>

## Creating a Next.js project with creat-next-app

Using create-next-app is simple and straightforward, plus you can also get going with a starter like Next.js with Redux, Next.js with Tailwind CSS, or Next.js with Sanity CMS etc.

    # Create a new Next.js app with npx
    npx create-next-app <app-name>

    # Create a new Next.js app with npm
    npm create-next-app <app-name>

    # With yarn
    yarn create next-app <app-name>

<a id="org82425cf"></a>

## Creating a Next.js project manually

This requires three packages: next, react, and react-dom.

    # With npm
    npm install next react react-dom

    # With yarn
    yarn add next react react-dom

Then add the following scripts to package.json.

    "scripts": {
      "dev": "next dev",
      "start": "next start",
      "build": "next build"
    }

- dev starts Next.js in development mode.
- start starts Next.js in production mode.
- build builds your Next.js app for production.

<a id="org7884698"></a>

# Folder Structure

One salient thing you might notice after creating a Next.js app is the lean folder structure. You get the bare minimum to run a Next.js app. No more, no less. What you end up with as your app grows is up to you more than it is to the framework.

The only Next.js specific folders are the pages, public, and styles folder.

    # other files and folders, .gitignore, package.json...
    - pages
      - api
        - hello.js
      - _app.js
      - index.js
    - public
      - favicon.ico
      - vercel.svg
    - styles
      - globals.css
      - Home.module.css

<a id="org22c9d82"></a>

# Pages

141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
In a Next.js app, pages is one of the Next-specific folders you get. Here are some things you need to know about pages:

Pages are React components
Each file in it is a page and each page is a React component.

    // Location: /pages/homepage.js
    // <HomePage/> is just a basic React component
    export default HomePage() {
      return <h1>Welcome to Next.js</h1>
    }

<a id="orga415139"></a>

# Custom pages

These are special pages prefixed with the underscore, like `_app.js`.

`_app.js`: This is a custom component that resides in the pages folder. Next.js uses this component to initialize pages.
`_document.js`: Like `_app.js`, `_document.js` is a custom component that Next.js uses to augment your applications `<html>` and `<body>` tags. This is necessary because Next.js pages skip the definition of the surrounding document’s markup.

<a id="org503df0c"></a>

# File-based routing system based on pages

Next.js has a file-based routing system where each page automatically becomes a route based on its file name. For example, a page at `pages/profile` will be located at `/profile`, and `pages/index.js` at `/`.

    # Other folders
    - pages
      - index.js # located at /
      - profile.js # located at /profile
      - dashboard
        - index.js # located at /dashboard
        - payments.js # located at /dashboard/payments

<a id="org325c687"></a>

# Routing

Next.js has a file-based routing system based on pages. Every page created automatically becomes a route. For example, `pages/books.js` will become route `/book`.

    - pages
      - index.js # url: /
      - books.js # url: /books
      - profile.js # url: /profile
    Routing has led to libraries like React Router and can be daunting and quite complex because of the sheer number of ways you might see fit to route section of your pages in your Next.js app. Speaking about routing in Next.js is fairly straightforward, for the most part of it, the file-based routing system can be used to define the most common routing patterns.

Routing has led to libraries like React Router and can be daunting and quite complex because of the sheer number of ways you might see fit to route section of your pages in your Next.js app. Speaking about routing in Next.js is fairly straightforward, for the most part of it, the file-based routing system can be used to define the most common routing patterns.

<a id="orga726681"></a>

# Index Routes

The `pages` folder automatically has a page `index.js` which is automatically routed to the starting point of your application as `/`. But you can have different `index.jss` across your pages, but one in each folder. You don’t have to do this but it helps to define the starting point of your routes, and avoid some redundancy in naming. Take this folder structure for example:

    - pages
      - index.js
      - users
        - index.js
        - [user].js

There are two index routes at `/` and `/users`. It is possible to name the index route in the users folder `users.js` and have it routed to `/users/users` if that’s readable and convenient for you. Otherwise, you can use the index route to mitigate the redundancy.

<a id="org6889d83"></a>

# Nested Routes

211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280

How do you structure your folder to have a route like `/dashboard/user/:id`.

You need nested folders:

    - pages
      - index.js
      - dashboard
        - index.js
        - user
          - [id].js # dynamic id for each user

You can nest and go deeper as much as you like.

<a id="orgff53802"></a>

# Dynamic Route Segments

The segments of a URL are not always indeterminate. Sometimes you just can’t tell what will be there at development. This is where dynamic route segments come in. In the last example, `:id` is the dynamic segment in the URL `/dashboard/user/:id`. The id determines the user that will be on the page currently. If you can think about it, most likely you can create it with the file-system.

The dynamic part can appear anywhere in the nested routes:

    - pages
      - dashboard
        - user
          - [id].js
              - profile

will give the route `/dashboard/user/:id/profile` which leads to a profile page of a user with a particular id.

Imagine trying to access a route `/news/:category/:category-type/:league/:team` where category, category-type, league, and team are dynamic segments. Each segment will be a file, and files can’t be nested. This is where you’d need a catch-all routes where you spread the dynamic parts like:

    - pages
      - news
        - [...id].js

Then you can access the route like `/news/sport/football/epl/liverpool`.

You might be wondering how to get the dynamic segments in your components. The `useRouter` hook, exported from `next/router` is reserved for that purpose and others. It exposes the `router` object.

    import { useRouter } from 'next/router';

    export default function Post() {
      // useRouter returns the router object
      const router = useRouter();

      console.log({ router });
      return <div> News </div>;
    }

The dynamic segments are in the `query` property of the `router` object, accessed with `router.query`. If there are no queries, the query property returns an empty object.

<a id="org71cbdff"></a>

# Linking Between Pages

Navigating between pages in your apps can be done with the Link component exported by `next/link`. Say you have the pages:

    - pages
      - index.js
      - profile.js
      - settings.js
      - users
        - index.js
        - [user].js

You can `Link` them like:
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
import Link from "next/link";

    export default function Users({users) {
      return (
        <div>
          <Link href="/">Home</Link>
          <Link href="/profile">Profile</Link>
          <Link href="/settings">
            <a> Settings </a>
          </Link>
          <Link href="/users">
            <a> Settings </a>
          </Link>
          <Link href="/users/bob">
            <a> Settings </a>
          </Link>
        </div>
      )
    }

The **Link** component has a number of acceptable props, **href** — the URL of the hyperlink — been the only required one. It’s equivalent to the href attribute of the HTML anchor (`<a>`) element.

Other props include:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Prop</th>
<th scope="col" class="org-left">Default value</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left"><code>as</code></td>
<td class="org-left">Same as <code>href</code></td>
<td class="org-left">Indicates what to show in the browser URL bar.</td>
</tr>

<tr>
<td class="org-left"><code>passHref</code></td>
<td class="org-left">false</td>
<td class="org-left">Forces the <code>Link</code> component to pass the <code>href</code> prop to its child./td&gt;</td>
</tr>

<tr>
<td class="org-left"><code>prefetch</code></td>
<td class="org-left">true</td>
<td class="org-left">Allows Next.js to proactively fetch pages currently in the viewport even before they’re visited for faster page transitions.</td>
</tr>

<tr>
<td class="org-left"><code>replace</code></td>
<td class="org-left">false</td>
<td class="org-left">Replaces the current navigation <code>history</code> instead of pushing a new URL onto the <code>history</code> stack.</td>
</tr>
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420

<tr>
<td class="org-left"><code>scroll</code></td>
<td class="org-left">true</td>
<td class="org-left">After navigation, the new page should be scrolled to the top.</td>
</tr>

<tr>
<td class="org-left"><code>shallow</code></td>
<td class="org-left">false</td>
<td class="org-left">Update the path of the current page without re-running <code>getStaticProps</code>, <code>getServerSideProps</code>, or <code>getInitialProps</code>, allows the page to have stale data if turned on.</td>
</tr>
</tbody>
</table>

<a id="orgcbc3718"></a>

# Styling

Next.js comes with three styling methods out of the box, global CSS, CSS Modules, and styled-jsx.

<a id="orgddf34fe"></a>

# Linting And Formatting

Linting and formatting I suspect is a highly opinionated topic, but empirical metrics show that most people who need it in their JavaScript codebase seem to enjoy the company of ESLint and Prettier. Where the latter ideally formats, the former lints your codebase. I’ve become quite accustomed to Wes Bos’s ESLint and Prettier Setup because it extends eslint-config-airbnb, interpolate prettier formatting through ESLint, includes sensible-defaults that mostly works (for me), and can be overridden if the need arises.

<a id="orga41a9a6"></a>

# Static Assets

At some or several points in your Next.js app lifespan, you’re going to need an asset or another. It could be icons, self-hosted fonts, or images, and so on. To Next.js this is otherwise known as **Static File Serving** and there is a single source of truth, the public folder. The Next.js docs warns: Don’t name the `public` directory anything else. The name cannot be changed and is the only directory used to serve static assets.

Accessing static files is straightforward. Take the folder structure below for example:

    - pages
      profile.js
    - public
      - favicon.ico #url /favicon.ico
      - assets
        - fonts
          - font-x.woff2
          - font-x.woff # url: /assets/fonts/font-x.woff2
        - images
          - profile-img.png # url: /assets/images/profile-img.png
    - styles
      - globals.css

You can access the the `profile-img.png` image from the `<Profile/>` component:

    // <Profile/> is a React component
    export default function Profile() {
      return {
          <div className="profile-img__wrap">
            <img src="/assets/images/profile-img.png" alt="a big goofy grin" />
          </div>
      }
    }

or the fonts in the fonts folder in CSS:

    /* styles/globals.css */
    @font-face {
      font-family: 'font-x';
      src: url(/assets/fonts/font-x.woff2) format('woff2'),
           url(/assets/fonts/font-x.woff) format('woff');

421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
}

<a id="org2f59d4b"></a>

# Data Fetching

Data fetching in Next.js is a huge topic that requires some level of undertaken. Here, we’ll discuss the crux. Before we dive in, there’s a precursory need to have an idea of how Next.js renders its pages.

**Pre-rendering** is a huge part of how Next.js works as well as what makes it fast. By default, Next.js **pre-renders** every page by generating each page HTML in advance alongside the minimal JavaScript they need to run, through a process known as Hydration.

It is possible albeit impractical for you to turn off JavaScript and still have some parts of your Next.js app render. If you ever do this, consider doing it for mechanical purposes alone to show that Next.js truly Hydrates rendered pages.

That being said, there are two forms of **pre-rendering**:

1.  Static Generation (SG),
2.  Server-side Rendering (SSR).

The difference between the two lies in **when** data is been fetched. For SG, data is fetched at **build time** and reused on every request (which makes it faster because it can be cached), while in SSR, data is fetched on every request.

What they both have in common is that they can be mixed with Client-side Rendering with fetch, Axios, SWR, React Query etc.

The two forms of pre-rendering isn’t an absolute one-or-the-other case; you can choose to use Static Generation or Server-side Rendering, or you can use a hybrid of both. That is, while some parts of your Next.js app uses Static Generation, another can use SSR.

In both cases, Next.js offers special functions to fetch your data. You can use one of the Traditional Approach to Data Fetching in React or you can use the special functions. It’s advisable to use the special functions, not because they’re supposedly special, nor because they’re aptly named (as you’ll see) but because they give you a centralized and familiar data fetching technique that you can’t go wrong with.

The three special functions are:

<a id="org809906a"></a>

## 1. `getStaticProps` — used in SG when your **page content** depends on external data.

`getStaticProps` is a sibling to `getStaticPaths` and is used in Static Generation. It’s an async function where you can fetch external data, and return it as a prop to the default component in a page. The data is returned as a props object and implicitly maps to the prop of the default export component on the page.

<a id="orga43d844"></a>

## 2. `getStaticPaths` — used in SG when your **page paths** depends on external data.

Similar to `getStaticProps`, `getStaticPaths` is used in Static Generation but is different in that it is your page paths that is dynamic not your page content. This is often used with `getStaticProps` because it doesn’t return any data to your component itself, instead it returns the paths that should be pre-rendered at build time. With the knowledge of the paths, you can then go ahead to fetch their corresponding page content.

Think about Next.js pre-rendering your page in the aspect of a dynamic page with regards to Static Generation. For it to do this successfully at build time, it has to know what the page paths are. But it can’t because they’re dynamic and indeterminate, this is where `getStaticPaths` comes in.

<a id="org91c0cdf"></a>

## 3. `getServerSideProps` — used in Server-side Rendering.

<a id="orgfb662a4"></a>

# Information
