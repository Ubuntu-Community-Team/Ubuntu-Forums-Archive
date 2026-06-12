---
title: "Awful sound performance ONLY on mains power, battery is ok!"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by mmcnamee on 2007-06-16
Hi all,

I have a really strange power supply related problem with a Sony VAIO A497XP Laptop.

I installed the latest updates this week, and was demonstrating this audio problem (described below) to a guy in the office, and blow me, it's crystal clear and working perfectly!!! Then about 10 minutes later, my battery was running low, so I plugged in the power, and the problem returned!!

The machine has always been dual boot Ubuntu and factory installed Windows XP Pro, had some problems with Wireless in pre 6.06 and also 6.10. Installing Fiesty was a bit of a revelation, as everything just worked, except this strange issue. Here's the details....

I did a fresh, standard options installed from the i386 Desktop standard installer CD. Setup the wireless lan, checked Firefox was working ok, installed all the updates.. then loaded the latest .deb file for Skype from Skype.com. The sound quality is terrible, stuttering, distorted audio, verrrrrryyyy slloooooww and laggy.. just horrible really! Using XMMS or Totem plays videos and audio perfectly fine, via speakers and headphones. The Ubuntu sound theme general noises are fine too. As soon as I try to call the Skype call testing service (callto://echo123) the audio quality is absolutely dreadful!

I've tried disabling WLAN, and using the gigabit LAN onboard, same problem.
Another dedicated Ubuntu box I have works fine with 6.06LTS, so I know this CAN work!
Ekiga using Sipgate also suffers from the same audio corruption problem.

Here's the strange part...

I unplug the laptop PSU and run it on battery, instantly the audio starts working properly, plug the power back in, and it bladders it!

I thought, perhaps it's some CPU throttling thing, as on battery it runs at 800MHz, and on power it runs at the full 2GHz, yeah, I know it's the opposite to what you would expect the problem to be like...

Tried disabling CPU throttling, by installing cpufreqd rather than powernowd, the problem persists.

So, it doesn't matter if the CPU is running at 800Mhz or 2GHz, either way, if it's on battery, is works nicely, if it's on mains power, it stutters and corrupts like hell.

Also, the graphics speed is much slower on POWER, than it is on BATTERY! Using something like 3DDesk to spin the desktops round is blisteringly fast on battery power with the CPU at 800MHz, or stuttery and sluggish with it at 2Ghz on mains power.

Help, I'm baffled by this! I have since installed Beryl and that is working really sweetly... but the audio problem persists.... I don't want to have to keep unplugging the PSU when someone skypes me! :-D

Any suggestions or help much appreciated!

Mark

---

### Post by coffeecat on 2007-06-16
I've set my Vaio VGN-FS215B up as a multi-booter. I've noticed this issue with several recent distros. It doesn't just affect sound - everything slows down when the power is plugged in. With both Feisty and PCLinuxOS, I notice that even nautilus and konqueror are slower to open a subfolder when you double-click on its parent folder. And they both take ages to boot up with the power in. Interestingly, Dapper wasn't affected so I guess it's something to do with later kernels. Dapper used the 2.6.15 kernel and Feisty the 2.6.20 one. As far as I remember (too idle to boot it up and check) PCLinuxOS2007 is using the 2.6.18 kernel.

However, it can't be just the kernel version, it may be be how it's compiled. I'm also running Gentoo with a 2.6.20 kernel I compiled myself and I don't get this problem.

This is only a guess. I've not bothered to research it further. I simply choose whichever distro I want to boot into partly on the state of charge of the battery.

My only suggestion - install Gentoo and compile your own kernel. :wink:

---

### Post by Austin_KW on 2007-06-16
What about on power with the battery removed.

Also check for some sort of interrupt storm
watch cat /proc/interrupts (in a terminal)

Even if the cpu is not pinned high, high interrupt rate could cause jerky sound/graphics

---

### Post by mmcnamee on 2007-06-17
Thanks for the suggestions... I'm likely to stick with Ubuntu, because even with the issue the performance is acceptable, except for the audio problem of course! Even on power with degraded performance, spinning the desktop cube around with compiz/beryl is fast, with all the textures on high quality and transparency and all other options on!

Here's what I've tried..

Currently the kernel is booting with this command... (removed the UUID for clarity)
kernel		/vmlinuz-2.6.20-16-generic root=<snip>  ro quiet splash irqpoll

So, I tried removing irqpoll - same problem persists on power
Removed the battery and booted normally just on power, same problem
Without battery, without irqpoll - same
Without battery, without irqpoll, with noapic noacpi apic=false acpi=false  - same problem
Battery back in, added noacpi acpi=false - same problem, but different interrupt output from /proc/interrupts

Interestingly, checking /proc/interrupts with "watch -n 1" (every second) I can't see any noticeable difference whether it's on power or on battery..

Here's the output with irqpoll on, and with the battery in, but on power

--
           CPU0       
  0:      87651   IO-APIC-edge      timer
  1:        661   IO-APIC-edge      i8042
  8:          3   IO-APIC-edge      rtc
  9:        858   IO-APIC-fasteoi   acpi
 11:          3   IO-APIC-edge      sonypi
 12:        107   IO-APIC-edge      i8042
 14:       2386   IO-APIC-edge      libata
 15:          0   IO-APIC-edge      libata
 16:      38002   IO-APIC-fasteoi   HDA Intel, radeon@pci:0000:03:00.0
 17:      29761   IO-APIC-fasteoi   uhci_hcd:usb4, yenta
 18:       6633   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5, ohci1394
 19:          8   IO-APIC-fasteoi   uhci_hcd:usb2, tifm_7xx1
 20:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 21:       9835   IO-APIC-fasteoi   ipw2200
 22:      10614   IO-APIC-fasteoi   libata, eth0
NMI:          0 
LOC:      28511 
ERR:          0
MIS:          0
--

IRQ 0, 16, 17 were all the busiest, moving at around 300/s for IRQ0 and about 100-200/s for the other 2. That increased if I move a window around to hammer the graphics card a bit.

Without battery, so on power only, with the options
without irqpoll, with noapic noacpi apic=false acpi=false
I get this...

--
           CPU0       
  0:      42825    XT-PIC-XT        timer
  1:        255    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:       7958    XT-PIC-XT        uhci_hcd:usb1, ehci_hcd:usb5, ohci1394, ipw2200
  4:          0    XT-PIC-XT        uhci_hcd:usb3
  5:       8766    XT-PIC-XT        libata, eth0
  6:          8    XT-PIC-XT        uhci_hcd:usb2, tifm_7xx1
  7:      10475    XT-PIC-XT        uhci_hcd:usb4, yenta
  8:          3    XT-PIC-XT        rtc
  9:        116    XT-PIC-XT        acpi
 11:       9025    XT-PIC-XT        HDA Intel, sonypi, radeon@pci:0000:03:00.0
 12:        107    XT-PIC-XT        i8042
 14:       1428    XT-PIC-XT        libata
 15:          0    XT-PIC-XT        libata
NMI:          0 
LOC:       8039 
ERR:          0
MIS:          0
--

I ran this earlier on, so the values aren't as high yet... but the ones that are high were again the ones which were streaming lots of interrupts.

I wonder if it's worth writing a script to collect 10 minutes of Interrupt data into a CSV file, and plot a graph using OpenOffice to see if there are any trends...

As I said earlier, there's not a massive difference between the interrupts if I'm on power or battery only... which leads me to believe that this might be a slightly masked problem, perhaps kernel related?

Austin_KW - how many interrupts / second constitutes an interrupts storm?

Thanks for the help, it's much appreciated.

---

