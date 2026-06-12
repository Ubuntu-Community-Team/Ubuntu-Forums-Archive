---
title: "GRUB error 18"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by wakatobi on 2005-12-11
I had just install Ubuntu 5.10 in my old machine celeron 400mhz and I find error stage 1.5 error 18. How can I fix the problem ?

---

### Post by Herman on 2005-12-11
wakatobi, here's what the GRUB manual has to say about error 18:
18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 
I think how you fix that maybe depends on a few other things.
Can you tell us more about your computer, how big is the hard-disk and how big is your Windows partition if you have one and how big is your Ubuntu partition?
Is this a new hard-disk you just installed in this old computer? Was the computer made before 1999, or else what year was it made? 
I also have an old 400 Mhz celeron 'book pc', running Win98 with two installs of 'Breezy' (triple boot), and it used to have a 6.0 GB disk, that died. I tried a 40.0 GB one, but it wouldn't work at all. The operating systems wouldn't even install on it. I tried 'flashing the BIOS', and also installing 'disk manager', but the old computer of mine (made before 1999), still had a '32 GB barrier'. I went and bought a 30.0 GB hard disk and it works great now.
[http://www.stud.fernuni-hagen.de/q3998142/pcchips/howto/hdds.html](http://www.stud.fernuni-hagen.de/q3998142/pcchips/howto/hdds.html)
Here's a good link (above) that I found for you, it says you don't have to do anything but install the boot partition within the BIOS limit. (Under 'solutions', under 'not affected operating systems- real operating systems- Linux).:D 
I hope that helps, (Herman).

---

### Post by wakatobi on 2005-12-11
Thank,s for your reply. My computer is celeron 400 mhz, with new harddisk 40Gb 
memory 128 kb, 7GB for ubuntu, 355mg for swap. please help me , I bought this new harddisk because I love Ubuntu and start to learn this software from My old  computer first.

---

### Post by Herman on 2005-12-11
> Thank,s for your reply. My computer is celeron 400 mhz, with new harddisk 40Gb
memory 128 kb, 7GB for ubuntu, 355mg for swap. please help me , I bought this new harddisk because I love Ubuntu and start to learn this software from My old computer first.
Well, that sounds like it's all inside the 8.0 GB limit already, I was thinking if you were dual booting and you had Windows on a larger than 8.0 GB partition you could shrink Windows and try putting Ubuntu in again and it might be okay. But I think now if you have only Ubuntu in already, and it's already within the 8.0 GB limit, you might have to do what I did and buy a smaller sized hard-drive that your motherboard and BIOS can support.
However, the fact that the operating system even installs is encouraging. Please let us know a lot more about your computer, what brand of BIOS it is, what brand of computer, motherboard model, year of manufacture, and all kinds of stuff like that and I'll try to come up with any helpful suggestions I can.
If not me, then someone who is an expert in installing hard-disks in older computers and setting up their BIOSs might happen along.(I've only done my own, and it's not every day a hard-disk needs replacing, so I've a lot to learn too).:D  (Herman)

---

### Post by Herman on 2005-12-11
Oh, yes, I forgot to ask; is it one of those normal sized hard-disk drives: about 100 X 145 X 25 mm? If it is, it's more likely it will have some 'jumper settings' on it, so you can 'jumper' it down to fake a smaller disk size if you have to.
My old computer is just one of those old PCchips 'Book PCs', and it takes the small 'laptop' size hard-drives. (100 X 70 X 10 mm ). A big one will fit in, but that's not the kind it came with. ...Well, at least on the ones I've seen, there are no jumpers I could use to 'jumper' it off. But you might be able to with yours. It might just do the trick too. :D  (Herman)

---

### Post by wakatobi on 2005-12-12
Thank's for your advice. I try another trick, I change my bios setting for my harddisk from LBA mode to normal mode and suddenly everything ok. 

Once Again thank's for your help.

---

### Post by AlesUbu123 on 2007-09-29
Hej thanks for your advice on changing hard drive modes. I changed mine to LARGE (from AUTO) and it worked like a wonder. I got no error 18 message at boot - GRUB just stopped at 

Loading GRUB ...

Now it works - thanks!

Ales

---

