---
title: "USB 2/3 device descriptor read64, error -110"
date: 2010-10-31
forum: Hardware
---

### Post by wcorey on 2010-10-31
I am trying to install Ubuntu Server 10.10 on a Dell XPS-9000. Previous versions worked as this was my NC for UEC. With 10.10 after the install and reboot I get the error

USB 2/3 device descriptor read64, error -110 three times followed by

usb-2/3 device not accepting address 4, error -110
usb-2/3 device not accepting address 5, error -110

hub 2-0:1.0 unable to enumerate usb device on port 3

followed by a second series referring to usb-7/1

hub 7-0:1.0 unable to enumerate devices on port 1

I can not use the keyboard. 

The keyboard worked fine during the install and 
when I installed another competing Linux the keyboard and mouse worked fine after the install.

Can anyone tell me what's going on?

---

### Post by IcarusR on 2010-10-31
If you do a google search for this you will see threads on loads of forums going back years, 2004, & not limited to debian derivatives.

I guess it is something to do with how the kernel interacts with / sets up the USB system.
The distro without the problem probable handled setting up USB in a different way to Ubuntu 10.10.

Have you tried booting with ps2 keyboard ? If so does usb keyboard work after bootup ?

Have you tried going back to Lucid kernel, or even installing Lucid.

I tend to say clear of new versions for a while to let the bugs get ironed out.

---

### Post by wcorey on 2010-10-31
> **IcarusR said:**
> If you do a google search for this you will see threads on loads of forums going back years, 2004, & not limited to debian derivatives.

I guess it is something to do with how the kernel interacts with / sets up the USB system.
The distro without the problem probable handled setting up USB in a different way to Ubuntu 10.10.

Have you tried booting with ps2 keyboard ? If so does usb keyboard work after bootup ?

Have you tried going back to Lucid kernel, or even installing Lucid.

I tend to say clear of new versions for a while to let the bugs get ironed out.

And I generally do precisely that, stay away from new releases (Including especially Microsoft's) until they work the bugs out. What I didn't mention before is from the very same cd I installed Ubuntu 10.10 cloud onto a new Dell XPS 9100. It installed flawlessly and I see no issues with USB at all. The 9100 is the new UEC cluster controller. The existing 9000 was and is the UEC node controller.

So to answer the obvious question of if it worked ok on 10.4 why don't I just go back to 10.4.  Because what comes with 10.10 is UEC 2.0 based upon Eucalyptus 2.0. What this has over Eucalyptus 1.62 is better ... well better everything, support for Windows, support for virtIO, cloud-init to improve image startup and deployment. These all requires 10.10 as Eucalyptus 2 can not be installed on top of 10.4.

All of the forums over the years .... like they guy who said his USB ports haven't worked in 18months?? As I mentioned, it worked fine during the install script. It works fine with F13, It worked fine with U10.4. It works fine on 10.10 on a Dell XPS 9100, which I can not see the difference between the 9100 and 9000. 

No, I don't see anything of interest in the google results...it worked on 10.4 and works on F13. It also works, 10.10 exact same cd, on xps 9100.

I guess my question really was what would cause this issue which seems unique to that machine and that OS. 

Something else that is different, not to conflate this problem with another is both of those machines (from Dell) came with Win 7 installed, both have Raid 1 configured. On the 9100 U10.10 installed fine with RAID 1 still active in BIOS and configuring for RAID and LVM while I could not get the 9000 to install with RAID and LVM, only with RAID.. 

Here is what is in dmesg

[    1.762268] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.762281] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.762295] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.762298] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.762318] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.762342] ehci_hcd 0000:00:1a.7: debug port 1
[    1.766212] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.766224] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8c00000
[    1.785878] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.785989] hub 1-0:1.0: USB hub found
[    1.785993] hub 1-0:1.0: 6 ports detected
[    1.786046]   alloc irq_desc for 23 on node -1
[    1.786047]   alloc kstat_irqs on node -1
[    1.786051] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.786060] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.786063] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.786091] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.786111] ehci_hcd 0000:00:1d.7: debug port 1
[    1.789987] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.789998] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8e00000
[    1.805828] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.805926] hub 2-0:1.0: USB hub found
[    1.805929] hub 2-0:1.0: 6 ports detected
[    1.805978] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.805986] uhci_hcd: USB Universal Host Controller Interface driver
[    1.806021] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.806027] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.806030] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.806051] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.806080] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a400
[    1.806153] hub 3-0:1.0: USB hub found
[    1.806156] hub 3-0:1.0: 2 ports detected
[    1.806198]   alloc irq_desc for 21 on node -1
[    1.806200]   alloc kstat_irqs on node -1
[    1.806203] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.806208] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.806210] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.806230] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.806257] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a480
[    1.806328] hub 4-0:1.0: USB hub found
[    1.806331] hub 4-0:1.0: 2 ports detected
[    1.806331] hub 4-0:1.0: 2 ports detected
[    1.806372] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.806376] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.806379] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.806399] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.806427] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000a800
[    1.806500] hub 5-0:1.0: USB hub found
[    1.806502] hub 5-0:1.0: 2 ports detected
[    1.806543] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.806547] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.806550] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.806575] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.806595] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a880
[    1.806668] hub 6-0:1.0: USB hub found
[    1.806671] hub 6-0:1.0: 2 ports detected
[    1.806713] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.806717] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.806720] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.806743] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.806764] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ac00
[    1.806839] hub 7-0:1.0: USB hub found
[    1.806841] hub 7-0:1.0: 2 ports detected
[    1.806885] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.806889] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.806892] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.806914] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.806934] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b000
[    1.807007] hub 8-0:1.0: USB hub found
[    1.807009] hub 8-0:1.0: 2 ports detected
[    1.807083] PNP: No PS/2 controller found. Probing ports directly.
[    1.809249] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.809255] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.809308] mice: PS/2 mouse device common for all mice
[    1.809378] rtc_cmos 00:03: RTC can wake from S4


Then a little while later....

[    2.127623] usb 2-3: new high speed USB device using ehci_hcd and address 2


Then later after establishing the bridge br0

[   14.865418] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.286034] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.286168] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   15.286170] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   15.286171] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   17.205193] usb 2-3: device descriptor read/64, error -110
[   18.242523] br0: port 1(eth0) entering forwarding state
[   19.609606] br0: no IPv6 routers present
[   19.968092] eth0: no IPv6 routers present
[   25.132422] virbr0: no IPv6 routers present
[   25.701322] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   26.254454] lo: Disabled Privacy Extensions
[   26.369926] aoe: AoE v47 initialised.
[   32.390179] usb 2-3: device descriptor read/64, error -110
[   32.619453] usb 2-3: new high speed USB device using ehci_hcd and address 3
[   47.693228] usb 2-3: device descriptor read/64, error -110
[   62.876661] usb 2-3: device descriptor read/64, error -110
[   63.105976] usb 2-3: new high speed USB device using ehci_hcd and address 4
[   73.494138] usb 2-3: device not accepting address 4, error -110
[   73.613786] usb 2-3: new high speed USB device using ehci_hcd and address 5
[   84.001871] usb 2-3: device not accepting address 5, error -110
[   84.001897] hub 2-0:1.0: unable to enumerate USB device on port 3
[   84.500385] usb 7-1: new full speed USB device using uhci_hcd and address 2
[   99.575222] usb 7-1: device descriptor read/64, error -110
[  114.776212] usb 7-1: device descriptor read/64, error -110
[  115.008152] usb 7-1: new full speed USB device using uhci_hcd and address 3
[  130.086945] usb 7-1: device descriptor read/64, error -110
[  145.277947] usb 7-1: device descriptor read/64, error -110
[  145.507390] usb 7-1: new full speed USB device using uhci_hcd and address 4
[  155.905032] usb 7-1: device not accepting address 4, error -110
[  156.020414] usb 7-1: new full speed USB device using uhci_hcd and address 5
[  166.413698] usb 7-1: device not accepting address 5, error -110
[  166.413724] hub 7-0:1.0: unable to enumerate USB device on port 1
[  166.692984] usb 7-2: new low speed USB device using uhci_hcd and address 6
[  167.161781] usb 8-1: new low speed USB device using uhci_hcd and address 2
[  167.395087] usbcore: registered new interface driver hiddev
[  167.410061] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input2
[  167.410172] generic-usb 0003:04CA:0027.0001: input,hidraw0: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input0
[  167.450812] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input3
[  167.450978] generic-usb 0003:04CA:0027.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:1d.2-1/input1
[  167.451003] usbcore: registered new interface driver usbhid
[  167.451007] usbhid: USB HID core driver
[  167.630621] usb 8-2: new low speed USB device using uhci_hcd and address 3
[  167.822993] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4
[  167.823130] generic-usb 0003:0461:4D65.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-2/input0


At this point the keyboard is 'dead'. I would expect the mouse to be dead as it is a non GUI interface.

What's interesting is this went from a high speed USB to a low speed USB. Maybe that is normal, I can't say.

The other question regarding the ps/2 plug is no, it's been years since machines have shipped with the old style keyboard and mouse plug. Everything now is USB.

lsusb shows: Machine with dead keyboard
walt@cor9000:~$ lsusb
Bus 008 Device 003: ID 0461:4d65 Primax Electronics, Ltd 
Bus 008 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 006: ID 04eb:e033 Northstar Systems, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

machine with live keyboard

walt@cor9100:~$ lsusb
Bus 008 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04eb:e033 Northstar Systems, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


It turns out, on the effected machine the keyboard is not dead, per se as the num lock and caps lock lights respond to the respective buttons. Its just the login message can not be responded to. From all outward appearances, the keyboard and enter key are dead.

---

### Post by wcorey on 2010-10-31
Something caught my eye after looking at some of the other threads. In one of them it mentioned something about power. I disconnected the machine, not shutdown -P and reconnected the power cord.

Not only was I able to format with LVM as I was with the 9100 but after the reinstall there are no errant messages about the usb ports but the keyboard works perfectly. 

There was also something I hadn't mentioned previously that during the install when prompted for locale it took a couple of minutes before hitting enter selected English, or anything else. This time it took the enter key right away. Who'd have thought power off / power on sequence would have resolved so much.

---

### Post by nikeairj on 2010-11-20
> **wcorey said:**
> Something caught my eye after looking at some of the other threads. In one of them it mentioned something about power. I disconnected the machine, not shutdown -P and reconnected the power cord.

Not only was I able to format with LVM as I was with the 9100 but after the reinstall there are no errant messages about the usb ports but the keyboard works perfectly. 

There was also something I hadn't mentioned previously that during the install when prompted for locale it took a couple of minutes before hitting enter selected English, or anything else. This time it took the enter key right away. Who'd have thought power off / power on sequence would have resolved so much.

Perfect! I had the same problem. Disconnecting my computer from power fixed it. That's pretty odd, too. I'm glad it works now.

---

### Post by SpinUp on 2011-02-02
Thanks for posting this -- I also had this error showing up, and a long lag during the USB section of the BIOS loading, as reported in some other threads.  The result for me was that the onboard bluetooth adaptor wasn't working.

Shutdown, unplugged for 5 minutes, replugged, and now the lag is gone, bluetooth is working.  Wonderful!

---

### Post by SystemTester on 2011-03-04
> **wcorey said:**
> Something caught my eye after looking at some of the other threads. In one of them it mentioned something about power. I disconnected the machine, not shutdown -P and reconnected the power cord.

Just posting in here confirming that this suggested fix also worked for my problem with "unable to enumerate USB device on port n" being the search parameters I have been using to troubleshoot.  I posted a complete breakdown over at an Australian Website ([here]("http://forums.whirlpool.net.au/forum-replies.cfm?t=1652883"))

---

### Post by vittynoz@yahoo.es on 2011-12-30
hello, it's so late but i've this problem too.

usb 4-4: device descriptor read/8, error -62

it's not clear for me
DO you disconnect the psu suddenly and wait for 5 minutes?

thanks

---

### Post by SpinUp on 2011-12-30
I'm not sure what you mean by suddenly -- are you considering giving your computer a verbal warning first?  :D

I did a normal shutdown first, if that's what you're asking.  The important thing seems to be to remove power for a few minutes so that some flip-flop resets itself.  I've had to repeat this trick several times in the intervening months, and it has worked every time. Doesn't seem like it should be necessary though...

---

### Post by stbcomp on 2013-03-26
> **wcorey said:**
> Something caught my eye after looking at some of the other threads. In one of them it mentioned something about power. I disconnected the machine, not shutdown -P and reconnected the power cord.

Not only was I able to format with LVM as I was with the 9100 but after the reinstall there are no errant messages about the usb ports but the keyboard works perfectly. 

There was also something I hadn't mentioned previously that during the install when prompted for locale it took a couple of minutes before hitting enter selected English, or anything else. This time it took the enter key right away. Who'd have thought power off / power on sequence would have resolved so much.

I've got to say, having read just about every forum over the last few days trying to fix this problem, and coming from a technical background, your fix struck me at first as not likely. But I figured what the heck it can't hurt to give it a go.
While the computer was off, I had time to actually think about the technicalities of it all, and realized that because a USB port is powered, that your fix is actually the only logical answer, hopefully long term as well.
Cheers and thanks for a simple fix to a hugely annoying problem.

---

### Post by panPsax on 2013-05-07
As others I spend time browsing Linux forums to solve "USB 2/3 device descriptor read64, error -110" error. Keyboard, mouse and tablet unavaiable.
It could looks absurd, but the solution is realy to shuttdown the computer, plug off the power cords and wait..
[h=1][/h]

---

### Post by Sulomania on 2014-01-12
> **stbcomp said:**
> I've got to say, having read just about every forum over the last few days trying to fix this problem, and coming from a technical background, your fix struck me at first as not likely. But I figured what the heck it can't hurt to give it a go.
While the computer was off, I had time to actually think about the technicalities of it all, and realized that because a USB port is powered, that your fix is actually the only logical answer, hopefully long term as well.
Cheers and thanks for a simple fix to a hugely annoying problem.

Hi,

I have read that error -110 means not enough power supplied  to the usb device. So, I was just thinking, can it be because the  computer cuts the power to the usb device due to heating or something?  (Maybe cuts the power depending on priority and usb has the lowest?) Then  when you remove the power cable, the computer cools down or does  something that enables it to supply power again to the usb port.

---

### Post by lacho8713 on 2014-08-06
> **Sulomania said:**
> Hi,

I have read that error -110 means not enough power supplied  to the usb device. So, I was just thinking, can it be because the  computer cuts the power to the usb device due to heating or something?  (Maybe cuts the power depending on priority and usb has the lowest?) Then  when you remove the power cable, the computer cools down or does  something that enables it to supply power again to the usb port.

Not really, since there shouldn't be any reason whatsoever for the motherboard's USB controller to stop power going to the USB port that is connected to an input device (which of course, is recognized by the OS's I/O interface). But instead, it has more to do on the configuration your motherboard provides regarding power saving.

For instance, I did have the same problem, but it actually happened just after I performed some tweaks on the UEFI interface, specifying for power balance. After having the errors ```
USB 2/3 device descriptor read64, error -32
``` and ```
USB 2/3 device descriptor read64, error -110
``` appear for me, I reverted the UEFI setting and nothing happened.

After coming here and looking at the suggested solution, I too realized that, well, it has to be this way. Mostly, since it was caused by me screwing around with power consumption and balancing on the motherboard, I guess it's only natural that I should allow any capacitor and/or transistor to be fully discharged before my changes take effect in the desired way.

---

### Post by mehaga on 2014-10-10
Four years later, this fixed my issue :) Thanks a lot.

---

