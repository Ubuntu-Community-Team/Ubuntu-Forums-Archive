---
title: "Gamecon module Trouble"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by Nekrataal on 2005-03-19
Hi, i have a problem with the gamecon module, when i try to load it it says no such device...i have the joysticks pluged in the pararell port, ive read something about it online, it seems to be a problem with the 2.6 kernels...i hope you solve here at ubuntu ;) \\:D/

---

### Post by Nekrataal on 2005-03-21
So...no one knows anything about it??

---

### Post by Nekrataal on 2005-03-25
Hey developers look at this please...

---

### Post by Nekrataal on 2005-03-31
Help??

---

### Post by lanhelp on 2006-07-23
"no such device" problem is solved with:
$ sudo modprobe joydev

but ubuntu kernels are freezing with gamecon, i'm on gentoo partition right now and here the module doesn't freezes.. Seens that nobody at developers and mantainers team are looking at this problem. :-k

---

### Post by RaymondQE on 2006-08-02
Hey guys, was just browsing through the kernel changelogs and noticed this entry for the 2.6.16 kernel:
```

commit c7fd018d75cae2b0c1cf03003b38f4c76e3df826
Author: Dmitry Torokhov <dtor_core@ameritech.net>
Date:   Sun Jan 29 21:52:04 2006 -0500

    Input: gamecon - fix crash when accessing device
    
    Signed-off-by: Dmitry Torokhov <dtor@mail.ru>
```

You may need to recompile your kernel if you want the Snes parallel port pad support.  If you don't mind potentially screwing up your system, you can follow the instructions to compile the kernel in this thread --> [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=custom+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=custom+kernel)

Note:  From the wiki page on custom kernel:

"Building and using a custom kernel will make it very difficult to get support for your system. You will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without explanation)."

---

### Post by rsay on 2006-10-16
I was having the same problem with the "device not found" issue using gamecon. I was attempting to get my parallel port cobalt flux DDR dance mat working without success. When I couldn't get gamecon working I tried using the ddrmat module. Luckily, in the readme file troubleshooting section they mentioned that if you were having problems to make sure that you didn't have the lp module loaded. Since ddrmat module is based on gamecon I thought maybe the troubleshooting would apply to both.  I checked /etc/modules and found that lp was indeed loaded. I removed lp from /etc/modules and then did:

rmmod lp
modprobe gamecon map=0,8

I then added the following two lines to /etc/modules to make things permanent:
joydev
gamecon map=0,8

I am now dancing away with no delay!!!:-D

---

### Post by plap on 2008-04-08
Cool! This works with psxpad in ubuntu too (a snes controller hooked to the parallel port).

I just editedt /etc/modules to:

```
fuse
rmmod lp
modprobe gamecon map=0,1,0,0,0,0
joydev
gamecon map=0,1,0,0,0,0
```

psxpad: [http://www.raphnet.net/electronique/snes_adaptor/snes_adaptor_en.php](http://www.raphnet.net/electronique/snes_adaptor/snes_adaptor_en.php)

---

