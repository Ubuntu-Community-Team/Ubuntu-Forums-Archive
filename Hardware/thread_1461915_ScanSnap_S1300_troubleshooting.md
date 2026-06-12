---
title: "ScanSnap S1300 troubleshooting"
date: 2010-04-24
forum: Hardware
---

### Post by davidk01 on 2010-04-24
I recently bought a Fujitsu ScanSnap S1300 but I'm having a really hard time getting it to work. The device is not listed in the fujitsu backend so I used sane-find-scanner and added the required information to the configuration file but xsane still can't find the device. I appreciate any help you can provide to resolve this problem. Also, I need to use sudo sane-find-scanner to get the scanner to show up and I'm also wondering if there is a way to do this without sudo.

---

### Post by mannyweb.ca on 2010-08-25
^Bump because I am also in the same boat.   Can't get Scansnap S1300 to work.

Help me please.

---

### Post by Gnea on 2010-12-06
I'm having similar problems.  I located the firmware and copied it over to /usr/share/sane/epjitsu/ and modified /etc/sane.d/epjitsu.conf and nothing will see it still.  :(

---

### Post by SammichDinosaur on 2011-02-02
OK here is how I got it to work.

If you read /etc/sane.d/epjitsu.conf you see:

> # For scanners connected via USB on a known device (kernel driver):
#usb /dev/usb/scanner0

# For scanners connected via USB using vendor and device ids (libusb):
#usb VENDORID PRODUCTID

# NOTE: if you have to add your device here- please send the id and model
# to the author via email, so it can be included in next version. kitno455 at
# gmail dot com - with epjitsu in the subject line

# These devices require a firmware file in order to function, which must be
# extracted from the Fujitsu Windows driver. Presumably the Mac versions
# contain the firmware as well, but the author has no access such a machine.

# Firmware is installed in several different locations by the fujitsu software, 
# using the windows 'search' feature to look for '*.nal' is the easiest way to
# find them. They should be ~65K, and have the scanner's name as part of the
# file name. They are often inside a .cab file.

# Copy the file someplace sane can reach it. Then update the line below.
# NOTE: the firmware line must occur BEFORE the usb line for your scanner

# Fujitsu fi-60F
firmware /usr/share/sane/epjitsu/60f_0A00.nal
usb 0x04c5 0x10c7

# Fujitsu S300
firmware /usr/share/sane/epjitsu/300_0C00.nal
usb 0x04c5 0x1156

# Fujitsu S300M
firmware /usr/share/sane/epjitsu/300M_0C00.nal
usb 0x04c5 0x117f

# Fujitsu S1300
firmware /usr/share/sane/epjitsu/1300_0C26.nal
usb 0x04c5 0x11ed

So I went and found a windows machine. Installed the software. Got a copy of 1300_0c26.nal and put it in /usr/share/sane/epjitsu

And that seemed to make it work. It isn't fully functional, but works decently. I haven't figured out how to duplex scan yet though, which is a bummmer.

---

### Post by Ixtao on 2011-02-10
> **SammichDinosaur said:**
> OK here is how I got it to work.

If you read /etc/sane.d/epjitsu.conf you see:



So I went and found a windows machine. Installed the software. Got a copy of 1300_0c26.nal and put it in /usr/share/sane/epjitsu

And that seemed to make it work. It isn't fully functional, but works decently. I haven't figured out how to duplex scan yet though, which is a bummmer.
Thanks for that SammichDinosaur! I love to have a device like this, but I suppose features like

* scanning a double sided paper directly to an editable pdf file
* automatic resolution function
* intelligent auto colour detection

are only possible with the original software.. so I wonder if it works when you run the original software over wine?

---

### Post by ExactDiff on 2011-03-07
Hello, this sequence was very interested, and I have completed all the steps described by SammichDinosaur, **_but without success_**. I can not seem to recognize my ScanSnap S1300 by XSane.
The origin of my problems could it not come from the file version 1300_0c26.nal?
Could someone send me by mail 1300_0c26.nal its own file?
Thank you in advance for your help.

---

### Post by YetAnotherPhysicist on 2011-06-02
Hi.  

I see that sane now lists [support for the S1300]("http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=s1300&bus=any&v=&p=") as good using the epjitsu backend. Would somebody with this scanner please be able to describe what 'good' means in real terms?  For example, does it now work when connected or should I expect to modify config. files?  Also, when scanning with xsane, is there an option for front, back or duplex scanning?

To contribute some extra information on other scanners, I have been able to borrow an S1500 and that works just by connecting the USB cable and starting xsane (I'm running 64bit Ubuntu 9.10 and sane lists support for the S1500 as complete).  It can scan front, back or duplex.  It is however considerably bulkier and more expensive than the S1300; I like portability!  

Also, be warned that Canon's P-150 does not work easily with 64bit Ubuntu, despite advertising that a linux driver is available (32bit driver only).  If anyone does get stuck with one of these plastic bricks there is some advice [here]("http://ubuntuforums.org/showthread.php?t=1504656"), but it requires making binaries and doesn't seem to work for everyone.

Thanks for any replies.

---

### Post by chiplet on 2011-11-11
After scouring the internet, I was able to get the fujitsu snapscan S1300 running under Ubuntu 10.04 (64 bit) acceptably.   It does duplex, color, and a few different resolutions.  

There are 3 key parts that I had to do:

1)  install the S1300 software on a windows box and copy the file **300_0C00.nal** file from **c:\WINDOWS\SSDriver\S300\300_0C00.nal** to **/usr/share/sane/epjitsu/300_0C00.nal **on your linux box.  You may be able to find this driver online without installing the software.  Life would be easier if Fujitsu would make this available from their site.  I was unable to extract it right from the CAB files.

2) edit **/etc/sane.d/epjitsu.conf** so that it has the following:

[B]# Fujitsu S1300
firmware /usr/share/sane/epjitsu/300_0C26.nal
usb 0x04c5 0x11ed                      [/B]

3) run **simplescan** or **gscan2pdf** as **root**.  There is some sort of permission problem with the **saned** package which is why root users can see the scanner, but running as a regular user, the software can't find the device.  This is the second time I've seen this issue in a few years, and is no doubt a source of lost-time and frustration for many users.  Unfortunately, (in my case, at least), I don't change scanners too often, and forget the workaround each time I come across the problem.


Notes:

I tried the **1300_0C26.nal** file, but it kept giving a floating point exception.  It looks like the S300 and S1300 are the same device, just with a different ID, so this shouldn't be a problem.

Hopefully this saves someone some time and frustration.  Happy scanning.

---

### Post by brainjuice on 2012-02-11
@chiplet, I think there is a minor typo in step #2 above.

it should read (note the 00 in the file name):

> 
# Fujitsu S1300
firmware /usr/share/sane/epjitsu/300_0C**00**.nal
usb 0x04c5 0x11ed 


Otherwise your instructions were perfect.

One other positive note...on my 11.10 system I am not required to run simple-scan as root. So, in my book, all is good.

Bummer it takes such detailed troubleshooting to make it all work so I am indebted to all those that contributed to bring our collective knowledge to the place where it is possible to get this working so smoothly.

Thanks all!

---

### Post by kernst on 2012-07-09
It *seems* that the S1300 can be made to work on Lucid without (much) extra fiddling, if you add [this PPA]("https://launchpad.net/~robert-ancell/+archive/sane-backends"). Run the typical 
```
sudo apt-add-repository ppa:robert-ancell/sane-backends
sudo apt-get update && sudo apt-get upgrade

```
and all that, assuming you already had the Ubuntu SANE packages installed in the first place.

You will still, of course, have to copy the firmware file, **1300_0C26.nal**, to the appropriate location, as detailed in other posts above. I did not need to use&#8212;and indeed could not find&#8212;the S300 firmware file from my Mac where the full ScanSnap software package had been installed. On Mac OS X, the S1300's firmware files were located in /Applications/ScanSnap Manager.app/Contents/Resources/Firmware, FYI. The [FONT="Courier New"]/etc/sane.d/epjitsu.conf[/FONT] config file from the PPA version of [FONT="Courier New"]libsane[/FONT] already contained the required entry for the S1300.
[URL="http://www.sane-project.org/sane-backends.html#S-EPJITSU"]
This page[/URL] on sane-project.org mentions that the [FONT="Courier New"]epjitsu[/FONT] backend was "updated for SANE release 1.0.21," from which I conclude that the S1300 didn't really work prior to that release. Lucid (10.04) only provides version 1.0.20 of the backends (packages [FONT="Courier New"]libsane[/FONT] and [FONT="Courier New"]sane-utils[/FONT], basically) in the Canonical repos. The above PPA provides the latest stable version (1.0.22) [available from the SANE project]("http://www.sane-project.org/source.html") as of this writing, packaged for Lucid. You could theoretically get the same result from compiling from source if you didn't want to trust some random PPA.

Once updated [FONT="Courier New"]libsane[/FONT] and [FONT="Courier New"]sane-utils[/FONT] packages from the PPA were installed, the scanner pretty much worked for me. Anyway, as well as can be expected given that SANE's support for this scanner is only listed as [COLOR="#90B000"]Good[/COLOR], which is to say the front-panel scan button doesn't work and about half of the available SANE front-end GUIs either blow up with errors or produce garbled output**[COLOR="Red"][SIZE="2"]*[/SIZE][/COLOR]**. The S1300 [doesn't appear to be supported]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=614312") by [FONT="Courier New"]scanbuttond[/FONT] at the moment, in case you were wondering about that.

I *might* have needed to refer to [these instructions]("https://help.ubuntu.com/community/SettingScannerPermissions") for fixing the scanner permissions so I could run the frontend GUIs as a normal user instead of root. Or else the PPA packages updated [FONT="Courier New"]/lib/udev/rules.d/40-libsane.rules[/FONT] to include the S1300 for me. Can't recall.

**[COLOR="Red"][SIZE="2"]*[/SIZE][/COLOR]Tested satisfactorily with Skanlite.** Simple Scan did **not** work; it seemed to lose communication with the scanner a few centimeters in and threw up and error. Unfortunately, the gscan2pdf included with Lucid also didn't work, regardless of the backend selected. (Which is too bad, because gscan2pdf seems like a good tool.)

All in all, it's still a frustrating enough experience that I'm contemplating VirtualBox (with the [non-free extension pack]("https://www.virtualbox.org/wiki/Downloads")to enable USB pass-through) as an option, just to get this thing working reliably for scanning to Evernote.

---

### Post by netjay on 2012-10-26
I was able to get the fujitsu snapscan S1300 running under Mint 13 LTS (64 bit) acceptably.   It does duplex, color, and a few different resolutions. **_  ***NOTE*** Works without using root to access the scanner _**

There are 2 key parts that I had to do:

1) extract firmware file
You will still, of course, have to copy the firmware file, 1300_0C26.nal, to the appropriate location. /home/username/Documents/300_0C26.nal

2) edit **/etc/sane.d/epjitsu.conf** so that it has the following:

[B]# Fujitsu S1300
firmware /home/username/Documents/300_0C26.nal
usb 0x04c5 0x11ed                      

Good Luck!

---

### Post by noideawhatimdoingatall on 2013-02-22
Firstly - thanks! I've managed to get my very expensive (when I got one at least!) scanner to work. This is one of the only things holding me into Windows XP still. 

I have options to scan Front, Back and Duplex in Xsane - it **can** do front **or** back but when I select Duplex it's only doing one of them (the front I think)

Can anyone here recommend an app/option/tweek to get Duplex working?

Does Duplex work for you?

Thanks

---

### Post by Vurol on 2013-09-23
> **noideawhatimdoingatall said:**
> 
Can anyone here recommend an app/option/tweek to get Duplex working?


I'm very interested if you or anyone else has managed to make double sided/duplex scanning work? If so, how? Thanks!

EDIT: Found it! When using Simple Scan (default scanning gui for Ubuntu) you can choose from the dropdown menu 'Scan', for 'Text' instead of 'Photo'. You can scan in double side when in Text mode if you set your in preferences (Document > Preferences) Scan Side to Front and Back.

---

