---
title: "Managed to get wireless to work but..."
date: 2008-05-14
forum: Hardware
---

### Post by carlolovearianne on 2008-05-14
Hi everybody.

I've been using Hardy on my 2 month old Asus A8HE laptop (check out [https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8HE](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8HE)) and everything is working great, especially now that I finally got the wireless to work. No small thanks to the post I found at [WWW] [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#). That post was truly life-affirming:).

However, I still have a few of issues that I will greatly appreciate if it gets solved:

1. Webcam. The Asus A8HE's got a built-in webcam and I'm truly at my wits end on how to get it to work. I tried installing EasyCam2 and unfortunately it didn't worked. Hope anybody can help.

2. VCDs doesn't work. Is there a way to play VCDs without installing mPlayer? 

3. Can anybody suggest a dvd ripper that *actually* works?:)  What I'm looking to do is to rip my dvds and convert them to mp4s. 

4. When I try to burn cds (whether a music cd or a data cd) I end up with a useless (but shiny) silver coaster. I tried using Brasero and Nautilus but it doesn't work. DVD burning works flawlessly, though. Am I missing something?

---

### Post by balagosa on 2008-05-14
> **carlolovearianne said:**
> 

1. Webcam. The Asus A8HE's got a built-in webcam and I'm truly at my wits end on how to get it to work. I tried installing EasyCam2 and unfortunately it didn't worked. Hope anybody can help.

2. VCDs doesn't work. Is there a way to play VCDs without installing mPlayer? 

3. Can anybody suggest a dvd ripper that *actually* works?:)  What I'm looking to do is to rip my dvds and convert them to mp4s. 

4. When I try to burn cds (whether a music cd or a data cd) I end up with a useless (but shiny) silver coaster. I tried using Brasero and Nautilus but it doesn't work. DVD burning works flawlessly, though. Am I missing something?

kudos to Asus A8HE User. :lolflag:

anyways,

1) please type in and post the outcome of
```
lsusb
```

I typed this in and i got a certain USB ID without a name aside from the **0000:0000**. it was the **built-in webcam.**

you can search a driver for this.

2) hmmm....not that i know of? maybe you can mount a VCD and get it's files but playing a movie without a mplayer?? 

3)havent tried this yet. all i tried was Burning with brasero.

4) hmmm....might be hardware problems? i tried burning a CD on 7.10 and it was flawless (as testified by MD5 checksum). to be specific, i burned a C&C Generals (Image) to the CD.

---

### Post by carlolovearianne on 2008-05-14
Here's the lsusb results:

```
Bus 005 Device 002: ID 174f:aa11  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
```

I don't know where to start :)

---

### Post by carlolovearianne on 2008-05-14
I did a little web searching and managed to downloaded the stk11xx driver for my webcam. ([http://www.qbik.ch/usb/devices/showdev.php?id=435](http://www.qbik.ch/usb/devices/showdev.php?id=435)) It's a tar.gz file and sitting on my desktop at the moment. 

I don't know what to do with it and I'm clueless right now:)

There is a link from the address above on how to install it but it's in German.

Please help.

---

### Post by balagosa on 2008-05-14
carlo, please clarify if your camera is supported in Linux.

because i got sources from two websites saying that 174f:aa11 isnt supported on linux. tough luck. i also have the same prob.

[Website 1]("http://www.qbik.ch/usb/devices/search_res.php?pattern=Cam")

[Website 2]("http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html")

---

### Post by carlolovearianne on 2008-05-14
I just checked the sites ,so I guess tough luck indeed, huh? Well I could live without the webcam and it wasn't that too much of a big deal, anyway. I just thought that it would be nice if I could get it to work. Anyway the wireless is working perfectly, no connection drop outs... We just can't win them all :).

And apart from the webcam and a few nibbles, my laptop is working (almost) perfectly. I love it. 

And big thanks to Canonical! I just recieved a copy of Ubuntu and Kubuntu 8.04 that I requested back in April 22nd. I can throw away the cheapo dvd-r I burned the Hardy ISO a few weeks ago :)

Long live Ubuntu!

---

### Post by balagosa on 2008-05-14
but do not loose hope though. just keep updated. those sites i referred to you were old. just keep searching the net for your Cam Driver.

i even heard that my Cam now has a Driver, just released months ago.

---

### Post by balagosa on 2008-05-15
carlo...i got good news.

i got my built-in Cam workign with USB ID: 
Bus 006 Device 002: ID 174f:5a11 Syntek

weird though...

i want you to execute this command carlo, because this made my cam work

```
sudo update-usbid
```

i would like to thank nicedude for giving me an idea, he had one post where he said updating pci ids by

```
sudo update-pciid
```

---

### Post by carlolovearianne on 2008-05-15
Thanks.

I ran the command and i got a sudo: update-usbid: command not found.


Anything you did before running sudo: update-usbid?

---

### Post by carlolovearianne on 2008-05-15
Thanks man.

I tries it with an "s" (sudo update usbids) and I got this: 

```
--11:24:11--  http://linux-usb.sourceforge.net/usb.ids
           => `/var/lib/misc/usb.ids.new'
Resolving linux-usb.sourceforge.net... 66.35.250.209
Connecting to linux-usb.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 347,477 (339K) [text/plain]

100%[====================================>] 347,477       88.81K/s    ETA 00:00

11:24:16 (80.85 KB/s) - `/var/lib/misc/usb.ids.new' saved [347477/347477]
```

Then I ran lsusb. Here is the result:

Bus 005 Device 002: ID 174f:aa11 Syntek Web Cam
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Whereas before it was:


Bus 005 Device 002: ID 174f:aa11  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Did it work for you straight away?

I have Cheese installed and its not working (yet) sadly.

---

