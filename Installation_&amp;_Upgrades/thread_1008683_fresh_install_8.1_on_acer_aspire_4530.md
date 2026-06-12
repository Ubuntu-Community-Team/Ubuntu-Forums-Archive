---
title: "fresh install 8.1 on acer aspire 4530"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by acnyc2000 on 2008-12-11
Hello peeps,
I am trying to install 8.1 via live-cd on my new laptop aspire 4530 without success, i have read though all the installation guide and it just wont budge. (i am going for dual OS)

I got 8.1 from the site and created the live-cd, when i tried to boot from cd without installing, ubuntu would run for a bit (you can see the bar moving back and forth) , then freezed up with caps lock flashing. Same thing happened when i tried to install ubuntu right away.

error as following:

end _request i/o error dev sr0 sector 1431624 (repeating couple times)
butter I/O error on decive sr 0 logical..... 
end _request i/o error dev sr0 sector 1431624
then a few more lines 
it stopped at

--[end trace 357eac136b8dd8b2  ]--

thats when caps lock started flashing...

spec: 
acer aspire 4530
amd athlon 64 x2 (1.9ghz 1mb l2cache)
nvidia geforce 9100m G turble cache
4 gig ram
802.11b/g WLAN Atheros AR50007EG wireless network adapter

---

### Post by Pumalite on 2008-12-11
This might help you:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by albinootje on 2008-12-11
Those errors are about your install cdrom.

You should check the md5sum of the iso image you've downloaded.
Those checksums are here : [http://releases.ubuntu.com/intrepid/MD5SUMS](http://releases.ubuntu.com/intrepid/MD5SUMS)

And burn the cdrom at a slower speed to be sure it is usable.

---

### Post by acnyc2000 on 2008-12-11
I have tried to re-download the file 4 times, burnt 5 times at 10x speed all with correct checksum, and yet they all failed the same way.

anything else i can try?

i tried to install fedora and it didnt work either

---

### Post by albinootje on 2008-12-11
Ouch, sorry to hear that :(

You could try installing with a usb-stick.
The newest Ubuntu has an option to easily create a bootable install usb-stick, but there are other options too, see here :
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Partyboi2 on 2008-12-11
You could also try using [[COLOR=Blue]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html") to install ubuntu

---

### Post by acnyc2000 on 2008-12-12
i used ubuntu 32bit and it worked, however everything is a bit slow. ie: scroll down a webpage each  scroll down takes about .5 sec to respond instead of smooth motion. Opening applications takes a sec to process too.

---

### Post by Siddhartha Koirala on 2008-12-31
I also managed to install 32bit. in my acer 4530. thought i was smart and somehow managed to get the wifi started.... but its tooooooooooooooooooooooo slow... so i thought i should update it and see. well still it made no effect infact my wifi also stoped... grrrrrrrrr..  so i would not suggest anyone useing the 32bit... however having said that i still have not come up with 64bit solution to this laptop. so if there is someone who can help please help... i'm sure there are lots of people out there with the same problem all over the world...... and happy new year everyone...

---

