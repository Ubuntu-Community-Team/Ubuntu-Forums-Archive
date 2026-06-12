---
title: "Nvidia Optimus 310M / Intel HD Integrated Problem with 10.10"
date: 2010-11-24
forum: Hardware
---

### Post by zerosixx on 2010-11-24
I just installed 10.10 this morning from a live cd and the install went flawlessly, up until the driver manager suggested I install the driver for the Nvidia Card. I rebooted and ubuntu dropped down to the console area, unable to start X. I am semi new to the full ubuntu setup, coming from Redhat server side in 1998. In other words, I'm a complete noob. 

The laptop I am currently using is a Samsung qx410:
i5-460M 2.53, Nvidia 310M Hybrid optimus with Intel integrated gfx
4 gigs of ram

I need help researching this problem, as I have looked on google for about 2 hours now and come to these forums for only variant answers. Everything else on the laptop seems to be working fine. Touchpad, Wifi, kbd, ect. 

Any help (negative or positive) is greatly appreciated.

- zero

---

### Post by Roadmaster on 2010-12-22
Hi, it's been 3 weeks since your post, so hopefully you worked things out by now. This thread has some instructions on how to disable the nvidia driver on the QX410:

[http://ubuntuforums.org/showthread.php?t=1628673](http://ubuntuforums.org/showthread.php?t=1628673)

That is, until the drivers get updated and we can get this chipset to work.

---

### Post by Sudheesh on 2010-12-22
I had the same problem with my Toshiba satellite A665 laptop with ubuntu 10.10. I have Nvidia Geoforce 310M and Intel graphics.  I couldn't make the Nvidia work till now even after going through various forums.  Installing Nvidia ( official from Nvdia site, as well as via jockey ) always cause the laptop to end up in 'command line mode'.

Is there any solution to this?.  I saw this thread just now, and currently planning to disable Nvdia via jockey.  It is frustrating to see that we cannot use Nvidia driver in Ubuntu :-(

---

### Post by cascade9 on 2010-12-23
> **Sudheesh said:**
> I had the same problem with my Toshiba satellite A665 laptop with ubuntu 10.10. I have Nvidia Geoforce 310M and Intel graphics.  I couldn't make the Nvidia work till now even after going through various forums.  Installing Nvidia ( official from Nvdia site, as well as via jockey ) always cause the laptop to end up in 'command line mode'.

Is there any solution to this?.  I saw this thread just now, and currently planning to disable Nvdia via jockey.  It is frustrating to see that we cannot use Nvidia driver in Ubuntu :-(

Right now, and for the forseeable future, there will be no way to get optimus/switchable graphics working with linux. nVidia doesnt support optimus for linux (lame, nvidia).

---

### Post by Sudheesh on 2010-12-23
> **cascade9 said:**
> Right now, and for the forseeable future, there will be no way to get optimus/switchable graphics working with linux. nVidia doesnt support optimus for linux (lame, nvidia).

OK.  I don't need a switchable graphics in ubuntu.  Is there anyway to enable Nvidia drivers always?.  ie instead of Intel gra[hics I want to use nvidia always.

---

### Post by cascade9 on 2010-12-23
The only way I know of is if your BIOS allows you to force the nvidia GPU, or disable the intel video.

---

### Post by Sudheesh on 2010-12-23
> **cascade9 said:**
> The only way I know of is if your BIOS allows you to force the nvidia GPU, or disable the intel video.

Thanks for the reply . I do have a dual boot with windows7. If I change BIOS setting then the switching will not work even in Windows 7 also, making one of the key feature in my laptop useless  :-(.  Hence I prefer to keep the same settings.

Hope Nvidia will come up with this feature for Ubuntu soon.

---

### Post by cascade9 on 2010-12-23
nVidia isnt even working on it. :(

---

### Post by CDR Services on 2012-01-01
Been using 11.04 on my QX for a couple months it has a new expreimental nvidia driver that works but it reduces the battery time quite a bit so i have found the default intel driver works best!  the only other thing I havn't got working correctly is the scroll on the trackpad!

---

