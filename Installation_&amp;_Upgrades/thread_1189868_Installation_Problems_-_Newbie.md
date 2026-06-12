---
title: "Installation Problems - Newbie"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by daveH3009 on 2009-06-17
Hi People

First time user of Ubuntu, had it recommended after I lost everything on my Asus netbook.  Here is what I have done so far, please excuse my newness to all this.

Netbook - Asus eee 4Gb 701
New OS - Ubuntu 9.04 for Netbook, freshly downloaded.
Installing the OS to an SD card using a windoze powered laptop.

Install instructions state the need for 1Gb min physical memory.  I have a 1Gb SD card.  Attempted to follow instructions for Graphical Interface and am told I do not have enough space.  Odd considering it is a freshly formatted SD Card.

So attempted install using command line instructions.  Told access is denied (the card isn't locked or anything).

Figured this must be pushing the limits of my pokey 1Gb card so I go out and buy a 4Gb SD card (I enjoy photography so it'll get used).  Attempt both methods with a similar outcome.

Is this normal, did I do something wrong somewhere.  Is there anything else I should try, I could go buy a 2/4Gb USB stick but I'd rather not if I can avoid it.

Thanks for any help and pointers.

Regards


Dave

---

### Post by madverb on 2009-06-17
What exactly are you trying to do?
Are you trying to install Ubuntu on an SD card from within Windows on another PC? That won't work.
What instructions are you following?
You could boot into a Ubuntu Live CD and run the USB Startup Disk Creator and install Ubuntu onto the SD card that way. I'm pretty sure that would work.

---

### Post by Harpie Queen on 2009-06-17
I'm having a bit of trouble understanding what you are asking, but go to download ubuntu, it will give you instructions on how to burn it a disk, which you can boot the computer off. I think you simply want to boot it and grab stuff from your hard drive? In that case boot ubuntu from the disk, go to system-administration-usb startup disk creator (I've never done that, but it seems pretty self explanatory), boot off the usb and install a nfts driver (search for that on the forums), and you should be able to get to your stuff. If you want to install ubuntu to the hard drive, when you put the disk in simply select to install.

---

### Post by daveH3009 on 2009-06-17
Instructions I was folloing are here

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

It didn't say anything about not being able to do this from windows and includes windows installation guide.

I have the latest ubuntu downloaded.  I want to write the image to an SD card to use in another machine.

---

### Post by Neobuntu on 2009-06-17
I think you meant 1Gb storage space recommended, not "memory"(RAM). 

#1 Installing Windows is likely already done for you AND it's matched and enhanced for the device set, per computer. If you have done or did a XP install totday, you would note that it's more trouble.

#2 That said, it takes a lot of patients and learning to "wrap" Ubuntu around ALL your devices. Most of them are automatic. Sometimes all of them. Some times, extra procedures must be done and in a patient and logical manner. Google is your friend. Mainly the Ubuntu forums (24/7). Usually, this is because of law suit threats and due to non-free crap. They (the abusive monopolists) could never win the suit but the fight would waste money. This is why a distribution as large as Ubuntu doesn't already have things like Flash and Java already done for you. It's not that hard to add them though. It's just frustrating that the best manner, to install them, slightly changes; per Ubuntu release. Just be sure, you CAN obtain complete functionality, even with the so called "non-free" add-on stuff. It's a game we are forced to play. It will get much better, if Ubuntu can become more accepted and by non-technical users. It's a chicken or the egg first, thing.

My experience has been, stability comes about 3 months after a new release. DO NOT attempt a new release until three months AFTER it is official. Do (easy) upgrades without fail, but ONLY in the release. Do a clean install of a new release + 3 months; NOT a distribution upgrade. Not if you want production stability. You can do anything to test. Just don't expect strong stability from any brand new OS. It's just too much; massive code.

I must recommend that newbies do both XP and Ubuntu. I prefer Kubuntu but the KDE 4 thing, is in process. Unfortunately, a dual boot setup requires a wee bit of expertise. Such as an understanding of partitions. Because an automatic dual boot setup (for newbies) depends on the release CD, I find it best to burn a separate "Gparted CD" and use it to re-size Windows partitions and simply leave the last 50% of the drive blank, for a new distributions auto installer. Let it write to the "MBR". You can then select between Windows or Ubuntu after you turn on your computer.

This way, you can experience the best of both worlds (and the worse) and naively (full featured OS, not emulated). Most people flip-flop back and forth between XP and (K)Ubuntu. Over time (and only over time) can you see the real and current pros and cons, and how they differ.

ALWAYS, backup whatever you can't live without FIRST; on TWO different drives.

Developers should understand that XP is the "competition" because about 60% of all computer users are on it AND they had almost 8 years to patch the thing up. Vista and Win 7 is NOT the "competition" YET! XP (tweaked) is. This is why I vote for a stability push, with (K)Ubuntu; in EVERY release.

They say you can always hang back; in any (*)Ubuntu release and one does not have to skip to the new release (for years). That's very true and great for businesses. But the reality is, if you use it for multiple tasks, you may get (your app and the function you need) left behind. Another (MAIN) reason that I think we need to understand that XP is the "competition". 

In other words, we need all the benefits that XP has, plus much better ones. That's the only way to get more(%) and non-technical users. The underlying core doesn't matter, to the user. Even with Windows gaping security holes. They don't care!

Also, see:
[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by daveH3009 on 2009-06-17
Thanks neobuntu.

Actually I don't plan to use Ubuntu on my Windows Machine.

I want to use my Windows machine to install Ubuntu onto a flash card so I can install Ubuntu on the Asus eeepc my son uses, instead of the bundles of stuff Asus packed it with.

---

### Post by madverb on 2009-06-20
I figured that is what you wanted to do and my instructions will do that for you. You basically want to turn you memory card into a Ubuntu Live CD.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

