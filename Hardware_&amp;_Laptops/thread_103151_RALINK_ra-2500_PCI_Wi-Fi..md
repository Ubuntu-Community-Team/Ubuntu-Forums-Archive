---
title: "RALINK ra-2500 PCI Wi-Fi."
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by ATAQ on 2005-12-13
Hey does anybody know where I can go to find drivers for my Ralink ra2500, There website doesnt provide the correct drivers.
Thanks!

---

### Post by danne on 2005-12-13
[QUOTE=ATAQ]Hey does anybody know where I can go to find drivers for my Ralink ra2500, There website doesnt provide the correct drivers.
Thanks![/QUOTE]

under normal circumstances..the ralink 2500 is supported under ubuntu and no extra drivers are required. a wireless card should appear in the network config

---

### Post by ATAQ on 2005-12-13
strange, I better go and have a look so to see whats up, Sound, thanks bud

---

### Post by danne on 2005-12-13
if your card doesn't appear ...try to install ndisgtk with synaptic....just use the windows drivers of the card...nice and graphical install of the card (eheh)

---

### Post by ATAQ on 2005-12-13
cool I never knew it was possible to use windows drivers! cool, never had a prob with drivers untill this one now.

---

### Post by John.Michael.Kane on 2005-12-14
I have an RAlink wifi and under 5.04 it was not seen. however under 5.10 it is seen and fully works. you may just want to upgrade to 5.10

---

### Post by jml on 2005-12-14
Here is a link to the Open Source rt 2x00 driver project.

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

They have taken over development of the raLink drivers from the manufacturer.  But SD-Plissken is right, Ubuntu 5.10 recognizes the RaLink card out of the box.  Unencrypted wireless and WEP are supported.  WPA is more of a problen, though, since the application often used for configuring WPA (WPA_Supplicant) does not support thr rt2500 chipset.  Hope this is of help.

Joe

---

### Post by ATAQ on 2005-12-14
Nice one that seems to have worked grand there, Thanks Jml, I will be upgrading to 5.10 anyway soon though. Do you know is there many on this forum that are Irish by the way?!

---

### Post by kellyhardinguk on 2005-12-15
I have one of these cards (PC Card version).

Under Hoary (5.04) I had to download the driver source and compile it against my kernel. Then I could goto the System -> Administration -> Networking
where it'd show as ra0, activate the card and then configure it and presto it worked fine. Tested it when on holiday with a hotel wifi set up, 2 days later after getting all this working my laptops 20Gb hard drive died on me :(

Still I knew the card worked with Linux ok :)

Installed Breezy (5.10) later when I aquired an old 5Gb laptop drive.

Plugged the card into my laptop, and it was seen with no need for me to compile anything. Just had to do the usual activate and configure.

Not tried the card out on a wifi network yet mind, as there isn't one here till we can afford an AP. But when we can, it should get used by both my laptop and Zaurus (now i've got a CF WLan card for it!).

Kelly

---

### Post by jdp on 2005-12-15
I just tried the 5.10 LiveCD on an in-laws machine.  It has a Linksys PCI G card and it's RALink RT2500 based.  Ubuntu found it and allowed me to use it just fine.  I just had to use the WEP key in HEX, instead of ASCII.  Otherwise it's fine.

---

