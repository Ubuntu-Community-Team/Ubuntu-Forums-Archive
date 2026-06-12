---
title: "Canon LIDE 100 scanner"
date: 2008-12-04
forum: Hardware
---

### Post by sahmed001 on 2008-12-04
I just bought a Canon LiDE 100 scanner. 

Cheap USB scanner. Pretty good quality. Bus powered

lsusb shows the following
Bus 007 Device 007: ID 04a9:1904 Canon, Inc. 


However xsane doesn't detect it. Any suggestions?

Saif

---

### Post by Gallardo Spyder on 2008-12-04
I had the Lide 200 USB...  I am pretty experienced in Linux and Ubuntu - but there is really nothing I could do to get the 200 to work.  Ended up putting it on a Windows box (the only one I have left in the house).

Good scanner overall - cannon is not real good when it comes to Linux support...

---

### Post by koba101 on 2008-12-19
anyone got any clue about this?  there's got to b a way for this scanner to work 

 i get this output when running san-find-scanner

```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9, product=0x1904, chip=GL843?) at libusb:007:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

but scanimage -L generates the following


```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

any tips? suggestions?

---

### Post by segmentoffset on 2008-12-21
I would love to hear any ideas or suggestions as well- I'm having the same problem with a LIDE 200.  It looks like both the 100 and 200 aren't even listed on the SANE site at all..

---

### Post by redonwhite on 2008-12-23
I was thinking about purchasing the 200 and would also like to see if there are any ways to get it working.

---

### Post by sideburns on 2008-12-23
> **redonwhite said:**
> I was thinking about purchasing the 200 and would also like to see if there are any ways to get it working.

Go to the SANE project site's list of supported scanners, [http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl), and see if yours is listed.  If so, download the driver (as a .deb) install it and see if that helps.  it's how I got an Epson CX7450 to scan.

---

### Post by Alex22 on 2008-12-28
Guys, have you tried to use the driver of similiar Canon scanner? This method often goes succesful.

Here we have close number models, like LIDE 90, 80, and so on:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide+100&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide+100&bus=usb&v=&p=)

You know, they put new models every month to keep up selling, but it might only be the different outside of the same sh.t.
I do care, 'coz i'm interested in buying LIDE 100. :)

---

### Post by sideburns on 2008-12-28
> **Alex22 said:**
> Guys, have you tried to use the driver of similiar Canon scanner? This method often goes successful.

An excellent suggestion.  Right now, both CUPS and xsane think my CX7450 all-in-one is a CX7400.  Who cares, as long as it works?  Try the model numbers closest to yours, and see if one works.  You've got nothing to lose except a little time because the worst thing that can happen is, quite literally, nothing.

---

### Post by marekklein on 2009-01-12
Anyone found solution?

---

### Post by fno on 2009-01-14
> **marekklein said:**
> Anyone found solution?

Unfortunately not, and it's unlikely anyone will find a solution anytime soon due to the fact that Canon considers the information needed to produce drivers classified, and by explicitly not supporting Linux.

Just checked with Canon support since a LiDE 200 would be nice for my needs, but obviously Canon wants to stay on my boycott list.

---

### Post by phaggood on 2010-02-04
I purchased this as a gift last Christmas because I had so much success with a previous Lide and Linux.  Oh well.  Anyone know another good sub $100 scanner that *does* support Ubuntu?

---

### Post by Thomas Garman on 2010-02-04
I got a Cannon Pixma MP250 for $40 at Microcenter, which comes with a Scanner, and downloaded the scangearmp driver from the Canon website.  It works very well.

---

### Post by mookiemeister on 2010-03-03
I have a Canon LiDE 100 scanner too.  Anyone know if someone is working on adding support of this scanner in XSane?

---

### Post by desertdog on 2010-03-04
One of the Sane project developers is working on adding support for the Canon Lide 200. He predicts support by the end of this year.

---

### Post by AlexanderDGreat on 2010-04-20
Oh man! I got 2 of these scanners. Why don't they support a Linux driver? The thing is, **THERE SHOULD BE A LAW THAT ALL HARDWARE MUST INCLUDE A TAR BALL FOR OPEN SOURCE OS!**

M$ Winblow$ is preventing the advancement of technolog, or not.

---

### Post by desertdog on 2010-06-14
The Lide 100 is now supported by Sane. You need to download and compile the latest source code. Support for the LIDE 200 should be added soon.

> To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

sudo apt-get install libusb-dev build-essential libsane-dev

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

sudo apt-get install git-core

3) Now use the git that was just installed to get the sane backends using the following command:

git clone git://git.debian.org/sane/sane-backends.git

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

cd sane-backends

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

make <--- this one takes a while

sudo make install

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

5) You need to edit a file, but you need to be root to edit it, so:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY!  
Instructions modified version of Shutter4U's post.


---

### Post by fno on 2010-06-15
> **desertdog said:**
> The Lide 100 is now supported by Sane. You need to download and compile the latest source code. Support for the LIDE 200 should be added soon.
That is great news! Thanks for the info! Finally!

---

### Post by rsaavedra on 2010-06-15
> **desertdog said:**
> The Lide 100 is now supported by Sane. You need to download and compile the latest source code. Support for the LIDE 200 should be added soon.

Did not work for me at all. I have the Lide 100, and followed your instructions exactly, under Ubuntu 10.04. After all your instructions I rebooted Ubuntu. Went to Applications->Graphics->XSane Image Scanner; then got the following two little message dialogs, one after the other:

Title  : "xsane 0.996"
Message: "scanning for devices"

Title  : "No devices available"
Message: "no devices available"

I believe those were exactly the same messages I was getting from xsane before your suggested steps.

Also tried invoking gksudo xsane, same thing.

---

### Post by desertdog on 2010-06-15
Hmmm, try installing libsane-dev, then recompiling. (I edited my earlier post to include this step earlier tonight).

$sudo apt-get install libsane-dev

then skip to step #4 above.

Also check the file /etc/sane.d/genesys.conf and make sure your scanner is listed.

---

### Post by rsaavedra on 2010-06-16
> **desertdog said:**
> Hmmm, try installing libsane-dev, then recompiling. (I edited my earlier post to include this step earlier tonight).

$sudo apt-get install libsane-dev

then skip to step #4 above.

Also check the file /etc/sane.d/genesys.conf and make sure your scanner is listed.
I did have libsane-dev --followed your steps after your latest modification on the steps post.

Will check that file genesys.conf later today once back at home. Thanks!

---

### Post by berthold_dk on 2010-06-16
I have a CanoScan Lide 200 and I am running 10.04. I tried desertdogs recipe, but to no avail. I realize that the support for 200 is underway but had to give it a go. If the developer is out there - you :guitar: if you finish the support for the 200 soon... ):P

---

### Post by desertdog on 2010-06-16
The lide 200 should be partially supported. 

Try checking $cat /etc/sane.d/genesys.conf and see if your scanner is listed in that file. 

If not, try 
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

Then try $scanimage -L and $scanimage >image.pnm

---

### Post by rsaavedra on 2010-06-17
> **desertdog said:**
> Also check the file /etc/sane.d/genesys.conf and make sure your scanner is listed.
I can see the following entries for LiDE 35/40/50, and for LiDE 60 in genesys.conf:
```

# Canon LiDE 35/40/50
usb 0x04a9 0x2213

# Canon LiDE 60
usb 0x04a9 0x221c

```

But LiDE 100 is not listed. What values should I exactly add for it?
By the way, my lsusb command shows the following:
```

raul@raul-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 12a7:3160 Trendchip Technologies Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:1904 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by desertdog on 2010-06-17
try
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

Then try $scanimage -L and see if it is listed.
Then try $scanimage >image.pnm

---

### Post by madmaddin on 2010-06-17
I have a Canon LIDE 200 and I'm running Ubuntu 10.04. I managed to get the LIDE200 running following deserdog's steps. The scanner is now recognized by the system and it can be controlled. Unfortunately the scanning results are not ok yet. The result is always a kind of weird pattern. I tried different settings (color/grey, resolution) but the result was always the same. Can somebody look into this or give me hints what to do?  Thanks! Great achievement so far!

---

### Post by desertdog on 2010-06-17
@madmaddin: I am glad my instructions worked for you. I think that problem that others were having was related to the scanner not showing up in /etc/sane.d/genesys.conf file.

As far as your images not looking good, here is a quote from the sane developers mailing list 2 days ago:> Hello,

       with the latest git version of the genesys backend Canon LiDE 100 is now
completely supported, and also the LiDE 200 which is only missing 2400 dpi
resolution. I'm currently working on 2400 dpi support and it should be
available in a couple of weeks.

       Bug and success reports are welcomed.

Regards,
       Stef


There may have been some updates to the source code since my initial instructions. To check to see if you have the latest source code,
$cd ~/sane-backends
$git pull
If it says you are up to date, do nothing. If there is new source, then repeat the 
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install

---

### Post by madmaddin on 2010-06-17
@desertdog    

I'm aware that the problems mentioned before were related to the genesys.conf file. I just wanted to confirm that your steps did work for me (I have never ever compiled anything with my Linux system before and I'm rather a pure user than a Linux expert). In my opinion your instructions are clear and do work if all the steps are carefully executed.    

Ok, it seems like the problem I have experienced is quite common at this early point of the development. I will wait patiently for some code update.    

Thanks!

---

### Post by berthold_dk on 2010-06-17
> **desertdog said:**
> The lide 200 should be partially supported. 

Try checking $cat /etc/sane.d/genesys.conf and see if your scanner is listed in that file. 

If not, try 
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

Then try $scanimage -L and $scanimage >image.pnm

The Lide 200 was not in the genesys.conf file, so I copied the one from sane-backends. 

$scanimage -L gave this

> device `genesys:libusb:001:005' is a Canon LiDE 200 flatbed scanner$scanimage > image.pnm actually got the scanner doing something - it didn't sound quite as on Windows ;) and the resulting image was a blank page of about 8 mb.

If I start Xsane up from the menu, it still doesn't find the scanner.

---

### Post by rsaavedra on 2010-06-17
> **desertdog said:**
> try
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

Then try $scanimage -L and see if it is listed.
Then try $scanimage >image.pnm

That made it work, thanks! 

Ran XSane and scanned a sample image in color and 16 bit depth, looks a little dark but looks ok. Will play with the gamma and brightness option. 

Also ran the git pull but mine was up-to-date.

PS. The scanner does sound different on Ubuntu compared to on Windows XP. It seems noisier on Ubuntu.

---

### Post by desertdog on 2010-06-23
@berthold_dk and @madmaddin
There have been a couple of updates in the last couple of days. You might want to update to the latest version with
```
cd ~/sane-backends
git pull
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
scanimage -L
scanimage --resolution 150 --mode Color >image.pnm
```

@rsaavedra
I am not sure why scanner is louder in linux. I don't have this scanner to confirm your observation.

---

### Post by madmaddin on 2010-06-25
@desertdog
I have compiled and installed the updated but still scanning doesn't work properly. However the pattern which I mentioned in the beginning changed so it looks like something has been updated.

Can someone else confirm the same observation with LIDE 200? Or is there somebody who managed to scan properly?

---

### Post by desertdog on 2010-06-25
@madmaddin
The developer stated that LiDE 200 support should be complete very soon. So you can keep checking back with the "git pull" command to see if there are any updates.

Meanwhile, you could try both Xsane and SimpleScan frontends to see if there is a difference. If you are having problems with Xsane, you might want to adjust the gamma and brightness settings.

You could also try scanning from the command line with something like.

```
scanimage --resolution 150 --mode Color >image.pnm
```

Try resolutions of 75, 150, 300, 600, 1200, and modes of Color, Gray and Lineart. If you have a webcam or second scanner add 

```
-d genesys
```
to your list of command flags.

I don't have that scanner to confirm your findings.

---

### Post by madmaddin on 2010-06-25
@desertdog

Thanks for your support! I have tried all these options (Xsane, scanimage - with different brightness and gamma settings and different resolutions). I believe there is a general problem with the capture/transfer of the scanned picture. The pattern of the scan looks completely strange and has not much to do with the original which has been scanned. Even if you do an empty scan the pattern is there. Maybe I can provide some sample over the weekend. At the end I think I need to wait until LIDE 200 gets full support.

Anyway, thank you for your help!

---

### Post by kelvin spratt on 2010-06-25
I have a Lide 20 This scanner works in Linux/ubuntu using Xsane and any old cannon drivers in fact its a superb scanner.
Except it does not work in Win7 with the correct drivers.
So its 1 up for Linux.

---

### Post by xionc on 2010-06-29
> **AlexanderDGreat said:**
> Oh man! I got 2 of these scanners. Why don't they support a Linux driver? The thing is, **THERE SHOULD BE A LAW THAT ALL HARDWARE MUST INCLUDE A TAR BALL FOR OPEN SOURCE OS!**

M$ Winblow$ is preventing the advancement of technolog, or not.

I agree. I even came as far as sending email to European Comission. You can find it on my Polish blog: arekk.blox.pl

The post is in Polish, but my letter is in English.

I encourage you to lobby local regulators for appropriate laws that would encourage more competition from OS producers. In case of EU members - it may help to contact the Commission which has a record of getting on the way of IT monopolies.

---

### Post by laprjns on 2010-07-03
First, I use Salix, which is a derivative of Slackware, not Ubuntu.  But I do have a Canon Lide 200 and was googling to find how to get it working when I found this thread. Followed desertdog instructions, obviously making the necessary adjustments for my flavor of Linux, and got it working  Color pictures come out a little darker than when done in Windows, but it can be adjusted using xsane.  Scanning black and white text, the white background come out somewhat grey but again it can be adjusted.  Used the 20100703 version from git. Thanks for the info.

---

### Post by berthold_dk on 2010-07-05
I followed these instructions
> **desertdog said:**
> 
```
cd ~/sane-backends
git pull
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
scanimage -L
scanimage --resolution 150 --mode Color >image.pnm
```

and got a result that was pretty ok, although a bit dark. The scanner sounds less loud now btw. thx :)

But the scanner programs (Xsane and simple scan) still report that no scanners are found.

---

### Post by agaida on 2010-07-06
> **AlexanderDGreat said:**
> Oh man! I got 2 of these scanners. Why don't they support a Linux driver? The thing is, **THERE SHOULD BE A LAW THAT ALL HARDWARE MUST INCLUDE A TAR BALL FOR OPEN SOURCE OS!**

M$ Winblow$ is preventing the advancement of technolog, or not.
And all cars have to run on biogas. This is really out of world. Every Vendor will make money with his product. So if the product dont work with your operation system, got it to work by yourself or buy another product. IMHO thats also called market..

BTW. not Microsoft, the vendor has to write the drivers. This can be very expansive, so not every vendor does this for linux.

---

### Post by zharley on 2010-08-05
I bought an LIDE 200 because the git (development) version of SANE   currently lists the support  for both LIDE 100 and LIDE 200 as  "complete":

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON)

@desertdog:  Good directions (#16 of this thread).

I followed these steps on a clean install of Ubuntu 10.04

```

sudo apt-get install libusb-dev build-essential libsane-dev git-core
git clone git://git.debian.org/sane/sane-backends.git
cd sane-backends
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install

```However, as others have noticed, LIDE 100 and LIDE 200 don't end up in /etc/sane.d/genesys.conf

That's definitely a problem. But it seems strange to then manually copy over genesys.conf.in from the sources.

I found that simply uninstalling and reinstalling finally puts the right stuff in genesys.conf and possibly corrects other things. (Probably a bug?)

```

sudo make uninstall
sudo make install

```Anyway, it works. The scanners show up in genesys.conf and my LIDE 200 scans.

```

sudo scanimage -L

```Yields:
> 
device `genesys:libusb:001:007' is a Canon LiDE 200 flatbed scanner
A 600 dpi color scan looks good to me. Perhaps it's a pinch dark, so it might benefit from gamma tweaking.
```

sudo scanimage --progress --mode color --resolution 600 > /tmp/test.pnm

```

Here is part of a playing card:
[IMG]http://skythink.com/get/016aa61d67c8/card.jpg[/IMG]

At 600 dpi, you can see some fine detail on a cheque... that small black text on the right is the signature line.
[IMG]http://skythink.com/get/856ece87ae04/microprint.jpg[/IMG]

---

### Post by fig_wright on 2010-08-11
Any thoughts on how to get a LiDE 700F to work? I tried the above methods, but get no joy:
> ~/sane-backends > sudo lsusb
Bus 001 Device 007: ID 04a9:1907 Canon, Inc. 

~/sane-backends > sudo scanimage -L
device `v4l:/dev/video0' is a Noname Camera virtual device


And no, my scanner isnt a camera!

---

### Post by fig_wright on 2010-08-11
For a laugh based on the above I tried adding the following to my /etc/sane.d/genesys.conf
> # Canon LiDE 700F
usb 0x04a9 0x1907

... and 
> -d genesys
flags, but still just 
device `v4l:/dev/video0' is a Noname Camera virtual device

That'll teach me to buy something new with Linux. :(

---

### Post by desertdog on 2010-08-11
@fig_wright: the 700f has been reported to have a GL847 processor chip, like the Lide 100 and 200. To confirm this, you could type:
$sane-find-scanner -v -v.

You could then try to follow the instructions at [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone) to hijack the settings for either the 100 or 200.

That other device that is showing up as a scanner is probably a webcam. You could comment out v4l in the file /etc/sane.d/dll.conf using a text editor as sudo.

---

### Post by AlexanderDGreat on 2010-08-12
> And all cars have to run on biogas.
No, actually, it depends on what type of vehicle that is, a diesel or a gas, or biogas, but in terms of computing, ALL devices should be compatible on all OS, just to make it run.

Have you ever bought a car that the salesman said, Oh sorry you can only drive this at night.


> This is really out of world. Every Vendor will make money with his product.
Yeah, you sold me, mental note, DON'T BUY CANON SCANNERS, how's that for making money?

> So if the product dont work with your operation system, got it to work by yourself or buy another product.
CANON = number of customers - 1, that is me.

> IMHO thats also called market..
Don't they need to INCREASE their market share? Oh, Linux users, who cares about them?

> BTW. not Microsoft, the vendor has to write the drivers. This can be very expansive, so not every vendor does this for linux. - Yes, I agree, but why can HP do it? :D

---

### Post by Uncle Bill on 2010-08-14
I ran desert dog's procedure, and as su I can work the scanner. However, simple scan and Xsane don't find the scanner. I suspect some file needs a permission changed, but which one? (LIDE 100)

---

### Post by desertdog on 2010-08-14
Uncle Bill:
Reboot and try again. 
If that doesn't work the following thread has some other ways to set permissions, so that you won't have to scan as sudo

[http://ubuntuforums.org/showthread.php?t=1147052&highlight=canoscan](http://ubuntuforums.org/showthread.php?t=1147052&highlight=canoscan)
(see post #16)

---

### Post by Uncle Bill on 2010-08-15
desertdog,

After many years of Windows :(, I always try rebooting as a first attempt when something doesn't work, so that didn't fix it. I edited (Ubuntu 10.04)

sudo gedit /lib/udev/rules.d/40-libsane.rules 

and added the lines (info from the scanimage -L)

# Canon CanoScan LiDE100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

saved the file, then rebooted, and it WORKS through both SimpleScan and XSane!

Thanks!!!:D

---

### Post by calande on 2010-08-15
Hi there, I'm following [this tutorial]("https://help.ubuntu.com/community/CompileSaneFromSource"), and sane-find-scanner reports my scanner connected on the USB port, however, sudo scanimage -L doesn't return any scanner. Any idea? Thanks.

---

### Post by desertdog on 2010-08-15
Uncle Bill,
I am glad it worked for you.:o

For what it is worth, you shouldn't have to reboot in linux, when updating a program. There is probably a command line entry to restart the sane daemon and the udev daemon, but for me it is faster to reboot than to research how to restart the daemons.

---

### Post by desertdog on 2010-08-15
> Hi there, I'm following this tutorial, and sane-find-scanner reports my scanner connected on the USB port, however, sudo scanimage -L doesn't return any scanner. Any idea? Thanks.

Did you check the file /etc/sane.d/genesys.conf to see if your scanner is listed? If not you will need to open a text editor as root and add your scanner to this file

```
sudo gedit /etc/sane.d/genessys.conf
```

Then add the entry for your scanner to that file.

```
# Canon LiDE 100
usb 0x04a9 0x1904

# Canon LiDE 200
usb 0x04a9 0x1905
```

---

### Post by calande on 2010-08-16
Thanks, desertdog, it allowed me to scan as root but not as a user, so I went on to the "Permissions" section of the tutorial, it didn't work. I restarted my computer and I am now able to scan as a regular user. I can't believe I can use this scanner on Linux after all these years! Thanks again ;)

---

### Post by diegocarrera on 2010-08-24
Hola a todos, 

Hoy encontré en internet una solución que sí funciona y permite instalar el escaner CANON LIDE 100 en Ubuntu 10.04.

[http://ubuntuforums.org/showthread.php?t=1001955](http://ubuntuforums.org/showthread.php?t=1001955)


Saludos

---

### Post by diegocarrera on 2010-08-24
.[]("http://ubuntuforums.org/showthread.php?p=9462309#post9462309")

---

### Post by diegocarrera on 2010-08-28
_._[]("http://ubuntuforums.org/showthread.php?p=9462309#post9462309")

---

### Post by mahiyar on 2010-08-30
Based on this single post, I went ahead and got the canoscan lide-100,  previously I had HP Scanjet which also had iffy working and in 64bit  system did not work. However there was no such problem for Lide-100,  works perfectly in 64bit also. Thanks Desertdog.

---

### Post by clickwir on 2010-09-28
> **mahiyar said:**
> Based on this single post, I went ahead and got the canoscan lide-100,  previously I had HP Scanjet which also had iffy working and in 64bit  system did not work. However there was no such problem for Lide-100,  works perfectly in 64bit also. Thanks Desertdog.

Did you have to do anything special other than just plug it in and start xsane? Did you have to follow his instructions for re-compiling?

I need a better scanner for Linux and I really REALLY like the size and single USB cable concept for the LiDE series.

I'd be willing to put up $10 towards drivers for the 100 and 200 series if it would help move it along quicker. I'd rather put that $10 into driver development than a different scanner that just simply costs more.

---

### Post by mahiyar on 2010-09-28
Just follow instructions in post #16 and you are done, thats what I did. And yes the steps do need compiling of git-core, however the instructions are easy to follow.

---

### Post by PJW9779 on 2010-10-21
Excellent HowTo on [http://robsworldoftech.blogspot.com/2010/09/canon-canoscan-lide-100-on-ubuntu-or.html](http://robsworldoftech.blogspot.com/2010/09/canon-canoscan-lide-100-on-ubuntu-or.html).
Works for me.

---

### Post by rdesgroppes on 2010-10-22
Hi,
There is a simpler solution, just consisting in adding an [adhoc ppa repository]("https://launchpad.net/~info-g-com/+archive/gc-sane") to your apt sources:
```

sudo add-apt-repository ppa:info-g-com/gc-sane
sudo aptitude full-upgrade
sudo restart udev

```
(or reboot)
That way, there's no compilation, no manual edit, and the most important: your system remains under apt control.
Régis

---

### Post by RobertEr on 2010-10-27
I have to get my Canon Canoscan Lide 100 scanner working and Haven't had any success. I have got to the where I was  on the libsane rules. O believe  I was supposed to add two lines which would then have added my scanner but exactly was i supposed to add those two lines. was I jsut to add it to the bottom of the list or with the other Canon scanners, Just because I add it to the list does it work. I have tried on Windows XP  and it only limps along on XP.

---

### Post by egay on 2011-01-13
Hello Desertdog,

I am a complete novice in Linux/Ubuntu but I decided to migrate anyway from Win OS - so naturally, I met a number of difficulties, and one of them is exactly this issue:confused:

But I am very happy I found your post - it is very asy to follow, especially for someone like me who can't understand what those commands are (reminds me of my DOS years... I am not a techy, but just a common user).

THANK YOU VERY much for your solution!

I love to be in company of geniuses!

Regards from Manila!

egay
**.e.**
):P

PS: I am going to post this in my blog [http://ezdapiton.wordpress.com/](http://ezdapiton.wordpress.com/) ciao! .e.


> **desertdog said:**
> The Lide 100 is now supported by Sane. You need to download and compile the latest source code. Support for the LIDE 200 should be added soon.

---

### Post by JCM3000 on 2011-06-06
Posts #16 and #19 solved this for me - found the scanner at the back of a cupboard where I had put it about 18 months ago after failing to get it to work.

Many thanks desertdog!

---

### Post by Hartmut27 on 2011-07-02
Since I have Ubuntu [SIZE=2]10.04[/SIZE] LTS which does *not* support _Canon LIDE [SIZE=3]*100*[/SIZE]_ out of the box, I had to get the support from Ubuntu [SIZE=2]10.10[/SIZE] like the following:

[SIZE=4]First:[/SIZE]
In the shell do:
sane-find-scanner -v -v |less
With the / and &#8216;n&#8217; key do a search for &#8220;found&#8221;
Then you find somewhere &#8220;found scanner ...&#8221;
Check the vendor and product code
vendor 0x04a9
product 0x1904

[SIZE=4]Then[/SIZE]
sudo add-apt-repository ppa:laxx/random-fixes
sudo apt-get update
&#8230; the last step prints *errors*, since the sources are valid only for &#8220;Ubuntu 10.10 Maverick&#8221;, that means...

goto to &#8220;Ubuntu Software Center&#8221;, then Edit->Software Sources &#8594; Other Software &#8594;edit the line
&#8220;[http://ppa.launchpad.net/fredp/ppa/ubuntu&#8221;]("http://ppa.launchpad.net/fredp/ppa/ubuntu%E2%80%9D")

therein change the &#8220;lucid&#8221; to &#8220;maverick&#8221;.

run Ubuntu Update service, which detects new packages and install them

or do ...

sudo apt-get install libsane sane-utils[SIZE=4]

Finally[/SIZE]
the hardware is working, ..

[SIZE=4]But[/SIZE]
... I have still light vertical bars a bit left from the middle, their width is approx. 1 cm.
But this has to do with calibration I am sure. Windows drivers are different, because windows results are fine. When I have a look at the hardware / glass, where the scanning begins, there is an calibration bar beneath, white, under the glass. At exactly the position where the stripes appear in the software, there the white is discontinued for 1cm at the hardware. 

Please if there is anybody having the Canon Lide 100, can you have a look at your hardware and tell me, if the calibration stripe is also discontinued?

Picture:
[https://picasaweb.google.com/lh/photo/1xU2ddvOLIuKMTcfzf4Xkg?feat=directlink](https://picasaweb.google.com/lh/photo/1xU2ddvOLIuKMTcfzf4Xkg?feat=directlink)

:) If that does not help I sell this to an Windows User and buy an "LIDE 60" which should work better under Ubuntu ...
[IMG]https://picasaweb.google.com/lh/photo/1xU2ddvOLIuKMTcfzf4Xkg?feat=directlink[/IMG]

---

### Post by cy3a on 2011-11-15
> **rdesgroppes said:**
> Hi,
There is a simpler solution, just consisting in adding an [adhoc ppa repository]("https://launchpad.net/~info-g-com/+archive/gc-sane") to your apt sources:
```

sudo add-apt-repository ppa:info-g-com/gc-sane
sudo aptitude full-upgrade
sudo restart udev

```
(or reboot)
That way, there's no compilation, no manual edit, and the most important: your system remains under apt control.
Régis

how to add repository? after command 
sudo add-apt-repository ppa:info-g-com/gc-sane 
i get message:
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~info-g-com/+archive/gc-sane](https://launchpad.net/api/1.0/~info-g-com/+archive/gc-sane)

---

### Post by gencon on 2012-05-14
Thanks all.

FYI:

To get it working in Lucid I added this repository:

[https://launchpad.net/~robert-ancell/+archive/sane-backends?field.series_filter=lucid](https://launchpad.net/~robert-ancell/+archive/sane-backends?field.series_filter=lucid)

with:

sudo apt-add-repository ppa:robert-ancell/sane-backends
sudo apt-get update

sudo apt-get install sane libsane sane-utils xsane libsane-dev

[Not sure 'libsane-dev' is necessary, probably not.]

No need to change the config files, the ones from the PPA already have 'Canon CanoScan Lide 100' in them. 

Simple Scan does not work, but who cares xsane is brilliant. Start it from the Applications menu: Applications -> Graphics -> XSane

HTH.

---

### Post by drc73 on 2013-02-22
Update - I plugged my CanoScan 200 into my Kubuntu 12.10 laptop and went looking for drivers, found none at Canon.com.au then went to this forum.  

I was just about to give up and tried the pre installed 'Skanlite' and it found the scanner 1st pop.  In fact it works quicker than the canon driver on my windows box.

---

