---
title: "Forced suspensions with dapper"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by Saladino on 2006-06-13
Hi,
Since I upgraded from breezy to dapper i've been experimenting a forced suspension every 3 or 4 minutes. I've no choice, it doesn't matter what am i doing. I've been looking through the system and looks like anacron and apmd daemons are misunderstanding each other.
Ive tried installing dapper from the CD and even using it as live cd and the same situation.
Some info from my laptop
root@etxea:/home/etxea# tail -30 /var/log/syslog
Jun 13 12:42:01 etxea anacron[4707]: Normal exit (1 job run)
Jun 13 12:42:30 etxea anacron[5554]: Anacron 2.3 started on 2006-06-13
Jun 13 12:42:30 etxea anacron[5554]: Normal exit (0 jobs run)
Jun 13 12:42:34 etxea apmd[4208]: Proxy exited with status 1
Jun 13 12:42:34 etxea apmd[4208]: Standby rejected by proxy
Jun 13 12:42:34 etxea apmd[4208]: Standing by now
Jun 13 12:42:38 etxea anacron[5611]: Anacron 2.3 started on 2006-06-13
Jun 13 12:42:38 etxea anacron[5611]: Normal exit (0 jobs run)
Jun 13 12:43:26 etxea kernel: [  546.969995] spurious 8259A interrupt: IRQ7.
Jun 13 12:44:30 etxea anacron[5676]: Anacron 2.3 started on 2006-06-13
Jun 13 12:44:30 etxea anacron[5676]: Normal exit (0 jobs run)
Jun 13 12:44:34 etxea apmd[4208]: Proxy exited with status 1
Jun 13 12:44:34 etxea apmd[4208]: Standby rejected by proxy
Jun 13 12:44:34 etxea apmd[4208]: Standing by now
Jun 13 12:44:39 etxea anacron[5733]: Anacron 2.3 started on 2006-06-13
Jun 13 12:44:39 etxea anacron[5733]: Normal exit (0 jobs run)
Jun 13 12:46:33 etxea anacron[5800]: Anacron 2.3 started on 2006-06-13
Jun 13 12:46:33 etxea anacron[5800]: Normal exit (0 jobs run)
Jun 13 12:46:37 etxea apmd[4208]: Proxy exited with status 1
Jun 13 12:46:37 etxea apmd[4208]: Standby rejected by proxy
Jun 13 12:46:37 etxea apmd[4208]: Standing by now
Jun 13 12:46:41 etxea anacron[5858]: Anacron 2.3 started on 2006-06-13
Jun 13 12:46:41 etxea anacron[5858]: Normal exit (0 jobs run)
Jun 13 12:48:42 etxea anacron[5927]: Anacron 2.3 started on 2006-06-13
Jun 13 12:48:42 etxea anacron[5927]: Normal exit (0 jobs run)
Jun 13 12:48:46 etxea apmd[4208]: Proxy exited with status 1
Jun 13 12:48:46 etxea apmd[4208]: Standby rejected by proxy
Jun 13 12:48:46 etxea apmd[4208]: Standing by now
Jun 13 12:48:50 etxea anacron[5985]: Anacron 2.3 started on 2006-06-13
Jun 13 12:48:50 etxea anacron[5985]: Normal exit (0 jobs run)

root@etxea:/home/etxea# lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 31)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
0000:00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
0000:00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:03.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

Thanks for your time

---

### Post by targaman on 2006-07-19
I appear to have exactly the same problem, with the same hardware (ie SiS 630 etc). I get a virtually identical screendump and the problem is not consistent because sometimes I can run all day without a hassle, and at other times it will go into this mode after anything between 3 and ten minutes.

I posted about my problem yesterday in another thread about "screen goes blank after ~10 min" (sorry I don't know how to find and link back to it), but I now think that this thread is where the problem will be solved.

Thanks to all.

---

### Post by sanskbn on 2007-02-05
I had the same problem and I could solve it editing the grub init info:
sudo vi /boot/grub/menu.lst
In every line that begins with kernel add acpi=force at the end

I hope it helps you.

---

