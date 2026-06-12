---
title: "Dual boot questions"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by geirr on 2005-12-12
Hello Ubuntu Forum, 
this is my first post, but hopefully not my last, as I have not installed Ubuntu yet, but I am about to. Important: I am quite new to Linux, but not to computers (windows) in general.

Can anyone help me out or point to where answers can be found?

I have a windows installation that I have to keep, and it is utilizing all of my 100GB disk, so I would like to set up dual boot, with both OS on the same disk. That means repartioning, so I can get space for Ubuntu. Is there a partition resizing utility on the Ubuntu (Breezy Badger) install CD/LIVE CD? How can I use this?

Once the disk is repartioned, how do I configure the boot manager?

Any help will be appreciated :smile: 

Rgds. Geirr

---

### Post by gosh on 2005-12-12
You can go here [https://wiki.ubuntu.com/HowtoPartition?highlight=%28partition%29](https://wiki.ubuntu.com/HowtoPartition?highlight=%28partition%29)
for some info on partitioning.

You can also use Partition Magic (a commercial but reliable tool) to partition your disk.

---

### Post by lutrafobic on 2005-12-12
The easies way to make this work is if you use something like partition-magic in Windows. If you can find a way to get a few GB free from that 100GB partition and make it 'unused space' the installation of ubuntu will go really easy.

In the ubuntu installation you'll get an option called something like 'use the largest free harddrive space avalible for the installation' and I believe that this is the easiest way to do the installation. So what you do want before the ubuntu installation is some 'unpartitionised space'.

If you do this, the dualboot will run fine. The ubuntu installation will ask you if you want a dual-boot-menu (due to that it notices that you have another OS on the machine.)

hope this will help..

/L

---

### Post by Herman on 2005-12-12
geirr,
>  Is there a partition resizing utility on the Ubuntu (Breezy Badger) install CD/LIVE CD? How can I use this?
      
Yes, there is. You should check the three illustrated example installs in my 'signature' link, at the bottom of this post and choose whichever one suits you. There is some other information there as well.
> Once the disk is repartioned, how do I configure the boot manager?
That is explained in the signature link too, it's very easy if you just use GRUB, and let the software automatically install it to your MBR, that's what most people prefer, including me.

I also recommend reading this after you install it will give you some valuable information to help you get started easily: [http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf)

All the best of luck with it! :D  (Herman)
  V  Sig. link below here   V

---

### Post by geirr on 2005-12-12
Thank You All for Excellent information, and quick response.

-I bow my head in awe, and humbleness, oh Great Ones.

Can't wait to get started tonite!  :p 

Rgds.
Geirr

---

### Post by snowjunkie on 2005-12-12
[QUOTE=geirr]Thank You All for Excellent information, and quick response.

-I bow my head in awe, and humbleness, oh Great Ones.

Can't wait to get started tonite!  :p 

Rgds.
Geirr[/QUOTE]

I don't want to dampen the atmosphere, but it is always wise to back up your critical files first!

---

