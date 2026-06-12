---
title: "HP Scanjet 3500 series SANE backend for Breezy!"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by NeTo on 2005-12-10
A backend for the Scanjet 3500 series (3500c, 3530c, 3570c) has been recently released. You can find information about it [here](http://projects.troy.rollo.name/rt-scanners/). That means you can now use those scanners in Linux using any SANE frontend, like xsane.

Considering the patch works for a sane-backends version newer than the one in Ubuntu, I slightly modified it to work in Breezy. You can find the attached file in this post. I have also compiled a libsane deb that supports the hp3500 scanners.

A lot of thank yous to Troy Rollo for making this much needed backend.

**To download and install the package**
If you don't want to apply the patch yourself, you can download the modified libsane deb files:```

wget http://netosoft.no-ip.org/Ubuntu/breezy/sane-backends/libsane_1.0.15-10~neto1_i386.deb
wget http://netosoft.no-ip.org/Ubuntu/breezy/sane-backends/sane-utils_1.0.15-10~neto1_i386.deb
```Notice the files are hosted in my own pc, so they won't be online most of the time.

You can install them by running:```
sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
```Now if you run:```
scanimage -L
```You should see something like:```
device `hp3500:libusb:001:005' is a Hewlett-Packard ScanJet 3500 scanner
```That means your scanner has been detected successfully by sane.

**To compile the package**
The attached file contains two patches:
[LIST]
[*]hp3500_debian_version.diff changes the libsane version, so it doesn't get updated with the version in the breezy repos
[*]hp3500_breezy.diff contains the hp3500 backend
[/LIST]

To download and extract the attached file:```
wget -O hp3500.tar.gz http://ubuntuforums.org/attachment.php?attachmentid=4378
tar -xzvf hp3500.tar.gz

```To apply the patch you need the libsane sources and its dependencies:```
apt-get source libsane
sudo apt-get build-dep libsane
```Finally, you need to apply the patches and compile libsane```
cd sane-backends-1.0.15
patch -p0 < ../hp3500_debian_version.diff
patch -p0 < ../hp3500_breezy.diff
dpkg-buildpackage -nc -uc -rsudo

```After the compilation is done, you will have three deb files that you can install as explained before:```
sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
```

---

### Post by kuleali on 2005-12-17
Could you be more spesific , where is the backends directory ?. Please give me a step by step howto. 

lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 03f0:2205 Hewlett-Packard ScanJet 3500c
Bus 001 Device 004: ID 03f0:1504 Hewlett-Packard DeskJet 920c
Bus 001 Device 001: ID 0000:0000


found USB scanner (vendor=0x03f0, product=0x2205) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by NeTo on 2005-12-17
I have updated the guide so it looks more like a HOW-TO. Hopefully that should help you get going with the driver compilation.

---

### Post by NeTo on 2006-03-21
It seems that no-ip.com doesn't redirect addresses that look like *membername.no-ip.com* anymore for non-premium members. I didn't realized the issue until now, so the links were down all of this time.

I have now registered a different address, so I have updated the (now hopefully) working links in the first post. Sorry for any inconvenience.

---

### Post by p221072 on 2006-03-22
Ok, I tried to get the files at different hours and day, thinking your pc was off.
Now I downloaded the libsane deb already patched. This evening I will aplly them.
Thank you

---

### Post by techflat on 2006-04-06
Hi NeTo

Aparently this worked for me, I executed
```
scanimage -L
```
and this is what i got:

device `hp3500:libusb:001:005' is a Hewlett-Packard ScanJet 3500 scanner

So I think it's working.

Now, could you explain a little what I just did to my computer please??  :D 

(I'm fairly new to linux...)

---

### Post by NeTo on 2006-04-06
[QUOTE=techflat]Now, could you explain a little what I just did to my computer please??  :D 

(I'm fairly new to linux...)[/QUOTE]

You installed a [Sane driver](http://www.sane-project.org/) for your scanner. That basically means that you can use Sane (or any of its frontends) to scan images from Linux.

Ubuntu comes with [XSane](http://www.xsane.org/) installed, so you can scan images in a breeze. Go to *Applications->Graphics->XSane Image Scanning Program* to start XSane.

Once XSane starts, click on *Acquire Preview*. You should see a sample scan on your screen (note that currently the scanner works slower, and hence noisier, than in windows). Click on *Scan* and wait a few minutes, you should end up with your first scanned image :D

---

### Post by linuxguiri on 2006-04-06
I get an error that the deb files posted above are not debian format:

```
~$ sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
dpkg-deb: `libsane_1.0.15-10~neto1_i386.deb' is not a debian format archive
dpkg: error processing libsane_1.0.15-10~neto1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: `sane-utils_1.0.15-10~neto1_i386.deb' is not a debian format archive
dpkg: error processing sane-utils_1.0.15-10~neto1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 libsane_1.0.15-10~neto1_i386.deb
 sane-utils_1.0.15-10~neto1_i386.deb

```

It looks like they downloaded correctly though:
```
~$ wget http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/sane/libsane_1.0.15-10~neto1_i386.deb
--09:26:59--  http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/sane/libsane_1.0.15-10~neto1_i386.deb
           => `libsane_1.0.15-10~neto1_i386.deb'
Resolving netosoft.no-ip.org... 204.16.252.98
Connecting to netosoft.no-ip.org|204.16.252.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 791           --.--K/s

09:27:00 (31.43 MB/s) - `libsane_1.0.15-10~neto1_i386.deb' saved [791]

~$ wget http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/sane/sane-utils_1.0.15-10~neto1_i386.deb
--09:27:22--  http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/sane/sane-utils_1.0.15-10~neto1_i386.deb
           => `sane-utils_1.0.15-10~neto1_i386.deb'
Resolving netosoft.no-ip.org... 204.16.252.98
Connecting to netosoft.no-ip.org|204.16.252.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 797           --.--K/s

09:27:22 (28.15 MB/s) - `sane-utils_1.0.15-10~neto1_i386.deb' saved [797]


```

---

### Post by linuxguiri on 2006-04-06
I compiled the source, but when I try to install the debs I get an error:

```
~/sane-backends-1.0.15$ sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
dpkg: error processing libsane_1.0.15-10~neto1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing sane-utils_1.0.15-10~neto1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libsane_1.0.15-10~neto1_i386.deb
 sane-utils_1.0.15-10~neto1_i386.deb

```

---

### Post by linuxguiri on 2006-04-06
Oh! Sorry I had to cd ..

Muchísimas gracias por el 'howto', NeTo.

---

### Post by NeTo on 2006-04-06
[QUOTE=linuxguiri]Oh! Sorry I had to cd ..

Muchísimas gracias por el 'howto', NeTo.[/QUOTE]

Glad to see you got it working. I will check out the files anyway to see if there is  anything wrong with them (the fact that wget returns *Length: unspecified [text/html]* sounds a bit odd to me).

Buena suerte con el driver! :KS

---

### Post by reginald on 2006-04-10
thanks very much for this.  This sorted me out nicely. 
much appreciated

---

### Post by p221072 on 2006-04-24
Hi I've got some problems. I downloaded the .deb files and launch:
sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
but I got these errors:
```
paolo@casa:~/Downloads$ sudo dpkg -i libsane_1.0.15-10~neto1_i386.deb sane-utils_1.0.15-10~neto1_i386.deb
(Lettura del database ... 74902 file e directory attualmente installati.)
Mi preparo a sostituire libsane 1.0.15-10~neto1 (con libsane_1.0.15-10~neto1_i386.deb) ...
Spacchetto il rimpiazzo di libsane ...
Mi preparo a sostituire sane-utils 1.0.15-10~neto1 (con sane-utils_1.0.15-10~neto1_i386.deb) ...
Spacchetto il rimpiazzo di sane-utils ...
dpkg: problemi con le dipendenze impediscono la configurazione di libsane:
 libsane dipende da libgphoto2-2 (>= 2.1.6-1ubuntu6.1); comunque:
  La versione di libgphoto2-2 nel sistema è 2.1.6-1ubuntu6.
 libsane dipende da libgphoto2-port0 (>= 2.1.6-1ubuntu6.1); comunque:
  La versione di libgphoto2-port0 nel sistema è 2.1.6-1ubuntu6.
dpkg: errore processando libsane (--install):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di sane-utils:
 sane-utils dipende da libsane (>= 1.0.11-3); comunque:
  Il pacchetto libsane non è ancora configurato.
dpkg: errore processando sane-utils (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 libsane
 sane-utils
paolo@casa:~/Downloads$

```
I'm sorry for it's in italian, but the problem seems to be with dependencies
anybody can help me?

thank you
Paolo


EDIT 
Finally solved the problem now that I had some time to work on it
I just had to update the libgphoto packets
now it's working fine
Thank you

---

### Post by ceng1984 on 2006-04-24
NeTo,

I have installed the sane backend for the HP3500 scanner and also applied the patches from your How-To.
The listing from scanimage -L returns:

device `hp3500:libusb:005:004' is a Hewlett-Packard ScanJet 3500 scanner

and listing from lsusb returns:

Bus 005 Device 004: ID 03f0:2205 Hewlett-Packard ScanJet 3500c
Bus 005 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Trying the xsane program under the Applications-Graphics listing returns a box flashing up (to fast to read), then nothing.

Trying the xsane program in a terminal window returns:

(xsane:10547): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(xsane:10547): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(xsane:10547): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(xsane:10547): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed
Segmentation fault

It appears the backend sees the scanner fine, but the xsane program is not. 
Any help would be appreciated.

---

### Post by No Whammies on 2006-04-24
Just tried this method and it works for Dapper as well.  It scans a bit slower and noisier than before (as said) but the scans are clear and it works on the rare occasions I need it.

edit:  OOPS!  When I do this on Dapper, it works, but the computer immediately requests an update and returns the computer to it's former state.  Could one of you please do something like this for Dapper?

---

### Post by ivomans on 2006-05-18
[quote=No Whammies]Could one of you please do something like this for Dapper?[/quote] 

I just did and I'm now able to use my 3530c on Dapper! I applied the changes described in NeTo's patchfiles to the current version in Dapper: 1.0.17-1ubuntu4.

Whoever is interested can download underneath files. You'll need at least nr. 1+2. Then give command:

```
sudo dpkg -i libsane_1.0.17-1ubuntu4.1~hp3500c_i386.deb sane-utils_1.0.17-1ubuntu4.1~hp3500c_i386.deb
``` 
1: [http://www.databrowser.org/download/sane-utils_1.0.17-1ubuntu4.1~hp3500c_i386.deb]("http://www.databrowser.org/download/sane-utils_1.0.17-1ubuntu4.1%7Ehp3500c_i386.deb")
2: [http://www.databrowser.org/download/libsane_1.0.17-1ubuntu4.1~hp3500c_i386.deb]("http://www.databrowser.org/download/libsane_1.0.17-1ubuntu4.1%7Ehp3500c_i386.deb")
3: [http://www.databrowser.org/download/libsane-dev_1.0.17-1ubuntu4.1~hp3500c_i386.deb]("http://www.databrowser.org/download/libsane-dev_1.0.17-1ubuntu4.1%7Ehp3500c_i386.deb")

---

### Post by No Whammies on 2006-05-20
Kick-***!  Thank you!

---

### Post by tuga on 2006-05-24
Thank you ivomans.
After install sane I download file 1 and 2. Then gave the command...
Xsane is now working!

---

### Post by valefr on 2006-05-27
You are my hero, i've got a ubuntu with breazi on PPC, it works fine.

Tanks

---

### Post by eymerich on 2006-09-13
Thx!!

Is the preview a little slow? .... there are settings to changge?

---

### Post by Orval on 2006-11-20
After the upgrade to Efty my scanjet still didn't work. But after a reinstallation of sane (frontends and backends) my scanner works! For the first time in Linux-land all my hardware works now. It's time to format my windows partion.

---

