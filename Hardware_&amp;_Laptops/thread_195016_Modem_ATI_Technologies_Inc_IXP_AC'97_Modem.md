---
title: "Modem ATI Technologies Inc IXP AC'97 Modem"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by jmarques on 2006-06-12
Hello,

I install Dapper in my laptop Toshiba Satellite A60-S1662, and I am trying configure my modem ATI Technologies Inc IXP AC'97, but I don't know how, can anyone help me?

Thanks,

---

### Post by vespo on 2006-06-12
[QUOTE=jmarques]Hello,

I install Dapper in my laptop Toshiba Satellite A60-S1662, and I am trying configure my modem ATI Technologies Inc IXP AC'97, but I don't know how, can anyone help me?

Thanks,[/QUOTE]

Hi

you are lucky, I just did it yesterday on my Toshiba p30.

First, let me tell how amazed I am for the modem working with very little tweak... very well done ubuntu.

So, here you go:

1. download and install the package sl-modem-daemon here (or with synaptic, multiverse):

[http://packages.ubuntu.com/dapper/misc/sl-modem-daemon](http://packages.ubuntu.com/dapper/misc/sl-modem-daemon)

It will automatically set-up the service to start at boot. It seems it is correctly configured to use alsa emulation, so no changes required here. On loading at boot it will create /dev/ttySL0 and a symlink to it called /dev/modem. The latter should be used as the modem device in every software you want to use to dial-up (kppp, etc).
You DON'T want to download the package to build slamr0 (proprietary) from source. Alsa is enough for basic internet connection.

2. The daemon defaults to USA country setting, if you are not dialing from there then you have to edit the file /etc/default/sl-modem-daemon. Look for the line that specifies the country and edit appropriately.

```
sudo gedit /etc/default/sl-modem-daemon
```

look for

```
COUNTRY="" 
```

3. Reboot (to load the daemon with correct country settings)
Alternatively, you could restart the daemon by hand:
```
sudo /etc/init.d/sl-modem-daemon restart
```

4. To set up ppp I suggest you use wvdial, it is command line but very helpful for debugging.
First you run:
```

sudo wvdialconf /etc/wvdial.conf
```

This probes the modem and writes down wvdial.conf with what it has found. If it ends with an error message we'll have to look into something else.

4.1 Set your ISP phone number, username and password by editing relevant sections of wvdial.conf

```
sudo gedit /etc/vdial.conf
```

When you open the file you will have something like:

```
[Dialer Defaults]
Modem = /dev/ttySL0
Baud = some speed
Init = ATZ
Init2 = AT S11=50 other digits relevant to your modem
Phone = 
Username = 
Password = 
```

wvdial.conf can have as many dialers you like, so I suggest you leave that default as is, you copy and paste and edit a new section with YOUR data. You also change [Dialer Defaults] to [Dialer OTHER_NAME].

4.2 TIPS:

4.2.1 It is helpful - and anyway harmless - to add these two lines at any dialer section:
```
Carrier Check = no
Stupid Mode = yes
```
I'm not kidding about the stupid line.

4.2.2 If you live in a country with very weak pulse signals (like me, in ITALY) you want to edit the modem init string to dial blindly.
In [Dialer OTHER_NAME] change:

```
Init = ATZ
to
Init = ATX3
```

5. Now you want to actually dial-up.
Plug the phone cable in your laptop (very important step indeed), open a console command line and type (you don't need to sudo)

```
wvdial OTHER_NAME
```

If you're lucky, after a half minute you see the output of your assigned IP and other infos about your working internet connection. Ctrl+C will gracefully disconnect.

cheers
vespo```

```

---

