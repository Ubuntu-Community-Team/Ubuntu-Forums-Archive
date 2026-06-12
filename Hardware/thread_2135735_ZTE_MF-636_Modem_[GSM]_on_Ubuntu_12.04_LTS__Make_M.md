---
title: "ZTE MF-636 Modem [GSM] on Ubuntu 12.04 LTS : Make My Ubuntu &quot;HANGS&quot;"
date: 2013-04-15
forum: Hardware
---

### Post by ygat on 2013-04-15
Hello,

I have a problem with my modem [**ZTE MF-636 GSM**], every time I try to connect my laptop to the modem, my Ubuntu [12.04 LTS] always hangs and can't be used.

I don't know if the modem doesn't support the Ubuntu 12.04 LTS or there is another problem. Can anyone help solve this problem ..?

Please help me. Thank you ..

Regards

---

### Post by GeorgeVita on 2013-04-18
Hi **ygat**, try the following and post the results:

- boot your system without modem
- attach modem and wait to "hang"
- remove modem
- reboot
- open a terminal window by pressing CTRL-ALT-T (all keys together)
- execute the following command (note: I am using date "**Apr 19**" within search strings to minimize output lines, if you try it another day you have to adjust it)
```
cat /var/log/syslog | grep -i -e zte -e ttyUSB -e 19d2 | grep -i "Apr 19"
```
- copy the output of above command from terminal into a new post inside "code tags" (button with symbol **#** at message editor)

---

### Post by ygat on 2013-04-19
> **GeorgeVita said:**
> Hi **ygat**, try the following and post the results:

- boot your system without modem
- attach modem and wait to "hang"
- remove modem
- reboot
- open a terminal window by pressing CTRL-ALT-T (all keys together)
- execute the following command (note: I am using date "**Apr 19**" within search strings to minimize output lines, if you try it another day you have to adjust it)
```
cat /var/log/syslog | grep -i -e zte -e ttyUSB -e 19d2 | grep -i "Apr 19"
```
- copy the output of above command from terminal into a new post inside "code tags" (button with symbol **#** at message editor)

Hi **GeorgeVita**,

I've followed the above and it says something like this :
```

ygat@ygatbase:~$ cat /var/log/syslog | grep -i -e zte -e ttyUSB -e 19d2 | grep -i "Apr 20"
Apr 20 03:10:43 ygatbase kernel: [ 8619.155254] usb 2-1.1: New USB device found, idVendor=19d2, idProduct=2000
Apr 20 03:10:43 ygatbase kernel: [ 8619.155274] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:10:43 ygatbase kernel: [ 8619.155281] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:10:44 ygatbase kernel: [ 8620.246996] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Apr 20 03:10:45 ygatbase usb_modeswitch: switching device 19d2:2000 on 002/003
Apr 20 03:10:53 ygatbase kernel: [ 8628.466569] usb 2-1.1: New USB device found, idVendor=19d2, idProduct=0031
Apr 20 03:10:53 ygatbase kernel: [ 8628.466578] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:10:53 ygatbase kernel: [ 8628.466581] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:13:49 ygatbase modem-manager[898]: <info>  Loaded plugin ZTE
Apr 20 03:17:52 ygatbase kernel: [  263.584403] usb 2-1.1: New USB device found, idVendor=19d2, idProduct=2000
Apr 20 03:17:52 ygatbase kernel: [  263.584417] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:17:52 ygatbase kernel: [  263.584423] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:17:53 ygatbase kernel: [  264.636028] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Apr 20 03:17:53 ygatbase usb_modeswitch: switching device 19d2:2000 on 002/003
Apr 20 03:18:01 ygatbase kernel: [  272.667590] usb 2-1.1: New USB device found, idVendor=19d2, idProduct=0031
Apr 20 03:18:01 ygatbase kernel: [  272.667605] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:18:01 ygatbase kernel: [  272.667610] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:18:06 ygatbase kernel: [  277.387080] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
ygat@ygatbase:~$ 

```

The result are as above. Please, give me a solution...

---

### Post by GeorgeVita on 2013-04-20
> **ygat said:**
> Hi **GeorgeVita**,

I've followed the above and it says something like this :
```

ygat@ygatbase:~$ cat /var/log/syslog | grep -i -e zte -e ttyUSB -e 19d2 | grep -i "Apr 20"
Apr 20 03:10:43 ygatbase kernel: [ 8619.155254] usb 2-1.1: **New USB device found, idVendor=19d2, idProduct=2000**
Apr 20 03:10:43 ygatbase kernel: [ 8619.155274] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:10:43 ygatbase kernel: [ 8619.155281] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:10:44 ygatbase kernel: [ 8620.246996] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Apr 20 03:10:45 ygatbase usb_modeswitch: **switching device 19d2:2000** on 002/003
Apr 20 03:10:53 ygatbase kernel: [ 8628.466569] usb 2-1.1: **New USB device found, idVendor=19d2, idProduct=0031**
Apr 20 03:10:53 ygatbase kernel: [ 8628.466578] usb 2-1.1: Product: ZTE CDMA Technologies MSM
Apr 20 03:10:53 ygatbase kernel: [ 8628.466581] usb 2-1.1: Manufacturer: ZTE, Incorporated
Apr 20 03:13:49 ygatbase modem-manager[898]: <info>  **Loaded plugin ZTE**
...
Apr 20 03:18:06 ygatbase kernel: [  277.387080] usb 2-1.1: **GSM modem (1-port) converter now attached to ttyUSB0**
```

It seems that your modem is identified correctly and system switches peripheral state from "USB CDROM" (19d2:2000) to "USB 3G MODEM" (19d2:0031) but there aren't all the communication ports needed (ttyUSB0, ttyUSB1 and ttyUSB2). At first you have to search for any firmware update for the modem, looking at your 3G provider's website. My MF-636 had problems that corrected after flashing firmware V1.0.4B11 (downloaded from my local provider). It is safer to use your local firmware version as it may includes network parameters.

edit: or start from: [http://www.ztedevices.com/support/](http://www.ztedevices.com/support/) (enter country, type="Data Card", Product="MF636")

---

