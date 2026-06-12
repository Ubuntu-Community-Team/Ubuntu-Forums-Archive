---
title: "how to install epson scanner in ubuntu 10.04 ?"
date: 2010-11-11
forum: Hardware
---

### Post by green69 on 2010-11-11
Hi guys!

I need help to install my epson scanner (perfection 3170 photo). I'm running on the 10.04.

I've tried to follow the istruction from old threads:

* downloading the drivers (iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm) from: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
* converting them to deb (using alien)
* installing: xsane sane-utils libsane libsane-extra etc.

but when I try to run xsane it keep saying "no devices available"

Please can anybody help me?   :confused:

---

### Post by needastick on 2010-11-17
Hello green69,
                    I have to start by saying I probably can't help you but by bumping the thread someone with more experience may help both of us.

I also have been trying to install the 3170 and have been getting the same results. My problem is that I am unable to install the .rpm using alien, I have tried the direct install and converting it first. I have also tried extracting the tarball.

When you get " no device available" I wonder if this is because you need to sudo it, if so you will have to change your user permissions, or, perhaps the .rpm hasn't installed properly. ( I'm also getting no device available)

Are you running 32 or 64bit? My system is 64 which I think is giving the alien problems. I have tried force install, also with no effect.

Anyone solved this? regards, Tony.

---

### Post by green69 on 2010-11-19
> **needastick said:**
> Hello green69,
                    I have to start by saying I probably can't help you but by bumping the thread someone with more experience may help both of us.

I also have been trying to install the 3170 and have been getting the same results. My problem is that I am unable to install the .rpm using alien, I have tried the direct install and converting it first. I have also tried extracting the tarball.

When you get " no device available" I wonder if this is because you need to sudo it, if so you will have to change your user permissions, or, perhaps the .rpm hasn't installed properly. ( I'm also getting no device available)

Are you running 32 or 64bit? My system is 64 which I think is giving the alien problems. I have tried force install, also with no effect.

Anyone solved this? regards, Tony.

I've still not solved this tread and honestly I don't know how to advance.
I'm running on a 32 bit. To me it seem that the conversion from rpm to deb went right but once installed I still have the "no device available" message. Please can anybody help us?

---

### Post by dargaud on 2010-11-19
Have you tried recompiling the source file that you get from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do) ?

---

### Post by manton1263 on 2010-11-21
> **green69 said:**
> Hi guys!

I need help to install my epson scanner (perfection 3170 photo). I'm running on the 10.04.

I've tried to follow the istruction from old threads:

* downloading the drivers (iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm) from: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
* converting them to deb (using alien)
* installing: xsane sane-utils libsane libsane-extra etc.

but when I try to run xsane it keep saying "no devices available"

Please can anybody help me?   :confused:
I had the same problem. I've spent days trying everything I know (not much really).  I reinstalled just about everything including iscan from avasys. sane-find scanner finds the scanner. lsusb  finds the scanner. scanimage says 'no scanner  found'. Under Graphics menu, xsane image scanner says 'no scanner found'. I went under users & groups and there was no 'scanner' group, so I skipped over that. I don't have dev/usb directory so I skipped over that. I had previously spent hours slooking thru posts about installing epson perfection 3170 and  they said to do everything i had tried. I decided i would scream for help. Then i decided i would try one more thing. I entered "xsane epson" on the command line._ And IT WORKED! _I tried it  3 times, once with epkowa and that worked. I wonder if someone can  tell how to make it work Grapics menu?

---

### Post by manton1263 on 2010-11-21
> **manton1263 said:**
> I had the same problem. I've spent days trying everything I know (not much really).  I reinstalled just about everything including iscan from avasys. sane-find scanner finds the scanner. lsusb  finds the scanner. scanimage says 'no scanner  found'. Under Graphics menu, xsane image scanner says 'no scanner found'. I went under users & groups and there was no 'scanner' group, so I skipped over that. I don't have dev/usb directory so I skipped over that. I had previously spent hours slooking thru posts about installing epson perfection 3170 and  they said to do everything i had tried. I decided i would scream for help. Then i decided i would try one more thing. I entered "xsane epson" on the command line._ And IT WORKED! _I tried it  3 times, once with epkowa and that worked. I wonder if someone can  tell how to make it work Grapics menu?
Sorry! I was premature with my response. When I tried to do a scan preview or just scan, I get the  msg "failed to start scanner: invalid argument".
maybe someone can help me with this or should i start a new thread?

I'm using ubuntu 10.4 LTS.

---

### Post by manton1263 on 2010-11-21
> **manton1263 said:**
> Sorry! I was premature with my response. When I tried to do a scan preview or just scan, I get the  msg "failed to start scanner: invalid argument".
maybe someone can help me with this or should i start a new thread?

I'm using ubuntu 10.4 LTS.
Sorry twice. Shot from the hip again. When I tried it with "xsane epson" I got the message "failed to start scanner: invalid argument" then I tried it with the command line "xsane epkowa" and it scans the document fine, but I do get a message in the terminal window that says "(xsane:1715): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated."
     I guess I Have a long row to hoe, though at least it scans.
 I just don' know where to start, any help would be appreciated. (how to correct the error messages and how to make it work under the graphics menu)

---

### Post by GLH on 2010-11-22
I had this problem after upgrade from Hardy LTS to Lucid LTS.  Epson 3170.  In my case the scanner worked when I ran any access program as root via sudo.  eg.
$ sudo iscan
or
$ sudo   sane-find-scanner

If this is your case try this fix that supplies a missing file so that the scanner can be accessed by any user that is a member of group scanner: 
create a new file by for example:

$ cd /etc/udev/rules.d
$ sudo nano 45-libsane.rules

Enter the following single line in the text editor:
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="664", GROUP="scanner"

Save and close.

If you are not already a member of group "scanner"  add yourself.

Power cycle the scanner and verify that an access program connects without sudo.

For other scanners, change the idVendor and idProduct using values from your scanner.
$ lsusb
...
Bus 001 Device 007: ID 04b8:0116 Seiko Epson Corp. Perfection 3170 (GT-9400)
....

For more details see:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/121082](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/121082)

---

### Post by mandebvu on 2010-12-04
As there are no further comments this may be old news, or a solution for some.
I had the same problem as manton1263, i.e. the scanner worked when invoked as 'xsane epkowa'. All attempts to correct permissions, etc solved nothing.
The solution is in the sane manual (man sane), with a bit of digging.
Put simply:
[INDENT]sudo gedit /etc/sane.d/dll.conf[/INDENT]
[INDENT]Add the line 'epkowa' (I added it with the epson lines)[/INDENT]
[INDENT]Save and exit[/INDENT]

According to the manuals, iscan, sane and xsane all use the sane backends. This therefore fixes the problem for all 3.
Other users may have different issues, but this certainly sorted my problem out. Just a thought, this system was upgraded from Hardy, under which the scanner was running as 'epkowa'. It may be that there were existing files from that installation, which will not exist on a new installation?

For Info: Ubuntu 10.4 LTS, Epson 3170 Photo scanner.

---

### Post by emiliobasaldua on 2010-12-04
Thanx Buddy for this kind of info, i think they help us

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-03-17
you should visit
[http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

---

### Post by jbrice on 2011-03-17
> you should visit
[http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

I find that the appropriate scanner utility from avasys and the associated plug-in work fine here with a V350 scanner (dig down from the URL above to get the appropriate installation .debs). Though I now prefer to use gscan2pdf (from the Software Centre) for routine scanning - but it also needs the avasys plug-in installed to provide the interface with the scanner.

Hope that helps.

---

### Post by bregale on 2011-12-10
hi i have been trying to get my epson scanner 3170 perfection to run on ubuntu for the last 4 or 5 ubuntu releases i have been trying again today with no success saw the link on this page but link appears to be dead, has anyone got these scanners to work on ubuntu ? i have even tried to get advice from my local linux group but still it does not work , i have to have a dual boot system and run windas when i want to scan and i hate that .

---

### Post by dargaud on 2011-12-10
Link is still good, I just checked. And I reinstalled an epson scanner on Linux with their drivers a couple months back without issue. Give it another try.

---

### Post by bluexrider on 2011-12-10
> **green69 said:**
> Hi guys!

I need help to install my epson scanner (perfection 3170 photo). I'm running on the 10.04.

I've tried to follow the istruction from old threads:

* downloading the drivers (iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm) from: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
* converting them to deb (using alien)
* installing: xsane sane-utils libsane libsane-extra etc.

but when I try to run xsane it keep saying "no devices available"

Please can anybody help me?   :confused:

You should have downloaded iscan_2.10.0-1.tar.gz it can be used from the archive manager. Right click to open.

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

It has an install file contained within the compressed archive.

The Readme tells about "Image Scan! for Linux" contains the following parts:

  iscan            the program you use to scan your images
  libsane-epkowa    an improved driver for EPSON scanners
  libesmod        a proprietary module used by iscan

and 

It is required that the following packages are installed previous to 
the installation of Image Scan! for Linux.
 - sane-backends

---

### Post by bregale on 2011-12-11
thanks for the help i will keep you posted if it works ok

---

