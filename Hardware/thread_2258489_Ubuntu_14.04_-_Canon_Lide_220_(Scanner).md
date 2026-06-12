---
title: "Ubuntu 14.04 - Canon Lide 220 (Scanner)"
date: 2014-12-28
forum: Hardware
---

### Post by Riftyful on 2014-12-28
Hello! I have problem with scanner, Canon Lide 220.

I have connected the scanner and it was detected by running "sudo sane-find-scanner". The program reported that the scanner is probably detected, but it seemed that it was recognized. "scanimage -L" nor "xsane" or "sudo xsane" found any scanners, though. Any ideas if it's possible to make the scanner work? Canon provides software for Windows and OS X. If it's impossible to make the scanner work in Ubuntu, would it be possible to do so through Wine, perhaps?

Thank you for help.

---

### Post by pdc on 2014-12-28
from here [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) your device is completely supported by SANE and so xsane the front-end should be fine

_____________

if you type ```
lsusb
``` in a terminal, do you get something like ID 04a9:1905 Canon, Inc.

_____________

are you using a usb hub .............. is it a usb 3.0 port ................ ?

________________

if you can see it on "sudo" .......that suggests a permissions issue ........................................ 

________________

here is the full page on scanner issues [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

_________

however if we do some probability gambling, and add your username to the scanner group 

if you go from Administration to Users and Groups; and you will need your sudo password; if you ensure the saned and scanner groups are added to those groups you are allowed to access ........ does that help?

---

### Post by eezacque on 2014-12-29
I had a similar issue with a CanoScan Lide 50, and solved it by disabling xHCI in BIOS ([http://ubuntuforums.org/showthread.php?t=2253359](http://ubuntuforums.org/showthread.php?t=2253359))

---

### Post by mail-gabe on 2015-03-26
The current sane version of Ubuntu 14.04 doesn't support the CanoScan LiDE 220 yet. I've got the scanner running only with the snapshot build of the SANE backend. You can use this ppa for installation: [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

---

### Post by edward28 on 2015-04-01
I would like to add to "mail-gabe" (previous message): The scanner is also not yet supported by Ubuntu 14.10.

As indicated by "mail-gabe", simply type (copy) the following to a terminal:

> [FONT=DejaVu Sans]sudo add-apt-repository ppa:rolfbensch/sane-git[/FONT]

Then update your system. You should now be using the development version of libsane.

The scanner should now work by simply starting xsane (or similar).

See also:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide)

(= as of 1 April 2015, the Canon LIDE 220 is under "Backends included in the development repository" )

---

### Post by jweber53 on 2015-05-05
The scanner is also not yet supported by Ubuntu 15.04. Adding the above suggested PPA gets it recognized. I haven't tested it much yet.

---

### Post by jweber53 on 2015-05-18
I'm using Ubuntu 15.04, but suspect the fix may be the same.

I added the repo as mentioned above:

 ```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

And update the system.

The scanner is now recognized, but produces many errors and sometimes the scan element hits the end and it must be unplugged to reset it...but sometimes it works OK. This happens from any of the GUI frontends and also scanimage from the command line.

I put the following lines in my .bash_aliases:
```
export SANE_DEBUG_GENESYS=255
export SANE_DEBUG_GENESYS_LOW=255
export SANE_DEBUG_GENESYS_GL124=255
```

Logged out and back in and it seems to be working very well. I found some discussion on the sane development discussion list about a possible race condition and setting these DEBUG variables seemed to fix it.

---

### Post by houstontyoung on 2015-10-10
> **jweber53 said:**
> 

I put the following lines in my .bash_aliases:
```
export SANE_DEBUG_GENESYS=255
export SANE_DEBUG_GENESYS_LOW=255
export SANE_DEBUG_GENESYS_GL124=255
```

Logged out and back in and it seems to be working very well. I found some discussion on the sane development discussion list about a possible race condition and setting these DEBUG variables seemed to fix it.

This fixed grayscale scanning for me on Ubuntu Studio 14.04.  Thanks!

---

### Post by littlej on 2015-10-26
Hi, using Lubuntu 12.04 i had to add this :

> 

# Canon LiDE 220
usb 0x04a9 0x190f




into /etc/sane.d/genesys.conf for my scaner to work with simple-scan or xsane.

Thanks

---

### Post by Alex 2 on 2016-03-03
With my Ubuntu GNOME 15.10 (kernel 4.2.0-30-generic) the scanner (ID 04a9:190f) worked out of the box with Simple Scan!

*EDIT: the hardware buttons on the device have (of course) no function in Simple Scan.*

---

### Post by swarup on 2016-04-15
I use Ubuntu 14.04 on my laptop, and having read [this blog post]("http://gsusmonzon.blogspot.com/2015/06/canon-lide-220-in-ubuntu-1404.html?showComment=1460746047070#c6059937944149518459") about how to use the Canon lide 220 scanner with 14.04, I purchased one. The blog post pretty well incorporates the suggestions on this thread as to what needs to be done, and I've taken those steps. Here below I'm pasting the text of the instructions, which seem to me quite good:

> connect the scanner

ensure it is recognized

    lsusb

in the output, search for the Canon device

...
Bus 003 Device 003: ID 04a9:190f Canon, Inc.
...

ensure your user has access to the bus (otherwise  you'll have to launch everytime  xsane as root)

    sudo chmod u+w /dev/bus/usb//

in my case

 sudo chmod u+w /dev/bus/usb/003/003

Then, add this ppa to install latest version of xsane

sudo add-apt-repository ppa:rolfbensch/sane-git

and install xsane

    sudo apt-get update && sudo apt-get install gocr libsane-extras xsane-common xsane

if you have problems, install a couple of additional packets with

    sudo apt-get update && sudo apt-get install gocr libusb-dev libsane-dev libsane-extras xsane-common xsane

now you can run

  xsane

 and the scanner is working!


So I've carefully followed the instructions above. But when at the end I run xsane, I get the reply "no devices available". I've done the chmod to ensure my user has access to the bus. And I've also tried running xsane as root, but still get the same message that no devices are available. 

I've also added

```
# Canon LiDE 220
usb 0x04a9 0x190f
```

into /etc/sane.d/genesys.conf

And here are the results of "sane-find-scanner"--

```
~$ sudo sane-find-scanner
[sudo] password for xxx: 

found USB scanner (vendor=0x04a9 [Canon], product=0x190f [CanoScan]) at libusb:001:010
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE.
```


So everything looks good, but when I run xsane or simple scan, I am still getting "no devices detected".

And "scanimage -L" gives the following result:

```
~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

What should I do now?

---

### Post by swarup on 2016-04-15
I've gotten a solution of sorts: after having taken all the steps mentioned in the previous post, I have done the following: 

```
$ sudo apt-get -y dist-upgrade
```

After that, the scanner is recognized by Xsane. But only when I start Xsane as root. So I can open Xsane and successfully make scans, when I start Xsane in the following fashion:

```
$ sudo xsane
```

Otherwise even after doing chmod command as described in the last post to ensure my user has access to the bus, xsane will not recognize the scanner device when xsane is started as a general user.

And there is another problem: when xsane is opened as root, then the scans which are made and saved, can only be viewed as root user. When I click on any image scanned in this fashion, the image is not viewable as a general user.

If anyone has some insight as to how to get xsane to recognize the scanner when opened as a regular user, please let me know-- that will make using the scanner much more convenient.

---

### Post by mus1cfreak on 2017-03-14
Does this scanner works in 16.04?

---

### Post by pdc on 2017-03-14
Support by open source software for scanning in linux comes from SANE: Scanning Access Now Easy;

they maintain a page that lists those devices that are supported: [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

there are two groupings: those supported by **Current Stable Sane Version** [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) and a separate grouping: **SANE Development (git) Version** [http://www.sane-project.org/lists/sane-mfgs-cvs.html](http://www.sane-project.org/lists/sane-mfgs-cvs.html)

 ............in the CURRENT STABLE version, the Lide 220 shows [COLOR="#008000"]COMPLETE[/COLOR] support ....... (please see thumbnail) .....  ....... so one would assume ............

________________

it is often worth starting a new thread: the older "cruft" behind your latest post describes how to add the ppa for the Sane Development (git) version ............and it is NOT needed for the 220: adding the ppa is valuable .... when you need it ...........

---

### Post by mus1cfreak on 2017-03-17
Thanks.
I have ordered the device today.

---

### Post by mus1cfreak on 2017-03-18
Yes,

Scanner works.
Thanks

---

### Post by pdc on 2017-03-18
great; glad it went well; enjoy

---

