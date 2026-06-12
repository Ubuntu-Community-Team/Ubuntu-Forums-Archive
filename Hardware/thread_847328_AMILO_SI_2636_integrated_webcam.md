---
title: "AMILO SI 2636 integrated webcam"
date: 2008-07-02
forum: Hardware
---

### Post by 64stefano64 on 2008-07-02
Dear all 

I have an Amilo SI 236 with an integrated webcam.

This webcam is working with vista but under linux no.

this is the messages i got after lanching Camorama: 

could not conect to video device (/dev/video0)
please check conection

and this after lsusb

stefano@stefano-linux:~$ lsusb
Bus 007 Device 005: ID 5986:0202 Bison 
Bus 007 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 059f:0c41 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
stefano@stefano-linux:~$ 

So it seems that ID 5986:0202 Bison  is the usb device detected but it does not work.

I have followed the post

[http://ubuntuforums.org/showthread.php?t=768937&highlight=INTEGRATED+webcam+amilo&page=2](http://ubuntuforums.org/showthread.php?t=768937&highlight=INTEGRATED+webcam+amilo&page=2)

but with no result at all.

Could anyone help me?

Many thanks

Stefano

---

### Post by linuxwizard on 2008-07-02
Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by 64stefano64 on 2008-07-02
Yes I did....  no results....

it is a major problems...

Stfano

---

### Post by 64stefano64 on 2008-07-03
this is the vista (windows ) .inf file

---

### Post by 64stefano64 on 2008-07-03
and this is the vista .ini file

---

### Post by Milan SPK on 2009-01-07
did you manage to get it working? i have the same laptop (and a girlfriend abroad ;) and i really hate booting vista just to use skype video

---

