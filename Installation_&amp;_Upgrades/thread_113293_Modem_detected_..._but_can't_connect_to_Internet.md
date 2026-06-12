---
title: "Modem detected ... but can't connect to Internet"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by sbasak on 2006-01-06
After a long battle of several days, I finally made Ubuntu make my WinModem recognize  (Conexant HSF).

But even I can't connnect to Internet.
I've configured wvdial.conf file but when I issue this command

sudo wvdial

modem makes sound, says connecting, shows some DNS address on screen

Now if I try to open any website in FireFox, it can't open :mad: 
I'm sure the username/password & dialed number is correct.

PS: I followed all the steps from
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28up%29%7C%28dial%29#head-2a65918cb1a6ceef620573ed7c1b04aa6a12f93a](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28up%29%7C%28dial%29#head-2a65918cb1a6ceef620573ed7c1b04aa6a12f93a)

except the adding X3 to Init2 line because when I do Ubuntu reported error in the file.

---

### Post by wanger123 on 2006-01-06
Hi, do you also use the ethernet card or a wireless card. If so you may have to replace the default route by adding replacedefaultroute to your wvdial options file.
Can you ping by ip address?
eg. Type this in a terminal: ping 211.29.123.456 (replace with the remote ip address you are getting after connection). 
Then try by name: ping [www.google.com](www.google.com).

wanger

---

### Post by sbasak on 2006-01-06
[QUOTE=wanger123]Hi, do you also use the ethernet card or a wireless card. [www.google.com](www.google.com).
wanger[/QUOTE]

I don't have wireless so it must be ethernet. I just added defaultroute that didn't work. So, I'll add replacedefaultroute and try again.

---

