---
title: "how to apply .dpatches?"
date: 2008-11-25
forum: General Help
---

### Post by evanct on 2008-11-25
I have this .dpatch file but I haven't the foggiest as to what to do with it. all i've found is this: 
[http://matrixhasu.altervista.org/index.php?view=use_dpatch](http://matrixhasu.altervista.org/index.php?view=use_dpatch)
but that does not explain things very well.

here is the patch:

```
#! /bin/sh /usr/share/dpatch/dpatch-run
## 08_gvba_load_gb_rom.dpatch by Javier Serrano Polo <jasp00@terra.es>
##
## All lines beginning with `## DP:' are a description of the patch.
## DP: Fix GB ROM loading in gvba

@DPATCH@

--- visualboyadvance-1.8.0.orig/src/gtk/window.cpp	2008-01-28 18:20:28.000000000 +0100
+++ visualboyadvance-1.8.0/src/gtk/window.cpp	2008-01-28 18:04:24.000000000 +0100
@@ -1428,6 +1428,7 @@
     bLoaded = gbLoadRom(csFile);
     if (bLoaded)
     {
+      gbReset();
       m_eCartridge = CartridgeGB;
       m_stEmulator = GBSystem;
     }

```

---

