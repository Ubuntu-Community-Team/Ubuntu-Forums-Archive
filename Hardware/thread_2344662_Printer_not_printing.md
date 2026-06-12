---
title: "Printer not printing"
date: 2016-11-27
forum: Hardware
---

### Post by everick on 2016-11-27
I have a Samsung SCX3405FW Laser printer, I downloaded  the Linux drivers and tried to install the. No success. I was told to install something called package Installer, I did that and then tried to install the drivers. No success. All that appeared on the screen was a lot of cryptic text which i cant understand.
Secondly my sound doesn't work, despite everything (cables etc.) are connected correctly (as was done previously in Windows).

Can you please help. 
The guy who installed linux for me installed V14, but during one of the software updates, I accenditally upgraded to V16.04.
He suggested that I go to a Techmint site and download 7 things to do after installing linux. That didn't help at all.

---

### Post by ajgreeny on 2016-11-27
We need to know a lot more than you have told us to be able to help you.

What drivers did you download and from where?
It would help us to know exactly what the cryptic output was that you saw when you tried to install the driver.

Your sound problem is best dealt with in a separate thread, but we again need to know a lot more about your system hardware and software version.

You might also tell us what of the things recommended at the techmint site that you actually did after installing Ubuntu; a few of those things are what I would do because I want to use those applications (vlc, audacity, for example) but certainly not all of them.  However, I do not see that any of that would have affected your sound output, so I suspect an incorrect configuration; so open up **Sound settings** from the volume icon in the panel and see if that shows anything for a start.

---

### Post by timfinley on 2016-11-27
I did a quick google search of your printer model and saw that it has the capability of connecting to your home network. That's usually a great thing since, at least from my experience, network controlled printers play well with Linux distros. 

Although, I'm going to reiterate what ajgreeny has said already. We need more information to help with the fix. Links to the guides you have used already is a start. That error message would be a huge help. If I got this right, the package installer should have been installed by default. 

Often times, the drivers you might find on the Package Installer (or through apt) don't work as well as the proprietary driver supplied by the manufacturer. 

As for your sound issue, it is likely an easy fix. I've never had issues with sound that weren't a quick and easy fix. Simply giving us the make and model of your hardware might help us solve your issue. But, again as ajgreeny has stated already, that's a question you should pose on a different thread within this forum.

Finally, a note on peripherals: Finding the right equipment can be a little tricky when using Linux. It used to be much more difficult than it is today, but some research is still needed before buying new things for your Linux box. Brother Printer, for example, have given me massive headaches in the past, despite the manufacturer providing Ubuntu and other distro specific drivers. The term "Plug and Play" must be taken with a grain of salt when you're using Linux.

---

### Post by everick on 2016-11-27
here is my system
Memory: 7.7GProcessor Intel Core I3-3220CPU @3.30GHZ X4
Graphics:Intel Ivybridge  Desktop
OS: 64 bit
Ubuntu:16.04

I have a;ready opened the sound settings and all seems to be well configured.

At the Techmint site,  said to do 7 things. I tried to install the synoptic Package Manager. I did this because I had previously D/L an XIPHOS Bible and it asked for an package installer when I tried to install it.

I went to the Samsung support site and downloaded the drivers for my printer samsung Scx3405FW linux version ( I thought I had made that clear).
When I tried to install the driver is when I got the long lot of cryptic message. i cant remember all of that from here, and the result is it didn't  install the driver from the setup file. If I knew how to copy the desktop at that time I would capture it and post it.

---

### Post by kurt18947 on 2016-11-27
You downloaded the driver from here?

[http://www.samsung.com/us/support/downloads](http://www.samsung.com/us/support/downloads)

I have a different model Samsung monochrome multifunction machine and downloaded the driver from the above site. The download, once extracted seem to be bash scripts. I had a problem with the install.sh script, it would run but wouldn't enable the printer and scanner. I had to run install-printer.sh and install-scanner.sh separately.

---

### Post by everick on 2016-11-28
Thanks. 

I wasn't sure so I D/L the driver from the site that you mentioned. And lo and behold it is the same driver. The version numbers match.
Can you please give me specific details on how to install the printer-sh & scanner-ph ?
I dislike and hate having to take my private stuff to the office to print it. If I can just print and scan from home, then I can take my time to learn linux at my own pace.


> **kurt18947 said:**
> You downloaded the driver from here?

[http://www.samsung.com/us/support/downloads](http://www.samsung.com/us/support/downloads)

I have a different model Samsung monochrome multifunction machine and downloaded the driver from the above site. The download, once extracted seem to be bash scripts. I had a problem with the install.sh script, it would run but wouldn't enable the printer and scanner. I had to run install-printer.sh and install-scanner.sh separately.

---

### Post by SeijiSensei on 2016-11-28
First, if it's supports a network connection, I'd take that approach.  Give the machine a static IP address so you'll know how to reach it in the future.

Next, try opening a browser on any Ubuntu machine on the network and navigate to [http://localhost:631/](http://localhost:631/).  Follow the steps to add a printer and see whether it is automatically discovered.

---

### Post by oldrocker99 on 2016-11-28
Your printer likely has a setting where it prints network information, and you can find the IP address of the printer there, something like 10.0.0.161. Then, in the printer settings, under Device URI, make it like this:
```
lpd://0.0.0.0/Binary_P1
```
Obviously, you replace the 0.0.0.0 with the printer's actual IP address. This worked like a charm on my Brother HL3170CDW.

---

### Post by slickymaster on 2016-11-28
*Thread moved to **Hardware**.*

---

### Post by SeijiSensei on 2016-11-29
> **oldrocker99 said:**
> This worked like a charm on my Brother HL3170CDW.
I also have an HL3170CDW, and it was discovered automatically using the method I described above.

---

### Post by kurt18947 on 2016-12-01
> **everick said:**
> Thanks. 

I wasn't sure so I D/L the driver from the site that you mentioned. And lo and behold it is the same driver. The version numbers match.
Can you please give me specific details on how to install the printer-sh & scanner-ph ?
I dislike and hate having to take my private stuff to the office to print it. If I can just print and scan from home, then I can take my time to learn linux at my own pace.

I will try. I don't know how experienced you are with the command line so I'll try to make this simple. Please don't be offended if you're experienced. The way I've installed is to insure the downloaded file is in an account with SUDO privileges, usually the first account name created at install. Extracting the compressed file creates a folder named "uld". Make sure you know where it is. Open a terminal and CD to that folder, if the folder is on your desktop the command might look something like

```
cd Desktop
``` then 

```
cd ULD
```

If you were to run the command "dir" you should see something like this:

```

i386            install.sh          uninstall-scanner.sh

install-printer.sh  noarch          uninstall.sh

install-scanner.sh  uninstall-printer.sh  x86_64

```

Now you should be able to run these commands:

```
sudo bash install-printer.sh
```

You'll be prompted for the account password. Enter it, press the 'enter' key and the script should run. Once complete

```

sudo bash install-scanner.sh

```

At this point the printer and scanner should work. There are also uninstall scripts for printer & scanner. You'd need to retain that folder if you want future access to the uninstall scripts.

One issue I've noticed if copying this script via a flash drive, it may not retain its "execute" permission setting. Being primarily a GUI guy I navigate to the "uld" folder using the preferred file manager and click on the "install-printer.sh" file then right-click "properties" then "permissions". Be sure the "execute" entry is checked. Then same for "install-scanner"

I think running "install.sh" should install both printer & scanner. I tried it once and the script seemed to run but didn't install, I'm not sure why. Running the printer and scanner scripts separately seemed to address the problem. I hope this helps you.

---

