---
title: "Ubuntu on Toshiba Satellite A135-S4467 Notebook"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by almedson on 2007-04-24
Hi, 

I have a problem to install ubuntu linux on my Toshiba A135-S4467 notebook.
The sound card was not recognized neither Realtek 8101E 10/100 NIC  ethernet card.

 Toshiba A135-S4467 Laptop
    * Intel Core 2 Duo T5200
    * 15.4&#8243; Widescreen (1280×800)
    * 1 GB RAM
    * 160 GB 5400 RPM Hard Drive
    * DVD-RW/DL
    * Intel 3945ABG wireless
    * Realtek 8101E 10/100 NIC
    * 4 in 1 card reader
    * 1394 mini / 4 USB


Can anybody help me?

Regards,

Almedson

---

### Post by briangry on 2007-04-28
Are you sure the sound wasn't recognized?

On my 135-S4467, running 64 bit Ubuntu, the sound is recognized - snd_hda_intel is loaded - but it's producing no sound. I verified the mixers were at full volume. The previous version of Ubuntu worked fine.

I can't speak to the wired network adapter - never tried it.

---

### Post by dagrump on 2007-04-28
I have a toshiba a105-s4397, which looks to be the weak little sister to your machine & most everything works w/ feisty & dapper. I can't remember having to do anything to get sound working. You might rt.click the volume control & check the preference settings. I haven't tried using the wired nic but if your running feisty network manager might still be causing issues, I removed it from my start up & bring up my wireless w/network-admin.  without knowing which version you're using it's hard to speculate where to look, but I wager that when you find it, you'll kick yourself, I have found myself kicking myself several times in the last couple weeks getting things set up the way I like them.

---

### Post by VMan on 2007-07-17
I have Feisty (7.04) working just fine on my Toshiba A135-S4467.  Everything I use is or seems to be working.  I did notice that plugging in headphones will not mute the laptop speakers though.  I have added this laptop to the Laptop Testing Page at [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135")
I included how to get the sound working (initial install tries to use the modem as the sound card), and a list of the stuff I hook up to the laptop that works.  I am still trying to get a Hauppage WinTV USB tuner to work.  If I ever get that working, I will add it to the page linked above.

V-Man

---

### Post by whauser on 2007-07-18
I have an a135-s2386 running kubuntu feisty and wanted to verify that the fix works on my machine as well.  Load the new alsa drivers and then add the 3 stack option.

No one else has mentioned this but on my machine I could adjust the volume and whatnot but the external control and the volume adjustment on the menu bar did not affect the volume.  The mixer was the only way to adjust volume.  If anyone else has run into this issue it can be fixed very easily setting the master channel to the front speakers (on my machine at least).  To do this you have to right click on the sound icon on the menu bar and select the "select master channel" option.

---

### Post by erminator on 2007-08-06
Toshiba Satellite A135-S2386. 

Sound worked on edgy (6.10)  with linux 2.6.17 but not work on 7.04 with linux 2.6.20 

Doesn't work on Fedora Core 7 with linux 2.6.21.

Works on Fedora Core 7 with 2.6.22 !!!

I wonder if it works on Ubuntu with 2.6.22....


-E

---

### Post by Mr-Monkey on 2007-08-08
Open terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

copy :  ```
options snd-hda-intel model=3stack
```
 salve 

restart . :)

---

### Post by mwero001 on 2007-10-11
I am using a toshiba a135 s2386. I've done what you're advising but my soundcard is muted. Tried unmuting using the alsa-mixer from the console without success. Any help?

---

