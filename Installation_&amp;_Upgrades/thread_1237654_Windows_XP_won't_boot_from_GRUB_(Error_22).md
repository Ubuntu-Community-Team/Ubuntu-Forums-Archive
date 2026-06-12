---
title: "Windows XP won't boot from GRUB (Error 22)"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by theopeek on 2009-08-11
Hi all,

After several attempts to install Kubuntu 9.04 in a dual-boot with Windows XP, I am now officially stuck :(

I installed Kubuntu on my first SATA disk with that disk selected as the 
first one to boot in the BIOS. Windows XP was installed on the only PATA 
disk. Kubuntu boots fine, but when I select Windows XP, I get Error 22: No 
such partition.

I can boot Windows XP, but only by selecting the PATA disk as the first one 
to boot in the BIOS. Not the most practical solution, because I have to edit 
the BIOS again if I want to boot Kubuntu of course.

With the help of other posts on this forum, including [this one]("http://ubuntuforums.org/showthread.php?p=6638295"), 
I have tried to troubleshoot the problem, but unfortunately to no avail.

I have attached the menu.lst file, which shows Windows XP is on (hd4,0). That looks correct to me because there are four SATA disks and the PATA one is therefore the fifth. The attached device.map confirms this.

Using Boot Info Script I have generated a results.txt file which is also attached to this post.

I hope someone can help me solve this. Thanks very much in advance.

Theo

---

### Post by stlsaint on 2009-08-11
im not sure about where you have all your space spread out as i am new to GRUB myself but it looks like you have put GRUB in the wrong location! explain the order in which you insalled your OS on your system?

---

### Post by Cope57 on 2009-08-11
Since when does Windows boot GRUB?

---

### Post by stlsaint on 2009-08-11
it doesnt...GRUB sends the bootloading to MBR whenever XP is selected! maybe its a typo!!

---

### Post by theopeek on 2009-08-12
@stlsaint:

I first installed Windows XP and then Kubuntu. GRUB is on the first SATA disk which I have selected in the BIOS as the first one to boot, so the location looks good to me. But please correct me if I'm wrong! :)

@Cope57:

Not sure what you mean. I select Windows from the GRUB screen and it doesn't boot.

---

### Post by Mark Phelps on 2009-08-12
Was the PATA (XP) drive plugged in when you installed Kubuntu? OR did you connect it later and add the MS Windows stanza to your menu.lst manually?

---

### Post by theopeek on 2009-08-12
The PATA drive was plugged in at the time of Kubuntu installation and all attached files were generated; I haven't changed anything manually.

---

