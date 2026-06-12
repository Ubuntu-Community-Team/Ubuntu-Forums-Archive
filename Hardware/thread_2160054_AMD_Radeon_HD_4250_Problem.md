---
title: "AMD Radeon HD 4250 Problem"
date: 2013-07-05
forum: Hardware
---

### Post by MintyFresh12 on 2013-07-05
i cant get my amd graphics card to installed i have tried copy and pasting command line links that i have  seen in here but it works untill you get to that last command then it refuses to work even though i did the commands in order. i even did the 64-bit fix cause i have a 64bit machine i even tried the noobs labs way of doin it  it keeps with the annoying text box saying i have to install one or more tools for it to work and the thread i found here had the command line fixes for that to install them but it still wont work here is what i have on my machine

Ubuntu 13.04 64 bit
AMD radeon hd 4250 graphics card
AMD Athlon(tm) II P360 Dual-Core Processor × 2 


so if anyone can help me get the graphics driver to work properly and install that would be greatly appreciated i really want to use ubuntu beacuse i love it...everything else i got to work just having issues with that so if anyone can help i would very greatly appreciate it ^_^

---

### Post by Bashing-om on 2013-07-05
MintyFresh12; Hi !

edit: Just to add .. Welcome to the forum !

Seems ATI (AMD) pulled the rug out from under us>

> IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

Which means the only recourse is open source drivers; which for the most part work very well.

[INDENT][INDENT]ours' is not to ask why[/INDENT][/INDENT]

---

### Post by edb66083 on 2013-07-05
If you uninstall any proprietary AMD drivers, and let ubuntu boot up, it should use the open source radeon driver.

I was having other problems, in that ubuntu would use the radeon driver, but I would get terrible screen tearing to the point where it was unusable. I finally had to flash a modified BIOS with options to use only UMA rather than 'UMA + sideporting', and that got rid of my tearing problem. It is still using the radeon driver, though, without any issues. I have a RS690M graphics card, btw.

---

### Post by edb66083 on 2013-07-05
Sorry, duplicate post.

---

### Post by MintyFresh12 on 2013-07-05
that is wierd because in windows which is where i came over form because windows just didnt like my laptop they had teh 13.4 beta driver for my card and that worked very well....i am basically a first time hardcore ubuntu user in the past i have just done basic things via live usb but i decided to chunk windows and switch to ubuntu i am still learning the puzzling world of ubuntu....i assume since it wont install the radeon driver that it is already using the legacy or open source one mention in edb's reply but the wierd thing is in cylon linux which is based off of ubuntu 12.04 which is where they pulled the plug it finds my graphics driver straight away in the addional drivers section and it installs something idk what but it installs something and then it says i have my amd card installed i guess....idk ubuntu is confusing but im gonna learn it if it kills me lol

---

### Post by edb66083 on 2013-07-05
MintyFresh12, what is the output of this command?

```
lspci -nnk | grep -i vga -A3
```

---

### Post by MintyFresh12 on 2013-07-05
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1697]
    Kernel driver in use: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]


that is what it said when i copied and pasted it

---

### Post by edb66083 on 2013-07-05
> Kernel driver in use: radeon

Your computer is seeing your ATI RS880M GPU, and it is using the open source radeon driver. So your card appears to be working fine.

---

### Post by Mark Phelps on 2013-07-06
> in cylon linux which is based off of ubuntu 12.04 which is where they pulled the plug it finds my graphics driver straight away in the addional drivers section and it installs something

That's because 12.04.1 DID support the AMD restricted driver.  AMD dropped support for that driver for Ubuntu versions starting with 12.04.2.

---

### Post by Bashing-om on 2013-07-07
MintyFresh12; Hey !

There appears to be another option recently available to use the older ATI cards; check out:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
This repository provides AMD Catalyst Lagacy 13.1 (fglrx 8.97.100.7) drivers for Radeon HD 2xxx - 4xxx 

I only know presently that 3 people have reported happiness !
Edit:Not a "good" solution. Requires operation system awareness and future repercussions. See Mark Phelps' commentary.

[INDENT][INDENT]good things do happen[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-07-08
> There appears to be another option recently available to use the older ATI cards; check out:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Unfortunately, this links seems to be popping up in every thread where folks want to get AMD restricted drivers working with their HD 2x/3x/4x-series chipsets.

Problem is that folks don't read through the thread to notice that it requires downgrading your X-server to an older version.

This is trading short-term gains resulting from AMD driver installation to long-term risks of system corruption due to messing around with the X-server.

This option has actually been around for some time -- and I've been advising AGAINST it all that time -- it's just that this thread now exposes this approach to a wider audience.

---

### Post by Bashing-om on 2013-07-08
@ Mark Phelps ;

Thanks for the correction !
I am going back to my threads and altering those recommends.

[INDENT][INDENT]my high regards[/INDENT][/INDENT]

---

