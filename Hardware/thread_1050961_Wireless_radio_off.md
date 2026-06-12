---
title: "Wireless radio off"
date: 2009-01-26
forum: Hardware
---

### Post by spacedcowboy on 2009-01-26
Hi,

I'm pretty new to ubuntu/linux as I come from an apple/bsd world..

I'm having difficulty getting the wireless working on a clients laptop running ubunutu 8.10, it's an Acer Aspire 1642WLMi.

I have checked the BIOS for a setting to keep the wireless on, or controlled by software but there is nothing I can see. I have tried pressing FN-F2 not sure why, some others on there have suggested it, there's no dedicated button for the wireless I can see.

The only device I can see in Network Manager is the wired interface eth0. Nothing else is showing.

I'm assuming I need to somehow turn the radio on and everything will work.

My config files should be as default as I've not made any changes..

Here's the tech output...

sharon@sharons-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
sharon@sharons-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.




When I try set the power or anything on the card I get the following error

sharon@sharons-laptop:~$ sudo iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.

---

### Post by spacedcowboy on 2009-01-26
I've found the problem..

And its very straight forward.. there is a tiny transparent bar on the front of the computer, that needs to be pressed, there's no feedback to let you know it's been pressed other than by going in to terminal.

I pressed that, rebooted and the wireless card is functioning, I've not had time to test it but hopefully it'll stay working!

---

