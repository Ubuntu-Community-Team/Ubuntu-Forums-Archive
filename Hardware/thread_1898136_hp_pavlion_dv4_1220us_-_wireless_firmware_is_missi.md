---
title: "hp pavlion dv4 1220us - wireless firmware is missing after update"
date: 2011-12-20
forum: Hardware
---

### Post by gilaadb on 2011-12-20
Hello everyone.
I'm quite new to linux and ubuntu. I have it installed for about a year now, alongside with windows 7.
Right now I am running ubuntu 11.10.
when I first installed it some time ago, I connected it to the network with a cable, then ubuntu got all the drivers needed and my wireless was working as it should.
a few days ago I've used the automatic updates after few months of not installing any new updates. since then my wireless network stopped working. right now it says "wireless is disabled by hardware switch" and before it said "firmware is missing" (i have no idea what made it change)

And now I'm, of course, looking for the way to get it back to work.
from searching the forum for a solution, I've found people ask for the following information in order to be able to help:

output for: sudo lshw -C network
```

PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d1100000-d1103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 70:5a:b6:b4:44:a6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.146 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:00:a9:a0:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```output for: lspci -nn
```

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Hewlett-Packard Company Device [103c:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
08:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
08:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
08:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
08:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
09:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```Thanks!

---

### Post by pytheas22 on 2011-12-20
Please post the output as well of:
```

dmesg | grep -e b43 -ie radio -ie firmware -ie wlan
sudo iwlist scan
ls /lib/firmware
sudo rfkill list
```

---

### Post by gilaadb on 2011-12-21
Thank you for you fast reply. sorry i wasn't here to respond sooner:

dmesg | grep -e b43 -ie radio -ie firmware -ie wlan
```

[    0.182495] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.212704] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.213026] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.143388] ene_ir: Firmware regs: c0 01
[   19.171447] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.383347] b43-pci-bridge 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.383361] b43-pci-bridge 0000:09:00.0: setting latency timer to 64
[   20.078067] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   20.169363] Registered led device: b43-phy0::tx
[   20.169382] Registered led device: b43-phy0::rx
[   20.169419] Registered led device: b43-phy0::radio
[   20.169444] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   21.717528] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
[   21.717534] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
[   21.717537] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

ls /lib/firmware
```

3.0.0-12-generic             korg
3.0.0-14-generic             lgs8g75.fw
3com                         libertas
acenic                       matrox
adaptec                      mrvl
advansys                     mts_cdma.fw
agere_ap_fw.bin              mts_edge.fw
agere_sta_fw.bin             mts_gsm.fw
aic94xx-seq.fw               mts_mt9234mu.fw
ar3k                         mts_mt9234zba.fw
ar7010_1_1.fw                mwl8335_duplex.fw
ar7010.fw                    mwl8k
ar9170-1.fw                  myri10ge_ethp_z8e.dat
ar9170-2.fw                  myri10ge_eth_z8e.dat
ar9170.fw                    myri10ge_rss_ethp_z8e.dat
ar9271.fw                    myri10ge_rss_eth_z8e.dat
asihpi                       myricom
ath3k-1.fw                   NPE-B
ath6k                        NPE-C
atmel_at76c502_3com.bin      ositech
atmel_at76c502.bin           phanfw.bin
atmel_at76c502d.bin          ql2100_fw.bin
atmel_at76c502e.bin          ql2200_fw.bin
atmel_at76c504_2958.bin      ql2300_fw.bin
atmel_at76c504a_2958.bin     ql2322_fw.bin
atmel_at76c504.bin           ql2400_fw.bin
atmel_at76c506.bin           ql2500_fw.bin
atmsar11.fw                  qlogic
av7110                       r128
bnx2                         radeon
bnx2x                        rt2561.bin
bnx2x-e1-4.8.53.0.fw         rt2561s.bin
bnx2x-e1-5.2.13.0.fw         rt2661.bin
bnx2x-e1-5.2.7.0.fw          rt2860.bin
bnx2x-e1h-4.8.53.0.fw        rt2870.bin
bnx2x-e1h-5.2.13.0.fw        rt3070.bin
bnx2x-e1h-5.2.7.0.fw         rt3071.bin
brcm                         rt3090.bin
carl9170-1.fw                rt73.bin
cis                          RTL8192E
cpia2                        RTL8192SE
cxgb3                        rtl_nic
cxgb4                        rtlwifi
dabusb                       s2250.fw
dsp56k                       s2250_loader.fw
dvb-fe-xc5000-1.6.114.fw     sb16
dvb-usb-dib0700-1.20.fw      scripts
dvb-usb-terratec-h5-drxk.fw  slicoss
e100                         sun
ea                           sxg
edgeport                     TDA7706_OM_v2.5.1_boot.txt
emi26                        TDA7706_OM_v3.0.2_boot.txt
emi62                        tehuti
ene-ub6250                   ti_3410.fw
ess                          ti_5052.fw
f2255usb.bin                 ti-connectivity
GPL-3                        tigon
hp                           tlg2300_firmware.bin
htc_7010.fw                  tr_smctr.bin
htc_9271.fw                  ttusb-budget
i2400m-fw-usb-1.4.sbcf       ueagle-atm
i2400m-fw-usb-1.5.sbcf       usbdux
i6050-fw-usb-1.5.sbcf        usbduxfast_firmware.bin
intelliport2.bin             usbdux_firmware.bin
ipw2100-1.3.fw               v4l-cx231xx-avcore-01.fw
ipw2100-1.3-i.fw             v4l-cx23418-apu.fw
ipw2100-1.3-p.fw             v4l-cx23418-cpu.fw
ipw2200-bss.fw               v4l-cx23418-dig.fw
ipw2200-ibss.fw              v4l-cx2341x-dec.fw
ipw2200-sniffer.fw           v4l-cx2341x-enc.fw
iwlwifi-1000-3.ucode         v4l-cx2341x-init.mpg
iwlwifi-1000-5.ucode         v4l-cx23885-avcore-01.fw
iwlwifi-100-5.ucode          v4l-cx23885-enc.fw
iwlwifi-3945-2.ucode         v4l-cx25840.fw
iwlwifi-4965-2.ucode         v4l-pvrusb2-24xxx-01.fw
iwlwifi-5000-1.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-5000-2.ucode         vicam
iwlwifi-5000-5.ucode         vntwusb.fw
iwlwifi-5150-2.ucode         vxge
iwlwifi-6000-4.ucode         WHENCE.ubuntu
iwlwifi-6000g2a-5.ucode      whiteheat.fw
iwlwifi-6000g2b-5.ucode      whiteheat_loader.fw
iwlwifi-6050-4.ucode         yam
iwlwifi-6050-5.ucode         yamaha
kaweth                       zd1201-ap.fw
keyspan                      zd1201.fw
keyspan_pda                  zd1211


```

sudo rfkill list
```

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by pytheas22 on 2011-12-21
You have the firmware for the driver installed on your system under /lib/firmware/brcm, but the driver (according to dmesg) seems to be looking for it at /lib/firmware/b43 instead for some reason.  This was the path to the firmware in older versions of Ubuntu but since open-source firmware was developed I think they changed it to brcm.  I'm not sure why an upgraded version of the driver could cause it to look for the firmware in a different place but this may just be a bug in the driver code.

In any case, I can think of two possible solutions.  The first and simplest is just to download the traditional b43 firmware and copy it into your /lib/firmware directory.  I have a copy of that firmware on my server at [http://www.burnthesorbonne.com/files/b43_firmware.tar.gz](http://www.burnthesorbonne.com/files/b43_firmware.tar.gz) or you can find it lots of other places around the Internet.  If you need specific instructions on how to copy the firmware into place just let me know.

Another solution is to use the "fwpostfix" parameter of the b43 driver to tell it where to look for the firmware.  To do that, first unload b43 and ssb (which depends on it) with:

```
sudo rmmod b43
sudo rmmod ssb
```

Then reload them, specifying the name of the firmware directory:
```

sudo modprobe b43 fwpostfix=b43
sudo modprobe ssb
sudo ifconfig wlan0 up
```

Then wait a few seconds and see if the wireless works in NetworkManager.

---

### Post by gilaadb on 2011-12-21
Ok, so I tried copying both folders from within that archive to /lib/firmware/ then I rebooted, and nothing has changed. (was this the right method anyway?)
I also tried the second solution and for the last command i get this result:
```

SIOCSIFFLAGS: No such file or directory

```

---

### Post by pytheas22 on 2011-12-22
> Ok, so I tried to copying both folders from within that archive to /lib/firmware/ then I rebooted, and nothing has changed. (was this the right method anyway?)

Yes, that's the right method, but are you sure the files were copied?  If everything went as expected you should have a /lib/firmware/b43 folder, with some other files inside of it.  Also make sure the permissions are alright on those files with:
```

chmod -R 755 /lib/firmware/b43
```

If this looks to be as it should, does the system still complain about not being able to find the firmware?  In other words, what is the output (after ensuring that /lib/firmware/b43 exists and rebooting) of:
```

dmesg | grep -e b43 -ie radio -ie firmware -ie wlan
```

---

### Post by gilaadb on 2011-12-22
There were two folders in that archive. I've copied them both. I had to use sudo of course (if thats what made you wonder).
I've entered the chmod command and rebooted. everything is still the same.

output taken from "ls b*", under /bin/firmware/
```

b43:
a0g0bsinitvals4.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  pcm5.fw
a0g0bsinitvals5.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  ucode11.fw
a0g0bsinitvals9.fw   b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode13.fw
a0g0initvals4.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode14.fw
a0g0initvals5.fw     b0g0bsinitvals5.fw   lp0initvals14.fw    ucode15.fw
a0g0initvals9.fw     b0g0bsinitvals9.fw   lp0initvals15.fw    ucode4.fw
a0g1bsinitvals13.fw  b0g0initvals13.fw    n0absinitvals11.fw  ucode5.fw
a0g1bsinitvals5.fw   b0g0initvals4.fw     n0bsinitvals11.fw   ucode9.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0initvals11.fw
a0g1initvals13.fw    b0g0initvals9.fw     pcm4.fw

b43legacy:
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw  b0g0initvals2.fw  pcm5.fw     ucode5.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode11.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw  b43               ucode2.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw  pcm4.fw           ucode4.fw

```

I've entered the chmod command and rebooted. its still not working.

the output you requested:
```

[    0.173417] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.210624] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210624] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.255306] ene_ir: Firmware regs: c1 01
[   19.275159] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.548823] b43-pci-bridge 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.548839] b43-pci-bridge 0000:09:00.0: setting latency timer to 64
[   20.265141] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   20.354211] Registered led device: b43-phy0::tx
[   20.354231] Registered led device: b43-phy0::rx
[   20.354272] Registered led device: b43-phy0::radio
[   20.354295] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   21.028323] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
[   21.028401] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
[   21.028440] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  207.129706] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
[  207.129723] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
[  207.129736] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```


thanks

---

### Post by pytheas22 on 2011-12-22
It looks like the firmware file it wants (something called ucode16_mimo.fw) still isn't there.  That was my fault; I should have checked to make sure that the firmware I asked you to download actually contained that file.

But the good news is that I did some more googling and found [this thread]("http://comments.gmane.org/gmane.linux.drivers.bcm54xx.devel/11581").  It seems from there that you can get the ucode16_mimo.fw file by downloading a different copy of the driver firmware and extracting it yourself.  To do that, run these commands (you will need to have an Internet connection for them to work; if you can't get a wired connection temporarily let me know):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
cd /tmp
wget http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
tar -xjvf broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
cd broadcom-wl-5.10.56.27.3/driver/wl_apsta
b43-fwcutter wl_prebuilt.o
sudo rm -r /lib/firmware/b43*
sudo cp -r b43/ /lib/firmware
sudo chmod -R 755 /lib/firmware/b43/
```

If it's not too much work, please post the output of all of these commands (several of them may have no output) so I can make sure everything goes as expected.

When you're done, reboot and hopefully the wireless will work.  If it still doesn't, please let me know the output after the reboot of:
```

dmesg | grep -e b43 -ie radio -ie firmware -ie wlan
```

---

### Post by gilaadb on 2011-12-22
Wooohoo!
Thanks a million pytheas22!!! :D
My wireless came back at the moment I've preformed the "cp" command.
Thank you very very much for all your efforts!
I've made a log file while running all those commands. But since everything is working I believe you won't be interested in it.
If it can help you in any way, or you want to see it for some reason, let me know and I'll send it to you.

Thank you! :popcorn:

---

### Post by pytheas22 on 2011-12-23
Glad it worked :)  No need to see the log file in that case.  It's interesting that the driver came up as soon as you ran the "cp" command; it must be smart enough now to monitor the firmware directory in real time instead of only when the driver is loaded.

Hopefully whatever caused this issue will be fixed soon, but for now enjoy Ubuntu :)

---

### Post by morphprince on 2012-02-06
Hi, 

I have the exact same problem but I also cannot get my wired connection to work. What steps must I take to do this  ?

I am sorry about posting on a solved topic but since it was the exact same device, there was no need to put out a new post.

---

### Post by pytheas22 on 2012-02-06
**morphprince**: probably the easiest approach will be to get your ethernet working, then use that to grab the stuff needed for the wireless.  But please post the output of the following commands so I'll know exactly where you stand:
```

lspci -nn
lshw -C Network
dmesg | grep -ie eth -ie b43 -ie wl
uname -a
cat /etc/issue
```

Since you don't currently have any way of getting online in Ubuntu, you can paste the output into a text file, save it and use a USB stick to transfer the file to a computer with Internet access in order to post the output here.

---

### Post by blahtrash on 2012-09-14
I didn't want to start a new thread but I'm also having problems with my dv4 wireless after an update. It shows the available wireless networks but won't connect.  When running hardwired after 10 minutes or so sometimes it will randomly connect to the network, but if I restart I have the same problems.

anthony@anthony-HP-Pavilion-dv4-Notebook-PC:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:84:0f:86
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:d1100000-d1103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:fd:81:c1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff

---

### Post by pytheas22 on 2012-09-15
**blahtrash**: first of all, I would check whether changing any settings on your router makes a difference.  Try using a different channel or changing the mode (e.g., if it is now in 11g and 11n mode, try switching to only 11g, or vice-versa).

If that doesn't work, try blacklisting the "wl" driver and using ndiswrapper instead.  There is a link [here]("http://forum.mandriva.com/en/viewtopic.php?t=123263") to a Windows driver that should support your card in ndiswrapper.  General instructions on configuring ndiswrapper are available [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

If yous till need more help, it would be useful to know the output of these commands after you try to connect:
```

lspci -nn
dmesg | grep -e wl -e eth1
sudo iwlist scan
```

---

