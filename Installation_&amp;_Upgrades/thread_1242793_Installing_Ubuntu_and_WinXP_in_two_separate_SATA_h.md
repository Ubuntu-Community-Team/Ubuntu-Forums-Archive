---
title: "Installing Ubuntu and WinXP in two separate SATA hard drives"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by arepaking on 2009-08-17
Hello experts,
Does anyone knows the proper way to install Ubuntu and WinXP in two different SATA hard drives?

I have Windows Installed already in SATA0. Ubuntu is connected to SATA1 port in my motherboard. 

Thanks in advance for any guidance.

---

### Post by QIII on 2009-08-17
Here is what I have done for years, but it wouldn't hurt to wait for more people to chime in.

A word of warning:  I am going to ask you to "unplug drive so-and-so from the SATA cable".  Do so on the DRIVE end, because SATA headers have a nasty habit of pulling off the motherboard with the cables, even if you properly squeeze the little locking tabs.  You will be sunk if you bend any of the pins if that happens.

Another word of warning:  BACK UP ANYTHING YOU WANT TO KEEP from your Windows drive.  Mistakes happen.

1.  Label your drives on the back end so you can see the labels with the disks installed.  Label the one you have in there already, presumably your Windows drive as "Windows".  Label the other "Ubuntu".  This will avoid confusion and the potential for installing Ubuntu on the wrong physical drive.  It will also keep you from fouling up your Windows boot instructions.

2.  Install your new SATA cable on the next lowest numbered SATA header on your MOBO and leave it there for a moment.

3. Unplug the SATA cable from your Windows HDD -- at the hard drive end!

3.  Install your Ubuntu drive in the bay and plug in the SATA cable you just removed from your Windows drive.  This should be the lowest numbered SATA header on your MOBO.

4.  With the Windows drive still UNPLUGGED, install Ubuntu on your new drive.  Again -- it should be on the lowest numbered SATA header.

5.  When Ubuntu is installed, edit your menu.lst (If you do not understand this, let us know so that we can tell you how to do this.)   Depending on whether you want Windows to be your default start up or Ubuntu, add the following (there is an example in menu.lst) before or after the boot entries for Ubuntu (you should see three groups:  <somekernelversion>-generic, <somekernelversion> recovery, Memtest)

```
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```I'm not at my Ubuntu machine right now, so I can't C&P an example from mine.  It might be worth a wait until someone can do that or until I get home tonight.  The two "map" lines may come before "makeactive".  I don't know from memory.

6.  AFTER you have done all that, plug your Windows HDD into the other SATA cable (that is the second lowest numbered header on your MOBO).

What you should now have is a dual boot system, which you can return to a Windows pure machine by simply removing the Ubuntu HDD and switching your Windows drive to the lowest numbered SATA header.  What we have done by unplugging the Windows drive is to be sure that we have not tampered with the boot instructions of the Windows drive, so you are free to restore the machine or move the HDD if you choose.

Again -- this has worked for me.  Your mileage may vary, so wait a bit for more people to make suggestions.  This is a fairly risky undertaking, so don't go on my experience alone.

---

### Post by arepaking on 2009-08-17
Thanks QIII for your quick response.

Quick question: When I ran the Live CD - GParted, the drives are listed as "sda" and "sdb". Does this substitutes the "hd1" and "hd2" respectively?
 
Anyways, I am getting the following error when I choose the Windows XP Pro option on my grub: 

Error 23: Error while parsing number.

Thanks again!
-C

---

### Post by serpantman on 2009-08-17
I need to know the same thing, but i already have jaunty installed with FDE on a SATA,. And i need to install XP to a second HD, IDE though. I really don't want to overwrite grub(windows likes to do that). Do i have to worry about this? Never installed to a second HD before.

---

### Post by arepaking on 2009-08-17
Discard what I said before. I had a typo on my grub. It worked flawless following your advice.

Thanks Dude!!!!
-AK

---

### Post by serpantman on 2009-08-17
Anyone know if windows will still try to overwrite grub if install to a second HD? I don't want to re-install it since i will have to configure it for FDE.

EDIT: I'm installing windows on a second hd, i have ubuntu on the primary.

---

### Post by stlsaint on 2009-08-17
> **serpantman said:**
> Anyone know if windows will still try to overwrite grub if install to a second HD? I don't want to re-install it since i will have to configure it for FDE.

EDIT: I'm installing windows on a second hd, i have ubuntu on the primary.

follow the same steps giving above but for ubuntu!! yes windows will make itself the "big man on campus" but nothing a lil livecd cant fix! boot to the live cd and make changes to grub as necessary or re-install grub all together to give the crown to its rightful owner!!! (ubuntu that is!!)

---

### Post by presence1960 on 2009-08-17
> **serpantman said:**
> Anyone know if windows will still try to overwrite grub if install to a second HD? I don't want to re-install it since i will have to configure it for FDE.

EDIT: I'm installing windows on a second hd, i have ubuntu on the primary.

To install windows boot your machine and go into BIOS. Set your IDE disk (the one you want windows on) as first in the hard disk boot order. Then boot off the windows installation disk. If you fail to set your intended windows disk as first boot in BIOS windows will attempt to write it's bootloader to whichever disk is first in the hard disk boot order in BIOS. After windows is installed boot again and set your Ubuntu disk as first hard disk boot in BIOS so GRUB will take over when you boot. If you follow these steps GRUB will remain on your Ubuntu hard disk unscathed!

---

### Post by arepaking on 2009-10-31
> **QIII said:**
> Here is what I have done for years, but it wouldn't hurt to wait for more people to chime in.

A word of warning:  I am going to ask you to "unplug drive so-and-so from the SATA cable".  Do so on the DRIVE end, because SATA headers have a nasty habit of pulling off the motherboard with the cables, even if you properly squeeze the little locking tabs.  You will be sunk if you bend any of the pins if that happens.

Another word of warning:  BACK UP ANYTHING YOU WANT TO KEEP from your Windows drive.  Mistakes happen.

1.  Label your drives on the back end so you can see the labels with the disks installed.  Label the one you have in there already, presumably your Windows drive as "Windows".  Label the other "Ubuntu".  This will avoid confusion and the potential for installing Ubuntu on the wrong physical drive.  It will also keep you from fouling up your Windows boot instructions.

2.  Install your new SATA cable on the next lowest numbered SATA header on your MOBO and leave it there for a moment.

3. Unplug the SATA cable from your Windows HDD -- at the hard drive end!

3.  Install your Ubuntu drive in the bay and plug in the SATA cable you just removed from your Windows drive.  This should be the lowest numbered SATA header on your MOBO.

4.  With the Windows drive still UNPLUGGED, install Ubuntu on your new drive.  Again -- it should be on the lowest numbered SATA header.

5.  When Ubuntu is installed, edit your menu.lst (If you do not understand this, let us know so that we can tell you how to do this.)   Depending on whether you want Windows to be your default start up or Ubuntu, add the following (there is an example in menu.lst) before or after the boot entries for Ubuntu (you should see three groups:  <somekernelversion>-generic, <somekernelversion> recovery, Memtest)

```
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```I'm not at my Ubuntu machine right now, so I can't C&P an example from mine.  It might be worth a wait until someone can do that or until I get home tonight.  The two "map" lines may come before "makeactive".  I don't know from memory.

6.  AFTER you have done all that, plug your Windows HDD into the other SATA cable (that is the second lowest numbered header on your MOBO).

What you should now have is a dual boot system, which you can return to a Windows pure machine by simply removing the Ubuntu HDD and switching your Windows drive to the lowest numbered SATA header.  What we have done by unplugging the Windows drive is to be sure that we have not tampered with the boot instructions of the Windows drive, so you are free to restore the machine or move the HDD if you choose.

Again -- this has worked for me.  Your mileage may vary, so wait a bit for more people to make suggestions.  This is a fairly risky undertaking, so don't go on my experience alone.


QII,
I need your help buddy. I just installed Karmic but I noticed that GRUB2 works a little bit different. Your instructions really helped me back in GRUB so I was wondering if you have any idea about how to dual boot two SATA drives under Karmic??

I tried to copy and paste string above into /etc/grub.d/40_custom but it did not work.

Thanks in advance,
AK

---

### Post by arepaking on 2009-10-31
Problem solved on this thread:

[http://ubuntuforums.org/showthread.php?t=1307040](http://ubuntuforums.org/showthread.php?t=1307040)

---

