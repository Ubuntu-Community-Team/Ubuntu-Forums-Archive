---
title: "Media Remote"
date: 2008-05-14
forum: Hardware
---

### Post by scottuss on 2008-05-14
Hi everyone,

I've just about totally switched to Hardy Heron but need a few little things sorting out. The main one now is my Media Centre remote control:

Its an RC118 and I've Googled this but not no avail. When plugged in the Infra red receiver lights up when a button is pressed on the remote and then stays on constantly where on Windows it only lights up when a button is pressed.

Can anyone help me getting this working properly on Hardy 64 bit?

Thanks in advance

Scott

---

### Post by scottuss on 2008-05-17
BUMP

anyone??

---

### Post by teaker1s on 2008-05-17
If its usb connected
```
lsusb
```
if it&#347; connected to motherboard internally 
```
lspci-v
```
from vendor and product id we can tell exact model and revision

---

### Post by scottuss on 2008-05-18
Cool! I got Bus 006 Device 003: ID 147a:e017 Formosa Industrial Computing, Inc.

I'll have a look around on Google, but if no joy will you be able to point me in the right direction?

---

### Post by teaker1s on 2008-05-18
sure no problems:popcorn: You will have to investigate below suggestions

There is the linux remote project "lirc" which there are some packages available. 
[http://www.lirc.org/]("http://www.lirc.org/")

Secondly I don't know your plans for this computer but 
mythbuntu-desktop is a package available
[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")


lastly and I would try all options first, someone appears to have made a driver
[http://www.undergroundcircus.net/ir501d.html]("http://www.undergroundcircus.net/ir501d.html")

---

### Post by scottuss on 2008-05-21
Thanks for the assistance. I've got lirc installed and been trying to configure it. I got a step closer in that my infra red receiver now lights up and then goes off, but then lights back up when a button is pressed on the remote. However, it then stays lit up. I'm just gonna give up on this 'cos it's not that big of a deal. Thanks for the help anyways!

---

### Post by stueng on 2008-06-02
Did you get anywhere with this, I just bought a remote and its coming up with this device id - I cant get it to work with lirc

---

### Post by stueng on 2008-06-03
I'm actually experiencing the same symptons you had - plug it in, flicks on and then off when a button is pressed it stays on continuously and repeatibly sends the same command; have to unplug it and plug it back in again so it reponds to the next button press but then the LED stays on again and it continuously sends the same command until unplugged again

---

### Post by scottuss on 2008-06-05
No I never managed to get any further with it. I think it's one of those small things that I'll have a really good go at when I get some spare time in the Summer! :lolflag:

I did read however (can't remember where) that lirc should be able to make it work. However, as you have confirmed, the only thing it does it turn the LED on and repeatedly flash etc. :confused:

---

### Post by stueng on 2008-06-05
I'm taking mine back to maplins, going to pick up a phillips MCE remote

---

### Post by gweaver on 2008-06-05
If you have a Sony Ericsson Phone and a Bluetooth adaptor, you can control your PC from your phone.
You can find instructions here: [http://ubuntuforums.org/showthread.php?t=5412](http://ubuntuforums.org/showthread.php?t=5412)
It works for me, but the keyboard shortcuts in VLC player don't seem to work:(

---

### Post by stueng on 2008-06-05
I have already setup my iPhone to control MythTV - but I still want a proper remote control... hopefully the phillips will do what I need

---

### Post by scottuss on 2008-07-12
I know this is a while ago since discussed but did you ever get the Philips remote and if so does it work ok with Ubuntu?

I might have to go get one if it did! :guitar:

---

### Post by henrynocjj on 2011-01-15
> **gweaver said:**
> If you have a Sony Ericsson Phone and a Bluetooth adaptor, you can control your PC from your phone.You can find instructions here: [http://ubuntuforums.org/showthread.php?t=5412](http://ubuntuforums.org/showthread.php?t=5412)It works for me, but the [[COLOR=#000000]keyboard[/COLOR]](http://www.powdershell.com/sv/publishing/staring-into-the-face-of-death-on-halloween.html) shortcuts in VLC player don't seem to workIs the problem with the my network here? Is there something wrong with the link? It cannot be opened.

---

