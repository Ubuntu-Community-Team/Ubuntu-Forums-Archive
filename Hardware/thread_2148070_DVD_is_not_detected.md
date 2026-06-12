---
title: "DVD is not detected"
date: 2013-05-23
forum: Hardware
---

### Post by dimas869 on 2013-05-23
Hello, i am using Ubuntu 13.04 and i am trying to burn a .iso in a DVD but after i put the media in the driver does not get detected so i test putting a movie (DVD) and does not do anything either although CDs work properly

this is what i get from sudo lshw -C disk

*-cdrom
       description: DVD-RAM writer
       product: DVDRRW GSA-H21N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: D700
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by 2F4U on 2013-05-24
Can you read a data dvd? If yes, did you install the required codecs to watch a movie dvd?

---

### Post by grahammechanical on 2013-05-24
You could try going to System Settings>Details>Removable Media and seeing what setting you have for Select How Media Should be Handled. During much of the development cycle of 13.04 I could not even get an audio CD to play let alone burn an ISO. But it got fixed by release date. The fact that you are able to play audio CDs suggests that you should be able to play a video DVD with the right codecs and burn an ISO image.

Regards.

---

### Post by dimas869 on 2013-05-24
I had installed restricted extras, DeVeDe, K3b and like i am saying, so far had been only working the CDs as data storage, music or empthy media...and in the system manager everything is been confire to ask whar to do...other media is set to consider it a music DVD and suppose to also ask what to do

---

