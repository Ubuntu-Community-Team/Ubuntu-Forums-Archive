---
title: "Harddrive recurring error"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Linder on 2007-11-18
Hi there!

I get this error popping up several times during bootup and if I try to run a konsole (not the graphical, but ALT+F1) I get this error about once a second.


Syslog
```
Nov 18 09:25:07 Void kernel: [  928.001262] ata5: failed to resume link for reset (errno=-16)
Nov 18 09:25:07 Void kernel: [  928.001267] ata5: soft resetting port
Nov 18 09:25:07 Void kernel: [  928.001274] ata5: SATA link down (SStatus 1 SControl 300)
Nov 18 09:25:07 Void kernel: [  928.001282] ata5: EH complete
Nov 18 09:25:07 Void kernel: [  928.002715] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Nov 18 09:25:07 Void kernel: [  928.002718] ata5: (irq_stat 0x00000040, connection status changed)
```

Messages.log
```
Nov 18 09:25:07 Void kernel: [  928.001262] ata5: failed to resume link for reset (errno=-16)
Nov 18 09:25:07 Void kernel: [  928.001267] ata5: soft resetting port
Nov 18 09:25:07 Void kernel: [  928.001274] ata5: SATA link down (SStatus 1 SControl 300)
Nov 18 09:25:07 Void kernel: [  928.001282] ata5: EH complete
```
That on earth is all this? By the way, the first numbers (xxx.xxxxxx) change incremently for every line.

---

### Post by Tweenk on 2007-11-18
This looks like a hard disk related problem.

The solutions that come to my mind at the moment:
a) disable these messages from appearing by issuing **sudo dmesg -n1**
b) check if there are hard disk related options in BIOS and whether they affect this error or not.
c) replace the hardware.

I'm no expert so these are just wild guesses. Some information about the configuration of your disks would be useful, as well as the output of **lspci** and your Ubuntu and kernel version.

---

### Post by Linder on 2007-11-18
This particular error seem to be connected to using a RAID, however I am using no such configuration. It's a single S-ATA harddrive 500 Gb. Partitioned for 10 Gb WinXP, 50 Gb Root, 2 Gb Swap and the rest for /home. 

I've had errors show up on a file system check before, however not lately. Although this error has been appearing all since I got this new computer (and subsequently, since I installed Gutsy. Used to have Feisty.) I'll have a look in BIOS to check for RAID settings that should be turned off.

---

### Post by Linder on 2007-11-19
[IMG]http://img160.imageshack.us/img160/5210/bumpfu2.jpg[/IMG]

---

### Post by Linder on 2007-12-10
I did try the **sudo dmesg -n1** thing, and sure, it helps in removing the message from displaying in the console, however, it's still logged to syslog, kernel.log and messages.log, causing rampant growth in these files since the message repeats itself every other second or so. I have no idea how to solve this, and the harddrive works just fine and I've never had issues with it. I might also add that I did not have this message appear when I was running Ubuntu FF 7.04.

---

### Post by Eggbanjo on 2008-02-09
I've looked all over for a solution for this, its getting annoying now, not only is it filling up my logs, but ive been editing Xorg.conf and when that goes tits up i have to log in terminal i can't do anything because of the scrolling error message

I dont have sata drives on my system, ive run S.m.a.r.t on the only drive ive got and it passed, its pretty new (under 6mths), i dont experience this on any of the 2 other machines i have running gutsy.

The only difference between them and this one im getting an error on is. This one is dual core and a lot newer.

---

### Post by CleanSoap on 2008-02-18
I appear to be having this exact same error.
Running Ubuntu 7.10
Motherboard = Asus P5K
P35 Chipset
Hard Drive in question = WDC WD5000AAKS-0
SATA controller = 82801lB (ICH9)
Kernel 2.6.22-14 generic
Have a PATA device connected to the JMicron controller, both my HDDs are connected to the ICH9 controller.  I had twin 160 drives connected to said controller without issue, it was only when I removed one 160 GB drive and connected this new 500GB drive that the errors started.


Resolution attempts:
Same issue after replacing SATA cable.
Same issue when drive jumpered to SATA-I mode from default SATA-II mode.
Same issue after updating BIOS to latest revision (0902)
Same issue after changing SATA mode in BIOS from "Enhanced" to "Compatible"
Same issue after changing BIOS settings from "No PnP OS" to "PnP OS"




 Sample from /var/syslog:
```
Feb 18 10:18:10 soap-desktop kernel: [ 7357.522646] ata8: soft resetting port
Feb 18 10:18:10 soap-desktop kernel: [ 7357.522658] ata8: SATA link down (SStatus 0 SControl 300)
Feb 18 10:18:10 soap-desktop kernel: [ 7357.522667] ata8: EH complete
Feb 18 10:18:10 soap-desktop kernel: [ 7357.554029] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 18 10:18:10 soap-desktop kernel: [ 7357.554035] ata8: (irq_stat 0x00000040, connection status changed)
Feb 18 10:18:12 soap-desktop kernel: [ 7358.777733] ata8: soft resetting port
Feb 18 10:18:12 soap-desktop kernel: [ 7358.777746] ata8: SATA link down (SStatus 0 SControl 300)
Feb 18 10:18:12 soap-desktop kernel: [ 7358.777755] ata8: EH complete
Feb 18 10:18:12 soap-desktop kernel: [ 7358.838387] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 18 10:18:12 soap-desktop kernel: [ 7358.838393] ata8: (irq_stat 0x00000040, connection status changed)
Feb 18 10:18:12 soap-desktop kernel: [ 7359.553167] ata8: soft resetting port
Feb 18 10:18:12 soap-desktop kernel: [ 7359.553178] ata8: SATA link down (SStatus 0 SControl 300)
Feb 18 10:18:12 soap-desktop kernel: [ 7359.553186] ata8: EH complete
Feb 18 10:18:13 soap-desktop kernel: [ 7359.738226] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 18 10:18:13 soap-desktop kernel: [ 7359.738231] ata8: (irq_stat 0x00000040, connection status changed)
```

Of course it says "ata8" now, seems to change number every reboot:
```
Feb 17 19:54:18 soap-desktop kernel: [12336.863771] ata2: EH complete
Feb 17 19:54:21 soap-desktop kernel: [12338.998240] ata2: soft resetting port
Feb 17 19:54:21 soap-desktop kernel: [12338.998251] ata2: SATA link down (SStatus 0 SControl 300)
Feb 17 19:54:21 soap-desktop kernel: [12338.998260] ata2: EH complete
Feb 17 19:54:21 soap-desktop kernel: [12339.845647] ata2: soft resetting port
Feb 17 19:54:21 soap-desktop kernel: [12339.845658] ata2: SATA link down (SStatus 0 SControl 300)
Feb 17 19:54:21 soap-desktop kernel: [12339.845666] ata2: EH complete
Feb 17 19:54:23 soap-desktop kernel: [12340.984841] ata2: soft resetting port
Feb 17 19:54:23 soap-desktop kernel: [12340.984851] ata2: SATA link down (SStatus 0 SControl 300)
```

Drive appears to work fine.
Drive is brand new.

lspci output:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
```

---

### Post by ThArGos on 2008-02-21
Hi!
I have the exact same problem...

Moreover, I have the same motherboard : ASUS P5K
I have 2 IDE drives plugged on the sata bridge and a sata dvdwriter.

I run debian lenny with 2.6.22-3-686

here is a part of kern.log:

```
Feb 21 13:41:42 karl kernel: ata2: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 21 13:41:42 karl kernel: ata2: (irq_stat 0x00000040, connection status changed)
Feb 21 13:41:42 karl kernel: ata2: soft resetting port
Feb 21 13:41:42 karl kernel: ata2: SATA link down (SStatus 0 SControl 300)
Feb 21 13:41:42 karl kernel: ata2: EH complete
Feb 21 13:42:07 karl kernel: ata2: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 21 13:42:07 karl kernel: ata2: (irq_stat 0x00000040, connection status changed)
Feb 21 13:42:07 karl kernel: ata2: soft resetting port
Feb 21 13:42:07 karl kernel: ata2: SATA link down (SStatus 0 SControl 300)
Feb 21 13:42:07 karl kernel: ata2: EH complete
Feb 21 13:42:25 karl kernel: ata2: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 21 13:42:25 karl kernel: ata2: (irq_stat 0x00000040, connection status changed)
Feb 21 13:42:26 karl kernel: ata2: soft resetting port
Feb 21 13:42:26 karl kernel: ata2: SATA link down (SStatus 0 SControl 300)
Feb 21 13:42:26 karl kernel: ata2: EH complete
Feb 21 13:42:55 karl kernel: ata2: exception Emask 0x10 SAct 0x0 SErr 0x4060000 action 0x2 frozen
Feb 21 13:42:55 karl kernel: ata2: (irq_stat 0x00000040, connection status changed)
Feb 21 13:42:55 karl kernel: ata2: soft resetting port
Feb 21 13:42:55 karl kernel: ata2: SATA link down (SStatus 0 SControl 300)
Feb 21 13:42:55 karl kernel: ata2: EH complete

```

What option should we disable in the bios?
I don't use RAID technology.

This is particularly annoying in console mode.
Thanks for your feedback, I go on with my researches.

---

### Post by ThArGos on 2008-02-22
I think I have found a solution.

In the P5K Bios, I changed the following setting:
From
Main > Sata configuration > Sata configuration : [Enabled]
To
Main > Sata configuration > Sata configuration : [Disabled]

Hope it helps. I haven't got anymore errors since... but it may be a coincidence.

---

### Post by CleanSoap on 2008-02-22
> **ThArGos said:**
> I think I have found a solution.

In the P5K Bios, I changed the following setting:
From
Main > Sata configuration > Sata configuration : [Enabled]
To
Main > Sata configuration > Sata configuration : [Disabled]

Hope it helps. I haven't got anymore errors since... but it may be a coincidence.

That would (to my untrained eye) appear to fix any SATA problems by disabling the SATA controller.  Am I right?  

While my DVD drive is on the PATA, my hard drives are SATA.  I did not experience this issue when I had twin 160GB SATA drives, only after I upgraded my /home drive to the above mentioned 500GB SATA drive.

---

### Post by ThArGos on 2008-02-23
Indeed ! I realised this morning that my dvd wasn't enabled anymore.
so I put it  to [compatible] instead of [enhanced]
Now dvd is working and I haven't got the error.

So it seems that the option [enhanced] causes troubles on my configuration.

---

### Post by CleanSoap on 2008-02-23
> **CleanSoap said:**
> I appear to be having this exact same error.
Resolution attempts:
Same issue after replacing SATA cable.
Same issue when drive jumpered to SATA-I mode from default SATA-II mode.
Same issue after updating BIOS to latest revision (0902)
**Same issue after changing SATA mode in BIOS from "Enhanced" to "Compatible"**    

EDIT:  Formatting

---

### Post by CleanSoap on 2008-02-24
As there were a lot of ICH9 related fixes made in Linux kernel 2.6.24, I will try an Ubuntu 8.04 live CD later this week, and see if that fixes the problem.

---

### Post by ThArGos on 2008-02-25
Oh sorry for the noise then :-/

I didn't read carefully. Anyway it worked for me (well it seems)

---

### Post by BorrajaX on 2008-02-29
Same trouble, same motherboard (Asus P5k)

Indeed, disabling the Sata controller solves the problem, but is not a great solution, because my main hard drive is Sata... I'm using a Usb HD but...

---

### Post by Eggbanjo on 2008-02-29
after weeks/months of having this issue i think (hasnt happened again sine) i found the issue.

I was leaving my pc on over night to download, coming back to find it frozen, also found that if i left it for more than 20mins it would freeze to.

What i did was go into bios and change Upnp Os from NO to YES

no more log error messages, no more freezing!!!

---

### Post by CleanSoap on 2008-02-29
> **Eggbanjo said:**
> after weeks/months of having this issue i think (hasnt happened again sine) i found the issue.

I was leaving my pc on over night to download, coming back to find it frozen, also found that if i left it for more than 20mins it would freeze to.

What i did was go into bios and change Upnp Os from NO to YES

no more log error messages, no more freezing!!!

> **CleanSoap said:**
> I appear to be having this exact same error.
Running Ubuntu 7.10
Motherboard = Asus P5K
P35 Chipset
Hard Drive in question = WDC WD5000AAKS-0
SATA controller = 82801lB (ICH9)
Kernel 2.6.22-14 generic
Have a PATA device connected to the JMicron controller, both my HDDs are connected to the ICH9 controller.  I had twin 160 drives connected to said controller without issue, it was only when I removed one 160 GB drive and connected this new 500GB drive that the errors started.


Resolution attempts:
Same issue after replacing SATA cable.
Same issue when drive jumpered to SATA-I mode from default SATA-II mode.
Same issue after updating BIOS to latest revision (0902)
Same issue after changing SATA mode in BIOS from "Enhanced" to "Compatible"
**Same issue after changing BIOS settings from "No PnP OS" to "PnP OS"**


Glad it worked for you.  What motherboard and SATA chipset do you have?

I'm back from my business trip (no such problems on my Dell D820 thankfully) - and will test 8.04 soon.

---

### Post by CleanSoap on 2008-03-01
The Ubuntu 8.04 live CD failed to boot to a GUI, and kicked me to a text prompt which spat ata2 errors at me, not at all dissimilar to the ones before:
```
<I didn't write down the times>l: ata2:COMRESET failed (errno=-32)
<I didn't write down the times>l: ata2:COMRESET failed (errno=-32)
<I didn't write down the times>l: ata2:COMRESET failed (errno=-32)
<I didn't write down the times>l: ata2:Reset failed, giving up
```

---

### Post by Linder on 2008-03-04
Just wanted to add that my motherboard is indeed Asus P5k as well.

---

### Post by BorrajaX on 2008-03-11
Well... IN MY CASE, disabling the JMicron Ide controller works for not getting these error messages... but as a counterpart, I (obviously) lose my DVD reader (an Ide unit... ).

Not a great solution, I guess!! :( 

There seems to be something wrong with this JMicron controller (or at least, with the kernel module that controlls it). I found [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/198871")

Did anyone get a long-term solution? I mean... disabling my hard disk drives doesn't seem a very good one!! :)

---

### Post by CleanSoap on 2008-03-12
> **BorrajaX said:**
> Well... IN MY CASE, disabling the JMicron Ide controller works for not getting these error messages... but as a counterpart, I (obviously) lose my DVD reader (an Ide unit... ).

Not a great solution, I guess!! :( 

There seems to be something wrong with this JMicron controller (or at least, with the kernel module that controlls it). I found [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/198871")

Did anyone get a long-term solution? I mean... disabling my hard disk drives doesn't seem a very good one!! :)

That is very interesting, and something I am willing to test, but I am still curious why this problem only started immediately after installing a new 500GB HDD on the other controller?

---

### Post by BorrajaX on 2008-03-18
Mmm... I don't know what to say. In my case, it appeared suddently. I hadn't noticed anything wrong until a few days ago.I dno't know if it has been a kernel update or so.

I Windows (with the JMicron controller enabled) I don't see any error messages, but you know how Windows works...Maybe the errors are still there but aren't considered "relevants" :D

---

### Post by Linder on 2008-03-25
> **BorrajaX said:**
> Well... IN MY CASE, disabling the JMicron Ide controller works for not getting these error messages... but as a counterpart, I (obviously) lose my DVD reader (an Ide unit... ).

Not a great solution, I guess!! :( 

There seems to be something wrong with this JMicron controller (or at least, with the kernel module that controlls it). I found [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/198871")

Did anyone get a long-term solution? I mean... disabling my hard disk drives doesn't seem a very good one!! :)

Disabling the JMicron controller works for me too. I don't use and IDE devices, so for me it's  semi-permanent solution, but a bugfix for this issue would indeed be very nice. Currently typing this from Ubuntu 8.04 LTS Hardy Heron x64 LiveCD. It would not boot before I disabled the JMicron controller.

---

### Post by tienhn on 2008-04-10
Thanks so much for this post! This issue has driven me nut for a week.
In deed, disable JMicron IDE controller did the trick. I keep changing hard drive, cables, etc. to no avail.

Cheers.:guitar:

---

### Post by Linder on 2008-04-11
> **tienhn said:**
> Thanks so much for this post! This issue has driven me nut for a week.
In deed, disable JMicron IDE controller did the trick. I keep changing hard drive, cables, etc. to no avail.

Cheers.:guitar:

You're welcome. However, disabling the JMicron really isn't an alternative for many people due to them using IDE drives. For us that use only S-ATA drives, it's a workaround, but still not really acceptable.

---

### Post by Mr. Wishes on 2008-06-07
Just for the record, I'm getting the exact same error, again with an asus P5K. Also, I sometimes get crippling surges of hard drive activity for no apparent reason. By 'crippling', I mean that I can hear my (SATA) hard drive seeking like mad, and the whole system starts lagging terribly - sometimes it gets better again, but sometimes it lags more and more until I am forced to do a hard reset (after ~10 minutes).

I will try disabling the JMicron controller - I've had issues with that controller even in Windows, so I'm not too surprised that disabling it might fix the issue, but like many, my cd-rom drive is PATA, making this an annoying solution.

---

