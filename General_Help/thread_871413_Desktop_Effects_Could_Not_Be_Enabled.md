---
title: "Desktop Effects Could Not Be Enabled"
date: 2008-07-26
forum: General Help
---

### Post by KeybladeSephi on 2008-07-26
Hi everyone. I have been having a lot of graphics problems a little after I installed Ubuntu and Compiz on my computer. Whenever I try to change my desktop effects to normal or extra, I get an alert saying "Desktop Effects Could Not Be Enabled". Also, when I boot up my system, my screen flickers and has small vertical green lines at the top of my screen. My cursor then turns to an X, and I get an error that states my computer is going to run on low graphics mode. I then have to configure my screen resolution to the correct resolution that I have (1280x800), and then continue. Since I was tired of that alert, I automatically set my computer to Low Graphics Mode (there was a checkbox to automatically set my computer to Low Graphics Mode). Do you have any ideas how I could fix these problems? Thanks :)

---

### Post by overdrank on 2008-07-26
> **KeybladeSephi said:**
> Hi everyone. I have been having a lot of graphics problems a little after I installed Ubuntu and Compiz on my computer. Whenever I try to change my desktop effects to normal or extra, I get an alert saying "Desktop Effects Could Not Be Enabled". Also, when I boot up my system, my screen flickers and has small vertical green lines at the top of my screen. My cursor then turns to an X, and I get an error that states my computer is going to run on low graphics mode. I then have to configure my screen resolution to the correct resolution that I have (1280x800), and then continue. Since I was tired of that alert, I automatically set my computer to Low Graphics Mode (there was a checkbox to automatically set my computer to Low Graphics Mode). Do you have any ideas how I could fix these problems? Thanks :)

Hi and what is the model of the graphics card? You can also look at the link in my signature FAQ's on the effects.

---

### Post by jombeewoof on 2008-07-27
Sounds like you don't have the correct driver installed for your video adapter. What do you have for a video card?

---

### Post by KeybladeSephi on 2008-07-27
Thanks for responding, everyone; how exactly do you find out what graphics and video card you use?

---

### Post by Vakman on 2008-07-27
To determine what card you have in terminal enter
```
lspci
```

---

### Post by KeybladeSephi on 2008-07-27
This is what came up:

```
keybladesephi@Sheila:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
```

---

### Post by Vakman on 2008-07-27
Not a card I am used to. Those people above who posted that should help them. If I think of anything I will post again.

---

### Post by heyshona_mjdewji on 2008-07-27
i seem to be having a similar problem when i try to get the graphics.  all it does is crash and then the vertical lines.  i dont know if my graphics card is not good enough or what.

i did that lspci on terminal and this is what i got

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


i asked and read other forums to try and force it into doing it but no success:(

---

### Post by Ryan_macy on 2008-07-27
It seems there is a problem with the UniCrome driver.

also note that most integrated graphic cards do not support 3d acceleration.

I think beryl may be out for you.

Check out : 

[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by KeybladeSephi on 2008-07-29
Any other help, anyone?

---

### Post by overdrank on 2008-07-29
> **KeybladeSephi said:**
> Any other help, anyone?

Ok you have the intel graphics and the usually work well with ubuntu and the desktop effects. What is the amount of memory in the system and how much is being shared with the intel chipset? this could be one the the issues on the graphics distortion.

---

### Post by KeybladeSephi on 2008-07-30
How exactly do I find out how much memory is being shared with my graphics card? When I was using Windows, I had 60 GB of memory, but my systems says 108.2. However, it shows two different hard drives (one's daemon) with exactly the same disk usage and free disk space. So I'm assuming i have 54.1 GB of memory.

---

### Post by overdrank on 2008-07-30
> **KeybladeSephi said:**
> How exactly do I find out how much memory is being shared with my graphics card? When I was using Windows, I had 60 GB of memory, but my systems says 108.2. However, it shows two different hard drives (one's daemon) with exactly the same disk usage and free disk space. So I'm assuming i have 54.1 GB of memory.

Hi and I am speaking of the memory not hard drive space that you are referring to. If you open up system monitor located under system, administration. It will show the amount of memory on the system, to find out how much is being shared with the graphics you will need to look in bios before the OS starts up. To enter bios is different on each system some are using the delete key and some use the F1.

---

### Post by KeybladeSephi on 2008-07-30
I have 494.1 MB of memory with 1.4 GB swap

---

### Post by lazerradial2003 on 2008-08-01
I'm also having this problem, same graphics card and no desktop effects, anyone have any ideas?

---

