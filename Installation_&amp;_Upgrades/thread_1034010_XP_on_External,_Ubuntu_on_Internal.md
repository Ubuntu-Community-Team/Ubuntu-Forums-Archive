---
title: "XP on External, Ubuntu on Internal"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by drewcoll on 2009-01-07
Hi I was wondering if anyone can explain or give me a link to a howto or relevant thread on how to do this.

I have a laptop with 15 GB and a 160 GB external.  I'd like to install Ubuntu internally and have XP or Vista on the external drive.  I would like to have it boot Linux by default, but allow me to boot Windows on the external.  I don't plan on having the external with me all the time, and my computer does not support USB booting.

Thanks!

---

### Post by infamous-online on 2009-01-07
well you're really limited here. perhaps you could buy a bigger harddrive size for your laptop and put them both on the same harddrive. if your laptop has a sata port you can go as high as 500 gigs but for a pata or ata the highest harddrive i see on the market is 250 gigs. of course those may or may not be what you're looking for but they are just to give you an idea.

---

### Post by Tim Sharitt on 2009-01-07
I don't really see where you would have any problems. Ubuntu installs the GRUB bootlofader by default, which will easily let you boot from the external when it is attached, but will still boot Ubuntu when it is not.

If you have any specific questions relating to the install or preinstall feel free to ask.

---

### Post by drewcoll on 2009-01-08
> **Tim Sharitt said:**
>  GRUB bootlofader by default, which will easily let you boot from the external when it is attached, but will still boot Ubuntu when it is not.

Yep, I know GRUB can do this, but not how to do this.  :confused:

How do I install Windows to my external drive without screwing up my internal drive?  Wont it overwrite GRUB on the internal with the MBR?

And then, let's say I have my drive mounted at /dev/sdb.  What do I write into GRUB to get Windows to boot from there.

---

### Post by Tim Sharitt on 2009-01-08
You will need to reintall grun after  installing windows. Here's a guide to do that: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Add this to your /boot/grub/menu.lst to boot Windows
```

title         Windows Vista
root          (hd1,0)
makeactive
chainloader   +1

```

---

### Post by logos34 on 2009-01-08
> **drewcoll said:**
> 
How do I install Windows to my external drive without screwing up my internal drive?  Wont it overwrite GRUB on the internal with the MBR?

Allegedly it's possible--here's [the tut]("http://www.ngine.de/article/id/8").  Never tried it myself, nor can I say if it really works as advertised.

Give it shot and post back with the results

---

### Post by Engus on 2009-01-10
what if:
- i have a vista hd that used to be internal, and is now in a external inclosure. (usb connection)
- ubuntu is now the internal hd on my laptop.

both work as internal hd's but how do i get the vista one to boot from external?

---

### Post by caljohnsmith on 2009-01-11
> **Engus said:**
> what if:
- i have a vista hd that used to be internal, and is now in a external inclosure. (usb connection)
- ubuntu is now the internal hd on my laptop.

both work as internal hd's but how do i get the vista one to boot from external?
As I understand it, it takes a bit of hacking to get Windows XP to boot from a USB drive, so I would think that Vista is similar:

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

