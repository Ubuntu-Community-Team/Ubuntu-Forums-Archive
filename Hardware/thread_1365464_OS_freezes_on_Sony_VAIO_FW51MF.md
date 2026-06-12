---
title: "OS freezes on Sony VAIO FW51MF"
date: 2009-12-27
forum: Hardware
---

### Post by Spinny P on 2009-12-27
Hi!

It seems this occurs when using the WiFi heavily, like moving large amount of files over the network or using the bittorrent network.

**Kernel**
Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

**Network**
Description: Wireless interface
Product: Wireless WiFi Link 5100
Vendor: Intel Corporation

Cheers

---

### Post by coffeecat on 2009-12-27
I'm using a different Vaio (VGN-NS20S) but which has the same Intel 5100 wireless chipset and I haven't had any freezing problems at all. Which means that there is unlikely to be an intrinsic problem with the Intel wireless and drivers.

A common cause of freezing is bad memory. If you haven't had freezing in Windows, this doesn't mean there isn't bad memory. Linux allocates memory differently from Windows and is more likely to access any area that is bad. But this brings up an interesting point. I've done a quick google and it seems that your model comes with 6GB RAM and Windows 7 64-bit. Is that correct? However, from your 'uname -a' output I see you are running the 32-bit version of Karmic. Which means that the kernel won't be able to see more than about 3.2GB of that RAM. Open System > Administration > System Monitor > System tab and you'll see that confirmed.

So - to test the memory, you could try running memtest for several hours? And/or what size memory modules are there making up the 6? Can you easily remove some to test each module in turn by running Ubuntu with your file transfers?

---

### Post by Spinny P on 2009-12-27
Thank you for your reply!

The computer is brand new but when the problems began the first I did was running a memory test. There does not seem to be any problem with my memory. The laptop work fine with Windows 7 and will run without problems as long as I dont use the wireless to move files over the network, but will freeze within a few minutes when I start downloading or moving files to my fileserver.

I know that I use the 32-bit and the 32bit only have access to part of the memory, It was recommended to use the 32-bit by Ubuntu if you did not need all of the memory, but there was no explanation why. I am running the 64 bit version of the Ubuntu on my stationary computer and have had some problems with things like flash support (in firefox) and other small things s o I tried the 32-bit as suggested by Ubuntu.

Two of the lamps in front of the keyboard start to blink when the computer freezes (caps-lock and the one to the right), if that can be of any help?

Should I install the 64 bit version instead?

---

### Post by coffeecat on 2009-12-27
> **Spinny P said:**
> The computer is brand new but when the problems began the first I did was running a memory test. There does not seem to be any problem with my memory.

I'm not saying that memory is the problem but, unfortunately you need to run memtest for >24 hours sometimes to detect a bad register. How long did you run it? How many passes? And I'd also be more suspicious of brand new memory than memory that had been working OK for some time.

> **Spinny P said:**
>  The laptop work fine with Windows 7 and will run without problems as long as I dont use the wireless to move files over the network, but will freeze within a few minutes when I start downloading or moving files to my fileserver.

Sorry - that's a bit ambiguous. It sounds as though you're saying that you get problems in Windows when moving stuff over the network.

> **Spinny P said:**
> It was recommended to use the 32-bit by Ubuntu if you did not need all of the memory, but there was no explanation why.

The only reason I can think of for running 32-bit now is the flash problems you mention. Even that should be surmountable.

> **Spinny P said:**
> Two of the lamps in front of the keyboard start to blink when the computer freezes (caps-lock and the one to the right), if that can be of any help?

The lamps on my Sony are in different places so I don't know.

> **Spinny P said:**
> Should I install the 64 bit version instead?

You could run the 64-bit version live from the CD and try moving stuff around the network, or downloading stuff, and see if you get the same problems. It would save doing an install.

Apart from that I've got no further suggestions.

---

### Post by Spinny P on 2009-12-27
Thank you for your reply!

I meant that when I am using windows it works fine, even if I move large amount of files. :)

I will switch to the 64 bit version instead, I miss the rest of the memory (development tools hog a lot of memory) even if 3Gb is enough. ;-) I will also start a new extensive memory test.

---

### Post by Spinny P on 2009-12-28
Re-installation seemed to work, have tried to throw everything against the 64 bit and it works flawlessly, has not crashed once since yesterday.

Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

---

