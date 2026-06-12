---
title: "Pavilion dm1z AMD Unsupported hardware"
date: 2011-09-09
forum: Hardware
---

### Post by -Shuji- on 2011-09-09
I installed Ubuntu 10.10 on my dm1z.  Then I was offered to install proprietary drivers for my graphics.  I installed the offered driver and restarted my machine and now I have an ugly watermark on the lower right side of the screen that says "AMD Unsupported hardware".  I believe my graphics chip is AMD Radeon HD 6310 but Catalyst Control Center shows that graphics card is Wrestler 9802.  Please help me remove the watermark.  Thanks.

Shuji

---

### Post by -Shuji- on 2011-09-12
I was able to fix this problem by upgrading to Ubuntu 11.04.  I'm still using proprietary FGLRX graphics drivers but without the ugly watermark.  I hope someone finds this info useful.

Shuji

---

### Post by CTAPR on 2011-11-04
Crap, just used these drivers and getting the watermark as well. Oh well back to the standard graphics. Thanks for the post

PS: have you ran into any issues with the Ethernet not working on 11.04? My DM1 is a week old from the factory (ground shipping) so I am guessing they have changed to another Ethernet card so this may be why its not working currently.

---

### Post by -Shuji- on 2011-11-04
> **CTAPR said:**
> Crap, just used these drivers and getting the watermark as well. Oh well back to the standard graphics. Thanks for the post

PS: have you ran into any issues with the Ethernet not working on 11.04? My DM1 is a week old from the factory (ground shipping) so I am guessing they have changed to another Ethernet card so this may be why its not working currently.

If you're using 11.04, you don't have to use standard graphics.  Standard graphics is slow when playing movies.  I recommend that you use the proprietary FGLRX graphics drivers.  I still have to try how 11.10 is like on dm1z.  I like the high resolution login screen.

I never had any issues with my ethernet adapter.  Type ```
lspci -v | grep Ethernet -A 1
``` to see the type of ethernet adapter you have.  Mine is below.
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000
```Shuji

---

### Post by CTAPR on 2011-11-07
> **-Shuji- said:**
> If you're using 11.04, you don't have to use standard graphics.  Standard graphics is slow when playing movies.  I recommend that you use the proprietary FGLRX graphics drivers.  I still have to try how 11.10 is like on dm1z.  I like the high resolution login screen.

I never had any issues with my ethernet adapter.  Type ```
lspci -v | grep Ethernet -A 1
``` to see the type of ethernet adapter you have.  Mine is below.
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000
```Shuji

Yep mine shows up as the same Ethernet car just the Subsystem portion is a little bit different. Mine is:
```

"Subsystem: Hewlett-Packard Company Device 3387."

```
But this information should be whats actually coming from the device itself correct? If so i wonder if maybe there is change in the firmware on this device, that's causing it to conflict? Or i guess it could be something in the system to.

What do you see when you run? ```
ifconfig 
``` 
-CT

---

### Post by -Shuji- on 2011-11-08
> **CTAPR said:**
> Yep mine shows up as the same Ethernet car just the Subsystem portion is a little bit different. Mine is:
```

"Subsystem: Hewlett-Packard Company Device 3387."

```But this information should be whats actually coming from the device itself correct? If so i wonder if maybe there is change in the firmware on this device, that's causing it to conflict? Or i guess it could be something in the system to.

What do you see when you run? ```
ifconfig 
```-CT

I'm not sure if subsystem is coming from the hardware or affected by the installed driver.  I'm not very good at Linux.  Ethernet doesn't work even when you boot from the LiveCD?

I installed the latest firmware about a month ago.  I'm using F.13.  What version are you using?  Running ifconfig gives me eth0, lo and wlan0.

---

### Post by CTAPR on 2011-11-08
> **-Shuji- said:**
> I'm not sure if subsystem is coming from the hardware or affected by the installed driver.  I'm not very good at Linux.  Ethernet doesn't work even when you boot from the LiveCD?

I installed the latest firmware about a month ago.  I'm using F.13.  What version are you using?  Running ifconfig gives me eth0, lo and wlan0.

Yep Ethernet doesn't work when i boot from the live CD or DVD (with all of the drivers). Also after going in and updating everything it still doesn't show come up. However what is strange when i run ifconfig i get eth0, eth1, lo but now wlan0 even though my wireless is working. I am wondering if something in this is causing the Ethernet to not function correctly.

---

### Post by -Shuji- on 2011-11-08
> **CTAPR said:**
> Yep Ethernet doesn't work when i boot from the live CD or DVD (with all of the drivers). Also after going in and updating everything it still doesn't show come up. However what is strange when i run ifconfig i get eth0, eth1, lo but now wlan0 even though my wireless is working. I am wondering if something in this is causing the Ethernet to not function correctly.

That is strange.  You have eth0 and eth1 but you only have 1 ethernet port.  You also can't see wlan0 but wireless is working.  Could it be a hardware issue?  If you have Windows installed on another partition, (I'm dual booting 11.04 and Windows 7) can you check if ethernet works in Windows?

---

### Post by CTAPR on 2011-11-10
> **-Shuji- said:**
> That is strange.  You have eth0 and eth1 but you only have 1 ethernet port.  You also can't see wlan0 but wireless is working.  Could it be a hardware issue?  If you have Windows installed on another partition, (I'm dual booting 11.04 and Windows 7) can you check if ethernet works in Windows?

Yep checked it on windows and the Ethernet is working along with wireless. That's why I am thinking its something with the way Linux is seeing it. The other thing that is odd when i go in and look at the wireless info the IP address that listed doesn't show up as any of the IP's under ifconfig.

---

### Post by -Shuji- on 2011-11-10
> **CTAPR said:**
> Yep checked it on windows and the Ethernet is working along with wireless. That's why I am thinking its something with the way Linux is seeing it. The other thing that is odd when i go in and look at the wireless info the IP address that listed doesn't show up as any of the IP's under ifconfig.

I don't really know what's wrong but this is my recommendation:
1. Re-download a fresh copy of Ubuntu 11.04 AMD 64bit version.
2. Check the md5 hash after you download.
3. Verify the disc after you burn it and don't use the max speed.
4. Backup your data.
5. Destroy the linux partitions.
6. Reinstall and check.
Let me know if this works. =)

Sent from iPhone

---

### Post by jerrycrabb on 2011-11-20
NOT SOLVED   Watermark issue returns with latest UBUNTU release "11.10". I'm not smart enough to make it go away. :confused:

---

### Post by -Shuji- on 2011-11-21
> **jerrycrabb said:**
> NOT SOLVED   Watermark issue returns with latest UBUNTU release "11.10". I'm not smart enough to make it go away. :confused:

Jerry, I'm also now using Ubuntu 11.10 AMD 64-bit on an HP dm1z but never saw the watermark before installing the ATI/AMD proprietary FGLRX graphics drivers and after.

---

