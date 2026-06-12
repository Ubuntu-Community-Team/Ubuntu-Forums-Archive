---
title: "aes2501-wy biometric fingerprint fiesty"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by alexvd on 2007-07-18
I have a Authentic Fingerprint Sensor in my Motion tabletpc. 

I see that a package exists for this sensor but I don't think its fully developed.    Is this ready so that I can use it to login and authenticate to ubuntu?  

Any chance it will also work with Firefox for other passwords?

I have seen the thinkfinger project but it does not currently look like it is supported.

---

### Post by alexvd on 2007-07-18
So does anyone have a authentec aes2501 fingerprint reader working under ubuntu.

---

### Post by roaldz on 2007-07-21
I haven't got it working like you mean, but I have tried some drivers though. 

I found one here: [http://home.gna.org/aes2501/index_en.html](http://home.gna.org/aes2501/index_en.html)
here: [http://www.ag-networking.com/](http://www.ag-networking.com/)
and here: [http://packages.debian.org/unstable/graphics/aes2501-wy](http://packages.debian.org/unstable/graphics/aes2501-wy) (original site: [http://gkall.hobby.nl/authentec.html](http://gkall.hobby.nl/authentec.html))

I didn't try the first driver I mentioned, so I can't tell you about it. 
The second is as far as I know the most complete driver (if you download the aespack). It has a biologin utility too. This driver isn't finished yet. 

The third driver I mentioned worked also (if you install it with dpkg --force-depends), but this is only a scan capture driver which creates a fingerprint image.

So, as far as I know, there are some drivers, but it won't work yet becouse of the login utility's and such.

Greets,

Roald

---

### Post by tower_ on 2007-07-25
user@linux:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 003: ID 046d:c510 Logitech, Inc.
Bus 003 Device 004: ID 08ff:2580 AuthenTec, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

great: fingerprint sensor is recognized as "08ff:2580 AuthenTec, Inc" wich is included in aes2501-wy

then i downloaded from [http://packages.debian.org/unstable/graphics/aes2501-wy](http://packages.debian.org/unstable/graphics/aes2501-wy)

this deb package i installed it with
sudo dpkg -i --force-depends aes2501-wy_0.1-3_i386.deb

finaly i start the programm with

user@linux:~$ aes2501 -r
argc=2 Param=-r
Initializing, please standby...
aesSetup()...
aesStartScan()...
READY (touch the sensor to stop)

i touched the sensor wich gives me tow pictures (fporig.pnm and fp.pnm) in my home folder

so on my HP compaq 6710b with Feisty 7.04 it seems to work ;)

now next is to find a software wich compares a master fingerprint with the actual readed one...

---

### Post by dennda on 2007-08-03
> now next is to find a software wich compares a master fingerprint with the actual readed one...

Hi.
Did you find any?

Thanks in advance!

---

### Post by slasherx2 on 2007-08-07
any luck on finding one yet?

thanks
slasherx2

---

### Post by roaldz on 2007-08-07
The [http://www.ag-networking.com/](http://www.ag-networking.com/) sofware ([http://www.irctest.de/~agnet/aespack01.tar.gz](http://www.irctest.de/~agnet/aespack01.tar.gz)) has a utility that compares fingerprints, but that isn't working for me (yet). I've got it compiling (the creator made a typo). I'm getting a segmentation fault:
```
roald-laptop% linux32 ./biologin
---- BIOLOGIN ----
Please standby...
AES Device Found @ Address 002
--> AES driver ready

>>>> Please make a FingerScan NOW...
<-- Scanning...
>>>> Please Wait - Processing FingerPrint...
[1]    14212 segmentation fault (core dumped)  linux32 ./biologin
```
I don't know if this is because I'm running 64bit, I've compiled it myself.

Anyone more luck on this one?

---

### Post by slasherx2 on 2007-08-07
Yeah that's what I'm getting too on the 32bit version

```

craig@craig-laptop:~/dist/biologin$ ./biologin 
---- BIOLOGIN ----
Please standby...
AES Device Found @ Address 004 
--> AES driver ready

>>>> Please make a FingerScan NOW...
<-- Scanning...
>>>> Please Wait - Processing FingerPrint...
Segmentation fault (core dumped)


```

Anyone else getting any luck with this at all?

By the way I also emailed AuthenTec requesting a linux driver, I'd recomend you do the same.

---

### Post by KS_japan on 2007-08-17
I am running gutsy. I tried biologin. To avoid segmentation fault, create /etc/fps folder. Create "users" file in this folder and write the user name inside. Create your xpm file by running usbrunner and store it in /etc/fps folder in the [username].xpm format. Then the biologin runs smoothly and shows a long Angle list. I dont know how to proceed to apply this to authenticate my login. Does anyone know the method?

---

### Post by picopir8 on 2007-08-17
I downloaded the driver package from tower_'s post and that worked.  I then downloaded the "AES2501 USB Scan Software" from the ag-networking link from roaldz's post.  That too worked for me.  But it too just creates a finger print image as well, no comparison.  I have not tried the "AES2501 USB Scan Software + Driver Lib + BioLogin (unfinished)" link. The unfinished note and the fact that development seems to have been abandoned for about a year kinda scared me off.  Im a bit hesitant to install something that could mess up my login.

---

### Post by Jukka-Pekka on 2007-08-28
I can confirm that the AES2501 works on a HP nc8430 laptop to the point that you can get a fingerprint image - but that's where it ends.

I hope that fingerprint (biometrics) support arrives to the Linux world also. It is nice to just swipe your finger in response to password requests e.g. in logon/logoff, email, websites instead of those long and complicated (=safe) passwords.

Unfortunately this kind of functionality is still lacking in Ubuntu. The projects around fingerprint logging/authentication have probably silently "ended" without proper support from the manufacturers (AuthenTec).

As laptops are the growth area in PC's, it would be important to provide full functionality out-of-the box. Fingerprint sensors are integrated to many of these new laptops sold.
Many laptop buyers are also new to computing - students etc.. Providing a smooth user experience - without the disappointment of the integrated fingerprint sensor not working - could get Linux many new users.

Unfortunately I do not possess the proper skills to develop code to this end, but hopefully someone with those skills also gets excited about biometrics functionality for Linux!

Jukka

---

### Post by kao on 2007-09-01
AFAIK, 6710b was certified with SLED10 SP2. So, i think support for such device can be found very soon. I am searching for information about it now.
Anybody hear something?

---

### Post by GavinZac on 2007-09-18
I think biometrics, especially finger scanning, is an emerging field that people will definately want on their laptops very soon. I myself am a little disappointed that there has been no progress on this and get more disappointed every time i see the scanned images of my fingerprints in my /home folder: the hardware is working, but the software just isnt there. i wish i could write it myself but i havent written anything to do with images or security in linux.

---

### Post by roaldz on 2007-10-17
I've emailed authentec too, and as posted before, it's suggested we all try to email them, to get some proper linux open source drivers!

Roald

---

### Post by chadd on 2007-11-02
I received this response from Authentec regarding linux drivers:

Thank you for your interest in AuthenTec and our line of TruePrint
biometric fingerprint sensors. AuthenTec is dedicated to supporting the
many PC, cell phone, and other device manufacturers that integrate our
sensors, but unfortunately, at this time we do not provide drivers or
support directly to end users of those products. AuthenTec is aware
that the majority of PC manufactures do not offer Linux drivers for our
fingerprint sensors; however you will find a few open source sites that
may have Linux drivers available. For other support or software related
issues, we encourage you to contact the manufacturer of your PC.

** AuthenTec has not verified nor do we certify the Linux drivers found
on the following sites. They are merely provided for your reference.

1.     [http://gkall.hobby.nl/authentec.html](http://gkall.hobby.nl/authentec.html)

2.     [http://home.gna.org/aes2501/index_en.html](http://home.gna.org/aes2501/index_en.html)

Thanks and Best Regards,

AuthenTec, Inc
[www.authentec.com](www.authentec.com)

Haven't tried the links listed, but looks like they are pointing people back to their PC/laptop vendors.

---

### Post by GavinZac on 2007-11-03
> **chadd said:**
> Haven't tried the links listed, but looks like they are pointing people back to their PC/laptop vendors.
No, they're pointing them to the already existing (and currently, inadequate) open source solutions previously listed in this thread.

Basically Authentec sell this hardware, but only to PC/Laptop manufacturers, who havent cared at this point, to ask for linux drivers.

I would think our only hope is that those open source drivers get completed some day, or that HP/Dell decide they want Authentec biometrics in their Linux laptops.

---

### Post by r@ver on 2007-12-02
Hi :)

It's working on my Toshiba Tecra S3 laptop

BTW, I found this project but I didn't test it yet.

[http://www.reactivated.net/fprint/wiki/Main_Page]("http://www.reactivated.net/fprint/wiki/Main_Page")

---

### Post by roaldz on 2007-12-03
> **r@ver said:**
> Hi :)

It's working on my Toshiba Tecra S3 laptop

BTW, I found this project but I didn't test it yet.

[http://www.reactivated.net/fprint/wiki/Main_Page]("http://www.reactivated.net/fprint/wiki/Main_Page")

Well, I´ve tested it with my AES 2501, and it works! At least this is a project with future.. If we just do our best to support these guys, our goal will be achieved soon!

Keep your eye on [http://www.reactivated.net/fprint](http://www.reactivated.net/fprint) !

Btw, I´ve converted the Suse x64 RPM´s ([http://download.opensuse.org/repositories/home:/dgege/](http://download.opensuse.org/repositories/home:/dgege/)) to .deb´s with alien. See attachments

---

### Post by ghonz on 2007-12-11
> **roaldz said:**
> Well, I´ve tested it with my AES 2501, and it works! At least this is a project with future.. If we just do our best to support these guys, our goal will be achieved soon!

Keep your eye on [http://www.reactivated.net/fprint](http://www.reactivated.net/fprint) !

Btw, I´ve converted the Suse x64 RPM´s ([http://download.opensuse.org/repositories/home:/dgege/](http://download.opensuse.org/repositories/home:/dgege/)) to .deb´s with alien. See attachments

Thank you for the conversions, I've got them installed, do you have any advice on how to get fprint to work?

---

### Post by roaldz on 2007-12-11
> **ghonz said:**
> Thank you for the conversions, I've got them installed, do you have any advice on how to get fprint to work?

To be able to login with your fingerprint, I did this:

1. Install all the .debs I converted.
2. Now start ¨fprint_demo¨ using ALT+F2. Enroll 1 finger. Then go play with the identify and verify options. If it matches constantly you can quit the program.

3.If enrolling your finger works, then edit /etc/pam.d/common-auth using ¨sudo gedit /etc/pam.d/common-auth¨, and make it look like this:

```
auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth    required        pam_unix.so nullok_secure

```
Notice three times the same rule. I did that, because my scanner doesn´t always identify my finger, so it asks 3 times for the fingerprint, and then it fall´s back to password.

If you can´t run fprint_demo, then run it in a terminal. If it gives error messages, post them here, and I´ll help you through. I´ve had some errors myself too, but those were easy to fix, if I remember.

Good luck!

Roald

---

### Post by ghonz on 2007-12-12
> **roaldz said:**
> 

If you can´t run fprint_demo, then run it in a terminal. If it gives error messages, post them here, and I´ll help you through. I´ve had some errors myself too, but those were easy to fix, if I remember.

Good luck!

Roald

I've tried running it and nothing is happening

---

### Post by roaldz on 2007-12-12
> **ghonz said:**
> I've tried running it and nothing is happening

You ran it in a terminal and you didn´t get error messages? That´s very weird. Don´t know a solution to that one.. Are you sure you ran it in a terminal?

fprint_demo requires 
/usr/lib/libMagick.so.10 and
/usr/lib/libWand.so.10

but in gutsy

/usr/lib/libMagick.so.9 and
/usr/lib/libWand.so.9

are installed. I had to make symbolic links. Lets trick this baby:

First make sure you have 
/usr/lib/libMagick.so.9 and
/usr/lib/libWand.so.9
installed.
```
sudo ln -s /usr/lib/libMagick.so.9 /usr/lib/libMagick.so.10
sudo ln -s /usr/lib/libWand.so.9 /usr/lib/libWand.so.10
```

This is not the best solution, actually, it´s kind of a hack.

---

### Post by LinuxIsInnovation on 2007-12-13
I installed the 3 packages but I got this error:

glade@Muzic-Jukebox:~$ fprint_demo
fprint_demo: error while loading shared libraries: libWand.so.10: cannot open shared object file: No such file or directory
glade@Muzic-Jukebox:~$ 

Im using Gutsy amd64 version..

---

### Post by LinuxIsInnovation on 2007-12-13
Done.. thanx..
Worked for me!!

---

### Post by LinuxIsInnovation on 2007-12-14
By the way, the login wizard asks for the right index finger only.. cant it be configured to work with multiple fingerprints.. Ive enrolled all my fingers..

---

### Post by roaldz on 2007-12-14
> **sayakb said:**
> By the way, the login wizard asks for the right index finger only.. cant it be configured to work with multiple fingerprints.. Ive enrolled all my fingers..

I don´t think that´s possible now.
Well, it´s still in development, so I´m sure that feature will be added soon. Right now I´d just enroll your preferred finger (I´ve only enrolled my right index finger). Than it will ask for that finger only.

Good luck:)

---

### Post by ghonz on 2007-12-15
Wuhoo,
It now works, thank you so much :)

---

### Post by GavinZac on 2007-12-16
when i try to install the demo, it tells me it cannot find libpango, but libpango is installed.

edit: ok i got it working, there were some dependancies stopping me installing the newer libpango.

but now, it never recognises the same finger. :(

---

### Post by roaldz on 2007-12-16
> **GavinZac said:**
> when i try to install the demo, it tells me it cannot find libpango, but libpango is installed.

edit: ok i got it working, there were some dependancies stopping me installing the newer libpango.

but now, it never recognises the same finger. :(

Make sure you enroll it properly, and check the image. Every time you scan your finger, do it the same way. I find it easy to use my right middle finger.

---

### Post by kurazu2 on 2007-12-16
thanks **roaldz**, works great on HP 6710b.
*Edit: I just discovered, that it works not only for login, but also for invoking sudo. That's more than I expected :)*

---

### Post by GavinZac on 2007-12-16
> **roaldz said:**
> Make sure you enroll it properly, and check the image. Every time you scan your finger, do it the same way. I find it easy to use my right middle finger.

I've tried, and I've done it a few times over in the same way... it seems to be too sensitive. Maybe I need practice :/ I wonder, though, are the fingerprint sign ins on other platforms quite as fussy?

---

### Post by roaldz on 2007-12-16
> **GavinZac said:**
> I've tried, and I've done it a few times over in the same way... it seems to be too sensitive. Maybe I need practice :/ I wonder, though, are the fingerprint sign ins on other platforms quite as fussy?

Don´t know, I´ve only used Ubuntu and Kubuntu on this laptop. Haven´t tried other distro´s, and Windows will never touch it!:) It think it should be working ok, as long as you have the same FP reader hardware as I do.

---

### Post by maximilianhauser on 2007-12-17
Hello!
which package in Ubuntu Gutsy Gibbon contains the libWand10 libary? When I try to start fprint_demo i get the following message:
fprint_demo 
fprint_demo: error while loading shared libraries: libWand.so.10: cannot open shared object file: No such file or directory

The package imagemagick is already installed... I have a HP Pavillion 9533 eg Notebook with the Authtentec Fingerprint Reader and Ubuntu Gutsy Gibbon 64 bit. I'm sorry for my bad english, but this is not my native language :)

---

### Post by roaldz on 2007-12-17
> **maximilianhauser said:**
> Hello!
which package in Ubuntu Gutsy Gibbon contains the libWand10 libary? When I try to start fprint_demo i get the following message:
fprint_demo 
fprint_demo: error while loading shared libraries: libWand.so.10: cannot open shared object file: No such file or directory

The package imagemagick is already installed... I have a HP Pavillion 9533 eg Notebook with the Authtentec Fingerprint Reader and Ubuntu Gutsy Gibbon 64 bit. I'm sorry for my bad english, but this is not my native language :)

Read my previous posts, they will explain it:

> **roaldz said:**
> To be able to login with your fingerprint, I did this:

1. Install all the .debs I converted.
2. Now start ¨fprint_demo¨ using ALT+F2. Enroll 1 finger. Then go play with the identify and verify options. If it matches constantly you can quit the program.

3.If enrolling your finger works, then edit /etc/pam.d/common-auth using ¨sudo gedit /etc/pam.d/common-auth¨, and make it look like this:

```
auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth    required        pam_unix.so nullok_secure

```
Notice three times the same rule. I did that, because my scanner doesn´t always identify my finger, so it asks 3 times for the fingerprint, and then it fall´s back to password.

If you can´t run fprint_demo, then run it in a terminal. If it gives error messages, post them here, and I´ll help you through. I´ve had some errors myself too, but those were easy to fix, if I remember.

Good luck!

Roald
> **roaldz said:**
> 
fprint_demo requires 
/usr/lib/libMagick.so.10 and
/usr/lib/libWand.so.10

but in gutsy

/usr/lib/libMagick.so.9 and
/usr/lib/libWand.so.9

are installed. I had to make symbolic links. Lets trick this baby:

First make sure you have 
/usr/lib/libMagick.so.9 and
/usr/lib/libWand.so.9
installed.
```
sudo ln -s /usr/lib/libMagick.so.9 /usr/lib/libMagick.so.10
sudo ln -s /usr/lib/libWand.so.9 /usr/lib/libWand.so.10
```

This is not the best solution, actually, it´s kind of a hack.

Greetz

---

### Post by aitorhh on 2007-12-19
Hello, I saw this thread months ago, when it didn't exist any solution for our fingerprints sensors but yesterday I had a bid surprise when I saw this program, it's fantastic.

Well, It works well will login and sudo, but I auth only with the finger, then when it starts, ask mi the superuser password to unlock the password ring.

Another problem is that whit gksudo it doesn't say anything but if you scan the finger, it starts the program well.

Well, obiously it is still a development program and althoug it have some "problems" and it is not completely joint with our system it work perfectly.

---

### Post by roaldz on 2007-12-19
> **aitorhh said:**
> Hello, I saw this thread months ago, when it didn't exist any solution for our fingerprints sensors but yesterday I had a bid surprise when I saw this program, it's fantastic.

Well, It works well will login and sudo, but I auth only with the finger, then when it starts, ask mi the superuser password to unlock the password ring.

Another problem is that whit gksudo it doesn't say anything but if you scan the finger, it starts the program well.

Well, obiously it is still a development program and althoug it have some "problems" and it is not completely joint with our system it work perfectly.

That´s the fault of the PAM-implementation of fprint. I´m sure it will be fixed soon. As you said, development:) As long as you know when to scan your finger, it´s okay:)

---

### Post by ebe0 on 2007-12-19
Thanks roaldz. i followed your method and now have a working fingure print scanner!!! Its really cool.
I have :  08ff:2580 AuthenTec, Inc.  device on HP dv6502au laptop.
Initially had some problem with libs, but solved them like this:

downloaded from: [http://www.madman2k.net/files/fprint-packages.tar](http://www.madman2k.net/files/fprint-packages.tar)
unpacked it
installed all the packages inside

[COLOR="Blue"]sudo dpkg -i --force-depends libfprint_0.0.4-0ubuntu1~ppa1_i386.deb 
sudo dpkg -i --force-depends libpam-fprint_0.2-0ubuntu1~ppa1_i386.deb 
sudo dpkg -i --force-depends fprint-demo_0.4-0ubuntu1~ppa1_i386.deb[/COLOR] 

had to force since there were some older libs installed in my machine.
[COLOR="DarkRed"]
[since i forced it install, they are broken and get --
[I]You have 3 broken packages on your system!
Use the "Broken" filter to locate them.
[/I]message when i run synaptic package manager. Also i'm not able to install new apps without first removing these. guess the only proper method is to satisfy dependency, although it works without it][/COLOR]

ran: [COLOR="Blue"]fprint_demo[/COLOR] from terminal
then scaned my fingure ... rest is self-explanatory

to enable loging into ubuntu using fingure print scanning:
make [COLOR="Blue"]/etc/pam.d/common-auth[/COLOR] look like this:

[COLOR="Red"]auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth       sufficient   pam_fprint.so
auth    required        pam_unix.so nullok_secure[/COLOR]

wish list:
keyring, firefox and other app which need passwords shd support this feature. Even though it is in development stage, it \'ll be nice if it is added in ubuntu repo, making installation far more simpler. Hope it happens in the near future.

Thank you all.

---

### Post by maximilianhauser on 2007-12-19
Yeah :) Now it works on my hp pavillion 9533eg, too. Great! Thank you very much! And sorry for my stupid question... In the future I should read better... ;)

---

### Post by kcleong on 2007-12-19
Really great to see it finally words with my hp nc8430 laptop! Great work :guitar:

---

### Post by LinuxIsInnovation on 2007-12-28
roaldz
Looks like all HP users are delighted :D
Great work :)
Anyway, waiting for the final release to come out.. I just don't like 1 thing: when I open synaptic or something that is launched as root, it just waits quietly without telling you to swipe your finger :(

---

### Post by kao on 2007-12-30
Works well on HP 6710b. I have made deb packages for x86_64 gutsy with checkinstall. If anybody wish, i can send it.

---

### Post by Bakyt Niyazov on 2007-12-30
Thank you guys! Especially **roaldz** and **ebe0**
I've Kubuntu 7.10 installed on my lovely **FujitsuSiemens Lifebook E8410** and got Fp scanning working :)

Almost all of my fingers are recognized.

That's really cool! 

I exactly followed ebe0 steps.

BTW
I have *Authentec 08ff:2580*.

Sorry for my English which is getting better, though.

---

### Post by roaldz on 2007-12-30
Libfprint has been updated since december 7th ([http://www.reactivated.net/fprint/wiki/Libfprint_v0.0.5](http://www.reactivated.net/fprint/wiki/Libfprint_v0.0.5))
I´ve built an AMD64 .deb using checkinstall, see attachment.


Double-click to install using Gdebi, or ```
sudo dpkg -i libfprint_0.0.5-1_amd64.deb
```
in order for me to use this, I had to link libfprint.so.0 from /usr/local/lib/ to /usr/lib:
```

sudo ln -s /usr/local/lib/libfprint.so.0 /usr/lib/libfprint.so.0

```
Because fprint_demo and pam_fprint think the libs are located in /usr/lib/ while this new version of libfprint installs them in /usr/local/lib/.
You can always unlink symbolic links (links you make with ¨ln -s¨) with the command ¨unlink¨, like: ¨unlink /usr/lib/libfprint.so.0¨
enjoy,

Roaldz

---

### Post by alexvd on 2008-01-03
Wow I am so suprised!  I started this thread months ago and forgot about it and decided to check today to see if thinkfinger was supporting authentec.  I followed a link and it sent me back to my original thread.  

Great work all on this!  Can't wait to try it out.

---

### Post by ghonz on 2008-01-09
I'm having a couple of issues with using fprint.  The only way to get fprint_demo to work I have to go through a terminal which is fine it works.  When I enroll my finger it takes a a few times to get it to enroll I keep getting the error "verification error -5" and occasionaly the program crashes and closes.  When it does enroll it doesn't capture all of my fingerprint only a small section which it never recognizes when I try to login.

Got any advice.  Its great that the program finally works it would be even better to lose the kinks.
The text I get from the terminal is below.

Jon

gonz@baldrick:~$ sudo fprint_demo
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
[sudo] password for gonz:
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
Segmentation fault (core dumped)

---

### Post by roaldz on 2008-01-09
> **ghonz said:**
> I'm having a couple of issues with using fprint.  The only way to get fprint_demo to work I have to go through a terminal which is fine it works.  When I enroll my finger it takes a a few times to get it to enroll I keep getting the error "verification error -5" and occasionaly the program crashes and closes.  When it does enroll it doesn't capture all of my fingerprint only a small section which it never recognizes when I try to login.

Got any advice.  Its great that the program finally works it would be even better to lose the kinks.
The text I get from the terminal is below.

Jon

gonz@baldrick:~$ sudo fprint_demo
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
Scan right index finger on AuthenTec AES1610
Scan didn't quite work. Please try again.
Scan right index finger on AuthenTec AES1610
fp:error [fpi_imgdev_capture] no image height assigned
Fingerprint verification error -5
[sudo] password for gonz:
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5
Segmentation fault (core dumped)
That´s probably a hardware-specific problem, because I don´t get those errors.. Sorry, can´t help you on that one, maybe someone with similar hardware?

Roald

---

### Post by aelray on 2008-01-12
hey thanks for the hints so far, i had downloaded fprint stuff for along time, but never got it working until i read this thread. but i still got a little problem in the log-in screen i can only use my right little finger, somebody got any idea how to change this?

greets
adel

---

### Post by cacycleworks on 2008-01-21
> **GavinZac said:**
> I've tried, and I've done it a few times over in the same way... it seems to be too sensitive. Maybe I need practice :/ I wonder, though, are the fingerprint sign ins on other platforms quite as fussy?

yes... and there, too, is an issue of software. i have a sony vaio laptop at home with the fingerprint reader. I used XP with the computer for a couple years before I rediscovered linux and the fp software with it was not well integrated either. It also took several tries to register a finger. And sometimes multiple tries to authenticate a log in.

I'm looking in to this again, as I'm wanting to implement some kind of not-password-based authentication scheme at my workplace. 

:) Chris

---

### Post by Yes_It's_Me on 2008-01-30
Thanks for the instructions!

I got fprint_demo going, but for some reason when i try to verify the scans i take i can never get it to accept it. I don't know what's going on. I've scanned every finger so many times and have not got it accepted once :( It always says that it found tons of "minutiae".

Does anyone know if i am doing anything wrong? I am using the authentic 16XX series.

---

### Post by alexvd on 2008-02-01
roaldz,

I am a bit lazy any chance you are someone else has created a .deb for 32 bit gutsy?

---

### Post by kc600 on 2008-02-02
Alexvd, you will find a useful link on the libpam_fprint page (see link on page 2 of this thread).

Question: fprint_demo works, i added the lines to pam.d conf/common-auth.conf, but i am still prompted for passwords. When i log in via gdm, when i sudo in a terminal, when i login via terminal, when i start synaptic e.d. Any suggestions?

PS ubuntu gutsy 7.10 on hp 6710b gr679et

---

### Post by roaldz on 2008-02-04
> **alexvd said:**
> roaldz,

I am a bit lazy any chance you are someone else has created a .deb for 32 bit gutsy?

No I've not created 32bit debs.

---

### Post by kcleong on 2008-02-04
> **alexvd said:**
> roaldz,

I am a bit lazy any chance you are someone else has created a .deb for 32 bit gutsy?

Here you go:

[fprint-demo_0.4-3.5_i386.deb]("http://www.leong.nl/oss/deb/fprint-demo_0.4-3.5_i386.deb")
[libfprint_0.0.5-3.4_i386.deb]("http://www.leong.nl/oss/deb/libfprint_0.0.5-3.4_i386.deb")
[pam-fprint_0.2-4.5_i386.deb]("http://www.leong.nl/oss/deb/pam-fprint_0.2-4.5_i386.deb")

---

### Post by roaldz on 2008-02-06
> **kcleong said:**
> Here you go:

[fprint-demo_0.4-3.5_i386.deb]("http://www.leong.nl/oss/deb/fprint-demo_0.4-3.5_i386.deb")
[libfprint_0.0.5-3.4_i386.deb]("http://www.leong.nl/oss/deb/libfprint_0.0.5-3.4_i386.deb")
[pam-fprint_0.2-4.5_i386.deb]("http://www.leong.nl/oss/deb/pam-fprint_0.2-4.5_i386.deb")

Yeah,, another Dutch guy:)

---

### Post by alexvd on 2008-02-21
Thanks for the debs and my name is VanDeusen :)

---

### Post by mike984 on 2008-03-05
I was able to get my fingerprint reader to work fine using these directions.

However, I cannot attach to my wireless network now.  When I choose my network from the list, I get a prompt asking for the password and I type it in but it cannot connect.

Is there a way to temporarily disable the fingerprint software?

---

### Post by roaldz on 2008-03-07
> **mike984 said:**
> I was able to get my fingerprint reader to work fine using these directions.

However, I cannot attach to my wireless network now.  When I choose my network from the list, I get a prompt asking for the password and I type it in but it cannot connect.

Is there a way to temporarily disable the fingerprint software?

You can uninstall it for a while, and recover your pam config like it was before..?

---

### Post by sayakb on 2008-03-20
@roaldz
Is there any new version available for these packages? I would definitely appreciate it if my computer asks me to swipe the finger, rather than simply freezing and expecting me to know what to do..

---

### Post by roaldz on 2008-03-20
> **LinuxIsInnovation said:**
> @roaldz
Is there any new version available for these packages? I would definitely appreciate it if my computer asks me to swipe the finger, rather than simply freezing and expecting me to know what to do..

You asked at the right time, today a new version is available!

Check out [http://reactivated.net/fprint](http://reactivated.net/fprint)

---

### Post by lobo99 on 2008-03-22
Hello!
I have the same problem that  ghonz  (page 5)
fp:error [fpi_imgdev_capture] no image height assigned
fp:error [fp_enroll_finger_img] enroll failed with code -5

I have HP pavilion tx 1000 
 ID 08ff:1600 AuthenTec, Inc.

Any solution?

Thank you!

---

### Post by raidensix on 2008-04-03
I keep getting a "No Devices Found" with fprint_demo but lsusb tells me there's a generic finger print reader device. I'm using a Shuttle SP35P2Pro but I'm not sure of the exact model of the reader. Here's the output from lsusb:

------------------------------------------
Bus 005 Device 002: ID 1307:1171  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1307 
  idProduct          0x1171 
  bcdDevice            1.00
  iManufacturer           1 Generic USB Device
  iProduct                5 Generic Finger Printer
  iSerial                 3 01234567890123
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
------------------------------------------

Any help appreciated.

---

### Post by whitefort on 2008-04-05
> **roaldz said:**
> To be able to login with your fingerprint, I did this: (etc)

Thanks a million for this.  I bought a Lenovo n100 last year, and all my friends were wildly impressed when they saw it.

THEM: Oh WOW!!  It has a FINGERPRINT READER???  How cool is THAT?!
ME:  Uh, yeah...  Um... but y'know, I use Linux, and there's no software for fingerprint readers yet...
THEM:  Are you serious?  You GOTTA dump Linux!!  A fingerprint reader would be so, so COOL!

And so on.

Now, thanks to your post, I finally have my mega cool fingerprint logon working perfectly.
I followed your instructions (with a sinking feeling, because I was sure that it wouldn't work and that I'd totally mess up my machine).  I couldn't believe it when it 'just worked.'

Many thanks!!!  The honour of Linux is restored!

---

### Post by roaldz on 2008-04-05
> **whitefort said:**
> Thanks a million for this.  I bought a Lenovo n100 last year, and all my friends were wildly impressed when they saw it.

THEM: Oh WOW!!  It has a FINGERPRINT READER???  How cool is THAT?!
ME:  Uh, yeah...  Um... but y'know, I use Linux, and there's no software for fingerprint readers yet...
THEM:  Are you serious?  You GOTTA dump Linux!!  A fingerprint reader would be so, so COOL!

And so on.

Now, thanks to your post, I finally have my mega cool fingerprint logon working perfectly.
I followed your instructions (with a sinking feeling, because I was sure that it wouldn't work and that I'd totally mess up my machine).  I couldn't believe it when it 'just worked.'

Many thanks!!!  The honour of Linux is restored!

Well... You´re welcome:)

---

### Post by Gorlith on 2008-04-13
Trying to get this working on my System 76 Gazelle, not sure if the reader on it is supported using the drivers in this thread, but anyway:

Getting this error when I try to run fprint

fprint_demo: error while loading shared libraries: libfprint.so.0: wrong ELF class: ELFCLASS64

---

### Post by roaldz on 2008-04-13
> **Gorlith said:**
> Trying to get this working on my System 76 Gazelle, not sure if the reader on it is supported using the drivers in this thread, but anyway:

Getting this error when I try to run fprint

fprint_demo: error while loading shared libraries: libfprint.so.0: wrong ELF class: ELFCLASS64

Are you running 32 or 64 bit ubuntu? and have you installed 32 or 64 bit .debs? The debs I made are all 64 bit.

---

### Post by Gorlith on 2008-04-13
i'm running 64
i'll see if i missed anything

edit:
got it running, doesnt see my scanner though, guess it doesnt support the hardware in the gazelle

---

### Post by Vadi on 2008-04-15
> **raidensix said:**
> I keep getting a "No Devices Found" with fprint_demo but lsusb tells me there's a generic finger print reader device. I'm using a Shuttle SP35P2Pro but I'm not sure of the exact model of the reader. Here's the output from lsusb:

*[I]-snip-*[/I]

Any help appreciated.

I'm in the same boat as you. lsusb doesn't give much into about fingerprint, but doing a verbose check yielded this:

```
Bus 002 Device 003: ID 147e:2016  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147e 
  idProduct          0x2016 
  bcdDevice            0.01
  iManufacturer           1 TouchStrip        
  iProduct                2 Fingerprint Sensor   
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
```

Does anyone have any idea how to get fprint to recognize it?

---

### Post by roaldz on 2008-04-16
You need a driver. No driver, no joy.

---

### Post by GavinZac on 2008-04-25
works fine again in Hardy, but it is still far too sensitive. Only one in 20 scans matches.

---

### Post by alexvd on 2008-05-01
Hi after a very long time I got a chance to try this.  I am actually running Hardy now and I download the 32 bit debs and it all installed with no issue.  Running it from terminal brought up the fprint_demo with no errors.  However it says that it did not detect any hardware so I could not do any enrollment.  

I ran the following and got the output below.  
[I]
alexvd@alexvd-tablet:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 011: ID 08ff:2500 AuthenTec, Inc. 
Bus 003 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
alexvd@alexvd-tablet:~$[/I] 

Does this mean I don't have a authentec 2501? and its actually older and unsupported.  I was pretty sure it was a 2501?  Do I need another driver?

Any help would be great.

---

### Post by sayakb on 2008-05-23
Do the amd64 packages work for Hardy (they worked for me in Gutsy).. Shouldn't they cause a broken package because of dependence on old gutsy libraries? Or should I go ahead and install them in Hardy?

---

### Post by alexvd on 2008-06-06
Hi so I did more checking and it appears that the driver that is used in windows for the m1400 tablet I have is in fact the aes2501 so I don't understand what I am doing wrong that it does not detect properly.

I am running Hardy what should I do troubleshoot?

---

### Post by chiccoch on 2008-06-13
great work, thx roaldz!!!

works perfectly without one single error on Hardy 64Bit with HP 8510w!!!!

I have now even found a solution for the gksu-problem. My fingeprint-sensor now even works perfectly with synaptics and update-manager an stuff like this.

> **yupie said:**
> I have written a quick-made python script, interacting between sudo and gksu and supporting fprint. You must copy it to /usr/local/bin without an extension.

```
sudo mv ./gksu.py /usr/local/bin/gksu
sudo chmod 755 /usr/local/bin/gksu
sudo apt-get install python-gnome2-extras python-pexpect
```

Only sudo is supported, su will be handled directly by gksu.

___________________________________________
HP8510w, Intel Core 2 Duo T9300 (Penryn) 2.5GHZ, RAM 2x2GB OCZ 677MHZ, HD 200GB / 7200RPM, nVidia Quadro NVS FX570M (256MB), Ubuntu Hardy 64 BIT 8) :cool:

---

### Post by Vaseline on 2008-06-22
Question: fprint_demo works, i added the lines to pam.d/common-auth, but i am still prompted for passwords. When i log in via gdm, when i sudo in a terminal, when i login via terminal, when i start synaptic e.d. Any suggestions?

---

### Post by alexvd on 2008-06-24
Hi I have been searching on this and I think I found something.
The motion tablet works with fprint but I dont know how to do what he is describing below.

Can someone please help out?




[I]I have a Motion Computing M1400 Tablet with an AES2500 chip (or  
something like that).  The aes2501 driver works perfectly fine with  
it, but I needed to add 0x08ff:0x2500 to the driver's  vender/product  
table.  Other than that it works great!

BTW, I could not create an account on the Wiki to put this on the  
Supported Devices page, it did not give me an option to create an  
account.

Regards,
Daniel Hazelbaker
[/I]

---

### Post by roaldz on 2008-06-25
> **alexvd said:**
> Hi I have been searching on this and I think I found something.
The motion tablet works with fprint but I dont know how to do what he is describing below.

Can someone please help out?




[I]I have a Motion Computing M1400 Tablet with an AES2500 chip (or  
something like that).  The aes2501 driver works perfectly fine with  
it, but I needed to add 0x08ff:0x2500 to the driver's  vender/product  
table.  Other than that it works great!

BTW, I could not create an account on the Wiki to put this on the  
Supported Devices page, it did not give me an option to create an  
account.

Regards,
Daniel Hazelbaker
[/I]
You can´t use the binary (pre-compiled .debs) drivers for this.You need to get the source code, and make some adjustments.

---

### Post by alexvd on 2008-06-25
Thanks for the reply.  I have no idea how to do that for 32bit hardy.  Is thier a guide or how to on how to build from source and add that entry somewhere?  I am guessing I may have to ask the libfprint devs to do that and than try and use the binaries or get a kind soul to build a 32 deb right?

---

### Post by cacycleworks on 2008-07-01
> **alexvd said:**
> Thanks for the reply.  I have no idea how to do that for 32bit hardy.  Is thier a guide or how to on how to build from source and add that entry somewhere?  I am guessing I may have to ask the libfprint devs to do that and than try and use the binaries or get a kind soul to build a 32 deb right?

Compiling a package is actually easy ... it's getting all the packages on your system to do the compile is the harder part. I've compiled the kernel before, which ended up only being about choosing the options before the compile. The compile itself was anticlimatic.

Installing the packages to enable compiling doesn't hurt your system at all ... and once you're completely finished, you can remove the compiling packages so your updates are smaller/faster.

If I had my desktop configured to compile at this moment, I'd do it for you. Right now, none of my 5 x86_64 machines have linux headers or any make tools installed -- and I'm in the middle of a crunch. (but is that normal?) 

:) Chris

---

