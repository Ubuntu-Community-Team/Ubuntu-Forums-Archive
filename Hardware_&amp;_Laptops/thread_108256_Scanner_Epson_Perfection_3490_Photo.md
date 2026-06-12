---
title: "Scanner Epson Perfection 3490 Photo"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by efreddi on 2005-12-25
Hi All,

this evening I have been able to set-up xsane to manage my scanner Epson Perfection 3490 Photo.
Sorry if I'm not very precise, but I'm a novice of Linux

Some detail:

the scanner has hinted by *sane-find-scanner*, see below the output:
[I]
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.[/I]

So the scanner has been found, but this is not enough.
Then looking in internet I found that my scanner is supported by snapscan

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

Then I followed the instructions and:
- in the file */etc/sane.d/snapscan.conf* I added the lines:

[I]# Epson Perfection 3490
usb 0x04b8 0x0122
[/I]

- I changed the permissions for the files in /proc/bus/usb/001/ to enable read/writing for *group* and *other*



That's all, now xsane detect the scanner and it works fine.
I hope that this will help other people.
Best regards


Elia Freddi

PS: my pc is a Dell Latitude C600

---

### Post by daller on 2005-12-26
Thank you for this HOWTO!

Next time please add "HOWTO:" to the subject!

---

### Post by palsyboy on 2006-01-16
Thanks for the How-To.

I can't get this to work for my 3490.  I'm trying to follow the Snapscan instructions:
> 1. # detect your scanner device
machine# tools/find-scanner
 find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
 /dev/XXXXX
But here's what happens:
```

root@giedi-prime:~# tools/find-scanner
bash: tools/find-scanner: No such file or directory

```
What am I doing wrong?

---

### Post by palsyboy on 2006-01-18
Okay, so I got further.  First off, I was so stupid as to not run this as root, which explains part of the problem.

So I did the following with some slightly better results, but still no working scanner:

```

palsyboy@giedi-prime:~$ sudo sane-find-scanner
Password:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:021
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

```
palsyboy@giedi-prime:~$ sudo nano -w /etc/sane.d/snapscan.conf
```
snapscon.conf now looks like this:
```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /path/to/your/firmware/file.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

#-------------------------- SCSI scanners ----------------------------------
# These SCSI devices will be probed automatically
scsi AGFA * Scanner
scsi COLOR * Scanner
scsi Color * Scanner
scsi ACERPERI * Scanner

#--------------------------- USB scanners -----------------------------------
# These USB devices will be probed automatically
# (This will currently work only on Linux)

# Benq/Acer/Vuego 310U
usb 0x04a5 0x1a20
usb 0x04a5 0x1a26

# Benq/Acer/Vuego 320U
usb 0x04a5 0x2022

# Benq/Acer/Vuego 620U / 620UT
usb 0x04a5 0x1a2a
usb 0x04a5 0x2040

# Benq/Acer/Vuego 640U
usb 0x04a5 0x2060

# Benq/Acer/Vuego 640BU
usb 0x04a5 0x207e

# Benq/Acer/Vuego 640BT
usb 0x04a5 0x20be

# Benq/Acer/Vuego 1240U
usb 0x04a5 0x20c0

# Benq/Acer/Vuego 3300 / 4300
usb 0x04a5 0x20b0

# Benq/Acer/Vuego 4300
usb 0x04a5 0x20de

# Benq/Acer/Vuego 5000
usb 0x04a5 0x20fc

# Benq/Acer/Vuego 5300
usb 0x04a5 0x20fe

# Agfa 1236U
usb 0x06bd 0x0002

# Agfa 1212U
usb 0x06bd 0x0001
usb 0x06bd 0x2061

# Agfa Snapscan e10
usb 0x06bd 0x2093

# Agfa Snapscan e20
usb 0x06bd 0x2091

# Agfa Snapscan e25
usb 0x06bd 0x2095

# Agfa Snapscan e26
usb 0x06bd 0x2097

# Agfa Snapscan e40
usb 0x06bd 0x208d

# Agfa Snapscan e42
usb 0x06bd 0x20ff

# Agfa Snapscan e50
usb 0x06bd 0x208f

# Agfa Snapscan e52
usb 0x06bd 0x20fd

# Epson Perfection 660
usb 0x04b8 0x0114

# Epson Perfection 1670
usb 0x04b8 0x011f

# Epson Perfection 2480
usb 0x04b8 0x0121

# Epson Perfection 3490
usb 0x04b8 0x0122
```

I then changed the permissions of /proc/bus/usb/001/ so that anyone can read and write to it.

However, if I run "xsane", I get a small window with the message "no devices available".

If I run "sudo xsane", I get a window warning me not to run it as root, and then I get a window that says "Failed to open device" 'snapscan:libusb:005:021': Invalid argument."

I'm lost. :confused:

---

### Post by psb6m on 2006-01-31
The Epson Perfection 3490 and 3590 are functionally the same (as far as Linux is concerned). After a good bit of Googling and experimentation, I got the 3590 running as follows:

First make sure that libsane-extras is installed.

Next make sure that all users who are allowed to use the scanner belong to the "scanner" group.

The version of SANE distributed with Breezy is not sufficiently up to date to run the 3490 and 3590 without problems. I upgaded to 1.0.17-1 by adding these lines to /etc/apt/sources.list:

```

deb http://people.debian.org/~aurel32/SANE sarge main
deb-src http://people.debian.org/~aurel32/SANE sarge main
``` 
Then run apt-get update. Soon the upgrade manager will inform you that upgrades are available. Run the upgrade manager to upgrade SANE. It will warn you that the packages you are installing are not secure. But life's full of risks, right?

Now you'll need the firmware, which is in a cab archive on the CD that came with the scanner. To find it run (substitute the CD mount point for your system):

```

find /media/cdrom0 -name "ModUsd.cab"
``` 
Once you've found ModUsd.cab, copy it to a temporary directory. Run cabextract (you may need to install the program) on this file. One of the extracted files will be Esfw52.bin; this is the firmware. Copy it to some convenient location (I used /usr/local/lib/firmware).

The next step may not be necessary, but I edited /etc/sane.d/dll.conf: commented out the line "epson" and added a line "epkowa".

Now edit /etc/sane.d/epkowa.conf and comment out the "scsi" line; the only uncommented line should read simply "usb".

Examine snapscan.conf to make sure that it contains an entry for the Epson Perfection 3490. (You don't need a separate entry for the 3590.) It should read

```

#Epson Perfection 3490
usb 0x04b8 0x0122
``` 

Near the top of this file, change the "firmware" line to read (change the path if you didn't put the firmware where I did):

```

firmware /usr/local/lib/firmware/Esfw52.bin
```

Now to get the permissions right, you need to add a udev rule. You could edit /etc/udev/rules.d/025_libsane.rules or /etc/udev/rules.d/025_libsane-extras.rules, but what I did was to add a file 10-udev.rules (named to load after the libsane rules files). The file contained these lines:

```

#scanner devices
scanner:root:scanner:0660
usb/scanner*:root:scanner:0660
```

Now unplug the scanner's usb cable from the computer and plug it in again. If I've remembered everything, it should work.

Peter

---

### Post by totfit on 2006-01-31
Thanks! I just happen to be staring at a 3490 that I just hooked up. For some reason I was under the missimpression by reading elsewhere that it worked out of the box so I bought it. Well, guess I will study your post closely. 

Gregg

---

### Post by totfit on 2006-01-31
Well, I am too tired to mess with this any more tonight. I will resume tomorrow. No success yet.

---

### Post by psb6m on 2006-02-01
I also thought it would work out of the box (it probably will with the next release of Ubuntu), and I killed the good part of a day making it work. The instructions I've given above may seem involved, but they should take only about fifteen minutes; and then it really is a good scanner.

Peter

---

### Post by totfit on 2006-02-01
Thanks. I will get around to setting it up, but for now I need to just take a break. While it may seem simple to set up for some, for one that have just left windows and is still learning commands, file locations, etc., it is a much greater task. I have done well in a couple of weeks just getting files transferred, printer working (didn't have to do anything:) ), my financial info transferred to gnucash in an operable fashion. Really, it is finding locations or access that is most difficult at this point. Oh, well, I have cut and pasted all this information and will probably continue this weekend. Thanks again.

---

### Post by sv!en on 2006-02-02
Hi,

[QUOTE=psb6m]

<removed detailed tutorial>

Now unplug the scanner's usb cable from the computer and plug it in again. If I've remembered everything, it should work.

Peter[/QUOTE]

I just wanted to say thanks: I sit here with a Breezy notebook and could hook it up to the Epson Perfection 3490 by following your tutorial.

The only problem is that the scanner seems to go to sleep after some time, and then it seems not possible to wake it up by software or USB-(un-)plugging. In this situation, the scanner seems to be virtually invisible for the OS. 
Removing and reconnecting the power (on the scanner ...) worked, however.

Thanks again! 
Sven

---

### Post by totfit on 2006-02-03
Well, finally got mine working. Thanks Peter for the email help. Learned a great deal about commands and accessing and editing files. The scanner works great.

Gregg

---

### Post by bbrazil on 2006-02-06
I'm considering getting one of these scanners.  

Does anyone know if the transparency adapter works?
(According to the SANE site, it does not work on the 3590, but there's no mention on the 3490)

Thanks!

---

### Post by totfit on 2006-02-06
I really couldn't tell you if it does or not. I haven't tried it. I think the difficulty would be in setting up the available software. Can't use the software that comes with the scanner, so it would be a matter of configuring xsane or kooka or something else to do it. I think it would be a difficult propositon at best. The scanner does function well however using the above mentioned available software. I am still very new to Linux, so there might be someone that has more information. Also, just wanted to let you know that the "quick scan" buttons don't work or at least I haven't tried to find a way to configure them. I have really never used them on any scanner I have had.

Gregg

---

### Post by palsyboy on 2006-02-08
I'm with both of you on being mistaken about Epson product working out-of-the-box.

Thanks for the tutorial, psb6m.  I apologize for taking a week to get back to you.

As I've been a pure Linux user for three years now and as someone with virtually no physical storage space, I throw away all drivers CDs, etc.  Until now, I've always assumed that if I somehow needed them again, I could just find drivers, firmware, etc. online.  In this case, I was wrong.  So, yeah, um, I don't have my scanner's disc. :oops:

Could someone please mail me the firmware (ModUsd.cab)?  I'd greatly appreciate it.  My e-mail address is [email]palsyboy@gmail.com[/email], if you'd be nice enough to help a stupid person.

---

### Post by totfit on 2006-02-08
I sent you two emails one that I am sure turned out to be a text of the driver file location itself. I sent the driver in a .zip file (I think) in a second email. Let me know if it worked. I am still a neophyte, but learning.

Gregg

Now for the wireless on my laptop:-k

---

### Post by palsyboy on 2006-02-09
Thanks for the drivers, good sir! =D>

As soon as I have time to play with udev, I'll report back.  Until then, it's time to get some sleep.

---

### Post by vayde on 2006-02-09
my thanks too.  I had to replace my hp scanjet 4400c overnight due to no linux support.  Of course I didn't realize there was no hope of getting it running until I NEEDED it.

Your howto saved my blood pressure to say the least.

Thanks again.

---

### Post by efreddi on 2006-02-12
[QUOTE=bbrazil]Does anyone know if the transparency adapter works?
(According to the SANE site, it does not work on the 3590, but there's no mention on the 3490)[/QUOTE]

On my 3490 the trasparency adapter works fine, but xsane uses only part of it, I mean that only more or less 2 pics instead of 4 are available. Probably somewhere it's stored the size of the scanning area but I have no clue how to find and fix this datum.

Regards



Elia Freddi

---

### Post by ganatronic on 2006-02-21
Do you think this method would work with the Epson Perfection 4490?

Regardless, I guess, I'm giving it a try right now. However, I'm stuck on the last instruction:

> Now to get the permissions right, you need to add a udev rule. You could edit /etc/udev/rules.d/025_libsane.rules or /etc/udev/rules.d/025_libsane-extras.rules, but what I did was to add a file 10-udev.rules (named to load after the libsane rules files). The file contained these lines:

Code:

#scanner devices scanner:root:scanner:0660 usb/scanner*:root:scanner:0660

I don't understand what should be added to the rules files. And I also don't know how to add a file (10-udev.rules) to a directory. I know that's way basic, but I always seem to get stuck on it.

But if you guys don't think I should be using the method layed out in this thread, then I'll try and come up with something else.

Thanks.

---

### Post by totfit on 2006-02-21
First of all I am new to Linux, but the way I did it is to log in the terminal:

sudo nautilus

I then migrated to the directory, right click, create file and pasted the file name. I opened the file and pasted the command information that you cut in your reply. My scanner is working with proper permissions. The only problem I have now is that it seems to go to sleep on me and can't be accessed without unpluggging and replugging the usb cable.

---

### Post by lompolo on 2006-03-06
Thank you very much psb6m.

---

### Post by lompolo on 2006-03-06
Here is bug that might intrest us. [https://launchpad.net/distros/ubuntu/+source/sane-backends/+bug/25970](https://launchpad.net/distros/ubuntu/+source/sane-backends/+bug/25970)

Could someone confirm this.

---

### Post by efreddi on 2006-04-02
[QUOTE=lompolo]Here is bug that might intrest us. [https://launchpad.net/distros/ubuntu/+source/sane-backends/+bug/25970](https://launchpad.net/distros/ubuntu/+source/sane-backends/+bug/25970)

Could someone confirm this.[/QUOTE]


In my trials I found not exactly the samed problem, but maybe the root cause is the same: sometime, even if the USB connection is established, Sane is not able to identify the scanner. My solution (let's call it in this way) is to power-up the scanner only after the I connect it to the pc. Actually, if I remember correctly, in the Epson manual is suggested the same.

Regs



Elia Freddi

---

### Post by totfit on 2006-04-02
I have found that after the scanner sits for a while without use that it "sleeps". I have to reconnect the usb or power on and off to get the scanner to be recognized again. Not sure if this is a Windows problem also or not. I haven't been in Windows to investigate. I do know that I get excellent performance with xane after it is recognized each time. Same with Kooka.

---

### Post by csatlose on 2006-06-30
I believe it is Peter who gave the instructions on how to get the 3590 Photo to work.  Thanks to this post I am now completely Windows free, while being able to scan the hundreds of photos I have.

The directions were very clear and very useful.  Thanks a lot.

---

### Post by eagle101 on 2006-07-05
> Now unplug the scanner's usb cable from the computer and plug it in again. If I've remembered everything, it should work.

Peter

Thanks Peter!  Your instructions only took about 10 min to get my scanner working.
Thanks for spending the time to post here.

-Dave

---

### Post by totfit on 2006-07-05
[QUOTE=eagle101]Thanks Peter!  Your instructions only took about 10 min to get my scanner working.
Thanks for spending the time to post here.

-Dave[/QUOTE]

Hey Dave,

Are you using Breezy or Dapper. I find that in Dapper I have native support and don't have to configure anything.

Gregg

---

### Post by eagle101 on 2006-07-05
Oh - Just noticed I'm in the Breezy forum.

I'm running Dapper 6.06 with all the latest updates and had exactly the same problems as efreddi.

efreddi's finished & working Breezy system had the same configuration as my Dapper default non-working configuration.  It seems like this scanner should work by default in Dapper.

I'm not sure if I needed to follow all of Peter's steps (I just wanted to get it working) so I just followed all his instructions.  

The scanner seems to wake up fine too BTW.  Weird stuff huh?

---

### Post by totfit on 2006-07-05
That is odd, mine worked with the Dapper Live CD also, with no configuration. 

Beats me.

Gregg

---

### Post by noynac on 2006-07-06
<<Posting Deleted>>

Problem fixed by loading firmware in snapscan.conf file.

---

### Post by WoodLark on 2006-07-14
My new Epson 3590 scanner arrived today. I have spent 4 hours following the steps in this thread trying to get it to work properly in kubuntu 5.10 with no success. On rare occasions, xsane will load, but will not allow me to actually scan. Most of the time when I try to start xsane, I get a message that no scanners are detected.

sane-find-scanner correctly finds the scanner and /etc/sane.d/snapscan.conf, /etc//sane.d/epkowa.conf and /etc/sane/d/dll.conf have been edited as described in the thread.

Does anyone have any further suggestions?](*,)

---

### Post by totfit on 2006-07-15
I can't tell you specifically at this point what to do. I am on vacation working from a laptop and don't have my "notes" with me. After you edit the files as you mention you have already done, pay particular attention to the thread where it concerns permissions. Make sure you have the correct permissions or try and scan using sudo xsane from the terminal. Another thing you might think about doing is upgrading as there is native support with Dapper that wasn't in Breezy. You should even be able to scan using the live CD without any modifications at all. At least I was able to do this with the 3490. Not only for your scanner, but Dapper is a fabulous upgrade. Installing .deb's has never been so easy. As far as your scanner goes you might also try installing Kooka for use as your scanning GUI. Wish I could be more helpful, but I am fairly new to Linux and can't give you much off the top of my head.

Gregg

---

### Post by patrick295767 on 2006-07-18
I followed your how to : It's is great ! 
 
To install my epson 2480, I used this firware  "firmware /etc/sane.d/esfw41.bin"
  ( [http://doc.ubuntu-fr.org/materiel/scanner_epson_2480](http://doc.ubuntu-fr.org/materiel/scanner_epson_2480) )

---

### Post by lonrot on 2006-08-11
Hello, I have a little problem understanding this guide:

In the:
```
machine# tools/find-scanner
   find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
   /dev/XXXXX 
```

What is machine#, I'm very new to this, so I don't havea clue.

---

### Post by PaulEdwards on 2006-09-17
> **lonrot said:**
> Hello, I have a little problem understanding this guide:

In the:
```
machine# tools/find-scanner
   find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
   /dev/XXXXX 
```

What is machine#, I'm very new to this, so I don't havea clue.
That is indicating the machine name, or hostname.

---

### Post by Hellaxe on 2006-12-12
Is there anyone using Edgy with this scanner?
It ws running perfectly with Breezy and Dapper but now i upgraded to Edgy with a fresh install and get the message:

```
Failed to open device'snapscan:libusb:002:007': Invalid argument
```
The wierd thing is that libusb:002:007 was before i unpluged/pluged the usb cord libusb:002:005.

Another thing the epkowa.conf doens't appear at sane.d. I created one only with ```
usb
```.
Can you tell me what i've done wrong?

Thanks

**[COLOR="DarkRed"]BIG EDIT: Solved[/COLOR]** I put in the epkowa.conf this:```

usb

usb 0x04b8 0x0122
```
Then it worked.

But i don't know if this the correct procedure.

---

### Post by matchstich on 2006-12-16
ok, when i open snapscan.conf ,  it is blank,  nothing there. what does that mean?
thanks
i got this once before and then i reinstalled ubuntu. dont understand why i am getting a blank page again

---

### Post by kpictjl on 2006-12-17
> **matchstich said:**
> ok, when i open snapscan.conf ,  it is blank,  nothing there. what does that mean?
thanks
i got this once before and then i reinstalled ubuntu. dont understand why i am getting a blank page again

Are sure your are opening the file in /etc/sane.d/ ? :-k 

If snapscan.conf if truly pulling a disappearing act then I recommend reading the thread below.  Patrick has a great little script that will install a new snapscan.conf.
[http://www.ubuntuforums.org/showthread.php?t=143504](http://www.ubuntuforums.org/showthread.php?t=143504)

---

### Post by makoto149 on 2007-01-12
If you want to get your Epson 3590 Scanner working, carve out about 15 minutes, and follow Peter's instructions EXACTLY, which is on this thread (along with a lot of noise and worthless replies (like "Thanks for the email information" -- WHAT email information?  Care to share?)) but can be found [at this link.]("http://ubuntuforums.org/showpost.php?p=695750&postcount=5")

[http://ubuntuforums.org/showpost.php?p=695750&postcount=5]("http://ubuntuforums.org/showpost.php?p=695750&postcount=5")

Thanks, Peter!!!

---

### Post by totfit on 2007-01-12
> **makoto149 said:**
> If you want to get your Epson 3590 Scanner working, carve out about 15 minutes, and follow Peter's instructions EXACTLY, which is on this thread (along with a lot of noise and worthless replies (like "Thanks for the email information" -- WHAT email information?  Care to share?)) but can be found [at this link.]("http://ubuntuforums.org/showpost.php?p=695750&postcount=5")

[http://ubuntuforums.org/showpost.php?p=695750&postcount=5]("http://ubuntuforums.org/showpost.php?p=695750&postcount=5")

Thanks, Peter!!!

So you just continue to make noise to go along with what you consider the rest of the "noise".
You can certainly try and make constructive comments without bashing the others.

---

### Post by justanick on 2007-02-18
I just installed my Epson 3490 on Edgy this easy "automagic" way following this guide for the Epson 4490 (but with the iscan files for the 3490 of course):

[http://ubuntuforums.org/showpost.php?p=2098424&postcount=11]("http://ubuntuforums.org/showpost.php?p=2098424&postcount=11")

Also you only need to install libsane, libsane-extras and sane-utils as a minimum.

---

### Post by hopefull on 2007-04-11
patrick295767's Avatar  	
patrick295767

I have used the method you used for installing the epson perfection 3480 and it appears to have installed my 3490 as a 3480, is there a way of using the method you used to upgrade the software for a 3490: does it make a lot of difference?

Hopeful

---

### Post by cmavr8 on 2007-11-07
Here's how I did it, easily, just for reference:


HOWTO: Epson perfection 3490 Photo scanner on Ubuntu 7.10

0. (Not sure if needed: Install sane-utils from synaptics package manager)
1. Install the driver under Windows and find esfw52.bin from the installation directory or extract it from a cab in Epson drivers CD.
2. Place it in /usr/share/sane/snapscan.
3. Edit /etc/sane.d/snapscan.conf and replace the firmware directory in the first lines with /usr/share/sane/snapscan/esfw52.bin. Save and close the file.
4. Xsane should work just fine now!

---

### Post by cmavr8 on 2007-11-20
SOLVED! Left only for reference to stupid or sleepy people like me..

Guys, Strange phainomenon:

I had the scanner working after doing the above steps (the ones I posted). After my 3-day trip, I came back and the scanner does not work!

I deleted /usr/share/sane/snapscan/ and recreated as root, added the bin inside, double checked the snapscan.conf file, but the scanner does not initialize when connected, and it's led stays dimmed down to minimum.

Does it have to do with user permissions?

EDIT:
Sorry, forgot to say that I couldn't find /snapscan dir in /usr/share/sane after the trip.So I just created it again.

EDIT: SOLVED!
I was too stupid and deleted the word "firmware":

> 
# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/esfw52.bin

Sorry for bothering..

---

### Post by Aggrocrag on 2007-12-29
I too am unfortunately in the position where I do not have the firmware.  Does anyone know of anyplace I can find it?

---

### Post by Hellaxe on 2007-12-30
> **Aggrocrag said:**
> I too am unfortunately in the position where I do not have the firmware.  Does anyone know of anyplace I can find it?

It's on the instalation CD. But it´s Christmas time and i'm felling Santa Claus so here it is.

Happy New Year.

[ATTACH]54680[/ATTACH]

---

### Post by relovett on 2008-02-24
Thanks Hellaxe! I had downloaded the latest Epson driver from the website (epson12539.exe, a zip file) and ran cabextract on all the .cab files, but couldn't find the right .bin. Your attachment worked for me.

---

### Post by ib80 on 2008-04-20
Hi,

Anyone got this working on a 64 bit Ubuntu ?
I was wondering if the firmware from the windows XP (32 bits) zip file found on the epson website worked on a 64 bit system.
I didn't try it because I don't want to mess up my PC :cool:

I tried to build the iscan driver for the 64 bit, but I found too many dependencies ... It also doesn't detect my GTK 2.0 installation. Go figure.

Thanks.

---

### Post by ib80 on 2008-04-20
I don't know why I was so hesitant on trying it. After some reading, I found out that the firmware is sent to the scanner and not used by the OS.

So I tried it and all worked like a charm. I just did two scans. Perfect.

PS : I followed cmavr8's 5-step HOW-TO. psb6m's post (1st page of this thread) was also helpful in getting the right firmware file.

---

### Post by finneyabraham on 2008-05-03
Thanks peter, I was grappling with this problem for a while, but your howto worked well for me. I made all the file and folder creations after I logged in as root graphically.:)

---

### Post by morrison on 2008-05-22
Greetings to all! I am a recent escapee from Windows and under Ubuntu 8.04 (hardy), I am beathing fresh air for the first time in a long time. When I did the install, I did not have my Epson Perfection 3490 turned on and as a result, as I understand it, the scanner will not work. My experience with Windows is fairly broad but very limited with Linux. Still, having read threads in the Forum, I have learned several things.

For example, I ran sane-find-scanner:
 
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

I then ran scanimage -L and got the following message:

morrison@morrison-desktop:~$ scanimage -l
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:005:004 failed: Invalid argument

I don't know how to edit "the firmware entry" or for that matter, some of the other suggestions that have been suggested in this forum thread. I believe I'm close to getting the scanner to work and if it's not too much trouble, I would really appreciate it of would someone please assist me.

I was running Windows XP on my 2003 HP computer with an AMD Athlon XP 3000+ and over the years have had to "rebuild" the operating system three times. This last attempt took hours when I first tried a non-destructive reinstall that failed and then a full install that included formatting the hard drive. Either I had something in the master boot record or else Windows Service Pack three rendered some of my HP supplied hardware/software obsolete. Having spent most of the day trying to rebuild my system, I came to the conclusion that trying to go at it again with EIGHT cd's plus many upgrades from Microsoft was insane when I had this beautiful ONE cd installation of Ubuntu available. That said, even with the problem with the scanner, you couldn't pay me to go back to Windows.

---

### Post by cmavr8 on 2008-05-22
1. Welcome!

2. Don't worry, your problem is easy to solve. Here's my "mini guide":

> HOWTO: Epson perfection 3490 Photo scanner on Ubuntu 7.10

0. (Not sure if needed: Install sane-utils from synaptics package manager)
1. Install the driver under Windows and find esfw52.bin from the installation directory or extract it from a cab in Epson drivers CD.
2. Place it in /usr/share/sane/snapscan.
3. Edit /etc/sane.d/snapscan.conf and replace the firmware directory in the first lines with /usr/share/sane/snapscan/esfw52.bin. Save and close the file.
4. Xsane should work just fine now!

So you basically need to do steps 1,2,3. 
A little help in 3: use the command "sudo gedit /etc/sane.d/snapscan.conf" (without the quotes)

Tell us what you don't understand/ what stops you!
Good luck and Welcome to the free world..

&#8220;In a world without walls and fences, who needs Windows and Gates?"

---

### Post by morrison on 2008-05-23
cmavr8, thanks for taking the time to write. I have the file ESFW52.ibn saved on my desktop.

I looked for /usr/share/sane/snapscan in the sane folder. I don't see snapscan there (I'm running Ubuntu Hardy). Is this a protected file?  I'm assuming (dangerous word) that I have to copy the bin file and paste it in snapscan (?). I tried to go into snapscan via the edit command and got:

morrison@morrison-desktop:~$ edit /usr/share/sane/snapscan
Warning: unknown mime-type for "/usr/share/sane/snapscan" -- using "application/*"
Error: no write permission for file "/usr/share/sane/snapscan"
Please advise. Many thanks!!
Morrison

---

### Post by morrison on 2008-05-23
cmavr8, here's an update. I did update the snapscan.conf file to reflect esfw52.bin being in the snapscan folder. Since I mentioned that I had "no write permission" when I tried to use "edit" on /usr/share/sane/snapscan, I must menton that I also tried sudo gedit and gedit. With sudo gedit and gedit, I get a new window with a blank screen. Which makes sense since snapscan isn't there (or, is a hidden window?). I also tried to drag and drop the bin file into, for example, the bin directory and was unable to do so. So, I would appreciate you telling me how to place the file in the designated directory, when the time comes. I seem to be so close to getting this thing running and I have the patience if you do :) Again, many thanks! Morrison

---

### Post by cmavr8 on 2008-05-23
Ok, in order to add the file in the folder, you need to "see" the folder with superuser permissions.

In order to do that, in a terminal type "sudo nautilus" and the nautilus file browser will pop up WITH sudo permissions.

Be very careful now, you could destroy your whole system.
Browse to /usr/share/sane/snapscan (create snapscan if it does not exist). Copy the bin file from your desktop to the snapscan directory.

Change workspace and start xsane. The scanner should do the normal initialization sound..

---

### Post by morrison on 2008-05-23
cmavr8, "progress is out most important product". Okay, I created the snapscan folder and, thank you very much, was able to copy the file esfw52.bin into it. I also double checked and snapscan.conf does point to snapscan/esfw52.bin. I also double checked and the esfw52.bin is in the newley created folder snapscan. Still nothing though. I tried unplugging the scanner, rebooting, turned the computer off and then back on and still, when I open xsane image scanner from applications, I get the following error message:

"failed to open device 'snapscan:libusb:005:005' invalid argument"

Any ideas?
Morrison

---

### Post by cmavr8 on 2008-05-23
Grrr... none.
Sorry..

Try googling the error..

---

### Post by morrison on 2008-05-23
Will do. Thanks for your help!!
Morrison

---

### Post by Rmantingh on 2008-06-01
The following steps did it for me (running Xubuntu 8.04 Hardy):-

1) sudo apt-get install sane-utils

2) Go to the Users and Groups screen and add yourself (and other
   scanner users) to the "scanner" group.

3) Log off and on (or reboot) to make 2) effective.

4) sudo mkdir /usr/share/sane/snapscan

5) sudo cp Esfw52.bin /usr/share/sane/snapscan

6) sudo chmod 644 /usr/share/sane/snapscan/Esfw52.bin

7) sudo vi /etc/sane.d/snapscan.conf

  Change firmware entry to say:-
  firmware /usr/share/sane/snapscan/Esfw52.bin


I'm not sure if all of these points are needed but it worked for me.

Please note point 6 as the file was initially created with insufficient access.

Also check the exact name of the bin file as Linux is unforgiving
regarding mistakes in upper- / lowercase.

Hope this helps someone.

---

