---
title: "Power Manager problem on Acer netbook"
date: 2010-06-13
forum: Hardware
---

### Post by LKNT on 2010-06-13
Hi all,

I have recently bought an Acer Aspire One 532h Netbook and installed Ubuntu 10.04 (Desktop edition) on it. My problem is that when it is running on battery, the power manager occasionally goes crazy and gives wrong indications. I normally wouldn't be bothered if for a few moments the indicator gives wrong info, but usually it indicates that the battery is critically low and hibernates the computer, which is quite annoying. I would like to know if there is a possible fix to this problem, or if at least it is possible to stop the power manager from hibernating the system. I know the indication is wrong because when it hibernates, I switch it back on immediately and it is back to normal (and continues to work without plugging it in). I know I should boot into the preloaded Windows XP and see if the problem exists also there to know if it is a hardware or software problem, but I didn't do it yet. Does someone have any idea what I could do?

Thanks in advance

---

### Post by nickyap on 2010-06-17
i too have a Acer Aspire One 532H and Ubuntu's remix 10.04 with the same power management issue.  i still have Win 7 Starter available and do not have any problem with the battery when using Win 7.  have changed the power management setting to suspend the netbook as opposed to hibernating it.  this has shaved off some time wasted in between making the problem somewhat less annoying.

notice that the thread [http://ubuntuforums.org/showthread.php?t=1487918&highlight=aspire+netbook+ubuntu+10+battery](http://ubuntuforums.org/showthread.php?t=1487918&highlight=aspire+netbook+ubuntu+10+battery) has more users with the same issue, but still no resolution

---

### Post by LKNT on 2010-06-17
Yeah, I also set it to Suspend, however the problem is still there!

---

### Post by FearsomeOrange on 2010-06-18
I'm with you, currently I'm on the Windows 7 partition, showing 95% charge after Ubuntu panicked and shut me down saying my battery was critically low... What the heck?

---

### Post by Maximus559 on 2010-07-24
I had the same problem on my AO532h, but I think I may have found a fix:  BIOS update. If you're dual booting Ubuntu and Windows, just boot into  Windows and run the update utility provided by Acer in the downloads  section of their support site. If you're like me and are running Ubuntu  exclusively, it's a bit of a roundabout process. First, follow the  instructions [here]("http://www.bay-wolf.com/usbmemstick.htm")  to create a bootable DOS USB flash drive. Then, copy the folder  containing the DOS BIOS update utility to the flash drive. Next, simply  boot from the USB flash drive and run the batch file provided by Acer.  Hope this helps. For reference, this also fixed a warning message I'd  been receiving at boot time: "acer-wmi: Unable to detect available WMID devices".

---

