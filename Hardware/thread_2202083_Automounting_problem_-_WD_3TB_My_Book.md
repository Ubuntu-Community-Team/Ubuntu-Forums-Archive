---
title: "Automounting problem - WD 3TB My Book"
date: 2014-01-27
forum: Hardware
---

### Post by CwzJptG on 2014-01-27
Hello everyone!!!

Recently I purchased a 3TB Western Digital My Book. I have the same model but in 2TB version which works perfectly in Ubuntu, but it's full of multimedia content. The new one, the 3TB version, shows me a little problem. I must mount it manually always. Curiously BIOS can't detect the 2TB and 3TB HD, but they work perfectly on Ubuntu. I have tried the next options:

**_First Attempt - Format it manually (I have read the +2TB limitation so I partitioned manually  for a GPT partition table and EXT4 FS):_**

$ sudo parted /dev/sdg
   mklabel gpt
   mkpart primary ext4 0% 100%

$ sudo mkfs.ext4 /dev/sdg1
$ sudo e2label /dev/sdg1 WD2

Result: all ok but Ubuntu can't automount the unit
[U][B]
Second Attempt - Using fstab and mtab:[/B]
[/U]
$ sudo mkdir /media/WD2

$ sudo nano /etc/fstab
   UUID=4901a1e3-3fdb-4796-9e2e-2b42c0c600fb      /media/WD2                          ext4    errors=remount-ro                                                0       1
$ sudo nano /etc/mtab
  /dev/sdg1 /media/WD2 ext4 rw,errors=remount-ro 0 0

$ sudo mount /dev/sdg1


Result: all ok, but if I want to automount the unit, I need to connect the HD before turn on the PC or restart it.

[B]_Third Attempt - Use other OS:_

[/B]I have a Galaxy S3 with an OTG cable and SmartDroid ROM, so I can connect the HD and it works really great with USB OTG Helper and Solid Explorer APKs.
On a laptop with Windows 8.1, I formatted the HD in NTFS and it works great. The HD automounts correctly everytime I connect and disconnect it from laptop. If I go to the Ubuntu PC, HD doesn't automount.
Using a Ubuntu liveusb, the result is the same...
[B]
PC: [/B]OS -Ubuntu 13.10 x64 
     Kernel - Liquorix kernel 3.12-8.dmz.1-liquorix-amd64
     Motherboard - Pegatron Cleveland GL-8
 
**Question:** What other options do I have?


Thank you so much for your help!!!

---

### Post by cbaykal on 2014-02-28
Hi,
I have bought maybe the same drive. Then, I saw your post here.
Did you solve your problem?
What should I do first to set the drive right for use in w7 and ubuntu?
If you solved your problem. I would very much appreciate your assistance on this.
Thanks

---

### Post by CwzJptG on 2014-05-15
Hello!!!

After waiting a few months for the new Ubuntu 14.04, the "problem" has been solved :)

---

