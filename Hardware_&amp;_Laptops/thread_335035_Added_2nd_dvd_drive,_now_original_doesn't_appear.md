---
title: "Added 2nd dvd drive, now original doesn't appear"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by richard.hunt500 on 2007-01-09
Ok, I had one ide dvd rom drive in my pc which in Ubuntu (Dapper) was /dev/hda. Yesterday I added a 2nd dvd drive set as slave, and it works fine as /dev/hdb. However, I just tried to use the first drive and looked around and /dev/hda isn't there anymore. Both drives are working in windows (the original is D:, the new one is drive I: after all the multicard reader drives). Does anyone know why Ubuntu might not be able to use /dev/hda anymore?

I tried adding /dev/hda manually with mknod /dev/hda b 3 0, but when I try to mount I get an invalid block device error. tbh, I couldn't think of anything else to try, I've never had this problem before with linux.

Here's info about my pc:

Sempron 3400+, 512mb ram, K8M800 motherboard, 1 hard drive (/dev/sda), 2 dvd drives (the original one was /dev/hda but this is not showing up now, the new one is showing up as /dev/hdb) a multicard reader I haven't used so I'm not sure but I think it is /dev/sd* something. The only other hardware inside is a Geforce 6200.

Thanks for any help you can give. Also, does anyone have any idea if this is the sort of problem that might go away with a reinstall?

Thanks,
Richard.

---

### Post by teaker1s on 2007-01-09
I had a similar problem and i found it to be cable select-   set jumper to master and slave.
further to this make sure bios has enabled second drive and if it's not detected by ubuntu still change bios setting from auto to manual and select cdrom

---

### Post by ladiesrockmysox on 2007-01-09
let me start by saying i had the same problem. first, i need to know, what are the types of cables you use to hook up your hardware (ata 100/133)

also, i used the "jumperless" feature so my motherboard autodetected the hardware. i would also recommend making the DVD drives both "primary" and the HDD as secondary. in other words,  
Primary Master: DVD-rom drive 1         Secondary master: DVD-rom drive 2     
Primary Slave: user type HDD

---

### Post by richard.hunt500 on 2007-01-09
Thanks for both replies, I have tried playing with the jumper settings now, but the only change I can make is to make the 2nd one disappear in the BIOS.

In the BIOS both drives are detected, it forces me to put them as 1st Primary and Secondary. I only have 1 IDE cable and I think that when both are on the one cable one _has_ to be the slave of the other. I can pick up a 2nd cable or nick one from an old pc if this is likely to be necessary.

I'm curious why this might be a problem though, since the two drives are detected correctly in the BIOS and in windows. Also, it seems strange that Ubuntu knows to assign the second drive to /dev/hdb, but doesn't create /dev/hda for the first one. Anyway, if setting both to primary is likely to work, I'll pick up a cable tomorrow.

Thanks for your replies, at least I know that there is a solution to my problem. Now I just wish Lenovo had included an extra cable somewhere :).

Richard

---

### Post by richard.hunt500 on 2007-01-15
OK, I put in a second ide cable and now my two drives are working as /dev/hda and /dev/hdc as primary and secondary masters.

I was pretty disappointed that ubuntu couldn't use both drive's in my original setup with the drives as primary master and slave. Has anyone managed to used ubuntu with this configuration?

Richard.

---

