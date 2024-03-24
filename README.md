# NxReactViteWatchNoInferrence

To reproduce:

```
npm install
npx nx test my-lib
```

output:

```sh
❯ npx nx test my-lib

> nx run my-lib:test  [existing outputs match the cache, left as is]

 Vitest  "cache.dir" is deprecated, use Vite's "cacheDir" instead if you want to change the cache director. Note caches will be written to "cacheDir/vitest"

 DEV  v1.4.0 /Users/thdk/repos/thdk/nx/nx-react-vite-watch-no-inferrence/my-lib

 ✓ src/lib/my-lib.spec.tsx (1)
   ✓ MyLib (1)
     ✓ should render successfully

 Test Files  1 passed (1)
      Tests  1 passed (1)
   Start at  10:28:10
   Duration  591ms (transform 45ms, setup 0ms, collect 143ms, tests 9ms, environment 281ms, prepare 59ms)


 PASS  Waiting for file changes...
       press h to show help, press q to quit

————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

 NX   Successfully ran target test for project my-lib (58ms)
```

Note that is says: `Waiting for file changes` but it immediately exits the process.

Adding `--watch` as in `npx nx test my-lib --watch` doesn't change the result.

## Expected results

It should either:

- watch for changes and not exit the current process
- not watch for changes at all

To be discussed if `watch` should be the default when `!process.env.CI` for the nx executor just like it is for `vitest` or not.
