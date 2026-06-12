---
title: "Bluetooth"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by sven on 2005-05-11
How can i found my bluetooth key on gnome? I got a key Gembird. I would want transfer dates from smartphone to ubuntu gnome.

Thanks

---

### Post by ABU on 2005-05-12
[QUOTE=sven]How can i found my bluetooth key on gnome? I got a key Gembird. I would want transfer dates from smartphone to ubuntu gnome.

Thanks[/QUOTE]

Hi.

I have asked similar question ~10 days ago, but nobody replied.
Nobody uses bluetooth or everyone is too lazy to help us.

P.S.: on osnews.com I read that Ubuntu's community is one of best, friendly and helpful.
But it's not truth, Gentoo's is the best - they provide you with the helpful answer pretty quick.
I know, someone will ask me "so why don’t you go there ?". The answer is "I like ubuntu, it's philosophy and I expect better help *here*".

Best regards,
ABU

---

### Post by yusufk on 2005-05-12
[QUOTE=ABU]Hi.

I have asked similar question ~10 days ago, but nobody replied.
Nobody uses bluetooth or everyone is too lazy to help us.

P.S.: on osnews.com I read that Ubuntu's community is one of best, friendly and helpful.
But it's not truth, Gentoo's is the best - they provide you with the helpful answer pretty quick.
I know, someone will ask me "so why don’t you go there ?". The answer is "I like ubuntu, it's philosophy and I expect better help *here*".

Best regards,
ABU[/QUOTE]
 Use Synaptic or apt to install the package gnome-bluetooth, which should add items to your Applications->System Tools menu.

You might also want to try gnokii for connecting to your smartphone.

To test whether your Bluetooth / Bluez stuff is working, try typing:

hcitool scan

in a shell which will initiate a bluetooth discovery of nearby devices.

Hope this helps,
Y

---

### Post by sven on 2005-05-12
Linux,with my key,can detect the smartphone,but,i can't set up a connection. How can i do?

---

### Post by ltmon on 2005-05-12
Try looking at my reply <a href="http://www.ubuntuforums.org/showthread.php?t=33690">here</a>

Cheers,

L.

---

### Post by ABU on 2005-05-13
[QUOTE=yusufk]Use Synaptic or apt to install the package gnome-bluetooth, which should add items to your Applications->System Tools menu.

You might also want to try gnokii for connecting to your smartphone.

To test whether your Bluetooth / Bluez stuff is working, try typing:

hcitool scan

in a shell which will initiate a bluetooth discovery of nearby devices.

Hope this helps,
Y[/QUOTE]

Hi.

It's not possible - I can connect to the Internet via GPRS only. In order to do that I need bluetooth support, but in order to get that I need internet ..... Endless story, infinite loop or whatever you call it....

I think I need to download something for off-line installation, and my question is - what is that "something" ?

Any help ?

Regards,
ABU

---

### Post by ABU on 2005-05-13
[QUOTE=ltmon]Try looking at my reply <a href="http://www.ubuntuforums.org/showthread.php?t=33690">here</a>

Cheers,

L.[/QUOTE]


Thanks. But how to do that off-line ? My only chance to get connection - off-line installation of bluetooth stuff. I have no lan at home, no dial-up connection. I can collect all DEBs at work, then I can bring it home and install it in "off-line mode". What exactly do I need to get the working bluetooth connectivity ?

Thanks in advance,
ABU

---

### Post by sven on 2005-05-13
Bluetooth installed with succes lol

thk to this guide
[http://www.rlachenal.com/bluetooth-6600-linux/](http://www.rlachenal.com/bluetooth-6600-linux/)

---

