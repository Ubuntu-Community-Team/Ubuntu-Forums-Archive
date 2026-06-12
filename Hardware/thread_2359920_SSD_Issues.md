---
title: "SSD Issues"
date: 2017-04-29
forum: Hardware
---

### Post by d-v-t on 2017-04-29
I've been running Ubuntu for about a year and a half now on a WD Blue 1TB HDD (believe it to be 7200 rpm). Recently, I reinstalled Ubuntu on an SSD (OCZ Agility 2 3.5" 90GB) and reformatted the HDD. Both are ext4 partitions and are connected to my Asus z97a motherboard with SATA cables. I am using an Apevia Java 650W power supply and that's also feeding power to a GT 740 graphics card and a i7-4790k processor.

When I power my computer up after a long time of being powered off, it takes a long time to get through the boot and then hits initramfs. I then reboot it and it boots just fine. Also, after not using the computer for a significant period of time (between 20 minutes and a couple hours), the computer fails to wake up and prompt me with a login screen. I need to hard power down and restart the computer after this happens.

I'm not sure what to expect because my power supply is rated for much higher than what I'm running, plus it worked fine when I just used an HDD, plus in the BIOS the 12V reads 12.348V, the 5V reads 5.240V, and the 3.3V reads 3.360V, so nothing abnormally high or low. And previously, the SSD worked just fine, and also I've never had these issues just running the SSD, that is disconnecting the HDD's SATA cable. I'm wondering if there's an issue with Ubuntu or if my mobo is at fault or if there's something else I don't realize.

[EDIT] It takes much longer than 20 minutes of idling for it to become irresponsive. Probably between 2-6 hours.

---

### Post by Bashing-om on 2017-04-29
d-v-t; Hello;

I went round and round trying to get a SSD and my hard drives to co-exist - on old hardware .
I am now happy !
what I did:
1) Updated Bios to latest available version
2) AHCI enabled in bios ( my old bios did not explicitly have this option BUT enabling raid also enabled AHCI
3) move the hard drives off the same SATA controller bus 
4) installed a proprietary graphics driver - no idea as to the why here ! All my remaining system issues went away with the proprietary driver.
5) [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/1470014](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/1470014)
Still with problems - the system logs might give indications .
I booted up in 'text' mode to see all the boot messages and read through the system logs in /var/log .

Believe me - I was some kind of disappointed when I tried booting up the SSD ->

[INDENT][INDENT]took a while and a LOT of effort
[INDENT][INDENT]all happy now
[/INDENT][/INDENT][/INDENT][/INDENT]

---

