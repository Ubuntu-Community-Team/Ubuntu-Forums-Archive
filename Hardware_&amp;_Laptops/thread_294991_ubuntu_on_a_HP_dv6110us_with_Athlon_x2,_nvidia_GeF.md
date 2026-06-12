---
title: "ubuntu on a HP dv6110us with Athlon x2, nvidia GeForce Go 6150"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by cbruno on 2006-11-07
I just installed Dapper on an HP dv6110us. I have successfully installed the nvidia beta driver and gotten the 1200x800 resolution and 3D acceleration working.

I also installed the latest release of ndiswrapper and got the Broadcom wireless working using the Windows drive bcml5. 

The problem is that in order to boot I have to pass noapic to the kernel.

I think this is the source of my problem: after I successfully boot, with all hardware working (nvidia graphics, sound, wireless, ethernet, monitor dimming), the wireless and monitor dimming quits working after about 3-5 minutes. All of a sudden my wireless wont see any ESSIDs and my monitor wont dim when I remove the power.

I check my kernel messages in /var/log and there is a report about a "bad irq".

If I reboot the system, everything works again (wireless, monitor dimming) only to fail after about 3-5 minutes.

Anybody have any idea what is wrong?

Thanks

---

### Post by teaker1s on 2006-11-23
join the club, I've a dv 6116eu and I'm trying edgy on it and to be honest it works but booting/shutdown is erratic. I've also yet to play with the beta nv drivers and bcm43xx cutter the only way i got wireless working.
I think that as my needs are limited in respect of applications on the laptop that dapper LTS may be a better solution as edgy is far too buggy

---

