---
title: "Dell Inspiron 1501 won't load from CD"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by toodumbtorefine on 2007-01-09
Hoping you helpful folks can bail me out here...

I am relatively new to Ubuntu and linux in general and this particular problem has me a little perplexed...

I've recently purchased a Dell Inspiron 1501 laptop and am having immense difficulties installing or indeed running the live CD of 6.06 LTS on it.

The spec is: AMD Turion 64 X2 TL-50
                 1024MB (2 x 512) 533MHz DDR2
                 ATI Xpress 1150

Upon running the live CD, I get presented with the standard menu (start/install , safe graphics , check CD etc. ), but this is as far as I can get. Taking any of the first three options throws up the same error.

The liveCD/installer gets to the stage of booting the kernel, then seems to panic and presents with an error stating "MP-Bios bug 8254 timer not connected to IO-APIC". After this, the screen goes black and nothing seems able to elicit a response. I left it running for an hour or so, just in case there was some kind of ridiculously long timeout in the bootup but still no dice. 

Initially I thought it was maybe an issue with the graphics card (ATI Xpress 1150), but upon searching around, I'm now thinking it's a problem with the ACPI implementation in the BIOS (Dell revision 1.7.0 I think).  I've heard that the Dell BIOS for Turion X2 processors can be buggy as hell... 

Dell Support's position was that they don't support Linux on their machines and to contact my software provider... This is, as far as I can tell, the latest revision of the BIOS (12th December).

Any ideas you folks have for sorting this would be much appreciated.

---

### Post by redDEADresolve on 2007-01-09
to get it to install, read the thread 
add pci=nomsi to the kernel's boot sequence follow advice 
[http://ubuntuforums.org/showthread.php?t=299929&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=299929&highlight=dell+1501)

to get wifi
[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501)

My advice install, connect via ethernet. get updates then work on wifi then start customizing and adding programs

the wifi can be a pain to install

PM if you have questions

---

### Post by toodumbtorefine on 2007-01-10
Cheers for that...

Sorry, I should have mentioned that I've tried all the different boot parameters, 'pci=nomsi', 'irqpoll' etc. and still no luck!

This is with the LTS Dapper install though, I'm currently downloading an Edgy ISO, to see if that maybe works with these params...

Cheers again,

Dougie

---

### Post by redDEADresolve on 2007-01-12
I wrote a visual guide on my blogg about getting Ubuntu on the Dell 1501
Check it out for all things 1501 and Ubuntu

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

### Post by grzechowski on 2007-01-26
Thank's so much for this blog!! :-)
It's great!!

:-) Pozdrawiam!

---

### Post by RotoGrip on 2007-01-28
Trying to install Ubuntu 6.06 on my 1501 trying the pci=nomsi. Then i get an error message saying "unknown option nomsi". Then to a blank screen where it does nothing after that. I tried the how-to off of RedDeadResolve's blog. But it's not happining.

---

### Post by Ronirvol on 2007-01-28
6.06 wouldn't take the pci=nomsi on my Dell 1501 with AMD, however it seemed to work with 6.10.   I can run the live CD with 6.10, but I can't do the install because I can't figure out how to do the partition.  If you can do that, please let me know.

---

### Post by Ronirvol on 2007-01-29
Cobikegeek answered my question on another thread.  If you create an extended partition, you can create the ext3 and swap inside of it.  I did this and completed the install without deleting any pre-existing partitions.

---

### Post by jaka on 2007-02-01
I tray to run kubuntu 6.06 live cd they wont load. I tray acpi=force irqpoll and andpci=nomsi. I have hd from samsung.

---

### Post by slybob on 2007-02-19
I  take it it's the sata hard drive causing the problems then?

---

