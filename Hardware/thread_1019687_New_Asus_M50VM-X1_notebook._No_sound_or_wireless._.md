---
title: "New Asus M50VM-X1 notebook. No sound or wireless.  Help Please!"
date: 2008-12-23
forum: Hardware
---

### Post by painterh on 2008-12-23
I have a new Asus M50VM-X1 with Vista pre-loaded and a fresh install of Intrepid.  I set up additional partitions so that my 250 GB hdd has 4 nearly equal partitions.  Vista was already setup with one for the Vista OS and one for data and I set up the other 2 as ext3 and did my install.  I used "Easy BCD" for bootloader and the install went flawlessly.  I now have a major issue.  No sound

I have been messing around trying to get the sound working and can't get any sound at all from speakers or headphones.  I have also read about problems with Pulse audio and Alsa compatibility concerning this notebook.  If anyone out there has some expertise in setting up notebook hardware (Asus in particular) I would really appreciate some help.  Thanks in advance for any help.

---

### Post by SketchyClown on 2009-02-01
painterh,

Thought I'd make a first post to try and help a fellow Asus owner. I have the M50VM-A1 with the Atheros wireless card and it is supported in 8.10 Intrepid out of the box. Not sure if yours has this card as Asus seems to use somewhat of a smorgasboard of cards in these laptops.

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


Mine has the Intel HDA soundcard.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Now, my sound didn't work either out of the box. I left the sound preferences all at default. If you right click the sound icon in the panel and open the volume controls I made sure they were all checked and maxxed out for starters, then I found this:

[http://www.linlap.com/wiki/Asus+M50VM](http://www.linlap.com/wiki/Asus+M50VM)

"Sound works in ALSA with &#8220;options snd-hda-intel model=3stack-dig&#8221; to the file /etc/modprobe.d/alsa-base."

I added that line to the alsa-base and presto, sound works flawlessly.

Hope this may help you.

---

