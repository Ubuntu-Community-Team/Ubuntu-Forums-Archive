---
title: "Ubuntu + MS-Vista on notebook PC (pre-emptive) ?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by Beowulf.1000 on 2008-01-03
I just got a new Acer Aspire notebook PC and it has one hard drive in it that came already formatted as two partitions. One partition with MS_Vista (sigh) and the other partition is simple marked as a Data partition. I would like to put Ubuntu Linux on that data (second) partition, and of course use Grub as the bootloader that would end up on the first partition.

**My concern** is some horror stories I have read about Vista overwriting Grub and really messing up a system so that nothing boots. :mad:  Any pre-emptive advice on what I should do? I would even consider wiping Vista off the notebook and putting MS-Windows XP on it, alongside Ubuntu. But of course if Vista will play nice with Ubuntu I would like to go that route, as I have never used Vista and I assume Vista is needed along with the proprietary Acer software that runs the wifi and webcam built into the system. But that said, if Vista is going to constantly trash Grub then Vista would have to go, I could live without the webcam as long as WinXP would run the DVD drive, wifi, touchpad, mouse, ethernet.  Thoughts on what I should do, whether Vista plays nice with Grub, other? :confused:

---

### Post by Paul Moir on 2008-01-03
I would definitely have a CD with "supergrub" on it so you can quickly and easily fix grub if it goes bad.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

By the way, none of grub would really be on the first partition.  Part is on your linux drive but the other part (the part that gets wiped out) is in a special area before the first partition.  So when you get sick of Vista and format the first partition, grub won't get wiped out.  :)

---

### Post by mathnerd314 on 2008-01-03
> **Beowulf.1000 said:**
> I just got a new Acer Aspire notebook PC and it has one hard drive in it that came already formatted as two partitions. One partition with MS_Vista (sigh) and the other partition is simple marked as a Data partition. I would like to put Ubuntu Linux on that data (second) partition, and of course use Grub as the bootloader that would end up on the first partition.

**My concern** is some horror stories I have read about Vista overwriting Grub and really messing up a system so that nothing boots. :mad:  Any pre-emptive advice on what I should do? I would even consider wiping Vista off the notebook and putting MS-Windows XP on it, alongside Ubuntu. But of course if Vista will play nice with Ubuntu I would like to go that route, as I have never used Vista and I assume Vista is needed along with the proprietary Acer software that runs the wifi and webcam built into the system. But that said, if Vista is going to constantly trash Grub then Vista would have to go, I could live without the webcam as long as WinXP would run the DVD drive, wifi, touchpad, mouse, ethernet.  Thoughts on what I should do, whether Vista plays nice with Grub, other? :confused:

I have the same configuration. I just deleted the "Data" partition using Windows' drive manager, so I was left with unallocated space. Then I had the LiveCD install to the largest contiguous unallocated space", leaving the Vista partition alone.

Not sure if that's what you're asking.

---

### Post by Beowulf.1000 on 2008-01-03
I have put linux and grub, dual boot with WinXP, on many PCs, and also a few laptops, but never alongside a notebook laptop that has MS-Vista on it. I am concerned that Vista will trash Grub,  based on some preliminary googling on the matter. So my real concern is can grub and vista play nice, or would vista need to get wiped off the drive (which raises other problems, like voiding the warranty, so that i might want to get a new internal drive and swap out the original so the original can be put in when it needs to go back to Acer (I am already upset at Acer-- I bought this notebook just two weeks ago, the day I got it it had two dead (red) pixels-- so I returned it for repair, got it back today with NOTHING fixed--they will not repair anything under 5 dead pixels. Acer has lost my vote for any future purchases.).

Also, perhaps better for a separate thread, Ubuntu 7.10 live CD does not give me any audio on the notebook-- it looks like audio is playing but nothing is heard. I turned up the volume with the volume wheel on the side of the notebook, nothing. I went into Preferences->Sound and tried all possible devices and mixers and sound tests and it appears to be playing sound but still no audio is heard. That would really really not be good if I installed Ubuntu and could not hear any audio--what do you give my chances of getting audio if I install Ubuntu to a partition on this notebook?

Actually I just did some searching here on the forums and it looks like my Acer Aspire 5520 (AMD Turion 64 x2) might work better with the Ubuntu 7.10 AMD 64 live CD so I am going to download and burn that and give that a try to see if I get audio.


> **mathnerd314 said:**
> I have the same configuration. I just deleted the "Data" partition using Windows' drive manager, so I was left with unallocated space. Then I had the LiveCD install to the largest contiguous unallocated space", leaving the Vista partition alone. Not sure if that's what you're asking.

---

### Post by mathnerd314 on 2008-01-03
Dual booting Vista and Ubuntu 7.10 using GRUB works fine for me.

If you're not getting audio, it might be because the audio is going to the wrong channel. For example, I had to change the channel from "Front" to "Surround" on my laptop.

And i don't know anything about AMD64.

---

### Post by Daelyn on 2008-01-03
> **mathnerd314 said:**
> Dual booting Vista and Ubuntu 7.10 using GRUB works fine for me.

If you're not getting audio, it might be because the audio is going to the wrong channel. For example, I had to change the channel from "Front" to "Surround" on my laptop.

And i don't know anything about AMD64.

Same here. Had no problem what so ever with GRUB.

But, well, who cares these days. 
Windows is forever gone from all computers under my wings :)

---

### Post by Beowulf.1000 on 2008-01-04
I will give that a try (the channel).  I just tried a boot with live Ubuntu 64 7.10 and it did not go well--I could not get to a working desktop stage, I am going to have to go back to trying the regular 386 Ubuntu 7.10 and see if I can get audio.

> **Daelyn said:**
> Same here. Had no problem what so ever with GRUB. But, well, who cares these days. Windows is forever gone from all computers under my wings :)

---

### Post by Beowulf.1000 on 2008-01-04
Sigh, no audio. I am going to start a new thread on the audio issue, if I can get that solved I will keep this notebook, but without audio I think I must consider selling it on ebay.

> **Beowulf.1000 said:**
> I will give that a try (the channel).  I just tried a boot with live Ubuntu 64 7.10 and it did not go well--I could not get to a working desktop stage, I am going to have to go back to trying the regular 386 Ubuntu 7.10 and see if I can get audio.

---

