---
title: "Ivtv"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by Andrew-buntu on 2004-11-01
Hello.  I recently swapped my HTPC's KnoppMyth install for Ubuntu after trying Ubuntu on my desktop.  I used Ubuntu's multiverse package to install mythtv (worked great) but the ivtv driver for my Hauppage 250 wasn't installed.  I downloaded the source code but am lost when it comes to installing it.  I've seen instructions that involve ./configure make, make install, some that use perl Makefile.PL and some that involve copying files (that I don't have) from /usr/src/linux/.  ](*,) 

In short, I am VERY confused as to what I should be doing and all the resources for installing ivtv involve other distributions.

How should I go about doing this?  Should I add a debian package source and try to do it through apt-get install?  There's no ivtv driver in the multiverse.  Is there a special Ubuntu way to install drivers from source?  Can some Ubuntu master make an appropriate .deb file for us MythTV users?

Thanks for any help you can provide.

---

### Post by schaez on 2004-11-01
I'm interested in finding a solution too.  I made a post in the general support section, but I haven't gotten any replies.

So far I have tried ivtv packages for 2.6 kernel from [http://67.18.1.101/~ckennedy/ivtv/](http://67.18.1.101/~ckennedy/ivtv/) without much luck.  Although it didn't work, here's what I did.  Maybe you'll have better luck.

   Install kernel headers
   unzip the source code and goto driver folder
   make
   make install
   modprobe ivtv (does not find the module)

---

### Post by Andrew-buntu on 2004-11-02
Thanks for the help, schaez, but I can't even get a [FONT=Fixedsys]make [/FONT]done correctly.  It tells me that I'm missing a .config file in /usr/src/linux/build/ - sorry I don't have the exact message, I'm not at the computer right now.  I installed the linux-tree package for my kernel so I don't know why I'm missing files.

If I get this resolved, I'll come back here and post some precise directions on how I did it.

---

### Post by schaez on 2004-11-02
Have you installed linux-headers-2.6.8-xxxxx?

I've made some additional progress.  First you need the firmware, see these two sites:

[http://ivtv.writeme.ch/tiki-index.php?page=FirmwareVersions](http://ivtv.writeme.ch/tiki-index.php?page=FirmwareVersions)
[http://ivtv.writeme.ch/tiki-index.php?page=ExtractingTheFirmware](http://ivtv.writeme.ch/tiki-index.php?page=ExtractingTheFirmware)

After that I went to the driver director of the source code and did make; make install

Then i inserted modules in the following order:

modprobe i2c-core
modprobe i2c-algo-bit
modprobe tuner type=2
insmod msp3400.ko
modprobe videodev
insmod saa7115.ko
insmod tveeprom.ko
insmod ivtv.ko

This loaded everything but I still can connect to /dev/video0 when I load tvtime.

---

### Post by mduduzi on 2004-11-03
It's usually a good idea to download the kernel source code also, not just the kernel headers if you'll be compiling anything that requires the generation of modules.
 Synatpics will handle these kernel installations nicely.
In terms of the TVapplication, tvtime is working superbly for me.

---

### Post by schaez on 2004-11-03
I finally got it to work.  Like mduduzi said, you'll need the kernel source code too.  

After builing the ivtv modules, I copied /lib/modules/2.6.8.1/extras folder to /lib/modules/2.6.8.1-3-k7/extras (my kernel).

Then ran make, make install in the utils folder of the ivtv source code. Extracted the firmware.  Then created a file called ivtv in /etc/modutils/ with the following


alias char-major-81     videodev
alias char-major-81-0   ivtv
alias char-major-61 lirc_i2c
options ivtv debug=1
options tuner type=2
options msp3400 once=1 simple=1
add below ivtv msp3400 saa7115 tuner
add above ivtv lirc_dev lirc_i2c

After this I ran "update-modules" and modprobe tveeprom then modprobe ivtv

This loaded all the modules I needed without errors.  tvtime would still not work, but I read somewhere that it didn't work with pvr250 so I tried the mythtv interface and it worked.  I ope this helps

Ryan

---

### Post by Andrew-buntu on 2004-11-04
Well, I'm getting there.

I've installed my kernel-source and kernel-headers
I've extracted the firmware to /lib/modules using the ivtvfwextract.pl utility
I've use make mrproper and make oldconfig in my /usr/src/linux directory to get my .config files
but now when I cd to /ivtv/driver and do a make, I get a huge error.  I've seen a few other instances of it through google but no one has solved the problem.

Below is the error I've received.  Thanks for any light you can shed on this.
And congrats on getting your card working, schaez.

---

### Post by cbozic on 2004-11-19
I got my ivtv card working on ubuntu and I took some notes along the way.  I am not a linux genius so I don't always know the best way to do things.  Having said that, here is a document describing my success and the hicupps along the way to getting my card working.  I hope it is useful to some.

```
I have a hauppauge PVR 250 wintv card with the CX23416 chip.  I am using
the version 2.6.8.1-3-686 of the ubuntu provided linux kernel and version 3.3.4
(Debian 1:3.3.4-9ubuntu5) of gcc installed with the matching g++ ubuntu
package.

I got the drivers for the 2.6 kernel at:

http://67.18.1.101/~ckennedy/ivtv/

The particular file I downloaded was ivtv-0.2.0-rc2l.tgz because it was the most
recent at the time of this writing.  I found that repository off the beaten path
at this page:

http://ivtv.writeme.ch/tiki-index.php?page=Kernel-2.6.patches

The reason I say it is off the beaten path is because I couldn't find any links
from the ivtv download section to this area.  I just did a google search
for "ivtv 2.6 kernel" and this page came up.

I unzipped this file and then:

"$ cd ivtv-0.2.0-rc2l/driver"

From there I ran make as a non-root user.

"$ make"

Everything compiled fine for me so after that, I ran:

"$ sudo make install"

Running that command provided me with a warning telling me I should delete
the file "/lib/modules/2.6.8.1-3-686/kernel/drivers/media/video/msp3400.ko" but
I chose not to permanently delete.  Instead I just moved it to a backup
location in my home folder:

"$ mv /lib/modules/2.6.8.1-3-686/kernel/drivers/media/video/msp3400.ko ../../."

The instructions provided with the driver said that after that, I can just type
"modprobe ivtv" and everything should work.  However it said it could not
find the ivtv module when I ran that command.  I ran a find for the ivtv module
and found that it had been installed in the /lib/modules/2.6.8.1/extra/ folder
along with all the other ivtv modules.  Not knowing a better way to do this,
I just copied these files to the folder I thought they should live in.  I based
this decision on reading the Makefile2.6 file to see what it thought it should
be doing.  So, I ran the following commands to fix this:

"$ cp /lib/modules/2.6.8.1/extra/* /lib/modules/2.6.8.1-3-686/kernel/drivers/media/video/"
"$ depmod"

After that I could run modprobe like the instructions said:

"$ modprobe ivtv"

Then I checked dmesg to see if all went well:

"$ dmesg
Linux version 2.6.8.1-3-686 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 13:10:36 BST 2004
.
.
. (lots of unrelated output has been omitted)
.
.
Linux video capture interface: v1.00
ivtv: ==================== START INIT IVTV ====================
ivtv: version 0.2.0 (0.2.0-rc2l) loading
ivtv: Linux version: 2.6.8.1-3-686 preempt 686 gcc-3.3
ivtv: In case of problems please include the debug info
ivtv: between the START INIT IVTV and END INIT IVTV lines when
ivtv: mailing the ivtv-devel mailinglist.
ivtv: Autodetected WinTV PVR 250 card
ivtv: Found an iTVC16 based chip
PCI: Found IRQ 9 for device 0000:02:09.0
PCI: Sharing IRQ 9 with 0000:02:0d.0
ivtv: Unreasonably low latency timer, setting to 64 (was 32)
ivtv: XXX PCI device: 0x1a30 vendor: 0x8086
tveeprom: Hauppauge: model = 32552, rev = B123, serial# = 2751397
tveeprom: tuner = Philips FM1236 (idx = 23, type = 2)
tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
tveeprom: audio_processor = MSP3440 (type = 11)
ivtv: i2c attach [client=tveeprom[0],ok]
ivtv: Tuner Type 2, Tuner formats 0x00001000, Radio: yes, Model 0x00891493, Revision 0x00000001
ivtv: NTSC tuner detected
ivtv: Radio detected
tuner: chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
ivtv: i2c attach [client=(tuner unset),ok]
saa7115: starting probe for adapter ivtv i2c driver #0 (0x10005)
saa7115: detecting saa7115 client on address 0x42
saa7115: writing init values
ivtv: i2c attach [client=saa7115[0],ok]
saa7115: status: (1E) 0x48, (1F) 0xc0
msp34xx: ivtv version
msp34xx: init: chip=MSP3448W-A2, has NICAM support, simple (D) mode, simpler (G) no-thread mode
msp34xx: $Id$ compiled on: Nov  6 2004 18:32:41
ivtv: i2c attach [client=MSP3448W-A2,ok]
Unable to open '/lib/modules/ivtv-fw-enc.bin'.
ivtv: failed loading encoder firmware
ivtv: Error loading firmware -3!
ivtv: Error -3 initializing firmware.
ivtv: Error -12 on initialization
ivtv-iTVC15_16_mpg2_encoder_card: probe of 0000:02:09.0 failed with error -12
ivtv: ====================  END INIT IVTV  ===================="

So, I concluded that everything did NOT go well because of the errors at the
end of the dmesg output.  :)  Of course!  I haven't given ivtv my win binary
driver yet.  I did the following to remedy this problem:


-- Installing the firmware --

Go to http://ivtv.writeme.ch/tiki-index.php?page=FirmwareVersions and
download the recomended firmware version. In my case it was:
ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22168_inf.zip

Download that file and run:

"$ cd ../utils
"$ ./ivtvfwextract.pl pvr_1.18.21.22168_inf.zip"
"$ cd ../driver"
"$ make reload"


--- Installing perl modules ---

First use cpan to get the easy one:

"$ cpan -i Config::IniFiles"

Then go to http://www.pcxperience.org/james/ivtv/ and get the
Video::Frequencies and Video::ivtv modules.  We'll have to install these
manually.  To do this, follow the instructions at:
http://perl.about.com/library/weekly/aa030500a.htm.

Here's my paraphrase of the above instructions.  Change into the directory
where you downloaded the perl modules.  Type:

"$ tar -xzf Video-Frequencies-0.03.tar.gz"
"$ cd Video-Frequencies-0.03"
"$ perl Makefile.PL"
"$ make"
"$ sudo make install"

Do the same thing for Video-ivtv-0.13.tar.gz.

-- Installing the utils --

"$ cd ../utils"
"$ make"
"$ sudo make install"

-- That's it! --

You should be able to use the ptune.pl program that came with ivtv to set
the channel for your card and run

"$ mplayer /dev/video0" 

...to watch tv!
```

---

### Post by podmf on 2004-12-28
Hi

Your notes were most helpful, especially the link to newer releases of the drivers.  Future readers might find it useful to note two issues that you yourself may not have encountered:

* [http://67.18.1.101/~ckennedy/ivtv/](http://67.18.1.101/~ckennedy/ivtv/) was unavailable when I tried it, but I fould the same files at many other IP addresses by googling for "ckennedy ivtv"

* Important: Debian/Ubuntu naming policy appears to prevent the Makefiles from correctly locating .config, if you have kernel  images and headers with more than 3 dotted numbers in the name

I had both

/lib/modules/2.6.8.1-3-386
and 
/lib/modules/2.6.8-1-386

presumably as a result of security updates, but only /lib/modules/2.6.8-1-386 had a symlink called build to /usr/src/kernel-headers-2.6.8-1-386 and hence to the .configfile

Putting an identical symlink in /lib/modules/2.6.8-1-386 did the trick.

Dave

---

### Post by biTaZ on 2005-02-21
[QUOTE=Andrew-buntu]Well, I'm getting there.

I've installed my kernel-source and kernel-headers
I've extracted the firmware to /lib/modules using the ivtvfwextract.pl utility
I've use make mrproper and make oldconfig in my /usr/src/linux directory to get my .config files
but now when I cd to /ivtv/driver and do a make, I get a huge error.  I've seen a few other instances of it through google but no one has solved the problem.

Below is the error I've received.  Thanks for any light you can shed on this.
And congrats on getting your card working, schaez.[/QUOTE]
 Haha, i get exactly the same message... Darn, I'm so sad being forced to boot my XP just to watch TV, this is so sad :'(
Any help would be appreciated.

---

### Post by trubblemaker on 2006-11-12
here's some links that might help:

[http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation#Compile_and_Install_IVTV_driver](http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation#Compile_and_Install_IVTV_driver)

[and this is the killer link that worked for me]("https://wiki.ubuntu.com/Install_IVTV_Edgy")

---

