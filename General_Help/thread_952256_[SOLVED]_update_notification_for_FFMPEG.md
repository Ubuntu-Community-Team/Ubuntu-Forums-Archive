---
title: "[SOLVED] update notification for FFMPEG"
date: 2008-10-18
forum: General Help
---

### Post by mickcalcara on 2008-10-18
I compiled the FFMPEG for the non-free software encoding. Now I get a notification that I need to upgrade FFMPEG. Is there a way I can disable this notification since I want use the version I create from the source. 
I am doing this since I installed slide to video ( [http://jslideshow.sourceforge.net/README](http://jslideshow.sourceforge.net/README) )

thanks.

---

### Post by Yellow Pasque on 2008-10-18
Yes. Go to System -> Administration -> Synaptic Package Manager. Find ffmpeg, make sure Ubuntu didn't install its update, and select "Lock Version" under the 'Package' menu. Note that you can use 'Force Version' to go back to the version you built from source if you accidentally install the update.

---

