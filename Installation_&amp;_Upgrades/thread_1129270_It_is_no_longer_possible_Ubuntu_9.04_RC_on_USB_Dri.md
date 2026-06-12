---
title: "It is no longer possible Ubuntu 9.04 RC on USB Drive !!!"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by ilgiga on 2009-04-18
Sorry for my scholastic english, but I suppose this is a very important and very urgent question.
I was able to create a bootable Ubuntu Pen Drive with 8.04, 8.10 and also 9.04 beta. Today I tried 9.04 RC on USB Pen Drive, but ... It doesn't work !!! Tried on three different personal computer :-( ReDownloaded the ISO file and remastered ... NOTHING !!! :(
The possibility to put the new ISO on a USB Drive is so important with this release, cause of the enormous diffusion of NetBook without optical drive !!!
I'm not so expert in Linux and Ubuntu, so now can someone verify this probably enormous BUG before the final ISO ???
**With 9.04 RC the USB Pen boots correctly, than you can choose the language ... BUT, if you choose "Try Ubuntu" or "Install Ubuntu" in both cases in a few seconds a sort of shell appears and STOP !!! Tried on three PC, a NetBook and a Notebook, pen drie made 4 times, ISO redownloaded 2 times (ISO is OK from CD)**
Thank you so much for you help: this is not only a personal question, but a sort of alarm for the Ubuntu Gurus :-)
Have a nice week-end :popcorn:
Willy from Italy ;)

---

### Post by scottuss on 2009-04-18
I've got the exact same problem, I'm looking around Google and trawling through the forum to find some info. I'll post back here if I find anything.

---

### Post by lxskllr on 2009-04-18
It worked for me setting it up in Windows. I don't know about doing it in Linux.

---

### Post by scottuss on 2009-04-18
> **lxskllr said:**
> It worked for me setting it up in Windows. I don't know about doing it in Linux.

You used unetbootin then, I assume?

---

### Post by lxskllr on 2009-04-18
> **scottuss said:**
> You used unetbootin then, I assume?

Yup, that's right :^)

---

### Post by antsh86 on 2009-04-18
I'm having the same exact issue with trying to boot into kubunutu 9.04 off a usb stick! Used the usb boot disk creator in ubuntu to create it.

---

### Post by charleykay on 2009-04-19
> **ilgiga said:**
> With 9.04 RC the USB Pen boots correctly, than you can choose the language ... BUT, if you choose "Try Ubuntu" or "Install Ubuntu" in both cases in a few seconds a sort of shell appears and STOP !!! 

Do you see "initramfs" displayed? If yes try typing "exit" (without the quotes) and press enter. Repeat this several times if necessary until boot resumes.

If you want to use the Live USB drive facility (Try Ubuntu with no changes to your computer) it appears to be broken in 9.04RC, it runs OK but changes do not persist on the USB drive from one boot to the next as they should.

---

### Post by wirechief on 2009-04-19
This sounds similar to [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/363038](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/363038)

It is supposedly fixed, however I have yet to make it work normally, only
using F6 and removing the persistence worked. usb-casper 1.0.16 is out
I am waiting until the final is released and all my packages have been updated. Supposedly the casper package 1.73 is the fix. I updated this am and still not seeing it work ....the bug 363038 makes an interesting read though.
using exit has not worked for me, once i used rootdelay=90 and it worked but not recently.

---

