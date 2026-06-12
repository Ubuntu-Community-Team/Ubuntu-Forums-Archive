---
title: "Ubuntu 9.04 x64 or x32?"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by bloeper on 2009-05-15
Hi all,

I'm planning to install the new Ubuntu (9.04), although I'm in doubt which version i shall install the x32 or x64.

I have a dual-core processor with 8gb of ram. I know i need x64 to support all my ram. But how is the support with 32-bit applications in a 64-bit environment?

I would like to know some of your experience with it, so i can choose my "perfect" install.

Greetings,

Tom

---

### Post by marshall.robert on 2009-05-15
64 bit should be fine.

There is almost always a 64 bit version of your apps in the repos and I am pretty sure 32 bit apps should work.

---

### Post by bloeper on 2009-05-15
Well thats a bit of a burden to me.. 
I rather think 32-bit apps should work to.. 
Although I'm not sure.. And that's something i want to be, before putting a 64-bit OS on my computer.

---

### Post by overdrank on 2009-05-15
> **bloeper said:**
> Well thats a bit of a burden to me.. 
I rather think 32-bit apps should work to.. 
Although I'm not sure.. And that's something i want to be, before putting a 64-bit OS on my computer.

Hi and this quote is from [32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit")
> How to make 32-bit work on a 64-bit machine

It is possible to install and use 32-bit software on a 64-bit computer in different ways:

    * Installation of 32-bit compatibility libraries (ia32-libs)
    *

      A 32-bit chroot
    *

      Full virtualization through KVM or VirtualBox 

Applications found in the Ubuntu archives will however all work out of the box in 64-bit mode.

Happy 64-bitting! 

---

### Post by bloeper on 2009-05-15
Thanks for the reply :)
If it is possible to install x32 library's and thus possible to install x32 applications from scratch there's nothing to lose :)

* Starts back-upping all old stuff, so i can start a fresh install *

---

### Post by HavocXphere on 2009-05-15
I've got x64 installed...

It's all completely transparent anyway and I doubt you'll notice anything different.

e.g. firefox is still 32bit afaik and its not causing issues.

The only thing I'm not sure about is WINE...I think there may be some x64 issues lurking there.

[QUOTE=wikipedia]As of Firefox 3.0, Mozilla does not have any official 64-bit builds available. Although unofficial third-party builds exists for Windows[87] and unofficial "nightly builds" (referred to as Minefield) exists for Linux[88][/QUOTE]

---

### Post by bloeper on 2009-05-15
> **HavocXphere said:**
> The only thing I'm not sure about is WINE...I think there may be some x64 issues lurking there.

Why do you think there may be lurking some issues in Wine? 
It's not that i use it allot, but when i do i hope it works :P

---

### Post by aikiwolfie on 2009-05-16
64-bit Ubuntu 9.04 has proven to be very unstable for me. It's applications are crashinf far too often. It's worse than Windows.

I'm going to install the 32-bit version. Not exactly sure how to get 8GB RAM support for that but I know it can be done.

---

### Post by prgsdw on 2009-05-16
You can use the server kernel to access all 8 gb of RAM in a 32 bit kernel, but read up on it before you decide to try it. 

OP: Why not just try the 64 bit version? Install it (which will only take a few minutes) kick the tires before spending time with putting all your data back down and if you have no issues you are golden. I've been using 64 bit versions for a while with no issues that I was not able to quickly resolve.

---

### Post by HavocXphere on 2009-05-16
> **bloeper said:**
> Why do you think there may be lurking some issues in Wine?
I read about some issue involving Wine + x64 + a driver (ATI or nVidia, can't remember). It's a bit of a fragment of a memory, which is why I phrased it in very generic terms above.

Also, I ran into my first x64 issue yesterday: OpenOffice 3.1 32bit edition refuses to install on an x64 install. (I grabbed the .debs off the uni WAN). I guess I'll have to download the x64 version of OO.

---

### Post by durand on 2009-05-16
Been using x64 for about 2 months now, no problems. Everything is completely transparent and you don't need to chroot or anything.

---

### Post by bloeper on 2009-05-19
I have installed Ubuntu 9.04 X64, so far so good..
Most programs i could get to work.
so most of the burden is gone.
Although i need to compile some stuff and i need to look how that will work out.
I don't know if that al goes well, but i have the feeling it's gonna turn out just alright.

Thanks for all the reply's and information!

---

### Post by 3rdalbum on 2009-05-19
I'm using x86_64, no appreciable problems. There are absolutely no problems if you stick to repository software or take care with what you install (64-bit .debs/binary installers, 32-bit binary installers or source code).

---

### Post by aikiwolfie on 2009-05-19
Think I've figured out what's causing my problems. It could be BOINC. A lot of the apps it's running are ending with "computational errors".

---

