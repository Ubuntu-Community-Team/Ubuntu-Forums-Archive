---
title: "Blu-Ray Won't Work"
date: 2016-02-01
forum: Hardware
---

### Post by ThePowerpuffGirls on 2016-02-01
I recently bought a ASUS BluRay player, to replace my CD/DVD drive.
It won't play BluRay, DVD or even a CD.
I'm running Ubuntu 12.04 x64

- Blossom

---

### Post by Vladlenin5000 on 2016-02-02
> **ThePowerpuffGirls said:**
> 
I'm running Ubuntu 12.04 x64

^^^^
This is probably your main problem, an ancient release. And probably the hardware is also ancient, isn't it? If so, your expectations should be set accordingly.
Now, even an old SATA enabled motherboard should support a new BD drive unless it's so ancient it has SATA I (original SATA specs) only.

That said please post the exact drive model and the hardware specs of the machine where you fitted it.

---

### Post by Nuno_Abreu on 2016-02-02
This is probably the solution to your problem:
[http://bit.ly/20EaDXC](http://bit.ly/20EaDXC)

---

### Post by ThePowerpuffGirls on 2016-02-07
[B][SIZE=2]ASUS Black 12X BD-ROM 16X DVD-ROM 48X CD-ROM SATA Internal Blu-ray Drive Model BC-12B1ST/BLK/B/AS - OEM
Motherboard: ASUS Z87-K
Processor: Intel Core i3-4670K @3.40GHz x4
RAM: 16GB DDR3 @1600MHz
Kernel: 4.0.0-040000-generic
Drive: 120GB SSD
I thought it would work if it had the drivers and the drivers were with the Kernel. I've recently upgraded to Kernel 4.0. No luck yet.
[/SIZE][/B]
- Blossom

---

### Post by Vladlenin5000 on 2016-02-07
Do you realize you're using a Ubuntu release way older than your hardware, all of it? Retrofitting newer kernels may not be the solution...
But it could also be something else. What happens when you insert a CD?

---

### Post by ThePowerpuffGirls on 2016-02-07
I thought Ubuntu was supported until 2017. The only reason I don't upgrade is because of at least one thing which is they don't have the compact view. Unless I can install the gnome version I have now, in a new distro.
When I put in any CD (data, music, DVD or BluRay) nothing happens and it doesn't show up on the side menu in the folders like it used to (my previous one, which was just a DVD Drive).

- Blossom

---

### Post by Vladlenin5000 on 2016-02-07
Yes, it is supported. It doesn't mean it is recommended for newer hardware though. Not even the newer LTS - 14.04 - is for many hardware sold mid to late 2015.
I honestly don't know what "compact view" you're referring to but Ubuntu-GNOME has all the same releases as standard Ubuntu and is now a full-fledged official member of the Ubuntu "family".

That said, I suggest you try the following troubleshoot:
 - Boot from any bootable CD/DVD. Any Linux distro as well as any Windows installation DVD, tools like Clonezilla, Parted Magic, Hiren's Boot CD, etc. can be used for this purpose. You won't be installation anything, just booting a live session. Does it work?
- A different and independent approach from the above is to check in BIOS/UEFI whether or not the drive is properly recognized.

---

### Post by ThePowerpuffGirls on 2016-02-08
> **Vladlenin5000 said:**
> Yes, it is supported. It doesn't mean it is recommended for newer hardware though. Not even the newer LTS - 14.04 - is for many hardware sold mid to late 2015.
I honestly don't know what "compact view" you're referring to but Ubuntu-GNOME has all the same releases as standard Ubuntu and is now a full-fledged official member of the Ubuntu "family".

That said, I suggest you try the following troubleshoot:
 - Boot from any bootable CD/DVD. Any Linux distro as well as any Windows installation DVD, tools like Clonezilla, Parted Magic, Hiren's Boot CD, etc. can be used for this purpose. You won't be installation anything, just booting a live session. Does it work?
- A different and independent approach from the above is to check in BIOS/UEFI whether or not the drive is properly recognized.

I've tried a live CD to see if it'll work, but the same thing.
I've also tried booting from a live CD but it wouldn't work. I selected it via F8, but it just booted into the main drive instead.
I've also tried a different SATA cable thinking the one might be broke.
I've uploaded an attachment of it showing up in the list of drives, just in case there maybe something useful we're missing.

[ATTACH=CONFIG]267185[/ATTACH]

Update:
I've decided to replace it. I've read the reviews and on the front page where it compares a positive and negative review, someone had the same problem where it wouldn't read any discs.
 
- Blossom

---

### Post by Vladlenin5000 on 2016-02-08
Probably a good decision but we could have done some more troubleshooting like perhaps change some UEFI settings for that drive.

---

### Post by ThePowerpuffGirls on 2016-02-08
I still have it, and could hook it up again.

- Blossom

---

