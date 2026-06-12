---
title: "Panasonic Toughbook CF-29 Sound, ect"
date: 2010-06-17
forum: Hardware
---

### Post by GardenPlantCulture on 2010-06-17
So I Love Ubuntu... So easy and stable to use... Both myself and little sister switched over yesterday after hating the windows 7 upgrades... But I am having two small problems... I have read through the forums but have not found a working fix yet so I can use your help... I need to get the sound working... I am having no luck what so ever... Second I would like to configure the touchscreen to work properly... Right now it senses my touch but the mouse is nowhere near my finger... Thank You for everyones help...

---

### Post by lidex on 2010-06-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by SikDuk on 2010-06-21
Hi , I'm a Linux nut too... I am also a tough book  enthusiast also.. I bought a CF29E , it had Win7 installed ,but the sound didn't work. I played with it for days and got low volume with everything unmuted and cranked . I put another HD in it with Hardy installed out of one of my cf-48's and it fired up but no sound and the hotkey method for volume doesn't work either.. I've dug and tried just about everything except upgrading the bios..Which I have a question on to put usb option in boot menu... I downloaded drivers while I was teasting out Win7 and nothing.. Drivers for linux and nothing.. I'm begining to think its the sound card on the board ((SUCKS:mad:))))) I hope maybe a bios upgrade would be the answer ,haven't tried it yet.. Theres no CD/DVD to use to run a live CD ,but I have one on its way... I'm not new ,but it's been awhile since I had this problem back around 6.06 dapper...I followed the code thats posted here and nothing happened... Here-

buk@buk-laptop:~$ sudo uname -a
sudo: unable to resolve host buk-laptop
[sudo] password for buk: 
Linux buk-laptop 2.6.24-28-generic #1 SMP Fri Jun 18 12:02:15 UTC 2010 i686 GNU/Linux
buk@buk-laptop:~$ sudo aplay -l
sudo: unable to resolve host buk-laptop
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
buk@buk-laptop:~$ sudo dpkg -l | grep "alsa"
sudo: unable to resolve host buk-laptop
ii  alsa-base                                  1.0.16-0ubuntu4                                            ALSA driver configuration files
ii  alsa-utils                                 1.0.15-3ubuntu2                                            ALSA utilities
rc  alsamixergui                               0.9.0rc2-1-9                                               graphical soundcard mixer for ALSA soundcard
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-1                                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.18-3                                                  GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.38-0ubuntu9                                            Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                                           Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                                            Simple DirectMedia Layer (with X11 and ALSA 
buk@buk-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
buk@buk-laptop:~$ head -n l /proc/asound/card*//codec#*
head: l: invalid number of lines
buk@buk-laptop:~$ 

This is the what came back... I'm stuck... This little box runs great with the wifi and very fast online at 1.2 mbps speed I get from My IP here in town... If I can get the sound to work I will be happy and any help would be appretiated ... Thank you...](*,)

---

### Post by SikDuk on 2010-06-21
The hotswappable dvd/cd just arrived , I hope this works...:guitar:

---

### Post by lidex on 2010-06-21
*SikDuk*
Do yourself a favor...only run commands with sudo when it's required. The commands I posted should be run as a regular user.

What do you get for this:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0
```

---

### Post by lidex on 2010-06-21
Ran across this thread for touchscreen:
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/panasonic-toughbook-cf-29-touch-screen-485053/]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/panasonic-toughbook-cf-29-touch-screen-485053/")

---

### Post by SikDuk on 2010-06-23
Thanks for input all.. I did it !!!! I had a feeling it was a hard ware and not software issue.. I went to panasonics sight and downloaded the BIOS upgrade for the CF-29E (mk2).I installed it to a floppy while I was in windows then flashed the bios ,rebooted and now we rock..the site [http://pc-dl.panasonic.co.jp/cgi-bin/itn/toughbook/dl01.cgi](http://pc-dl.panasonic.co.jp/cgi-bin/itn/toughbook/dl01.cgi)  you can download the manual for upgrading your bios right there too , I stongly suggest it.. It didn't like my ubuntu live cd's but it did like PCLinuxOS 2010 . So it's like breaking in new boots... reboot and keep working the bios and as the bios breaks in the live cd's will start running full throttle .. You can only do the install to floppy and flash process while booted into windows..:guitar:

---

### Post by SikDuk on 2010-06-25
Well it looks like flashing the bios did the trick...

---

