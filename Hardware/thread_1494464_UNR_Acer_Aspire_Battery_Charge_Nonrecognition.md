---
title: "UNR Acer Aspire Battery Charge Nonrecognition"
date: 2010-05-27
forum: Hardware
---

### Post by thefalcon72 on 2010-05-27
I recently installed Lucid UNR on a netbook after using Karmic & Lucid on a desktop. I have a brand new netbook, Acer Aspire NAV50. When I turn the computer on, after around 5 minutes I receive a notification that the battery level is at 1% and the system is about to shutdown. After I turn it back on, it indicates the correct charge and works properly (until I shut down again). The battery charge profile at this point makes a sharp "V" drop down to "0", then bounces back to ~90%. I believe this has something to do with the Gnome Power Manager on Aspires. Has anyone else encountered this and is there a workable solution?

---

### Post by jonimg on 2010-05-31
[SIZE=2]Hello all!
I have also just installed Ubuntu 10.04 UNR in a brand new Acer AO532h-2350 netbook and get the same problem. After a few minutes I turn it on, it indicates low battery level (1%) and hibernates. When I turn it back on, resuming from hibernation, it indicates the correct battery charge level and works normally.
As I'm new in the GNU/Linux world, I'd like to know if anyone has find a solution to this problem. I have searched over this forum and the Internet and did not find yet a workable solution.
Thanks a lot for your time![/SIZE]

---

### Post by regeya on 2010-07-10
> **jonimg said:**
> [SIZE=2]Hello all!
I have also just installed Ubuntu 10.04 UNR in a brand new Acer AO532h-2350 netbook and get the same problem. After a few minutes I turn it on, it indicates low battery level (1%) and hibernates. When I turn it back on, resuming from hibernation, it indicates the correct battery charge level and works normally.
As I'm new in the GNU/Linux world, I'd like to know if anyone has find a solution to this problem. I have searched over this forum and the Internet and did not find yet a workable solution.
Thanks a lot for your time![/SIZE]

I have no answer but would love to see the answer to this.  I have the same problem.

---

### Post by nbaes on 2010-07-11
I have the exact same issue. It only happens once after the computer has been charging. It's like the first time I use it after unplugging it from the AC adapter, the OS will suddenly tell me that the battery has completely discharged and the computer will suspend. Kind of annoying, I'm also crossing my fingers for a fix!

---

### Post by zool2005 on 2010-07-15
I'm having a similar problem with my MSI Laptop using the full 64bit version of 10.04
Whenever I unplug the AC power adapter, a prompt screen appears to tell me that battery power is critically low and that the computer will be shutdown unless it is plugged in.
If I don't plug it in, it shuts down.
This same laptop worked perfectly with the previous version of Ubuntu.

---

### Post by Maximus559 on 2010-07-24
I had the same problem on my AO532h, but I think I may have found a fix: BIOS update. If you're dual booting Ubuntu and Windows, just boot into Windows and run the update utility provided by Acer in the downloads section of their support site. If you're like me and are running Ubuntu exclusively, it's a bit of a roundabout process. First, follow the instructions [here]("http://www.bay-wolf.com/usbmemstick.htm") to create a bootable DOS USB flash drive. Then, copy the folder containing the DOS BIOS update utility to the flash drive. Next, simply boot from the USB flash drive and run the batch file provided by Acer. Hope this helps. For reference, this also fixed a warning message I'd been receiving at boot time: "acer-wmi: Unable to detect available WMID devices".

---

### Post by peter_register on 2010-09-05
> **Maximus559 said:**
> I had the same problem on my AO532h, but I think I may have found a fix: BIOS update. If you're dual booting Ubuntu and Windows, just boot into Windows and run the update utility provided by Acer in the downloads section of their support site. If you're like me and are running Ubuntu exclusively, it's a bit of a roundabout process. First, follow the instructions [here]("http://www.bay-wolf.com/usbmemstick.htm") to create a bootable DOS USB flash drive. Then, copy the folder containing the DOS BIOS update utility to the flash drive. Next, simply boot from the USB flash drive and run the batch file provided by Acer. Hope this helps. For reference, this also fixed a warning message I'd been receiving at boot time: "acer-wmi: Unable to detect available WMID devices".

Thanks Max.  This worked great.  Just  got my netbook last week and this issue was one of the few remaining things that was annoying me.  :)

---

