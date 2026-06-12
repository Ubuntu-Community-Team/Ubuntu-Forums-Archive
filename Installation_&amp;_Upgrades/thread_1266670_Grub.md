---
title: "Grub"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by CarnivorouZ on 2009-09-14
Got a little problem with installing Windows 7. I know...:cringe:...I got the 64 bit free and I am going to do a fresh install soon over the vista 32 bit I got for free.  Now from years of experience I have at loading both M$ and Linux OS's I know that Windoze overrides the Ubuntu Grub Boot loader.  Is there a simple fix to making it not do this? I have the OS's on different drives, so can I unplug the SATA connector to the 1TB Ubuntu HDD and keep the Ubuntu Grub boot loader after I install windows 7 on the HDD devoted to M$? Thanks for any help guys.

---

### Post by presence1960 on 2009-09-14
> **CarnivorouZ said:**
> Got a little problem with installing Windows 7. I know...:cringe:...I got the 64 bit free and I am going to do a fresh install soon over the vista 32 bit I got for free.  Now from years of experience I have at loading both M$ and Linux OS's I know that Windoze overrides the Ubuntu Grub Boot loader.  Is there a simple fix to making it not do this? I have the OS's on different drives, so can I unplug the SATA connector to the 1TB Ubuntu HDD and keep the Ubuntu Grub boot loader after I install windows 7 on the HDD devoted to M$? Thanks for any help guys.

If they are on separate disks as long as GRUB is not on the disk that has windows GRUB will not be touched. Unfortunately if GRUB is on the windows disk it will be overwritten. Not a big issue just restore GRUB after the windows install. Don't know how? Post back.

---

### Post by running_rabbit07 on 2009-09-14
Not that I know of. You still most likely have to follow the steps on this [thread]("http://ubuntuforums.org/showthread.php?t=224351"), which only take about five minutes including the LiveCD startup time.

I have Windows 7 on mine that I got from MSDN. Looks nice, but all the programs I need are not yet compatible. Neither Wireshark (which is in the Ubuntu repository) and Cisco PacketTracer work on 7.

BTW please spell Microsoft properly. Thanks.

---

### Post by CarnivorouZ on 2009-09-15
Sorry I thought I did spell Microsoft correctly through the commonly used acronym that identifies them as the corporate powerhouse that uses monopoly tactics to shut down competition...my bad.  I'll try the disconnect presence1960, thanks for the input.

---

