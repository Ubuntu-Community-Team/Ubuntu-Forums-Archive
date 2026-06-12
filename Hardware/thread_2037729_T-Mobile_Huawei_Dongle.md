---
title: "T-Mobile Huawei Dongle"
date: 2012-08-05
forum: Hardware
---

### Post by Osric1 on 2012-08-05
Hi guys,

Having trouble with getting a Huawei E3131 Dongle to work. I have looked at the available documentation but either cannot make sense of it or it hasn't worked. As far as I can make out running lsusb is part of the diagnostic process so I will include the relevant line in the hope that it may assist. I cannot cut and paste because I'm having to use another computer to do this message., so I am having to do this by hand:

Bus 001 Device 004: ID 12d1:1f01 Huawei Technologies Co., Ltd

Any help would be much appreciated as the laptop belongs to a friend of mine and having rescued it from taking a half hour to  boot up Windows by installing Ubuntu I've ended up being tech support. The chap is laid up following a serious motorcycle accident and this is is window on the world at the moment. 

Many thanks

---

### Post by trundlenut on 2012-08-05
If I recall correctly, when you plug the dongle in it also shows up as a cd and you need to eject it before it is recognised as a dongle.

I can't remember the exact model of Huawei dongle I was using, I don't have it to hand at the moment.

---

### Post by Osric1 on 2012-08-06
Thanks for your help, I tried what you suggested but I suspect that performing the eject function kicks in the usb_modeswitch which in this case does not seem to work with the E3131.  I'm pretty sure this is a usb_modeswitch issue as the dongle is being read as a memory stick at the moment. The last dongle the bloke had I was able to set up in about 5 minutes, but this is a brand new one and without running the windows software which tells the computer to alter how it reads the dongle from a storage device to a mobile internet USB it gets stuck in "storage device mode". usb_modeswitch is supposed to mimic this in unbuntu, but it doesn't always work. I know there is a workaround but the only one I could find was in Polish and its pretty complicated so not much use. I'm hoping that someone will have come across this issue here and be able to explain it 1. In English, and 2. in terms a novice can understand, as with the best will in the world manually configuring usb_modeswitch when the instructions are in  Polish is a tall order.

Thankyou for your reply.

---

### Post by trundlenut on 2012-08-07
Do you have another (windows) computer you could try it in.  if it is brand new with a brand new simcard I think there is some kind of one time setup that needs to be down to register the sim card and get it up and running in the first place.

---

### Post by Osric1 on 2012-08-08
Good suggestion. I just tried it but no joy, its not an account activation issue and the installation of the windows software only affects how that particular PC reads it.  Its definitely a matter of getting usb_modeswitch to work to alter the way Ubuntu recognises the hardware and read it as an internet connection instead of a storage device. My friend will just have to buy another dongle and wait for usb_modeswitch to be updated to work for an E3131, or someone comes up with the workaround in a format I have a prayer of following.

Its a bit of a bummer really having bigged up Ubuntu. Fortunately his previously installed version of windows was too slow to use and it was either Ubuntu or new computer. Teach me to involve myself really, once you involve yourself in someone's PC you end up being tech support in perpetuity.

---

### Post by evaristo1974 on 2012-10-17
Is a translation from Spanish to English by google, 
Hello today I managed to install the usb stick, you must log as user graphical as root, copy the files from the usb stick in a new folder in the Users folder, the file install, you make clik at properties, permissions, and change it to read-write root for all, grab the terminal, make place yourself in that new folder of files, run. / install and the modem is installed ... I did all this with the sim inserted .. . a greeting:guitar:

for all people needs libusb, usbmodeswitch

---

### Post by evaristo1974 on 2012-11-01
greetings to all,,, today I installed the same way, the usb dongle in ubuntu 10.04 64 bit dongle copy files in the user's folder, a new folder with the name you want, and run as graphical user root in the command. / install after changing everything to root permissions, read write, etc..
to install everything I needed lib-usb, usbmodeswicth, and tcl

google translation of the Spanish

---

