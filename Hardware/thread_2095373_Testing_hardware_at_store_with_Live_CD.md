---
title: "Testing hardware at store with Live CD"
date: 2012-12-16
forum: Hardware
---

### Post by starstreams on 2012-12-16
I was looking through the [*Laptop compatibility* thread]("http://ubuntuforums.org/showthread.php?t=1543006") (at the newer posts) but the success factor sounds like a hit or miss no matter how you look at it. New firmware chips and other things can very by manufacture and model over a period of time on laptops that were posted as successful.
[B]
Q[/B] Just curious, if I were to go into a store with a live CD to test a laptop using my distro of choice (lubuntu), If everything seems to work in the store, can I assume that all the hardware will work after a full install at home? In other words, is the live CD an accurate method of testing a computer at the store?

---

### Post by haqking on 2012-12-16
> **starstreams said:**
> I was looking in the compatibly thread on laptops but the success factor sounds like a hit or miss if, new firmware chips and other things can very by manufacture and model.
Just curious, if I were to go into a store with a live CD to test a laptop using my distro of choice (lubuntu), If everything seems to work in the store, can I assume that all the hardware with work are a full install once I get it home? In other words, is the live CD an accurate method of testing a computer at the store?

It will give you an idea, not a completely accurate assessment though.

However I would say that it was extremely unlikely a store will let you, would you allow a stranger to come along and insert a disk into your computer ?

There are a ton of reasons not to allow that especially on hardware for sale.

But I guess it will be down to the store. YMMV

Peace

---

### Post by ahallubuntu on 2012-12-16
I have done this a few times.  (Most recently at Costco in the US.)  Really depends on the store and who works there.  If you go when it's not busy, maybe you'll find someone working there who is as techy as you are and will let you boot it.

You might have better luck with a bootable USB flash drive instead of a CD drive.  It should boot a lot faster, plus it seems less intrusive (even if it isn't).

Stores like Best Buy no longer have restocking fees as I understand it (ask).  Costco sure doesn't.  Explain when buying it that you'd prefer to try Linux before buying it rather than take it home, rip it out of the box, find out it doesn't support Linux, then bring it back and leave them with an open-box computer.

---

### Post by starstreams on 2012-12-16
> **haqking said:**
> It will give you an idea, not a completely accurate assessment though.
However I would say that it was extremely unlikely a store will let you, would you allow a stranger to come along and insert a disk into your computer ?
There are a ton of reasons not to allow that especially on hardware for sale.
But I guess it will be down to the store. YMMV
Peace


> **ahallubuntu said:**
> I have done this a few times. (Most recently at Costco in the US.) Really depends on the store and who works there. If you go when it's not busy, maybe you'll find someone working there who is as techy as you are and will let you boot it.
You might have better luck with a bootable USB flash drive instead of a CD drive. It should boot a lot faster, plus it seems less intrusive (even if it isn't).
Stores like Best Buy no longer have restocking fees as I understand it (ask). Costco sure doesn't. Explain when buying it that you'd prefer to try Linux before buying it rather than take it home, rip it out of the box, find out it doesn't support Linux, then bring it back and leave them with an open-box computer.



Some how we're getting into the discussion of whether or not the store allows it. 
I'm asking if the Live CD is an accurate indicator that a "full install" will work once home? Although I do realise that some updates after a full install can break things.
**@** *ahallubuntu*, you said you've done this a few times. Did it workout for you? That's what I'm asking? Did the full installation at home have the same results as what you seen from the live CD? Did everything that worked at the store work at home?

On an unrelated note:
It would be nice if a few stores had a few popular linux distro live CDs  for customers who want that options. And I don't see why they couldn't just  ID someone ahead of time. It's a shame that we live in a world were most  the mainstream stores are slaves to Microsoft and Apple. It's so close to  a Monopoly.

---

### Post by ahallubuntu on 2012-12-16
> **starstreams said:**
> 
I'm not asking about the rules of the store's, and I'm asking if the Live CD is an accurate indicator that the full install will work in the same way as the live CD.

Should be a fairly accurate indicator, but I have seen cases of things not working after an install after they worked in the live CD.

If you want to eliminate that possibility, do a full install on a USB stick.  I have done it many times though not yet with 12.04 or 12.10.  An 8GB USB flash drive is big enough for a basic install of Ubuntu.  (I am not talking about a "live CD with persistence," I'm taking about a real installation when the USB drive is treated like a hard drive.)  Then you can boot it on any computer and see how the hardware works.   (Note that if you boot this on a store demo computer, one side effect is that it may set the clock ahead so be prepared to correct them after Windows is rebooted, to be nice!)

While in theory you can wear out a flash drive pretty quickly when using it as a hard drive, in practice it hasn't happened to me, and 8GB flash drives are now easy to find for under $10 USD.   Almost disposable but very handy for things like testing and debugging!

---

### Post by malspa on 2012-12-16
You should be able to get a pretty good idea of how well the distro will work with the hardware from a live session. But what if the BIOS isn't set to boot from a disk or flash drive? Might have some trouble getting them to allow you to change that.

---

### Post by ahallubuntu on 2012-12-16
> **malspa said:**
> You should be able to get a pretty good idea of how well the distro will work with the hardware from a live session. But what if the BIOS isn't set to boot from a disk or flash drive? Might have some trouble getting them to allow you to change that.

Many modern computers will let you bring up a boot menu after POST, without the need to enter BIOS setup.  The trick is, which key brings up the boot menu?  (Also, not always enabled in BIOS.)  The "boot menu" key is not standard.  On a Dell, F12 is pretty standard for a boot menu, though.  On other manufacturers' computers it's F11 or even F8.

---

### Post by haqking on 2012-12-16
> **starstreams said:**
> Some how we're getting into the discussion of whether or not the store allows it. 
I'm asking if the Live CD is an accurate indicator that a "full install" will work once home? 


To which i answered you, i then offered an opinion which may or may not be correct, I wouldnt say we are having a discussion about it, go to a store and try.

---

### Post by starstreams on 2012-12-16
Interesting ahallubuntu, I wasn't sure if there was a difference testing a system with a live CD vers a full install. As you pointed out, It seems there obviously is. Good advices on installing the full OS to the USB. I've got tons of them. The only question is, how does the full install on a USB stick differ from the live CD? I mean either way, if you install a full version of the OS at home, the OS still has to detect the hardware when you plug it in at the store. What's different about the full install?
I'm in the market for a cheap laptop to bring to work. 

Another concern I'm little worried about is, the newer Unified Extensible Firmware Interface (UEFI) firmware. I just hope the manufactures don't start making these things proprietary in that if you buy a Microsoft only system they're lock out any option to install Linux.

@ haqking

Sorry, my mistake.

---

