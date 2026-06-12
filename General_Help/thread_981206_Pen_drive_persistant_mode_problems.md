---
title: "Pen drive persistant mode problems"
date: 2008-11-13
forum: General Help
---

### Post by shiznatix on 2008-11-13
I have been trying to get a persistant install on a usb key but am running into problems. The tutorial that I have been following is this one: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

I first tried the script one but I ran out of memory really quickly and everything crashed and I was forced to reinstall because I could no longer even boot into gnome due to lack of space.

Afterwards I tried the manual installation which went quite smoothly, no problems. That was the install though, now I have problems. Whenever I boot up and try to run in persistant mode everything will freeze for about 3 minutes after I press enter for persistant mode from the original menu. After that 3 minutes it starts to boot just fine, no problems at all. The problem though is that it does not seam to actually boot into persistant mode at all. I booted up the first time and created a folder and installed wine and then restarted, neither are there anymore.

Other than that, everything is working perfectly right out of the box, that part is beautiful.

So my question is, how do I get this to work properly. I don't even want a non-persistant option, that I don't even care about. What I really want is to use my USB key as an external HD of sorts so I don't have to use vista on my work laptop while at home and so I can move my OS around with me and use it on different computers.

I am using a 2GB USB key just so everyone knows. Thanks.

---

### Post by C.S.Cameron on 2008-11-13
Try the USB installer that comes with 8.10, its in System, Administration.
If you select the maximum Stored in reserved extra space it will allow, with 700 MB used for the O/S you should have about 1.3 GB for upgrades.
If you want to be able to save stuff to it from a Windows machine, don't put so much into reserved space.

---

