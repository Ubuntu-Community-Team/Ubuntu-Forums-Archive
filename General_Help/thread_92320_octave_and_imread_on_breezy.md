---
title: "octave and imread on breezy"
date: 2005-11-19
forum: General Help
---

### Post by neels on 2005-11-19
Hi all,

I just wanted to mention this somewhere:
In order to be able to use imread() to load a jpg or similar image into octave on breezy badger,
**YOU HAVE TO INSTALL ImageMagick!!**

That's all.

Otherwise you'll get an error message about a missing temporary file:

```
octave:1> i = imread('moneyTemplate.jpg');
error: could not read file: /tmp/oct-oIs7M5
error: evaluating if command near line 189, column 4
error: called from `imread' in file `/usr/share/octave/site/m/octave-forge/image/imread.m'
error: evaluating assignment expression near line 1, column 3
octave:1>
```


anecdote:
------------------------->8---------------------
I just spent DAYS trying to obtain Matlab, a micro-ass windumb version that actually works on my machine etc, all my efforts being kicked while they're down. After Matlab chose to crash on every startup but the very first, I decided it's just not worth it, and I should rather try to make octave load an image than try to make windows be useful.

Then I went and downloaded the latest stable source tarball, just to see that for some reason imread was gone completely. I cleaned the slate and reinstalled the ubuntu standard version, back to square one, to discover that the imread() function needs ImageMagick installed.
-------------8<------------------------------------

**So, should not someone add ImageMagick as a dependency to the octave package?** I'll try and get someone to do it.

There you have it. **WE LOVE ALL FREE AND OPEN SOFTWARE!!** windows is going to take care of itself in the end, as cumbersome as it is getting, no one needing to interfere much there. It just sucks.

---

