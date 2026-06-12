---
title: "Upgrade 9.04 to 9.10 crashes with mountall error for devpts"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by manankanchu on 2009-11-01
I just upgraded from 9.04 to 9.10 ... after reboot laptops crashes with mountall problem "mount /dev/pts terminated with status 32" and finishes in maintenance shell. Any ideas greatly appreciated !!

---

### Post by manankanchu on 2009-11-01
Problem solved after hours of searching:

I found many similar entries in different forums indicating a problem with fstab as fstab contained after upgrade a new entry killing mountall at boot. 

I checked it and found a formerly not present entry for devpts -  I deleted it and things worked. 

Needless to say, I think upgrade to 9.10 is NOT ready for production !!

I DO NOT RECOMMEND USING THE UPGRADE FUNCTION FROM 9.04 to 9.10 !!

This is what I did in detail (I hope I didn´t miss any step):

- boot from live CD
- open console
- generate new directory "newroot"   (sudo mkdir /newroot)
- I mounted my non bootable harddisk to newroot (sudo mount /dev/sda1 /newroot)  ... replace /dev/sda1 with your root disk
- go to newroot (cd /newroot)
- I opened fstab with an Editor (sudo gedit /etc/fstab)
- I commented out the fatal line by adding # in front
  (# devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)  )
- I saved the modified fstab
- I rebooted (shutdown -r now)

I have read many forum entries where different fatal lines in fstab were reported ... If you intend to use my approach make sure you know what you do ... playing around with fstab may cause serious defects to your system, use infos at your own risk !


Rgds

   Manankanchu

---

