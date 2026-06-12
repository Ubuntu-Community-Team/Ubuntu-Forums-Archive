---
title: "KPPP where?"
date: 2008-11-27
forum: General Help
---

### Post by Numbat on 2008-11-27
Having trouble getting on to the internet. First problem is getting the system to dial out (using dial-up modem). I have been told I need kppp but I can not find it. Is it in Ubuntu or do I have to load it? Needless to say, if it needs to load from the internet, I have no internet until I overcome my connection problems.

---

### Post by Numbat on 2008-11-27
Thing I need to point out is that I have zero! experience with Linux.


After finding some information in the Help files, I tried $ sudo apt-get install gnome-ppp to install and it tells me "couldn't find package gnome-ppp". But I have the disk in the machine and it is a fresh install. Why can't it find the packages? What use is a help system if it doesn't actually work?

---

### Post by Numbat on 2008-11-28
I think this is a major bug in this version of Linux. Is there some other version that actually works?

---

### Post by nitehawk777 on 2008-11-28
@numbat,..
I'm a real "newbie",....
but I had the same problem with Ubuntu 8.10.

I didn't have much problems with Ubuntu 8.04,...but everything has changed for dial-up users in the new 8.10, I'm afraid.  I was given some pretty complicated instructions from the forum, here,.. (well,..complicated for ME, because I'm still rather new to linux). I did manage to get on the internet,.....but decided to go with an easier distro, instead..(easier for dial-up users, that is).

There aren't many of those left,....(you have my sympathy).:(

---

### Post by editrix on 2008-11-30
KPPP is the easiest way to configure your modem for dialup. It's a KDE program, but it works in Gnome. The K/Ubuntu folks have, in their wisdom??, decided **not** to include a graphical way of configuring your modem in Intrepid. I assume you're using Intrepid.

Have you consulted this page?
Dialup modem HowTo [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

As far as I'm concerned, the easiest thing for you would be to have someone download the .deb for KPPP and then you can install it yourself by just clicking on it--unless that's been changed in Intrepid, too.

If it's any help, here's what my wvdial.conf looks like:


[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Init = ATZ
Phone = 1234567890
Username = myloginname
Password = mypassword
New PPPD = yes

Dial Command = ATDP--NB: the P is for pulse dialling, you probably want ATDT (T for tone)

---

