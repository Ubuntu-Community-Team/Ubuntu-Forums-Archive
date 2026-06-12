---
title: "Installing a Network Scanner"
date: 2010-01-21
forum: Hardware
---

### Post by erlguta on 2010-01-21
Hi.
I have one HP Photosmart All_in_one C4380 scanner properly installed in one Ubuntu 9.10 server.
If do one:
# scanimage -L

I can see it:
device `hpaio:/usb/Photosmart_C4380_series?serial=CN843F606V051Q' is a Hewlett-Packard Photosmart_C4380_series all-in-one

I have followed all of this instuctions:
[https://help.ubuntu.com/community/ScanningHowTo#Server-side Setup (9.04)]("https://help.ubuntu.com/community/ScanningHowTo#Server-side Setup (9.04)")

```

in /etc/default/saned
# Set to yes to start saned                                                     
RUN=yes
Now add the following line to /etc/sane.d/saned.conf to share the printer with all computers on your subnet:

192.168.1.0/24
Then start the Sane daemon (saned) by running: (when on Ubuntu 9.10)

sudo invoke-rc.d saned start (restert instead of start)
To configure the Sane daemon start automatically at boot up run:

sudo update-rc.d saned defaults

```

I can see that saned is runnig:
```

ps aux | grep saned
saned     4552  0.0  0.0  27300   628 ?        Ss   20:19   0:00 /usr/sbin/saned -a saned
saned     4553  0.0  0.0  27300   840 ?        S    20:19   0:00 /usr/sbin/saned -a saned

```

But i go to my PC and set /etc/sane.d/net.conf to my ip scanner server:

192.168.1.100

And when i start xsane or run the command 'scanimage -L' does not appear any scanne.

What the hell i am doing wrong?

Thank you for your help.

---

