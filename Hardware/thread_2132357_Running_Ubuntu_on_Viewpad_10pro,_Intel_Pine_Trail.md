---
title: "Running Ubuntu on Viewpad 10pro, Intel Pine Trail"
date: 2013-04-04
forum: Hardware
---

### Post by rabbiebuntu on 2013-04-04
Hi,

I'm a front-end web developer. I have a client who has purchased 34 Viewpad 10pro tablets for use in a Museum. These tablets are dual OS (but not dual boot) - running Windows 7, with an ancient version of Android on top.

[http://www.viewsonic.com/us/v10p-win-pro.html](http://www.viewsonic.com/us/v10p-win-pro.html)

They run the tablets in Windows kiosk mode. The purpose of the tablets is to run an offline web-site.  Every day, at least three tablets crash / lock up etc. When this happens, they have to boot into safe mode, and restart - or - plug a USB keyboard in so they can choose "normal" mode. Its a faff.

They have asked me to find a fix - and a friend suggested that a light weight installation of Ubuntu would do the job... as it boots faster, is more stable - and in the event of a crash, will just work again.

However, I have tried to install several linux distros: MINT, Ubuntu, Fedora - all of which report an X-server issue on install. I have found numerous forums in which people have got Ubuntu working on the Viewpad 10.... but cannot find any information about the Viewpad 10pro (it has a different chipset to the viewpad 10)

Is anyone able to advise me on how to get Ubuntu installed on the Viewpad 10pro (I understand ubuntu is touch ready out the box etc)? I've been reading lots of forums... even tried (but failed) to build my own linux distro with different drivers (it was all a bit above my head).

Thanks in advance for any advice you have.

Rob

---

### Post by nickdc on 2013-04-04
I'm just wondering whether you might be able to run Ubuntu in a virtual machine inside Windows 7. I've been pleasantly surprised how easy it was to get VirtualBox set up on an Ubuntu host and run XP as a virtual guest. But I've no experience of Windows 7 or running VB in Windows. Might be worth a try.

---

### Post by mörgæs on 2013-04-04
Hi, welcome to the fora.

Please post the exact error message(s) you get when trying to install.

Did you use 32 or 64 bit?

---

### Post by rabbiebuntu on 2013-04-05
Hi mörgæs and nickdc,
I'm using 32bit edition. Error messages vary between linux distros (paraphrased - but same error):

"Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to disclose the problem?

Thanks,
Rob

---

### Post by mörgæs on 2013-04-05
...and how does the X server output look?

---

