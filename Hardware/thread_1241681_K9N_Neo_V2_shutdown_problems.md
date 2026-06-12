---
title: "K9N Neo V2 shutdown problems"
date: 2009-08-16
forum: Hardware
---

### Post by fajardo on 2009-08-16
Hi everyone, 

My system:

Ubuntu 9.04
Processor: AMD Athlon 64 X2 4000+
Motherboard: MSI K9N Neo V2
Graphic card: ATI Radeon HD 2400 Pro

1) the first problem is experienced problems when shutting down my system:

-After shutting down, the system seemed to be in a suspend state (Power LED blinking) instead of really off. 

The problem is that, while in this state, the system cannot be started up again. Not with keyboard keys, enter, power button, reset, nothing. 

The only way is to pull off the power cable and wait for it to really shut down, starting it up normally aftewards.

Solution:
-I tried changing ACPI configurations and other things but no luck. My last attempt has been to add the line:

rmmod snd-hda-intel

to the first line of the halt script in "/etc/default/halt" as commented in [http://forum.eeeuser.com/viewtopic.php?id=1859](http://forum.eeeuser.com/viewtopic.php?id=1859) . 

Though it did not solve the problem. 

If I happen to find a solution I will edit this post.

2) The other problem are random shutdowns during normal computer use:

-There are no warnings or anything, the computer shuts down as if energy supply had been cut off. 

-I could force such shutdowns by converting with WinFF a video file and asserting Edit->Preferences-> than click Multithreading for Dual Core Processors. It took 15 minutes by 27 degrees Celsius for the computer to spontaneously shutdown. (you can monitor the CPUs temperatures with sensors-applet, I don't think it shutdowns due to them, since the computer has even shut down when running a DOS operating system, no application, on a usb-stick, in a hot summer day.)

I have found information about it in the customer descriptions of the motherboard in the website of the vendor. Some people say the motherboard crashes in summer, because the passive heat sink of the mother board chipset is not well dimensioned and sometimes also not well attached (somewhat loose). 

I have found some more information here: [http://forum.msi.com.tw/index.php?topic=99924.0](http://forum.msi.com.tw/index.php?topic=99924.0) but did not lead me to anything. 

I also tried to update the BIOS driver to the newest, have even seen that one of the fixes was about wrong temperature read values given by ACPI. It did not solve anything. I also guess linux doesn't directly use the ACPI temperature values. 

Solution:
-none

---

