---
title: "Ubuntu 8.10 on Toshiba R10-10W"
date: 2009-03-26
forum: Hardware
---

### Post by llelkes on 2009-03-26
Hi everyone!

I just delivered my new notebook **Toshiba Tecra R10-10W**. It was pre-installed with **Vista**, but I would like to use **Ubuntu** and **XP**.
I made 5 partitions (1 ntfs xp, 2 - test maybe later on Mac OS, 3 extended, 5 - ext3 ubuntu, 6 fat32 data).
For the first look the system semms to be ok.
I was using Ubuntu quite a time, but all the time there was something wat was not working 100% for me, but now I decided to **install all the stuff** for it - in between maybe learn linux a bit. Wright now I an using **GNOME** but also some KDE applications (like K3b, Ktorrent).

:) What is working:
    Bluetooth, network, wifi, sound, SD card reader,  ... and maybe a lot of thing what I did not recognize/mentioned here

:( What is not working - hardware stuff:
    **Suspend and hibernate** - after suspend the monitor did not came back
    **Fingerprint reader** - AES1600 on usb
    I seted up the **backlight** for my screen to **80%** but afre log in it comes with 100% and than goes back to 80%
    I checked '**dim dislpay when idle**' - it is working but sometimes - I do nothing - and is it blinking back to normal backlight

:( What is not working - software stuff:
    **Confirm file operation in Gnome**
        Delete in gnome - if I delete in gnome it goes without notification into trash (press del button) - configrm_trash in gnome-editor is checked
        move - if I accidently move a folder to an another it is moved without notification (it is happening sometimes with tachpad)
    **Sound in Skype** - is says the sound device is used by another program/process (ver. from skype page .deb version 8.04+)

:confused: Interesting behavior
    There is a switch (on/off) on the side of notebook to turn on wireless genaral - there is a switch on keyboard to turn on (fn + f8 ) - it is only on when I turn on both - how sould it work? I miss the point why shoud I turn on something 2 times?

:?: Not tested yet
    Webcam, external monitor, e-sata, 3g

Thanks for Your advices,
Laci

---

### Post by llelkes on 2009-05-12
:) I moved to Ubuntu 9.04
(The behavior of the notebook is similar to r600)

What is working:
Bluetooth, network, wifi, sound, SD card reader, webcam
Skype - need to unistalled pulse audio

3g - need to recompile the kernel - working only if it is switched on at boot up time
([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359474/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359474/+viewstatus))

What is not working:
Suspend and hibernate - problem with the screen - after suspend did not come back
Fingerprint reader - AES1600 on usb
external monitor

Not tested yet
e-sata

---

### Post by llelkes on 2009-07-23
Hi,
finally with toshset 1.75 the 3g is working

toshset -3g on

wright now I need only a nice gui 
(toshset-gui is nice but till now did not support 3g)

bye

---

