---
title: "USB printer and scanner not working with Ubuntu 11.10"
date: 2011-10-18
forum: Hardware
---

### Post by tomdkat on 2011-10-18
I have a Brother HL-2040 Laser printer that I connect to via USB.  It worked fine with previous versions of Ubuntu, including 11.04 but after upgrading to 11.10, the printer can't be detected at all.

I also have a HP ScanJet 5200C scanner, also connected via USB, and when I connect it to the system, these messages appear in dmesg output:

```

[17225.596041] usb 3-2: new full speed USB device number 3 using ohci_hcd
[17225.776162] usb 3-2: device descriptor read/64, error -62
[17226.060046] usb 3-2: device descriptor read/64, error -62
[17226.340054] usb 3-2: new full speed USB device number 4 using ohci_hcd
[17226.520039] usb 3-2: device descriptor read/64, error -62
[17226.804043] usb 3-2: device descriptor read/64, error -62
[17227.084042] usb 3-2: new full speed USB device number 5 using ohci_hcd
[17227.492032] usb 3-2: device not accepting address 5, error -62
[17227.668037] usb 3-2: new full speed USB device number 6 using ohci_hcd
[17228.076027] usb 3-2: device not accepting address 6, error -62
[17228.076071] hub 3-0:1.0: unable to enumerate USB device on port 2

```
I've researched the "error -62" messages and found some threads on things to try, like using this command to change how the USB module detects USB devices:
```

 echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first

```
but that didn't help.

When I turn on my Brother printer (which I tend to leave off until I need it), NO output from dmesg even references the printer.  When I try to print to it, using the previous printer definition, the system tries to print and I get a "Waiting for printer to become available." message.

Any ideas on where to start troubleshooting this?  I'm running Ubuntu 11.10 64-bit.

Thanks!

Peace...

---

### Post by redmon on 2011-10-19
I have same problem with Brother MFC-8840D, both printer and scanner not detected.  Both worked in 11.04.  Printer detected and prints with parallel connection, but not USB.  With USB, *"Waiting for printer to become available."*

---

### Post by jedson3 on 2011-10-21
I am having the same problem with Brother MFC-495CW. I get this message: Failed to open device 'brother3:bus5;dev1' Invalid argument. I had it working on the previous version of Ubuntu.  I went to the brother page to re-do their driver installation procedure. When I did the check they said to do, I got this:
root@jh-Dimension-4700:/home/jh/Desktop# dpkg -l | grep Brother
ii  brscan-skey                            0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                                0.2.11-4                                   Brother Scanner Driver
ii  mfc495cwcupswrapper                    1.1.2-2                                    Brother CUPS Inkjet Printer Definitions
ii  mfc495cwlpr                            1.1.2-1                                    Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                          1.3-0ubuntu11                              CUPS/Foomatic driver for Brother P-touch label printers 

I'm not very expert on all this, but that looks like the driver is there. And it was brscan3 that they recommended for my printer/scanner.

---

### Post by djneve on 2011-10-22
> **redmon said:**
> I have same problem with Brother MFC-8840D, both printer and scanner not detected.  Both worked in 11.04.  Printer detected and prints with parallel connection, but not USB.  With USB, *"Waiting for printer to become available."*

I have almost exactly the same problem and it's a big problem for me.

I have an HP flatbed ScanJet 5590P, connected via USB, which worked just fine in previous versions of Ubuntu, but is not detected since upgrading to 11,10.  What on earth can I do?

A lsusb shows this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 03f0:1705 Hewlett-Packard ScanJet 5590
Bus 003 Device 002: ID 04f2:0865 Chicony Electronics Co., Ltd 
Bus 007 Device 002: ID 03f0:3e02 Hewlett-Packard PhotoSmart 7550
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 11b0:6108 ATECH FLASH TECHNOLOGY 
Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

which shows that it CAN be detected at device 002 but I can't use it, for some reason.

When I run sane-find-scanner -v I get:

Couldn't set configuration: could not set config 1: Device or resource busy
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1705 [hp scanjet scanner], chip=GL842?) at libusb:002:002

# Your USB scanner was (probably) detected. It may or may not be supported by SANE. Try scanimage -L and read the backend's manpage.

Any ideas for what next?  (Xsane doesn't see it)

Thanks!

Derrick

---

### Post by redmon on 2011-10-24
> **djneve said:**
> I have almost exactly the same problem and it's a big problem for me.

I have an HP flatbed ScanJet 5590P, connected via USB, which worked just fine in previous versions of Ubuntu, but is not detected since upgrading to 11,10.  What on earth can I do?

A lsusb shows this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 03f0:1705 Hewlett-Packard ScanJet 5590
Bus 003 Device 002: ID 04f2:0865 Chicony Electronics Co., Ltd 
Bus 007 Device 002: ID 03f0:3e02 Hewlett-Packard PhotoSmart 7550
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 11b0:6108 ATECH FLASH TECHNOLOGY 
Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

which shows that it CAN be detected at device 002 but I can't use it, for some reason.

When I run sane-find-scanner -v I get:

Couldn't set configuration: could not set config 1: Device or resource busy
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1705 [hp scanjet scanner], chip=GL842?) at libusb:002:002

# Your USB scanner was (probably) detected. It may or may not be supported by SANE. Try scanimage -L and read the backend's manpage.

Any ideas for what next?  (Xsane doesn't see it)

Thanks!

Derrick


Maybe this will help.  See #15 for solution.

[http://ubuntuforums.org/showthread.php?t=1862413&page=2](http://ubuntuforums.org/showthread.php?t=1862413&page=2)

---

### Post by tomdkat on 2011-11-06
> **redmon said:**
> Maybe this will help.  See #15 for solution.

[http://ubuntuforums.org/showthread.php?t=1862413&page=2](http://ubuntuforums.org/showthread.php?t=1862413&page=2)
Thanks for the link!

Peace...

---

### Post by tomdkat on 2011-12-12
Well, I finally got the system upgraded to the 3.0.0-14 kernel and now the printer works.  :)

Peace...

---

### Post by tomdkat on 2012-01-25
Once I connected my HP ScanJet 5200c to my computer using a GOOD USB cable, I was able to get it working as well.

Woo-Hoo!  :)

Peace...

---

### Post by juventus on 2012-09-11
Ubuntu version from /boot kernel is 3-2-0-30

HP Scanjet 5200C using USB is not found in XSane 0.998

Scanjet is the only USB device plugged in .  lsusb shows :-
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | grep usb shows :-
[ 5098.984034] usb 3-2: new full-speed USB device number 2 using ohci_hcd
[ 5099.568027] usb 3-2: device not accepting address 2, error -62

Where would you suggest I go from here?

Thanks.

---

### Post by juventus on 2012-09-11
Want to move away from Windows XP to LINUX, so the following is annoying,

booted into windows XP and then:  Hello! Found new hardware HP Scanjet 5200C! Lets install it and then we can start scanning? and pushed the button and it worked. Damn Windows, but I want Linux to work for me.

---

### Post by juventus on 2012-09-12
The trick was to plug in the USB AFTER linux booted and the scanner had fully warmed up which seems to take ages to do (it has a cold fluorescent lamp)

Scans fine now under Ubuntu and better options than Win XP. All is forgiven Linux. ):P

---

### Post by tomdkat on 2012-09-25
Great!  Glad you got it working!

Peace...

---

### Post by KutWrite on 2012-11-04
In my case, just the scanner is a problem.

I have a Toshiba Satellite A650 laptop (Intel I5). All worked fine in Natty, 11.04.  Last month (Oct '12) I upgraded to Oneiric 11.10 and after some diddling, got everything going.  I've been doing updates weekly.

A week ago, the printer stopped being "seen."  I reinstalled CUPS and the HP driver and now have two drivers, but one works and I'm stickin' with that.

I've changed nothing else except updates, but a few days ago, the Scanner stopped being seen as connected. 

I normally use Simple Scan.  I tried XSANE, same problem.  lsusb does see the scanner:

Bus 003 Device 004: 
ID 04b8:0118 Seiko Epson Corp. Perfection 4180 (GF-F600)

I rebooted multiple times.  No change. I tried uninstalling and reinstalling Simple Scan. No change.

The laptop is dual boot, and Windows 7 operates the scanner through the same USB hub etc.

I'd appreciate all ideas and suggestions!

Dan

PS I tried unplugging the USB as above, no change.  I also checked the kernel: it's 
3.0.0-26-generic-pae.

---

### Post by pdc on 2012-11-04
can I suggest you install the Epson scanner drivers that they supply 

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

.........I started at the core page .....

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and typed in 4180 .........and got the top search result

it comes down as a .tar.gz file [COLOR="Green"]**iscan_2.10.0-1.tar.gz**[/COLOR]

....if you save to your Downloads directory.....

I would envisage the commands

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]tar -zxvf iscan_2.10.0-1.tar.gz[/COLOR]

> [COLOR="Red"]cd iscan_2.10.0-1[/COLOR]

> [COLOR="Red"]./configure[/COLOR]

> [COLOR="Red"]make[/COLOR]

> [COLOR="Red"]sudo make install[/COLOR]

I get that from the Epson instructions in their README

> 4-2  Installing a tar file

Execute the following command to complete the installation.

  # tar -zxvf iscan-${version}-${release}.tar.gz
  # cd iscan-${version}
  # ./configure
  # make
  # make install

Note that the installation of Image Scan! for Linux from tar requires 
that sane has been installed from tar as well.

---

### Post by KutWrite on 2012-11-04
I tried SANE before, and the output said to use XSANE instead, which I did.

I will try reinstalling as you so carefully outlined.  But I'm wondering why it worked before and not now.

I'll let you know how it goes.

Thanks!

OK... It worked at first.  When I did the "tar... "command a whole bunch of iscan things happened.  When I got to "[COLOR=Red]cd iscan_2.10.0-1[/COLOR]"  There is no such directory, at least not visible from Downloads.  I'll look further.

OK... there IS a folder called iscan_2.10.0  without the hyphen and 1 at the end...

OK... Now I'm at a standstill.  I ran the ./configure command. It ended with this:

"checking for GTK... no
checking for GTK... configure: error: Package requirements (gtk+) were not met:

No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

I assume this has something to do with Gnome, which is what I run under (classic, no animation)

I tried "make" anyway, and got this:

"daniel@daniel-toshiba:~/Downloads/iscan-2.10.0$ make
make: *** No targets specified and no makefile found.  Stop."

Any further instructions?  I hope so!

---

### Post by pdc on 2012-11-04
> No package 'gtk+' found

........to me, that means it is likely you do not have gtk installed;

if you google on 

> No package 'gtk+' found

you get things like this

[http://www.khattam.info/solved-no-package-gtk-3-0-found-2011-06-26.html](http://www.khattam.info/solved-no-package-gtk-3-0-found-2011-06-26.html)

.....looks like adding

libgtk-3-0 and libgtk-3-dev would help.........run the commands again after installing these two packages......


.......when you couldn't find the iscan directory, if you use the command

> [COLOR="Red"]ls[/COLOR] .....inside any directory.....it [COLOR="Green"]LISTS[/COLOR] what is there so you can identify the name of the directory you are looking for ..

........also if you type the first two or three letters of a word such as iscan


> [COLOR="Red"]cd isc[/COLOR]     ........... and then hit the [COLOR="Red"]**TAB**[/COLOR] key, 


...................the system should type out the rest of what you want..if there is only one directory starting with ........eg ...........[COLOR="Red"]isc[/COLOR]

---

### Post by KutWrite on 2012-11-04
Got the same error again...

Thanks, PDC, for the help. You've been very quick and patient, explaining these things.  

The problem I have is, I seem to fall down newer rabbit holes each time I try to fix something, even after 1 1/2 years of "trying out" Linux.

I did try using the Ubuntu Software Center to find GTK.  All I found were apps which run UNDER GTK, which just made me want to walk away for a bit.

Here's what happened:

I installed the Dev pkg per the post  you linked:

[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get install**[/COLOR] libgtk-[COLOR=#000000]3[/COLOR]-dev

I then looked for libgtk using Ubuntu Software center & it said I already had it:

"Installed - GTK+ is a multi-platform toolkit for creating graphical user interfaces. Offering a complete set of widgets, GTK+ is suitable for projects ranging from small one-off tools to complete application suites.
This package contains the shared libraries.  
Version libgtk-3-0 3.2.0-0ubuntu6"

I ran ./config and the same GTK+ error occurred as before.

I did a Google search and saw some admonishments as to using non-standard packages, but so far, not what to do if you have the package and something can't find it.  Perhaps a clue is in the config files mentioned in the error message, but I don't know where those are.

I searched for an hour or so, but seem to have hit another dead end.

 I'd again greatly appreciate your help.

- - - - - 

A few hours later:

I found and tried this suggestion:

I used

locate pkgconfig

to find that path. Well, there were two, but this one looked more like
the example in the post I saw, so I entered:

PKG_CONFIG_PATH=/usr/lib/pkgconfig
export PKG_CONFIG_PATH

But that didn't change anything.  I don't know why it's looking for GTK+ instead of GTK3.

Later... I found a folder at /usr/include/gtk-3.0.  there were a bunch of similarly named GTK folders 
which seem linked to GUIs, Python, etc.  

Do I need to point something to that?

There was also a folder named GTK-2.0 and similarly named ones, as above.

---

### Post by KutWrite on 2012-11-05
This AM I tried a few more things:

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0118 ) at libusb:003:007
found USB scanner (vendor=0x8086, product=0x0186) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

I'm not sure why it found two scanners I only have one. It matches the ID of the first found device, ending in 0118.   The scanner was powered on but my other USB devices were powered off (e.g. printer).

Then I tried:

$ sudo scanimage -L
[sudo] password for daniel: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Some of these posts go back to 2005.  I guess this is a long-standing problem.

---

### Post by pdc on 2012-11-05
how about one more go at installing iscan .......

if we use alien, to convert rpm packages to .deb packages

but first have a read at this Mint post..Mint is derived from Ubuntu..

....I don't know if it is relevant .......

[http://community.linuxmint.com/hardware/view/1450](http://community.linuxmint.com/hardware/view/1450)

as advised from here

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

> [COLOR="Red"]sudo apt-get install alien[/COLOR]

get the Epson rpm package from here 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15830&DSCCHK=405295b29a97b4e570a57ce69df9097305c1a464](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15830&DSCCHK=405295b29a97b4e570a57ce69df9097305c1a464)

download into your Downloads directory; save

so first command is 

> [COLOR="Red"]cd Downloads[/COLOR]..hit enter.....

check the package is there ......ask the directory to list its contents.....

> [COLOR="Red"]ls[/COLOR]

and convert and install with alien

> [COLOR="Red"]sudo alien -i iscan-2.10.0-1.i386.rpm[/COLOR]

and let's install the plugin (*making sure we are still* [COLOR="SeaGreen"]INSIDE[/COLOR] *the Downloads directory*........)

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15847&DSCCHK=566a22c9c5f08f6d0a7470d93ebcd8cdc0e141f1](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15847&DSCCHK=566a22c9c5f08f6d0a7470d93ebcd8cdc0e141f1)

> [COLOR="Red"]sudo alien -i iscan-plugin-gt-f600-1.0.0-1.i386.rpm[/COLOR]

... I wonder if all that gets you anywhere........

to get it running..............

> [COLOR="Red"]iscan[/COLOR]

and apparently it should open from within GIMP as well..............

---

### Post by KutWrite on 2012-11-06
Thanks PDC... Here goes.  I'll enter events step by step, as I don't think I can do this in one go.

 I looked at the Mint thread.  It was for Isadora; they are now on Maya. It says the Epson won't work with SimpleScan, but I've been happily using SimpleScan until 11.10 (oh, how much trouble I've had since I left 11.04).

OK here goes the rest...

1. I already had installed Alien using the Ubuntu Software center. 

2. RPM files... one mental bookmark: You linked to gcc 3.2/3.3.   I have gcc 4.6.1. So I looked for a higher version.  I found one and may later try the ones for gcc 3.4 and later. But they're from Avasys, not Epson, so I'll hold off  unless the file you  linked doesn't work.

Well... I cut & pasted your Alien command and checked; it was the same as the rpm file name I downloaded.  But... it didn't work. 

 I got a whole bunch of error messages like this:

error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/daniel/.rpmdb
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `iscan-2.10.0': File exists
unable to mkdir iscan-2.10.0:  at /usr/share/perl5/Alien/Package.pm line 257.

Should I try again, using the "--scripts" parameter?  I'm nervous to try it w/o an OK from someone who knows what's what.

---

### Post by pdc on 2012-11-06
crikey; .........better we rest on it and review all that has gone before..


[http://manpages.ubuntu.com/manpages/intrepid/man5/sane-epkowa.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/sane-epkowa.5.html)

have you got the epkowa backend installed............. seems like sane might work with that ..

......if you try running xsane from a terminal, I sensed you get error messages (that could be helpful)

> [COLOR="Red"]xsane[/COLOR]

---

### Post by KutWrite on 2012-11-06
I ran XSane before posting this. Got the same error: No scanner detected.

That's why I did the lsusb. If it hadn't shown there<, I probably would've given up.

Not sure about Epkowa or what a back-end is.... drivers?

I think if we got Alien to work it'd solve the problem, my friend. 
But then, what do I know? I'm the one who's asking for help?

I think you can see why I'm so frustrated with Ubuntu right now. I'm not the only one who regrets "upgrading" from 11.04, which worked just fine in all respects.  I hear (read) even more complaints about 12.04.

I'll take a deep breath and go read the link you provided.

OK, this is later.  It wasn't much help. Seemed to apply only if one uses iScan, which wasn't necessary for
me before. SimpleScan worked fine.

---

### Post by KutWrite on 2012-11-08
(sound of crickets)

I thought of upgrading to 12.04. But I see many complaints there, too.

Do I give up & go to Mac?

---

### Post by kurt18947 on 2012-11-09
I'm using Brother MFD's not Epson but 12.04 is rock solid for me.  12.10 on the other hand, not so much.

---

### Post by KutWrite on 2012-11-09
Sad that it seems to get worse and worse.

And my "mentor" above seems to have given up.

Mac is starting to look better and better.

Update 11/11/12
I saw something on YouTube about this, but it was for an earlier version of ubuntu.
The fix required pkgs in .deb format. Avasys and Epson only have rpm format
files. So, I'm still stuck.

So much for [solved].  Wish I could un-solve this thread!

I may wrestle with it for a while, but if it's this hard to fix things that should just work, and helpers
give up on us. What are we non-experts to do?  

Back to Mac?

---

### Post by KutWrite on 2012-11-12
OK... 

I haven't quite given up, 'cause I think I'm close.

I can unpack the rpm drivers and programs. I just don't know what to do with them after that. 

./configure doesn't do anything.

/make doesn't do anything.

Thoughts or suggestions?

Thanks,
Dan

---

### Post by kurt18947 on 2012-11-12
> **KutWrite said:**
> OK... 

I haven't quite given up, 'cause I think I'm close.

I can unpack the rpm drivers and programs. I just don't know what to do with them after that. 

./configure doesn't do anything.

/make doesn't do anything.

Thoughts or suggestions?

Thanks,
Dan

To use rpm packages in Ubuntu or other Debian based distros, you must first convert .rpm to .deb.  The usual method is to use alien.  I haven't had to do it but Google should be helpful.  Be aware that some scanner packages installed on 64 bit systems have 'issues'.  It happens with Brother (which is how I became aware of it) but I've seen it mentioned with other vendors as well.  Brother has both .rpm & .deb packages.  I suspect they create .rpm packages then convert to .deb using alien.  I poked around and found indications that other .rpm scanner packages converted to .deb packages have this issue.  Here is the Brother fix.  

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

I believe  you're working with Epson but I suspect they use similar if not the same files.  Just make sure the required files end up in the correct folder.

---

### Post by KutWrite on 2012-11-12
Thanks.

If you look above in this thread, you might see that I'm already past that point. Alien doesn't work on my 11.10, and I've unpacked the rpm packages.

Plus I don't know where to put them, i.e. the "correct folders."  

Thanks anyway for your time.

---

### Post by kurt18947 on 2012-11-13
> **KutWrite said:**
> Thanks.

If you look above in this thread, you might see that I'm already past that point. Alien doesn't work on my 11.10, and I've unpacked the rpm packages.

Plus I don't know where to put them, i.e. the "correct folders."  

Thanks anyway for your time.

Sorry, didn't see you'd tried alien.  AFAIK, if you can't get alien to work, you're out of luck, rpm packages will not work on Debian based distros.  Perhaps try a distro that uses rpm packages?  Fedora, PCLinuxOS and Open SuSe come to mind, I'm sure there are others.  The other possibility would be to have someone convert the .rpm packages to .deb for you.  I've never done this so don't know about possible pitfalls.

---

### Post by KutWrite on 2012-11-13
OK Kurt,

I think that's an important bit of info: That rpm/Alien won't work under Debian. No one has mentioned that!

I don't think I'll change distros at this point; I'm so disappointed in Linux.

I'll just go back to Mac OSX... which I guess is a whole 'nother "distro!"  But it's known, does what I want, and at least up to now, I haven't had to invest as much of my own time & effort to get simple things going. Or, not going as in this case!

Thanks again, I do appreciate your, pdc's and others' time in trying to help.

Dan
:guitar:

---

### Post by kurt18947 on 2012-11-15
Do what you need to do, I'd do the same.  I was curious about alien not working so I installed it on 12.10 gnome remix 64 bit.  I then downloaded an iscan .rpm package mentioned above and tried to run alien.  The version in the Ubuntu repos appears to only run on 32 bit systems.  Oops.  I did "man alien", there was nothing about anything to add to allow it to run on 64 bit systems.  I'll do a little more research in the future.  Right now I have to fix SWMBO's squirrel feeder.  The little bushy tailed ingrates pushed it on the ground and shattered it :P .

---

### Post by KutWrite on 2012-11-15
Hi Kurt,
 
Thanks for the research. 
 
I installed 11.04 as 32 bit. I didn't consciously change that for 11.10, but who knows, eh?
 
I still have the Ubuntu system installed in my laptop, so if you find a solution, I'd still be interested.
 
In the meantime, I bought a Mac mini. The scanner works great with it!
 
Dan

---

