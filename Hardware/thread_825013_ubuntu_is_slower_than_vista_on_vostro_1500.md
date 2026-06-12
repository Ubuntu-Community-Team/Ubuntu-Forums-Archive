---
title: "ubuntu is slower than vista on vostro 1500"
date: 2008-06-10
forum: Hardware
---

### Post by noobuntu_ger on 2008-06-10
Hi
i put ubuntu 8.04 on my vostro a couple of days ago. Everything works fine. I got the mic to work The only thing that really bugs me is that ubuntu is so slow !!! I already have the feeling it is slower than vista on my vostro !!! It shouldn't be because of old hardware. I have a 2 Ghz processor and 3 gig ram and 8600 gt.

Has anybody an idea why.

---

### Post by sdennie on 2008-06-10
Define "slower".  It's hard to know what needs to be fixed without more details.

---

### Post by noobuntu_ger on 2008-06-10
for example the compiz fusion animations are really jerky and it takes a second switching tabs in firefox. Also when i write something in pidgin my writing doesnt appear instantly.

---

### Post by stchman on 2008-06-10
> **noobuntu_ger said:**
> Hi
i put ubuntu 8.04 on my vostro a couple of days ago. Everything works fine. I got the mic to work The only thing that really bugs me is that ubuntu is so slow !!! I already have the feeling it is slower than vista on my vostro !!! It shouldn't be because of old hardware. I have a 2 Ghz processor and 3 gig ram and 8600 gt.

Has anybody an idea why.

Did you install the restricted driver for your Nvidia card?

---

### Post by Yellow Pasque on 2008-06-10
Are you using the amd64 version or the i386? Try Swiftweasel (link in sig).
Also, could you run some commands for us, so we get a better sense of your hardware?
```
sudo update-pciids
sudo lspci
```

---

### Post by noobuntu_ger on 2008-06-10
After the installation of ubuntu the hardware driver window popped up and I installed the nvidia driver it suggested. That was a restricted driver. i installed the i386 version because i was a little bit afraid of the 64 version because i haven't used ubuntu since 6.10 release. 
```
xxx@xxx-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01) 


```

---

### Post by Yellow Pasque on 2008-06-10
> i was a little bit afraid of the 64 version because i haven't used ubuntu since 6.10 release
I would suggest installing a fresh 64-bit Hardy on another partition (you can resize) and you'll see the difference.

---

### Post by sdennie on 2008-06-10
If you are using nvidia on a laptop and compiz is slow, this is probably related to PowerMizer.  I'd turn off Desktop Effects and see if Firefox is any faster.  If it is, you may have to force PowerMizer into its highest state with a script or modprobe hack.  There are dozens of threads about how to do this on this forum and the nvidia forum.  My method of choice is [http://ubuntuforums.org/showthread.php?t=747294](http://ubuntuforums.org/showthread.php?t=747294) however, I don't know if that will work with your particular card.

The other possibility is that you've set compiz vsync and auto-detect refresh rate.  It probably won't work.  Go to System->Preferences->Advanced Desktop Effects->General Options->Display Settings and uncheck "Detect Refresh Rate" and manually move the slider to 60.  If you don't have Advanced Desktop Effects under System->Preferences, this probably isn't your issue as I believe that vsync is off by default.

---

### Post by noobuntu_ger on 2008-06-11
i uninstalled my nvidia driver and followed the link in stchmans sig. It is really the powermizer which causes the trouble. It always is in performence level 0. Can i change its behaviour manually or do i have to use a hack ?

---

### Post by sdennie on 2008-06-11
At the moment there are only hacks to control PowerMizer.  Nvidia has said they are going to release a driver that has PowerMizer controls but, they didn't say when so, it could be 2 weeks or 2 years ("never" is also a reasonable timeframe for them).

---

### Post by noobuntu_ger on 2008-06-13
Thank you very much for your help. I'm going to install a 64 bit version and I have one last question. Were do i put the 99-nvidia.sh and the nvidia-power.sh ?

---

### Post by sdennie on 2008-06-13
That's kind of a tricky question.  If you look at the top of the long script, it has installation instructions however, the part about /etc/acpi/resume.d is no longer valid in Hardy.  This means that you can still use the functionality fine on startup/battery/ac but, if you, for instance, suspend on battery and resume on AC, it won't bring you up to full speed.  I haven't come up with a fix for Hardy yet.

To install the shorter script, I would do the following:

```

cd
mkdir bin
mv whatever_you_called_the_script bin
chmod +x bin/whatever_you_called_the_script

```

Then, you can just go to System->Preferences->Sessions and add a new startup item that runs "/home/your_username/bin/whatever_you_called_the_script".

Hope that helps.

---

### Post by noobuntu_ger on 2008-06-13
Thanks

---

