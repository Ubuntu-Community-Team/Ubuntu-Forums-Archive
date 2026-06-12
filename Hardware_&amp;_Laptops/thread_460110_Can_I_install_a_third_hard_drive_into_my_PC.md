---
title: "Can I install a third hard drive into my PC"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by the lemming on 2007-05-31
My PC has two internal drives and two DVD readers.

A mate of mine told me that I could remove one of my DVD reader drives and replace it with an Internal Hard drive.  Is this possible and if it is possible is it a simple process of swapping stuff or not?

Cheers

---

### Post by tehBoris on 2007-05-31
Should be very simple. The only thing to watch out for is that some older motherboards only allow hard drives on the primary IDE chain and CD/DVD drives in the secondary chain.

As far as Ubuntu is concerned it should see the new drive. It will appear in /dev/. You'll need to partition and format the drive your self and add it's entrie in fstab manually though.

---

### Post by the lemming on 2007-05-31
> **tehBoris said:**
> As far as Ubuntu is concerned it should see the new drive. It will appear in /dev/. You'll need to partition and format the drive your self and add it's entrie in fstab manually though.


I understood the first bit but the second part of your posting went way over my head.  Would it be possible for you to give a not technical explenation?

I'm from a windows environment and anything beyond pressing the On Switch and swapping a few cables is beyond the scope of my knowledge.

Cheers

---

### Post by tehBoris on 2007-05-31
> **the lemming said:**
> 
I'm from a windows environment and anything beyond pressing the On Switch and swapping a few cables is beyond the scope of my knowledge.


I like how you reinforce the stereotypical windows user persona ;)

Well (for all intents and purposes) all hardware devices appear /dev in some shape or form. Hard drives (for example) start with the prefix hd and then they are lettered a, b, c and d. So the first hard drive your computer knows is there will be located at /dev/hda and then each partition on the drive is numbered (starting at 1). So the first partition of the first hard drive will be located at /dev/hda1. you can't access it directly though, you have to mount the partition using a known file system. 

I could go on... it's not that complicated once you understand it :P Which version of Ubuntu are you using? I know Qtparted is able to help you set this up though a GUI (Qtparted is targeted at KDE).

---

### Post by the lemming on 2007-05-31
> **tehBoris said:**
> 
I could go on... it's not that complicated once you understand it :P Which version of Ubuntu are you using? I know Qtparted is able to help you set this up though a GUI (Qtparted is targeted at KDE).

I'm using ubuntu 7.4 gnome

However I do like PCLinux OS and it is a toss up between which one I keep on my PC.  Seeing as I've managed to get ubuntu to work I will keep it for a month or so before I finally decide.  :-)

---

