---
title: "Continuing Saga of Kodak Easyshare cameras"
date: 2013-03-26
forum: Hardware
---

### Post by Buntu Bunny on 2013-03-26
Seems these cameras have been an ongoing problem for years now. I happened to be gifted with one and when I had problems, of course I came to the forums. I don't have any profound solutions to the problems of this Linux non-friendly camera, but have gotten it to do what I need it to do. The purpose of this post is to maybe help others who have scoured the forums for answers like I have. There are a number of variations of problems, so these are with a Kodak Easyshare m583, Xubuntu 12.04, and Shotwell Photo Viewer.

When I first plugged in the camera, there was no computer acknowledgement *until* I disabled all sharing options.

After that, Shotwell could find the photos. I did find that the advice to turn the camera on first, did not work with Shotwell. If I did, I got this, 
> 
Shotwell needs to unmount the camera from the filesystem in order to access it. Continue?

I did not know the camera had even been mounted because there is no desktop icon for it, nor was it acknowledged by Thunar (but neither of those are new for this make and model of camera). If I leave the camera off and then plug it into my computer, no problem. Shotwell pops up and acknowledges the photos. 

I cannot however, "import all". From Shotwell:

> Files failed to import due to camera error.

If I select the images individually and import selected images, no problem. 

Shotwell can also delete the images in the camera with no problem. 

Trying to unmount was worrisome at first, because as others have pointed out, it's difficult to tell where it's mounted. However, since Shotwell already unmounted it, I've just been pulling the plug and going on about my photo taking business. 

I reckon this is an improvement to what others have experienced, and I hope it helps someone else.

---

