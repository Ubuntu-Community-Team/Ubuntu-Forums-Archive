---
title: "nVidia CUDA issue"
date: 2012-01-10
forum: Hardware
---

### Post by eckscalibur on 2012-01-10
I recently installed nVidia CUDA using ironhide.  Most of the sample programs seem to be working fine, however any of them that involve graphics or sound extensions (fluidsGL, Mandelbrot, simpleGL, SobelFilter, simpleTexteure, volumeRender, etc.) will not run.  I get errors similar to the following:


```
simpleTexture.cu(161) : CUTIL CUDA error.


Error, unable to open output image <../../../src/dxtc/data/lena_std.dds>


cutLoadPPM() : Failed to open file: output.pgm
simpleSurfaceWrite.cu(174) : CUTIL CUDA error.
```

or if no other errors are thrown, I get just a segmentation fault.

Any ideas?

---

