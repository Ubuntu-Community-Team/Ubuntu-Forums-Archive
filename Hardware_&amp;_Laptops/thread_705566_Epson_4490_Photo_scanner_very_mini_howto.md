---
title: "Epson 4490 Photo scanner very mini howto"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by luca.mg on 2008-02-23
I prefer to buy stuff that works automagically, however I must have bought this scanner by mistake... 

to cut a long story short: sane supports the Epson Perfection 4490 Photo scanner via a so called external backend, perhaps non GPL code that cannot be included in sane, this is how to install it, tested on Gutsy 32bit; it may work for other scanners/distributions, please post here if You find other uses for this mini-mini howto. 

I'll assume You're familiar with editing system files and running administrative tasks: 

1 - install libsane-extras

2 - edit /etc/sane.d/dll.conf and uncomment epson2

3 - go to [http://www.sane-project.org/lists/sane-backends-external.html](http://www.sane-project.org/lists/sane-backends-external.html) 

4 - click the link "Perfection 4490 PHOTO"
You'll be redirected to [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) 

5 - fill in the form and download iscan-plugin-gt-x750-1.0.0-10c2.i386.rpm and 

6 - convert it to deb with alien

7 - install it 

do not download iscan-2.10.0-1.c2.i386.rpm as the resulting deb conflicts with libsane-extras, moreover, uninstalling libsane-extras and installing iscan does not work as iscan does not find the scanner: well, I did not even try to configure it as I'm already familiar with xsane and quite happy with it 

8 - add Your user to the scanner group if not there already 

9 - power cycle or unplug-plug back in the scanner: these last two steps are necessary. 

The thang works, with transparences and as a user too! 

All suggestions are welcome, and if anyone can find a way to make iscan work and find that is better than xsane please post the recipe. 

ciao luca

---

### Post by Michaelg14 on 2008-02-23
Thank you for that information.  As I use Virtualbox for other things I just installed the Windows software that came with the scanner and it works fine.  Granted, that may not be a solution that appeals to the die-hard Linux users but it has the advantage of working without jumping through hoops.

Sorry this is in the wrong thread.

---

### Post by dryder on 2008-03-06
> fill in the form and download iscan-plugin-gt-x750-1.0.0-[COLOR="Red"]10c2[/COLOR].i386.rpm 

> do not download iscan-2.10.0-[COLOR="Red"]1.c2[/COLOR].i386.rpm as the resulting deb conflicts with libsane-extras

I chose Debian ... Others on your link and ended up on the www avasys.jp/lx-bin2/linux_e/scan/DL2.do site.  I can only see:

Download for Perfection 4490 PHOTO (for gcc 3.4 or later) - iscan-plugin-gt-x750-1.0.0-[COLOR="Red"]1.c2[/COLOR].i386.rpm   	 163,386 bytes
 and
Download for Perfection 4490 PHOTO (for gcc 3.2/3.3) - iscan-plugin-gt-x750-1.0.0-[COLOR="Red"]1.i386[/COLOR].rpm   	 161,133 bytes

Should I not have chose Debian or can you tell me the link please, in text (the download page link gives a 'url not found' when posted as a url)?

Also, > edit /etc/sane.d/dll.conf and uncomment epson2only had epson - no epson2??

Many thanks,

David

---

### Post by luca.mg on 2008-03-06
dryder, I went to the download page and yes indeed: the rpm file has another name, perhaps an update?! Download the file for gcc 3.4 regardless of the revision number and alien it. Regarding the epson2, did You install libsane-extras? 

luca

---

### Post by dryder on 2008-03-06
Thanks -
Feisty BTW [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] ...

I installed iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm. I left the /etc/sane.d/dll.conf alone as it did not have epson2, just epson and, yes, libsane-extras 1.0.18.5 is installed.

So far so good - the 4490 now works with Xsane in Feisty ... well, ...

1. efax doesn't receive it (efax was chosen as the fax program in Setup) which is very important to me. Any help here, please?

2. Before doing any of this, sane did not recognise any scanner but Vuescan did. Vuescan only said to download the necessary software.

Now Vuescan doesn't see any scanner - is there a way I can use both? I really would like to evaluate Vuescan without destroying my Xsane setup.

Many thanks,
David

---

### Post by dryder on 2008-03-08
UPDATE:
Efax says the file us the wrong format yet the correct tiff3g format was chosen for efax.
Thoughts anyone??

---

### Post by luca.mg on 2008-03-09
dryder, sorry I do not pop into the forums every day, I'm glad to hear You have a working scanner now; as for the fax I apologize but I'm unable to help 

luca

---

### Post by Mocker on 2008-03-16
> 
6 - convert it to deb with alien


I hit a snag here... when I use Alien on the RPM package for the latest GCC version, I get the error: 

```

dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

```

No .deb package gets built.

Yup, I am running 64 bits. So, is there a workaround for this? Alien doesn't seem to have any "force" or "ignore error" flags that I can find. I've also tried building from source, but can't seem to overcome this error:

```

/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC

```

This happens even if I stick -fPIC into every flag variable in the Makefile.

Any hints on getting this to work on x64?

---

### Post by luca.mg on 2008-03-19
Mocker, sorry for the delay, I regret to tell You that this howto only works for 32 bit systems, I just found this out after opening the thread, that should have had a title stating 32 bit only; sorry about it 

luca

---

### Post by dryder on 2008-04-15
Does --force-architecture work?

Worked for me with a Canon LBP3000 printer 32-bit driver in Hardy 64 bit ...

Please let us know.

David

---

### Post by rocketship on 2008-05-07
Yes!  --force-architecture works for Hardy amd64!  I followed the instructions for installing the x86 rpms, but added --force-architecture when I installed them.

RS

---

### Post by rocketship on 2008-05-15
Let me amend that, actually.  It works with Vuescan, which was what I wanted.  

I followed the steps found on the Avasys website:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

I did install the Iscan software, contrary to what the first post in this thread suggests.  I had to edit the sane config file for it to be able to recognize the scanner.  If ```
scanimage -l
``` recognizes your scanner, you're on the right track.  I wrote a little startup script for Vuescan, which calls ```
scanimage -l
``` before starting Vuescan - this seemed to be necessary, or else the scanner wouldn't be found on restart.

I apologize if this is spotty.  I'll write up a new thread when I get back to my 64bit machine next week and can find the actual config files.

RS

---

### Post by dryder on 2008-05-15
Thanks rocketship - look forward to seeing it :-)

David

---

### Post by rocketship on 2008-05-23
dryder,
I posted the new how-to at:
[http://ubuntuforums.org/showthread.php?p=5025860#post5025860](http://ubuntuforums.org/showthread.php?p=5025860#post5025860)

A funny thing - I discovered (when my wife was trying to get the scanner working while I was out of town) that I have to run "iscan" before "vuescan", otherwise the scanner isn't recognized and Vuescan.

RS

---

### Post by oschreiber on 2008-07-11
> **luca.mg said:**
> 
2 - edit /etc/sane.d/dll.conf and uncomment epson2
6 - convert it to deb with alien
8 - add Your user to the scanner group if not there already 
The thang works, with transparences and as a user too! 
[...]
ciao luca
Hi Luca,
About step 2, shouldn't you have a line with epkowa ?
About step 6, should one use --scripts option?
About step 8, is it this command?:
gpasswd -a myusername scanner
How do you test things work after step 9?
After step 9, I get:
ninja2:/home/olivier/scanner# sane-find-scanner
[...]
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:005:010

but then,
ninja2:/home/olivier/scanner# scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
ninja2:/home/olivier/scanner# 

If I look at /var/lof/syslog
Jul 10 23:04:37 ninja2 kernel: ppdev0: registered pardevice
Jul 10 23:04:37 ninja2 kernel: ppdev0: unregistered pardevice
Jul 10 23:04:40 ninja2 kernel: ppdev0: registered pardevice
Jul 10 23:04:40 ninja2 scanimage: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jul 10 23:04:40 ninja2 kernel: ppdev0: unregistered pardevice
olivier@ninja2:~$ dpkg -l iscan-plugin-gt-x750
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  iscan-plugin-gt-x750     1.0.0-2                  Image Scan! plugin for the GT-X750 / Perfection 4490
olivier@ninja2:~$ 

What about the /etc/udev/rules.d/z60_libsane.rules
Shouldn't it have a line with this?:
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="664", GROUP="scanner"

Thanks!

---

### Post by oschreiber on 2008-07-11
I just read in the iscan pdf file from the avasys download site:
[...] /etc/sane.d/epkowa.conf configuration file. It should have an usb line.

That file was missing in my case. It is not in libsane or libsane-extras packages or iscan-plugin-gt-x750

After I created it, I got:
ninja2:/home/olivier/scanner# scanimage -L
device `epkowa:libusb:005:013' is a Epson Perfection 4490 flatbed scanner
But xsane does not find the scanner, still.
Thanks.

---

### Post by oschreiber on 2008-07-11
This was a groups problem.
I had issued:
gpasswd -a olivier scanner 
but the other windows still were not showing scanner when I typed groups
so xsane or quiteinsane would not find the scanner.
By doing su olivier from root, I get groups to show scanner and then xsane finds the epson.
Strange that the first invocation of xsane does not signal scanner group membership is missing or could be a factor.
Thanks.

---

