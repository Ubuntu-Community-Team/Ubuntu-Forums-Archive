---
title: "Touch support in Ubuntu?"
date: 2009-07-07
forum: Hardware
---

### Post by danwalmsley on 2009-07-07
Does Ubuntu, or Linux support touch input (like tablet pc on Windows), what about multi-touch?
 
If so, how does Ubuntu communicate with these devices? Windows Vista and 7 is totally plug and play, using a HID protocol, can Ubuntu support the same protocol? If not why can't it? (I could assist as I am very aware of the protocols, (available publically from MS)
 
How does ubuntu plan to compete with Windows 7's multi-touch?
 
 
Dan

---

### Post by nema.arpit on 2009-07-07
Jaunty at least does support touch (no other distro used)
I have HP's touchsmart tx2z and pen input works fine,the touchscreen though does not.My laptop has the n-trig touch screen,which is set to work with the modified wacom drivers-there are no official n-trig drivers as of now and are not expected in the near future.

I don't know about the communication interface.

As for multitouch,I read somewhere on this forum that Ubuntu 9.10 will have the support.

---

### Post by Favux on 2009-07-07
Hi dan,

Welcome to Ubuntu!

Yes Ubuntu has touch support.  The driver depends on what sort of touch tablet you have, eg. Wacom digitizer with touch has linuxwacom while other touch tablets have evtouch.  With N-trig digitizer (HP TX2z and Dell Latitude XT) stylus and touch are supported in Intrepid (8.10) and Jaunty (9.04) using kernel patches to the usb HID and also patches to linuxwacom.

The plan is for MPX and other multi-touch support to be integrated into the next couple of releases of Xorg's Xserver.  Jaunty currently has kernel 2.6.28, most of Rafi Rubin's N-trig HID patches for the kernel are in kernels 2.6.29, 2.6.30, and 2.6.31 (which will be in Kharmic (9.10)).  So N-trig support is improving with each kernel release.

I hope that answers your questions.

---

### Post by danwalmsley on 2009-07-07
Thats great information thanks, I was wondering if Ubuntu was planning on implementing the same HID protocol as Windows 7, the information is publically available, and all the multi-touch and single touch devices after the release of Windows 7 will support this. It means ubuntu will support these devices and no drivers will be needed, just like a mouse.
 
Who do I need to talk to about getting this implemented. Im pretty sure ubuntu would be widely adopted if you can implement this. Its a very simple protocol with some minor HID extensions
 
Dan

---

### Post by Favux on 2009-07-07
Hi Dan,

I imagine your talking about joining the kernel.org's mail list and also Xorg's.  Rafi Rubin might be a good person to contact about what to do and who you need to talk to.  Here's his site:  [http://ofb.net/~rafi/latitude_xt.html](http://ofb.net/~rafi/latitude_xt.html)  I don't see contact info.  I have seen him posting his N-trig stuff on the kernel list.  Some multi-touch stuff on his site.

---

### Post by danwalmsley on 2009-07-07
I am not able to implement this myself, but I would like to request the development. I will try and contact this guy.

---

