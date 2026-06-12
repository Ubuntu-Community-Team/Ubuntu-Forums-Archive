---
title: "Completely new to kubuntu, help with installation!"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by nath2008uk on 2009-03-24
Yeah, i'm completely new to Ubuntu/Kubuntu (I have used ubuntu a tiny bit).

So, basically.
I downloaded the latest version of Kubuntu from the ubuntu site, Burned it to a DVD at 12x following the little guide on there (I was using windows then, about 4 hours ago).

I booted it up, pressed install on the menu (Didn't go into live desktop to test it), and pretty much just deleted all partitons, made one and got it to install.
Upon boot (And feel free to laugh at my noobiness), It gets stuck on one like of text reading something like:

Boot (Hd0,0) ext3 <Load of numbers>

And It just stays there, can't do anything.
I'm wondering, what I am supposed to do.
I went into the live desktop, and it froze after several seconds.
I'm stuck, and wondering what to do.

---

### Post by bubwitmaingay on 2009-03-25
Did it asked many questions during the installation? The usual installer will have 7 steps, the other have plenty (I don't count). If that is so, you must have downloaded the Alternative Install (the Server Version) of Kubuntu.

I think that a re-install would do the trick. I hope you did not erase your files when it installed last time. 8)

---

### Post by pbpersson on 2009-03-25
> **nath2008uk said:**
> 

I booted it up, pressed install on the menu (Didn't go into live desktop to test it), and pretty much just deleted all partitons, made one and got it to install.
Upon boot (And feel free to laugh at my noobiness), It gets stuck on one like of text reading something like:

Boot (Hd0,0) ext3 <Load of numbers>



Hmm....well, number one - I think when you boot that live CD you have an option to check it for errors - do that - if you continue to have problems - you find you cannot install with a GOOD CD - then you need to post all the details of your hardware - motherboard, graphics card, CPU,etc. - there might be some trick for your system - but that is a last resort.

Also, if you get stuck at the same point - what leads up to that?  That line you posted:
Boot (Hd0,0) ext3 <Load of numbers>
Looks to me like you are inside GRUB (the GRand Unified Bootloader) and it is confused on how to load your Ubuntu from disk

---

### Post by nath2008uk on 2009-03-25
I checked it with the live CD, no errors.

Sometimes it crashes after seconds in the live test, so I put it in Safe graphics mode, and it worked, little slow though, But note, I AM using a DVD-RW (lightscribe) External USB drive.

Basic Specs are:

512mb ATI Sapphire AGP Gpu (Don't know what model, but it's in the 1xxx series0

Single Core 3ghz P4 CPU
1x 512mb 333mhz Ram (Is running at 333)
160GB Sata 7200RPM Hdd.

My Pc is quite old, but it does run what I want perfectly, and that's great for me.

EDIT:

Yes, It is the grub loader.
It boots from the HDD, says 'press esc to load Grub menu' then counts down to 0 from 2, then just boots the default one.
I tried escape, I found somewhere to type grub, then enter Kernel=/boot/vmlinuz
but that didn't work, file not found. I tried kernel=/vmlinuz and it didn't say anything, just cleared it, so I assumed it had worked.
I tried it with the initrd file and go errors/crash, So I am thinking of reinstalling, but actually following a guide this time :lolflag:

---

