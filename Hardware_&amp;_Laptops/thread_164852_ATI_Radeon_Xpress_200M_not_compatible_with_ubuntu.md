---
title: "ATI Radeon Xpress 200M not compatible with ubuntu???"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by rishabh87cool on 2006-04-23
hey,
i m having toshiba satellite m50-mx2 with ati raadeon xpress 200m graphics card. the installation goes well till it asks me for login name and password. But after that it shows me a lot of noise and a big square in between which responds to the touchpad. what should be done??? any suggestions???

---

### Post by nanotube on 2006-04-23
boot in single user mode (recovery mode from the grub menu). that will throw you into a root shell.
edit your /etc/X11/xorg.conf file with the following command:
```
nano /etc/X11/xorg.conf
```
then find the line that looks like 
```
Device "ati"
```
and change it to 
```
Device "vesa"
```
reboot, and see if that works. that will leave you without 3d acceleration though, so you might want to look around afterwards on how to get your particular video card working. but at least you will get a normal desktop :)

---

### Post by rhelvey on 2006-04-23
Everyone seems to allude to problems similar to the one I'm having, rishab has the same video card so I am attaching to his thread. I loaded Breezy twice once on a fresh harddrive and now as a dual boot with XP. I had the same result with both loads, the installation went fine and the first time breezy was supposed to boot my screen clicks a couple of times (with two different monitors) then I get a blinking cursor, upper left hand corner. I know another gent had the same problem which was remedied with some command line typing however...... I can't get to command line using Ctl Alt F1. I'm not exactly a newbie although I havent used Linux for three or four years.

AMD Athlon 64 3000+
1.79 GHz 448MB DDR RAM
ATI Radeon Xpress 200
MDT MD800JB 80 GB hardrive

---

### Post by scoot1212 on 2006-04-24
this worked for me...i have the x700 on my msi 1029   [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Scott

---

### Post by rhelvey on 2006-04-24
Scott, thanks for your response. Does it matter that I'm using Breezy and not Dapper yet? Also I can't get to command prompt once it's booted, however I can get to a bash shell from grub. This seems to allow me limited control, can this be used to remedy this ATI snafu?

Thanks again...

---

### Post by lancest on 2006-04-24
Same problem. Toshiba Satellite L20- ATI express Radeon 200m. Get video error screen, Breezy.   Like to know what to do. Have used Linux successfully for more than 5 years. Laptops can be complicated though, especially Toshibas.

---

### Post by lancest on 2006-04-25
It worked! Breezy with ATI Radeon 200m. I followed [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
these steps. However it was combination of Method 1 & 2 commands.  Not real smooth, a bit of guesswork. Install the fglrx then edit xconf.conf with Device "fglrx" only. ACPI working!

---

### Post by loom777 on 2006-04-28
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) is better for Badger... i tried it with my ATI x700 XL and it worked (still trying to solve some resolution problems though...)

---

### Post by Yakkasimon on 2006-05-01
Hi all. I've been trying to get my Radeon Express 200 card up and running by following stuff on this page but as I'm using a 64 bit machine I don't know what to do when I come to the 64 bit users part of this...

[FONT="Fixedsys"]Installing the driver

All Platforms:

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver and 64-bit users should deselect int10a

64-bit users:

You have to downgrade to an older version of libdri.a due to an incompatilbity with the ATI drivers. Download it here

Change to download directory:

gunzip libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
sudo cp libdri.a /usr/X11R6/lib/modules/extensions/
[/FONT]

How do I 'download' the older version of libdri.a from the command line? I was fine up to that stage (had selected flgrx and deselected int10). Hoping someone can help a newbie.

---

### Post by Greg2 on 2006-05-01
[QUOTE=Yakkasimon]
How do I 'download' the older version of libdri.a from the command line? I was fine up to that stage (had selected flgrx and deselected int10). Hoping someone can help a newbie.[/QUOTE]
OK... in terminal do:```

mkdir temp
cd ~/temp
wget http://mail3.mpr.org/mlomker/libdri.a.gz
gunzip libdri.a.gz
```then finish the instructions.

---

