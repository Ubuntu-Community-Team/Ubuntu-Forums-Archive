---
title: "Dial-up help needed"
date: 2005-11-25
forum: General Help
---

### Post by Fittersman on 2005-11-25
How do i set up a dial-up connection for ubuntu 5.10 NOT 5.04?

---

### Post by towsonu2003 on 2005-11-25
sudo wvdialconf /etc/wvdial.conf

if that sees your modem, 

sudo gedit /etc/wvdial.conf

input your dial up info in there where asked, save & close.

sudo wvdial

if fails, try apending this line at the end of /etc/wvdial.conf:
Stupid Mode = yes

hopefully will dial. if it does not see your modem, go to linmodems.org and read along... good luck :)

---

### Post by wanger123 on 2005-11-26
If you want to use kppp you may have to create a file called /etc/resolv.conf. You can do this as root using kate, gedit, kwrite etc. and just create an empty text file. kppp will put the DNS addresses in there.

Also it is very important to edit the  /etc/ppp/peers/kppp-options  file and remove the # in front of noauth.

ie Change it from #noauth to noauth

ciao
wanger123

---

### Post by akiro.yamamoto on 2005-11-26
[QUOTE=Fittersman]How do i set up a dial-up connection for ubuntu 5.10 NOT 5.04?[/QUOTE]
If you are currently dual booting Ubuntu (Gnome) and M$ Win and you want a GUI dialer try downloading Gnome-ppp (.deb). As long as you have a hardware modem or a modem with linux drivers available and installed. Gnome-ppp will help you set up andlog on to the internet.
That's what I did and I'm currently using an Intel 537ep modem (Linmodem).

---

### Post by Fittersman on 2005-11-26
you guys totaly lost me 

The first guy that tried helping me i did that and it never detected my modem so i went to that site you reccomended and that is confusing me even more.

---

### Post by paddyg on 2005-11-26
Fittersman, first of all, i think the easiest way is to have an external modem (serial).
Then i wonder if you ever tried the gnome interface:
----------
System--->Administration-->Networking
modem connection--->properties--> tick off 'enable this connection' (and provide all dial-up info)
on Modem tab:
modem port: /dev/ttyS0 or ttyS1 (it depends on which serial port you are using)
Once finished, click OK
----------
If you've got an external modem, nothing more than that is needed...

---

### Post by Fittersman on 2005-11-26
lol too bad internal modem:razz:

---

### Post by Bachstelze on 2005-11-26
Then you should read this to have your winmodem detected

[http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

---

### Post by Fittersman on 2005-11-26
anything simplier than that cuz im not following

---

### Post by Bachstelze on 2005-11-26
Simpler... I don't think I could make it any simpler, anyway, here's what you have to do.

First, download this tool : [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

copy it onto your Ubuntu system, ru a terminal in the directory with scanmodem.gz and run those three commands

```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

Normally, you will have a Modem directory created with a bunch of files in it. Send an email to [email]discuss@linmodems.org[/email] asking for help with the ModemData.txt file as an attachement. You might have to register on the mailing list before sending, though. (for this send an e-mail with SUBSCRIBE as subject to [email]discuss-subscribe@linmodems.org[/email])

---

### Post by erik-the-red on 2005-11-26
First off, why did nobody mention GNOME-PPP in my thread ([http://www.ubuntuforums.org/showthread.php?t=86821)?](http://www.ubuntuforums.org/showthread.php?t=86821)?) Just curious.

Second off, if you can't easily get broadband in your area, like me, and you're on Linux, it would be wise to invest in an external serial modem. Most of these will work directly with Linux provided you know which serial port it is in.

Also, why did nobody mention pppconfig? I used that and that's how I'm online right now, and have been since Warty. I have never heard of wvdialconf until I read this thread.

---

### Post by Fittersman on 2005-11-27
they like me better than you :P


ok i got a question 

in ubuntu's device manager thing it had my modem listed there but when in system > administration > networking when i try and set up a modem connection i press autodetect but it cant find it. Whats up with that?

---

