---
title: "a big thanks"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by unisol on 2005-05-20
can someone show me the right way to configure ppp ithink im close but i may be missing some settings

---

### Post by ggozad on 2005-05-20
Well, could you provide some more info on what you want to do? Adsl? Modem? ppp does a million different things....

---

### Post by unisol on 2005-05-21
im sorry its a usrobitics 5610b internal pci modem which is compatible with linux 2.3 and higher i amm trying to connect to msn which is my isp minicom gets me a logon screen i type the user name but when i type the password msn says its bad (works in windowsxp) msn uses MD5chap im using pap and chap what do you think

---

### Post by ggozad on 2005-05-22
Try using wvdial.
Configure your modem with 
sudo wvdialconf /etc/wvdial.conf

Edit the settings for your isp and it should work:)

---

### Post by unisol on 2005-05-24
i use minicom to connect it lets me on msn but i am unable to do anything after that resulting in a timeout i tried amsn wvdial pppconfig  the only one that  connectd is minicom and then i cant  do anything

---

### Post by unisol on 2005-05-25
i tried everything i can think of i even tried amsn it said it needed to download TLS.sf which is already on my computer. i also tried to install gnome-ppp-0.3.21 when i got to ./configure it told me gtk2.0 and libgnomeui werent installed well there are do i have to point to them for this program to install. i feel retarded

---

### Post by eugene on 2005-06-01
[QUOTE=unisol]can someone show me the right way to configure ppp ithink im close but i may be missing some settings[/QUOTE]

I'm also having little success.  Im running a leased line off a serial port and somehow it seems the OS refuses to see the port.  I've tried pppd /dev/ttyS1 with a variety of options but with no luck - I keep getting a message about authentication password for the remote system required and not found - but the remote system is not being accessed at all. I've also tried pppconfig but with no luck there either.  Any help would be appreciated.

Eugene Griessel

---

### Post by unisol on 2005-06-01
i want to thank all of you who helped me cause i can finally connect to the internet i hope i can help someone as you have helped me

---

