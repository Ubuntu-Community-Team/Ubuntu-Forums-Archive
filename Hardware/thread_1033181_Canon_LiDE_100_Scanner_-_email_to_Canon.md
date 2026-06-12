---
title: "Canon LiDE 100 Scanner - email to Canon"
date: 2009-01-07
forum: Hardware
---

### Post by bazzer on 2009-01-07
I have purchased a Canon CanoScan LiDE 100 scanner and cannot seem to get it to work with Ubuntu Linux. I require Consumer Product support.

I tried to use your website, but unfortunately, there is no mention of the LiDE 100, only older models. Hence I could not complete the Websubmit page at [http://www.canon.co.uk/Support/Consumer_Products/index.aspx](http://www.canon.co.uk/Support/Consumer_Products/index.aspx). Specifically, the text entry box labelled 'Product:' would not accept ANY input. Maybe it's a browser issue? I use Firefox, and as previously mentioned I also use Ubuntu. So I tried a different browser, Epiphany. In Epiphany, your website rendered badly with all the text boxes extending over the right of the page. And again, I could not populate the Websubmit form. Incidentally, I'm just guessing that's the way to contact you because I've never heard of the term 'Websubmit' before and again, there are no explanations on your website.

Anyway, I decided to try a different tact. I called your telephone support on 00 800 22666 767 (I also tried 0844 369 0100 with exactly the same results).

I selected "Option 4" - Speak to an agent with regard to the use of a canon product. Your phone system replied with "We are sorry, but the system could not identify your choice"

Again I selected the number 4 on the telephone keypad. Again, your phone system replied with "We are sorry, but the system could not identify your choice", then "You will be connected to the next available agent"

Then, to my utter disbelief, your system told me that your offices are closed and that "Offices are open from nine to seventeen thirty." It was only 16:48.

So I tried again, and again, and again. Same response all times.

So, I would like to tell you how I feel about my 'Canon customer experience' at the moment. Frankly, it is not good at all. In summary, I've got a product that doesn't work, from a company that cannot be contacted by their own website, or their own telephone support.

You will of course see that I've sent this email to a whole load of email addresses in the hope that one may eventually get through this very effective wall and a person may be able to respond.

"We are committed to providing you, our customers with the best possible support... etc etc." Let's see it then, please.

---

### Post by McLogic on 2009-01-22
Canon has show little to no support for its products on Linux. The few scanners that work are community-developed items. That said, my Cannon scanner works well with SANE.

Check it out:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by bazzer on 2009-01-23
I googled for addresses to send to and chose half a dozen randoms..... Eventually, from Canon:> We do apologise that you have had limited success in trying to contact us for additional support.  You were correct in calling the appropriate support number for assistance but unfortunately, we were experiencing problem due to some system revisions.

In relation to your query, Canon does not support or provide the necessary drivers for the use of the LiDE 100F scanner on the Linux platform.  We do apologise for this but please continue to check our download site for further information or the latest drivers should the Linux platform eventually be supported.

[http://software.canon-europe.com/products/0010650.asp](http://software.canon-europe.com/products/0010650.asp)

We apologise again for the inconvenience caused in this matter, both as being unable to assist you in your query and that you experienced difficulties in trying to raise it in the first instance.


If there is anything further that we can do for you, please do not hesitate to contact us on the number that you have already tried on, which should now be working correctly, or via the web submit service on our site.

What a crock of cr@p.

---

### Post by russu52 on 2009-01-29
Aptly said!

at work they bought a new canon lide 100, which i plugged into my ubuntu laptop... nothing doing :( 
i asked our systems adminstrator about the problem...
his reply: "It works on windows!"

yawn...

talk about standing apart from the crowd :(

---

### Post by tjandracom on 2009-04-07
i have this lide 100 scanner too. sadly enough i didn't read the hardware compatibility list in the first place. so it kinda useless since i rarely using windows anymore...
:cry::cry::cry:

still hoping that someday sane will support this scanner...

---

### Post by ipernar on 2010-02-17
I bought this scaner before I switched to Linux Mint (Ubunutu derivate), and was shocked to realise that my scaner is unusable.

Therefor I installed virtualbox via which I installed windows drivers and use their scaner, however Ill never buy their equipment again... HP is much much better!

---

### Post by PeterOakland on 2010-03-05
I would dearly love to know how you got the LIDE100 to work in Vbox.
I have installed the software in Virtual XP, yet when I click on the MP Navigator EX 2.0 icon, I get a message telling me:
The scanner driver supporting this software is not installed.
Install it and then retry.

I have done that.  Still nothing.
How did you get past that roadblock, assuming that you in fact encountered it?

Thanks for any help/advice.

---

### Post by ipernar on 2010-03-11
I made a youtube video where I explained all motivated by you're question (and mentioned you!)

[http://www.youtube.com/watch?v=Z3teSzoXpNA](http://www.youtube.com/watch?v=Z3teSzoXpNA)

Good luck!

---

### Post by PeterOakland on 2010-05-14
Thanks very much for the video.
Unfortunately, following those steps didn't work.
I get a message which tells me that the driver supported by the software is not installed.
Yet I have installed it - the x86 driver.  Was that the wrong one?
What next?
Suggestions?

---

### Post by gigahz on 2010-05-18
Hi all, remember that ALL USB FUNCTIONALITY in VirtualBox needs the non-OSE edition (the paid edition). Don't be alarmed, you only pay if you want to make money with it. Personal and evaluation use is free.

Slightly off-topic: I made an auto-document-feeder with my Canoscan lide100, since if I broke it, well, I'd have to buy a not-Canon scanner that would support linux.

If anyone are interested:

[http://arno.homelinux.org/lide100-ADF/](http://arno.homelinux.org/lide100-ADF/)

best
Arno

---

### Post by MyR on 2010-05-23
Arno:

That is **awesome**! Hats off to you sir.

---

### Post by gigahz on 2010-05-25
> **MyR said:**
> awesome!
Well it was a lot of fun. I think it would be *awesome* if someone wrote "drivers" for the Lide100+SANE.

On second thought, that would kind of encourage people to buy these scanners wouldn't it.

Does anyone know of sites selling ONLY open-source compatible gear (incl scanners)?

---

### Post by MyR on 2010-05-25
> **gigahz said:**
> Does anyone know of sites selling ONLY open-source compatible gear (incl scanners)?

I'm glad you ask!
[http://www.linuxaisle.com/](http://www.linuxaisle.com/)

We still have a small inventory because we launched very recently.

---

### Post by desertdog on 2010-06-14
There are 2 ways to update SANE that will support your scanner:

EASY WAY-add ppa to your software sources
This is quick and easy, but might not always be completely up to date. If the ppa gets old and there are new features in sane that you want, you could try asking the ppa author nicely to update it. This should work in Ubuntu 9.10 and higher.

$sudo add-apt-repository ppa:robert-ancell/sane-backends
$sudo apt-get update


ADVANCE WAY-Build from source


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

TROUBLESHOOTING
$lsusb
$sane-find-scanner
$scanimage -L
$sudo scanimage -L
$scanimage -T
$scanimage -V  (should return scanimage (sane-backends) 1.0.22git; backend version 1.1.0)
unplug and replug scanner and retry scanimage
reboot computer (or $/etc/init.d/saned restart)

$cat /etc/sane.d/genesys.conf and make sure your scanner is listed.
If not listed then $sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

 

---

### Post by gigahz on 2010-06-15
> **desertdog said:**
> SCAN AWAY!

Hi thanks for your tips. I followed your instructions to the letter (even rebooted - been a while ;)

now, lsusb: 
```
Bus 001 Device 007: ID 04a9:1904 Canon, Inc. 
```

dmesg / /var/log/messages:
```
[ 1461.828095] usb 1-5: new high speed USB device using ehci_hcd and address 7
[ 1461.961653] usb 1-5: configuration #1 chosen from 1 choice
```

scanimage -L:
```
arnop@arno-work:~$ scanimage -L

No scanners were identified. …[snip]…
```

BUT:
```
arnop@arno-work:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0483 [STMicroelectronics], product=0x2016 [Biometric Coprocessor]) at libusb:005:003
found USB scanner (vendor=0x04a9 [Canon], product=0x1904 [CanoScan], chip=GL847) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
```

now, this means the backend wasn't discovered somehow?

---

### Post by desertdog on 2010-06-15
Let's find out if this is a permissions issue, try:

$sudo scanimage -L

and if that works, try to scan something

$sudo scanimage >image.pnm


Also, check to see if you have libsane-dev installed.

Also. check /etc/sane.d/genesys.conf to make sure your scanner is listed in this file.

($cat /etc/sane.d/genesys.conf)

---

### Post by gigahz on 2010-06-16
> **desertdog said:**
> Let's find out if this is a permissions issue, try:

$sudo scanimage -L

and if that works,
well, it's the same output. No scanner detected.
> **desertdog said:**
> 
Also, check to see if you have libsane-dev installed.
That I hadn't. Downloading it now. But being close to midnight… thanks I'll go on tomorrow :)

---

### Post by desertdog on 2010-06-16
Try installing libsane-dev and repeating step 4.

---

### Post by dafir06 on 2010-06-16
Thanks a lot...
I ve been waiting for this usefull solution for my canon lide100
now i can use my scanner :p
thanks again.......

---

### Post by gigahz on 2010-06-17
> **desertdog said:**
> 
Also. check /etc/sane.d/genesys.conf to make sure your scanner is listed in this file.

($cat /etc/sane.d/genesys.conf)


It wasn't, so I added

```
# Canon LiDE 100
usb 0x04a9 0x1904
```

didn't need reeboting, replugging scanner nor restarting saned.


You have no idea how much this ROCKS!:guitar:
It even scans in 1200dpi, which was not possible with virtualbox+windowsxp HAHA

THANKS AN AWFUL LOT to everyone who took part in this. ):P I can now script scans! Without autoit...

NO THANKS to canon for slowing down technology by not distributing their source code nor protocol specs.

(I don't normally use smileys but this deserved the extra effort :)

Had to update my ADF-scanner-page now, too. Much easier scripting :D

---

### Post by kajsa on 2010-06-18
> **desertdog said:**
> Let's find out if this is a permissions issue, try:

$sudo scanimage -L

and if that works, try to scan something

$sudo scanimage >image.pnm


Also, check to see if you have libsane-dev installed.

Also. check /etc/sane.d/genesys.conf to make sure your scanner is listed in this file.

($cat /etc/sane.d/genesys.conf)

After following your directions, I'm able to scan as root but not as myself. Any suggestions?

---

### Post by desertdog on 2010-06-18
> **kajsa said:**
> After following your directions, I'm able to scan as root but not as myself. Any suggestions?


> Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

5) You need to edit a file, but you need to be root to edit it, so:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

Or, if you have the Canon Lide 200, then add the following to /lib/udev/rules.d/40-libsane.rules

# Canon CanoScan Lide 200
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1905", ENV{libsane_matched}="yes"

---

### Post by kajsa on 2010-06-18
I already added the two lines you mentioned: 

kajsa@vox:~$ grep 'ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"' /lib/udev/rules.d/40-libsane.rules
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

---

### Post by gigahz on 2010-06-18
> **kajsa said:**
> <cannot scan as non-root>

Could you post the output of 
```
lsusb
ls -la /dev/bus/usb/*
groups
```

---

### Post by desertdog on 2010-06-19
> **kajsa said:**
> After following your directions, I'm able to scan as root but not as myself. Any suggestions?

Try checking users and groups.
Click System tab, then Administration, then Users and Groups. Click Manage Groups button. Click on the scanner group properties and make sure there is a check in the box for your user. Do the same thing for the saned group.

Another solution that I've seen suggested is:
$sudo chmod a+w /dev/bus/usb/*
But I think there are some security issues if this is a shared computer.

---

### Post by InvisibleEye on 2010-06-23
I just wanted to thank Shutter4U for his precious step-by-step post on how to compile the source for Lide 100! It finally works...! - I mean, it still doesn't work with the default simple-scan software, but it does with xsane. Thanks again! ):P

---

### Post by everweb on 2010-07-19
> **InvisibleEye said:**
> I just wanted to thank Shutter4U for his precious step-by-step post on how to compile the source for Lide 100! It finally works...! - I mean, it still doesn't work with the default simple-scan software, but it does with xsane. Thanks again! ):P

I also followed the compile steps and had the same result (working with xsane, not with simple-scan). The patch to genesys.conf fixed it. The scanner now works in both programs.

The fix:
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

---

### Post by thomas.w on 2010-07-30
> **everweb said:**
> I also followed the compile steps and had the same result (working with xsane, not with simple-scan). The patch to genesys.conf fixed it. The scanner now works in both programs.

The fix:
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

I ran this in terminal to no avail. After typing in my PW it went directly to back to the original home command line and produced no output. Is this normal? I checked the etc file in home and say the genesys.conf file located there. After reboot, Simple Scan still doesn't work. Xsane works, but is extremely blurry by default. Any advice on getting simple scan to work now?

cheers

---

### Post by thomas.w on 2010-07-31
> **thomas.w said:**
> I ran this in terminal to no avail. After typing in my PW it went directly to back to the original home command line and produced no output. Is this normal? I checked the etc file in home and say the genesys.conf file located there. After reboot, Simple Scan still doesn't work. Xsane works, but is extremely blurry by default. Any advice on getting simple scan to work now?

cheers

Sorry, I forgot to mention that I ran all the steps mentioned above which seemed to work fine and that when I click scan in simple scan, the lide scanner is recognized by the program and starts to run  unfortunately, the scan itself never materializes in the program. Any ideas?

Thanks,

Thomas

---

### Post by pir on 2010-08-16
Instructions worked for me. I did have to install from source (compile).

Thanks!

---

### Post by ruhataran on 2010-09-01
Hi, 

I try to follow the steps to install but it failed at step 4

$~/sane-backends$ make
make: *** No targets specified and no makefile found.  Stop.

did I do something wrong.., I am quite newbie in using script for installation...

---

### Post by ruhataran on 2010-09-02
It works, 

I forgot to follow step 4, and after I copied genesy.conf and genesy.conf.in from ~/sane-backends/backends to /etc/sane.d/ 

it works even with simple-sccan


> **ruhataran said:**
> Hi, 

I try to follow the steps to install but it failed at step 4

$~/sane-backends$ make
make: *** No targets specified and no makefile found.  Stop.

did I do something wrong.., I am quite newbie in using script for installation...

---

### Post by mahvin on 2010-09-17
> **thomas.w said:**
> I ran this in terminal to no avail. After typing in my PW it went directly to back to the original home command line and produced no output. Is this normal? I checked the etc file in home and say the genesys.conf file located there. After reboot, Simple Scan still doesn't work. Xsane works, but is extremely blurry by default. Any advice on getting simple scan to work now?

cheers

The cp command won't show any action being taken since its just copying a file from one directory to another.

Many thanks to Desertdog for the advanced compile instructions, my scanner is now working great! :) My situation was the same as Everweb's:

The fix:
$sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf

Now it works like a charm! Thanks again!

---

### Post by Blackdropbear on 2010-09-30
Would this work for a 700F LiDE scanner or is it a totally different beast ?

---

### Post by desertdog on 2010-10-04
> **Blackdropbear said:**
> Would this work for a 700F LiDE scanner or is it a totally different beast ?

The 700F is not supported. It is reported to have a GL847 chip, like the canoscan 100 and 200. If you already have one and are adventurous, you could try to compile sane from source and trick sane into using the settings for the 100 or 200 to see if it will work.

For instructions on how to do this, see:[https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

---

### Post by RobertEr on 2010-10-30
I have tried one option on Ubuntu to get my Canoscan lide 100 working but have no success. But then it only what I consider limps  along on Windows XP  so what  do I expect. I think I should be able to just hit the scan button on the front panel  and it should scan. But then it doesn't even have a driver for Ubuntu. I don't understand why Canon is concerned about anybody stealing their software. It doesn't work anyways. I guess I should have  looked and seen which scanner was supported before I bought one

---

### Post by gigahz on 2010-10-30
> **RobertEr said:**
> I have tried one option on Ubuntu to get my Canoscan lide 100 working but have no success. But then it only what I consider limps  along on Windows XP  so what  do I expect. 
Well if it's a hardware error even linux won't save you much. It works fine for me, though after having scanned 1700 pages in a row, the motor or gearbox gave up. Ugly grrrzzz noises and no movement... Maybe something similar is happening to you?

> **RobertEr said:**
>  I think I should be able to just hit the scan button on the front panel  and it should scan.

You need to install scanbuttond to do that: 
```
sudo apt-get install scanbuttond
```

> **RobertEr said:**
> But then it doesn't even have a driver for Ubuntu. I don't understand why Canon is concerned about anybody stealing their software. It doesn't work anyways. I guess I should have  looked and seen which scanner was supported before I bought one
Well, Canon does not have a scanner for ubuntu. But the open source community DO. 

This is what I did to make the 100lide work in ubuntu: just open a terminal and copy&paste the following lines into your terminal
```
# Get the sane sources
wget ftp://ftp.sane-project.org/pub/sane/sane-backends-1.0.21/sane-backends-1.0.21.tar.gz
# Unpack the sane sources
tar xzvf sane-backends-1.0.21.tar.gz
# Build sane backends
cd sane-backends-1.0.21
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
sudo gedit /lib/udev/rules.d/40-libsane.rules

```

and see if the following 2 lines are therein, unless, add them:

```

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

```

You might have to replug your scanner after doing this. 

try "sane-find-scanner" and "scanimage -L" in a terminal.

For some reason scanimage stopped working for me (the scanner scans away, but I get 0 bytes output files), but xsane and scanadf works just fine. "scanadf -o file.pnm -e 1" will do the same as "scanimage > file.pnm".

As a side note, my very old visioneer onetouch 7600 scanner does work with ubuntu while it's impossible to make it work in windows xp and later (vista, 7, 8).

We should create a site for abandonHARDware... that even if abandoned by whendoze still works just fine with linux :guitar:

Thanks again to the nice guys further up the thread that made the driver work for lide100 too (allan noah maybe? Can't see lide100 in the changelog...)

---

### Post by gigahz on 2010-10-30
Thinking back a bit, you can get even newer sane sources with git. These were the sources I used, but sane-backends-1.0.21 might work as well. I don't know.

To get the newest newest sources with git:

[COLOR="Red"]```
# Get the sane sources
git clone git://git.debian.org/sane/sane-backends.git sane-backends
# Build sane backends
cd sane-backends
```[/COLOR]

and then follow the howto in the last post:
> **gigahz said:**
> 
```

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install

...and so on, follow the above post

```




---

### Post by giusedia on 2011-01-23
I did a bit more of research and it turns out that the genesys backend version in sane 1.0.21 (presently included in ubuntu 10.10 and also in natty) it’s too old. Complete support for Canonscan 100 LIDE was added in Genesys 1.0.62 (see here [http://www.sane-project.org/lists/sane-mfgs-cvs.html](http://www.sane-project.org/lists/sane-mfgs-cvs.html)). So instead of compiling it on my lap, I just searched a newer package for Ubuntu.
It turns out that Alf Gaida  ([https://launchpad.net/~info-g-com]("https://launchpad.net/%7Einfo-g-com")) has it in his PPA (untrusted, **ppa:info-g-com/gc-sane)**. I installed them and the scanner is now working flawlessly.
Alf provides scanimage (sane-backends) 1.0.22git; backend version 1.0.22 
$ SANE_DEBUG_GENESYS=255 scanimage -L
[sanei_debug] Setting debug level of genesys to 255.
[genesys] SANE Genesys backend version 1.0 build 41 from sane-backends 1.0.22git

while Ubuntu stock version provides:
$ SANE_DEBUG_GENESYS=255 scanimage -L
[sanei_debug] Setting debug level of genesys to 255.
[genesys] SANE Genesys backend version 1.0 build 13 from sane-backends 1.0.21
If you don't mind installing from an untrusted PPA give it a try before compiling from source.:P

---

### Post by kcackler on 2011-01-27
Can you elaborate on this?  I added the ppa to my system and ran an apt-get upgrade but I am still unable to utilize my LIDE 100.  scanimage -L (and sudo scanimage -L) both report that no scanners were found, but sane-find-scanner sees my scanner.  

Even after I updated, I am still seeing libsane 1.0.21 and not 1.0.22.  I'm at my wit's end trying to get this scanner to work.  

Any tips are appreciated.

---

### Post by branko.savic on 2011-03-19
I followed all the steps to get my canoscan lide 100 working, and now I can finally use it in ubuntu, thank you very much!

I just have one more problem that I hope someone is able to help me solve!

Sometimes the scanner just does not want to work, it starts and it makes some noices and then I get an error! If I then unplugg and replugg it it will work! (Sometimes I have to unplugg it several times before it works!)

If I switch between scan programs, it will also stop working, and I have to unplugg it several times to get it working!

Hope that anyone can help me with this!

I am really new to linux, but I really want to get this going!

Thanks

---

### Post by branko.savic on 2011-03-19
Anyone?

I really need help with this! I know it&#347; not the scanner becouse it works perfectly in windows!

Thanks!

---

