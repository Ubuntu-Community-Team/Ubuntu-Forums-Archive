---
title: "USB Headphone"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by vassalle on 2005-03-22
Does anyone know how to configure USB headphones ? Im using Plantronics DSP-500 and its the only hardware that i cant get ubuntu to use. I could see it under device manager but thats about it.. theres no sound coming out from it.. can anyone help me out here ? One more thing, i also have a soundcard, which works well.. is there a way for me to choose which 'channel' the sound comes out from (ie soundcard or headphones?) hope u guys could help me out. Thanks in advance!

---

### Post by vassalle on 2005-03-22
anyway, managed to get it to work by editing my /etc/asound.conf. It did work but its really troublesome that i have to restart the computer just to get to use the headphones.. is there any other way for me to choose which channel to use that doesnt requires rebooting the computer ?

---

### Post by mips on 2005-03-23
I had a similair problem (DSP-300 same thing) and this solved my problem:

[http://www.ubuntuforums.org/showthread.php?t=18926&highlight=mips](http://www.ubuntuforums.org/showthread.php?t=18926&highlight=mips)

It now works even if I plug the headset in after the OS is loaded.

cheers
mips

---

### Post by j3x11 on 2007-10-27
I just got my Logitech Headset working by doing the following:
1. sudo gedit /etc/modprobe.d/alsa-base
2. Edited "options snd-usb-audio index=-2" to "options snd-usb-audio index=-1"
3. Saved
4. Rebooted.

I hope this helps. I did not however mange to get the USB MIC on the headset working..  Any help with this would be greatly appreciated.

---

### Post by maciekz on 2008-04-10
Hi,

I did above steps to make my Logiteh USB headphones work and they worked some time (like two days) then when I turned my PC on one day they were not working any more. I didn't change anything in alsa-base file - I still have options snd-usb-audio index=-1and snd_hda_intel keeps grabbing index 0 and I hear no sound in USB headphones. 

Do you know why this is ??

---

### Post by something458877 on 2008-04-24
Yeah I have the same problem but I cant fix it

---

### Post by maciekz on 2008-04-24
It turns out that in my case headphones sometimes work  and sometimes they just don't ;). It happens that when I listen to the music they suddenly stop working and I have to unplug and plug them to hear the sound again. I also had few cases that I had to restart my PC because pluging and unplging did not help.

So as you can see the whole thing is rather unstable ;(. I don't think this is hardware issue cause the headphones are brend new and work fine on MS Windows.

It is also anoying that when I plug them when the system is already runing I have to restart KMix to make it communicate with the headphones.

---

### Post by faraox on 2008-04-28
I have the same problem. Mi headphone works in Feisty, but yesterday, when i upgraded to Hardy, apparently don't work. lusb and dmesg detected:

Bus 002 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
[   43.483328] input: C-Media USB Headphone Set   as /class/input/input7
[   43.483328] input: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.0-1

But asound don't detect the headset:
asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Dummy
VirMIDI
ICH6

I made the change in /etc/modprobe.d/alsa-base and change snd-usb-audio to index -1.

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-1
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Any help?
Regards,

---

