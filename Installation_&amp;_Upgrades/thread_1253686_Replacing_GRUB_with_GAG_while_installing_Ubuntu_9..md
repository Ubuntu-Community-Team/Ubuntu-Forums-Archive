---
title: "Replacing GRUB with GAG while installing Ubuntu 9.04"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by RAM SEN on 2009-08-30
I did search the forums for a similar Q &#8211; if i missed it , i'm sorry &#8211; grateful if someone cud point me there ....

I already hv Windows XP & Vista pre-installed on some pc s &#8211; now planning to dual boot all with Ubuntu 9.04 

very clear about the install after reading this excellent tutorial ....

[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

wud also like to follow the advice in this tutorial & &#8220;put your GRUB bootloader in your / partition instead of your MBR. In your MBR you can install any third party bootloader like GAG&#8221;

this is where i need help on the right sequence

Let 
S1 = installing Ub 9.04 Jaunty from Live CD [ready] 
S2 = install GAG to master boot record {MBR }

for S1 & S2 i plan to follow the same tutorial above.....

S3 = installing GRUB to the first sector of my Ubuntu partition [& not to the MBR ]
for S3 i plan  to follow....

[http://members.iinet.net.au/~herman546/p12.html#Install_GRUB_to_a_Linux_O.S._Partition](http://members.iinet.net.au/~herman546/p12.html#Install_GRUB_to_a_Linux_O.S._Partition)

i hv the following Q ... if i do S1 first, then i assume [A1] that as part of the install, &#8220;the GRUB bootloader is by default, written to the first sector of your hard disk, a location for the Master Boot Record (MBR). &#8220;

is A1 correct?
Then i do S2.    Here i assume [A2] that this means that GAG erases GRUB from the MBR &#8211; or anyhow becomes the 1st priority bootloader in the (MBR). Based on the reasons given by nukleuscore, it seems that it's vital that GRUB not remain on the MBR?

is A2 correct?

So this means i have to now do S3, 'cos GAG can only point to GRUB & the latter has to load Linux.  Ok now if I just blindly follow the steps in 

[http://members.iinet.net.au/~herman546/p12.html#Install_GRUB_to_a_Linux_O.S._Partition](http://members.iinet.net.au/~herman546/p12.html#Install_GRUB_to_a_Linux_O.S._Partition)

will this also effectively tell GAG where to point to [for GRUB] when I choose to boot Linux? Or shud i do something else for that ?

I'm a non-techie trying to customize a dummy guide by reading all the extensive work that the experts have put on the web &#8211; [a big thanks for that btw!]

if any of the pros cud endorse / correct my impression/plan , it wud give me the confidence to execute it. 

Thanks in advance
**

---

### Post by Herman on 2009-08-30
GAG Boot Manager is a good GNU-Linux open source program and there's no reason why it doesn't get more use. It's easier for non technical people to set up than GRUB when operating systems are added or removed. GAG is a 'boot (loader) manager' though, not a boot loader, so we need GRUB or LiLo installed to the boot sector of the Linux partition to boot Linux.

By default, Ubuntu installs the stage1 for GRUB in the MBR of the first hard disk, followed by the (optional) stage1_5 in the first track, (where GAG also can be installed).
The main part of GRUB, called stage2, is located in the Ubuntu partition.
There's an option in the installation process of both the 'Alternate' installation CD and the 'Desktop' Live/Installation Ubuntu CD for not installing GRUB to MBR, but to the first sector of the Ubuntu partition instead.
It doesn't really matter if you do it during installation or later, but you can install GRUB to the Ubuntu partition during your install if you want to. You should install GAG to MBR first if you're planning to do it that way so you'll be able to reboot after the installation more easily.

I don't think it's safe to use Windows XP's 'Disk Manager' for partitioning, I have experienced a corrupted partition table once myself a while back shortly after using it. I have read that it has a bad track record for corrupting partition tables and and I'll never use it again.
I'm not sure about Vista or Win7's version of 'Disk Manager yet, I tried it last week, and it worked very nicely, and fast too, maybe it has improved since Windows XP. I hope so, but it's best to stick with Open Source software whenever we can. If we don't trust open source software then why are we installing Ubuntu?

There is no harm in leaving GRUB in your MBR, I have never heard of any virus affecting GRUB, just people who don't know how to use GRUB. If you use Ubuntu on the internet and restrict Windows to inside your LAN except for trusted sites you won't pick up any viruses anyway, or better still, just delete Windows. Then you won't have viruses. :)

---

### Post by RAM SEN on 2009-09-05
Herman
tks a ton for ur detailed reply 
i will follow instrcs & revert if i have any probs 

"delete windows " haha yes that is my long term goal - just as soon as i manage to migrate all my work to  a linux envirnment 

so many of the websites i use for work won't even work properly wi  FFox or Opera   so i am still forced to use primitive IE 8 - can u imagine !!!

anyway

---

### Post by Herman on 2009-09-05
> so many of the websites i use for work won't even work properly wi FFox or Opera so i am still forced to use primitive IE 8 - can u imagine !!!That's strange. Firefox always works well for me. 
Have you tried following the instructions here -  [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") - Ubuntu Web Forums ? :D

---

