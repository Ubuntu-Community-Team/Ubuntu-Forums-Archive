---
title: "Hauppauge 2250 / Not detected by 18.04 [was working in 12.04]"
date: 2018-09-08
forum: Hardware
---

### Post by dwsideri on 2018-09-08
OK, I'm upgrading my (admittedly very) old HTPC from Ubuntu 12.04 to Ubuntu 18.04, mostly because Plex Server could not update itself and my iOS apps needed the newer Plex Server. Years ago (2012) I installed a Hauppauge WinTV-HVR-2250, added some firmware files to Ubuntu and it worked pretty much effortlessly.

With a completely fresh install 18.04, I have not been able to get the OS to recognize the card. I have:
1. Installed packages from the Hauppauge PPA ([http://www.hauppauge.com/pages/support/support_hvr2250.html](http://www.hauppauge.com/pages/support/support_hvr2250.html))
2. Manually installed firmware according to [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250) (NOTE: this is exactly what I did for 12.04), also slightly more involved instructions at [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

First, there's some conflicting/confusing information out there. This page: [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255), indicates that the drivers are in kernels no later than version 4.2, so my kernel should be fine, right?

Second, my best guess is that the firmware modules are not being loaded. I put the five .fw files available from [http://www.steventoth.net/linux/hvr22xx/](http://www.steventoth.net/linux/hvr22xx/) in /lib/firmware, rebooted, and nothing. When I check dmesg or modprobe following reboots, there is no indication that any attempt was made to load the firmware, not even an error. I created a /lib/firmware/`uname -a` directory, moved the .fw files there, still nothing. lspci does not list the Hauppauge card.

Unless my approach is entirely wrong, it seems to me that the firmware is not being loaded by the kernel. How can I attempt to force the kernel to load the firmware or try to debug why it is not loading?

Current Situation:
Very vanilla installation of Ubuntu 18.04 Desktop, "Normal Installation"
Current kernel: 4.15.0-33
Motherboard: BIOSTAR TH61 ITX
CPU: Dual core Intel G620
Capture Card: Hauppauge WinTV-HVR-2250
(I know my hardware is old, but this is just a DVR box, it doesn't need to be anything special. Plus, it was working fine in 12.04)

---

### Post by Terry_Kramer on 2018-09-17
I've got the same problem.  Upgraded from 17.04 to 18.04 and no longer can get Tvheadend to find my Hauppauge 2255 card.  I also have a USB  ATSC Hauppauge WinTV-dualHD. Using the Hauppauge PPA. The WinTV-DualHD works fine. The 2255 not recognized. LSPCI -vnn shows the 2255 exactly like dwsideri  post.

---

### Post by dwsideri on 2018-09-26
> **Terry_Kramer said:**
> I've got the same problem.  Upgraded from 17.04 to 18.04 and no longer can get Tvheadend to find my Hauppauge 2255 card.  I also have a USB  ATSC Hauppauge WinTV-dualHD. Using the Hauppauge PPA. The WinTV-DualHD works fine. The 2255 not recognized. LSPCI -vnn shows the 2255 exactly like dwsideri  post.

I ultimately found a solution that was hidden deep in the details of other instructions.

First, copy the firmware from steventoth.net to /lib/firmware

Second, create a file /etc/modprobe.d/options with this in the first line:

options saa7164 card=8

Reboot, then it worked for me. I didn't need the Hauppage PPA at all. Use "ls /dev/dvb" and you should see "adapter0", "adapter1", etc., if the firmware loaded correctly. You can test it with Kaffeine before getting into the MythTV settings.

---

### Post by zikky on 2019-08-03
Hi to all ......I need help because I am new to linux so can someone help me to get my HVR 2250 to work it scan but no channels in analog i can get from my country mabe it's the error I am getting here...10.912666] saa7164 driver loaded
[   10.912837] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   10.912840] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 30, latency: 0, mmio: 0xfd800000
[   11.116049] saa7164_downloadfirmware() no first image
[   11.116058] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   11.178955] saa7164 0000:03:00.0: loading /lib/firmware/5.0.0-23-generic/NXP7164-2010-03-10.1.fw failed with error -20
[   11.765183] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   11.765184] saa7164_downloadfirmware() firmware loaded.
[   11.765187] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   11.765191] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.765192] saa7164_downloadfirmware() BSLSize = 0x0
[   11.765192] saa7164_downloadfirmware() Reserved = 0x0
[   11.765193] saa7164_downloadfirmware() Version = 0x1661c00
[   18.728161] saa7164_downloadimage() Image downloaded, booting...
[   18.840055] saa7164_downloadimage() Image booted successfully.
[   21.280152] saa7164_downloadimage() Image downloaded, booting...
[   22.912151] saa7164_downloadimage() Image booted successfully.
[   22.964565] saa7164[0]: Hauppauge eeprom: model=88061
[   23.705698] dvbdev: DVB: registering new adapter (saa7164)
[   23.705706] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   26.881824] dvbdev: DVB: registering new adapter (saa7164)
[   26.881830] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   26.917946] saa7164[0]: registered device video0 [mpeg]
[   27.144673] saa7164[0]: registered device video1 [mpeg]
[   27.356544] saa7164[0]: registered device vbi0 [vbi]
[   27.356627] saa7164[0]: registered device vbi1 [vbi]
[   30.730343] saa7164 0000:03:00.0: DVB: adapter 1 frontend 0 frequency 0 out of range (54000000..858000000)
[   33.796387] saa7164 0000:03:00.0: DVB: adapter 0 frontend 0 frequency 0 out of range (54000000..858000000)

---

### Post by zikky on 2019-08-03
If I can get the command in linux to fix the problem please post it and i will follow it or if i also need to remove/install it please post the command in linux to do it thanks.....

---

### Post by zikky on 2019-08-03
Btw useing ubuntu 
[h=2]18.04[/h]

---

### Post by zikky on 2019-08-03
Help please.......

---

### Post by oldos2er on 2019-08-03
Your request will be far more visible if you create a new thread for it. You can link back to this thread if you think it will help; and please give people information about your system, any error messages, etc.

---

### Post by zikky on 2019-08-04
> **oldos2er said:**
> Your request will be far more visible if you create a new thread for it. You can link back to this thread if you think it will help; and please give people information about your system, any error messages, etc.

thanks for the reply ...I will make a new thread for it.

---

### Post by ryanyoung on 2019-08-06
I installed the FW under the link "Installing [this firmware]("http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw") is all that is needed." and the card showed up in my Myth.

Now I need to figure out the rest!

[http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)

---

