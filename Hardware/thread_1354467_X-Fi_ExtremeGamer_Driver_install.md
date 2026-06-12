---
title: "X-Fi ExtremeGamer Driver install"
date: 2009-12-13
forum: Hardware
---

### Post by Killermadog on 2009-12-13
Hi,

I'm a noob to the Linux scene but I'm not dumb when it comes to computers and all that. Im trying to install the drivers for a X-Fi ExtremeGamer sound card but it wont work. 

I figured out how to get into the parent directory and i enter this command "make" and i get this in the terminal.
```
make -C /lib/modules/2.6.31-16-generic/build M=/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/madog/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2
madog@madog-desktop:~/Downloads/XFiDrv_Linux_Public_US_1.00$
```And when i run the "make install" command, i get this.
```
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.31-16-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1
madog@madog-desktop:~/Downloads/XFiDrv_Linux_Public_US_1.00$
```Can someone please tell me what im doing wrong or if I'm just SOL with this sound card?

Thank You,
Vince

---

### Post by raygj on 2009-12-14
i used the "alsa upgrade script" to upgrade alsa sound system to the latest sound drivers to auto detect and run my X-Fi sound card.go to the following link.
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")
[http://ubuntuforums.org/showpost.php?p=7942536&postcount=386]("http://ubuntuforums.org/showpost.php?p=7942536&postcount=386")
after upgrade right/click on your "puleaudio volume icon" in your desktop panel and left click on "Sound Preferences".
click on the hardware tab
left click on "SB X-Fi" and select the output profile(type of output=analog mono/stereo/suround version/digital.etc) you want the card to use.IE  Analog stereo output.
then left click on "Output" tab
then click "inside" the radio button to the left of "SB X-Fi Analog Stereo"
to switch sound output to your X-Fi card.

---

