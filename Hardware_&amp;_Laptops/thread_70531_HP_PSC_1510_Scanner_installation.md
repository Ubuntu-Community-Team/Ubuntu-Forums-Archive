---
title: "HP PSC 1510 Scanner installation"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-09-30
hello!
I just bought my new printer, a psc 1510 from hp. it is supposed to work 'perfectly' according to linuxprinting.org. unfortunately, i dont know how to set up the scanner.
i did the following:
-install hplip
-set up the printer as psc 1600  -> printing works!
-added hpaio to /etc/sane.d/dll.conf but sane does not find my scanner.
now i dont know what to try next...
thanks for any help in advance!
EDIT: next problem: whenever i turn on the printer, it prints the calibration page. is there a way to turn that off? I am a little bit angry about myself. while linuxprinting.org says the printer works perfectly, it is not yet listed on the hplip homepage. since i am an linux-only user, this is kinda big problem...

EDIT 2:
```

$ sane-find-scanner:
found USB scanner (vendor=0x03f0 [HP], product=0x4c11 [PSC 1500 series]) at libusb:005:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```
```

$ scanimage -L:
[dll] add_backend: adding backend `hpaio'

[dll] load: searching backend `hpaio' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] init: backend `hpaio' is version 1.0.6
[dll] sane_get_devices: found 0 devices

[dll] sane_exit: calling backend `hpaio's exit function

```

---

### Post by izmaelis on 2005-09-30
I have fully functional PSC 1315 at home. Have you tried using XSane for scanning images?

---

### Post by phen on 2005-09-30
yeah, xsane does not find any devices :-(

---

### Post by matthew on 2005-09-30
I am guessing the 1510 is similar to my 1210. Here's how I got mine working.

[http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

The same thing seems to have worked for this person with a 1310:
[http://www.ubuntuforums.org/showthread.php?t=62743](http://www.ubuntuforums.org/showthread.php?t=62743)

---

### Post by phen on 2005-10-01
matthew, thanks for your help. i've found your thread before. i turned of my printer and i restarted all printing services. but did you install hpoj? it is not possible to install it together with hplip (they want to remove each other). do i have to force that?

after rereading the threads, i think what did the trick for you was to add hpaio to the sane.d/dll.conf? i allready did that. 

does 
>make sure you are using the printer listed under other.
>there are two listed 
mean the third choice in step 1 of the printer installation? i've chosen that, too.

hmmm
thank for your help!

---

### Post by matthew on 2005-10-01
Sorry for any confusion, it's been several months since I did this and my memory has been overwritten by other stuff. I'm going to take another look and see if I can figure out what I did.

I just looked to confirm. I have hplip installed.

Here's my /etc/sane.d/dll.conf just for comparison with yours. The only change I remember making was to add the last line.

```
# /etc/sane.d/dll.conf -  Configuration file for the SANE dynamic backend loader
#
# See the end of this file for information on some specific backends.

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
coolscan
coolscan2
#dc25
#dc210
#dc240
dmc
epson
fujitsu
#gphoto2
gt68xx
hp
hpsj5s
hp5400
ibm
leo
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
nec
niash
pie
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
snapscan
sp15c
#st400
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

# The following backends are not part of the SANE distribution
# but are provided by the libsane-extras Debian package
#hp4200
#hp_rts88xx

# The HP OfficeJet backend is not part of the SANE distribution
# but is provided by the hpoj Debian package
hpoj
hpaio
``` 
Here's a step by step guide to what I did.
> 
1. Using Synaptic install "hplip" and "xsane"
2. a. at a command line type: sudo gedit etc/sane.d/dll.conf
b. find "hpoj" in the file and insert a new line after it containing "hpaio" *make sure you are using the printer listed under "other" in the file.
c. save and exit
3. Turn the printer off and turn it back on
4. a. System-->Administration-->Printing
b. click new printer
c. your printer should be detected, just follow the menu items 
I don't actually see the word "other" in my /etc/sane.d/dll.conf, but I believe that was replaced by the HP OfficeJet block at the end of the file.

That's all I can think of. If it still isn't working post again and maybe someone else will have an idea.

---

### Post by phen on 2005-10-17
thanks for all your help!

i did two things: waiting for breezy, (afterwards my scanner was detected, also my printer is now psc 1510, not 1600 anymore). The scanner was still not working, therefore i had to feed it with paper. I turned my printer on, and the warning "out of paper" blocked the whole system, not only the printer.

pressing "abort" enabled the scanner!

---

### Post by kanuso on 2005-10-17
[QUOTE=phen]EDIT: next problem: whenever i turn on the printer, it prints the calibration page.[/QUOTE]

Okaaay. First of all, read the "Start Here" 10 page pictographic pamphlet that come with the printer. It prints a calibration page because it wants you to feed it to the scanner. Just Do It.

---

### Post by kanuso on 2005-10-17
I've installed my new HP PSC 1510 just a moment ago, and I've found no problems in the process. 

I've just opened the printer add dialog in control center's administrator mode, and added a printer in the USB0 port with the HPLIP HP PSC 1510 driver. Selected A4 size, and printed a test page.

Then the scanner turn. Launched Kooka, accepted the hpaio scanner, scanned a preview, and then a full 1200 final scan.

So I found no problem at all. May anyone want the output of any command, just reply to this comment.

---

### Post by 11hjpphty76lkjj on 2005-10-17
Installing in Breezy; you should not have to modify ANY files with HPLIP.  No xsane files no conf files, none.

Install the newest version of HPLIP at [http://hpinkjet.sf.net](http://hpinkjet.sf.net) (version 0.9.6) as per the instructions, then let me know if you are still having issues.  The process should be this:

Install/compile software
Setup your printer using your printer manager software in kde or gnome, whatever.
Open HP-Toolbox.  you can print and scan direction from this interface, or you can type xsane and (in theory) it will find your printer.

If you are still having problems let me know what the exact problem is and I can help you troubleshoot it.  I install/compile/reinstall/test the software EVERY day. (I work in a software test environment.) and I can help you troubleshoot any issues you are having.  I have tested Hoary a very large number of times and the process is not the complicated.  If anyone is having problems let me know and I can walk you through the process.  The first step is to go to the [http://hpinkjet.sf.net](http://hpinkjet.sf.net) website and make sure your printer is supported.  The 1510 should work with no problems.  So let me know.  But install the newest version!

Aaron

---

### Post by phen on 2005-10-18
thank you all, the upgrade from hoary to breezy fixed my problems! before hplip did not recognize my psc 1510, only 1600. now it does, and everything is fine...

cheers

---

