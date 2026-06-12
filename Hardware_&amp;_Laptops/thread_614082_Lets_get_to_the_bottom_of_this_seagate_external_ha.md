---
title: "Lets get to the bottom of this seagate external hard drive &amp; ubuntu issue"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by Kouki on 2007-11-15
[Part solved] Just need to get it to automount now (see end)

Hi, my 320gb seagate hard drive used to work fine back in the days of dapper.  I'd plug it in and it would appear on my desktop, and I could use it.  Then I upgraded to Edgy and ubuntu stopped being able to see it.  However it still works fine with windows, fair enough I thought, I'll wait for the next one and see if the problem is fixed.  Along came feisty and still nothing.  Ah well I thought, wait for the next one.  We're now on Gutsy and I've not been able to listen to my music collection for some time.  To make matters worse, I've now binned windows, so I have a nice gray seagate box to look at but can't use.

The strange thing is that G-parted sees it fine, but I just can't do anything with it.  I've tried searching on here and Seagate usb hard drives don't seem to get on too well with ubuntu.  I've tried many recommended fixes but none have done the job.

Please can someone help me :)

Closest I've got to using it is by typing this into the terminal:

> sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media/sdb1

That pretty much showed the contents of my drive in the terminal, and the drive spun up.  However, assuming it had mounted I went to 'media/sdb1' and................... can't believe it, I've just made it work for the first time in months :guitar:

Was not expecting that.  I'll create a shortcut to that folder and put it on my desktop.

Still won't automount though which would be useful.  Any suggestions?

---

### Post by stefan_l on 2008-01-08
Still have the same problem and had the same under Fiesty also. 

Don't know what to do about it but I've the same solution as you. But I've also put the appropiate lines in /etc/fstab so that if I have my seagate on when I start my computer I will heve it mounted.

---

