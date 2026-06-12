---
title: "Epson Scanner"
date: 2011-12-20
forum: Hardware
---

### Post by bordercot on 2011-12-20
Hi, I'm new to Ubuntu (I've installed version 11.10 and am working my way round trying to get used to it), but am struggling to get my Epson 3490 scanner up and running. I have looked at other threads on this subject but cannot follow their terminology. My problem is this, how do you install a downloaded file in Ubuntu ? From the AVASYS website I've downloaded the.rpm package "iscan-2.10.0-1.c2.i386.rpm" into my download folder and extracted the relevant files. Where do I go from here ? How do I now install these files. Would appreciate any help for a Ubuntu newbie.

---

### Post by BC59 on 2011-12-20
The Epson Scanners are a long sad story for Linux.

To install this package.
First install the package **alien** from Ubuntu Software Center.
Then open it and convert the downloaded package to .deb.

First copy the .rpm package to /home and execute:

```
alien iscan-2.10.0-1.c2.i386.rpm iscan-2.10.0-1.c2.i386.deb generated
```

then run:

```
sudo dpkg -i iscan-2.10.0-1.c2.i386.deb
```

then you have to edit the file, so run:

```
sudo gedit /etc/sane.d/dll.conf
```

change epson to #epson and add epkowa

Search for your scanner with the command:

```
sane-find-scanner -q
``` you need to find a USB scanner

You have to find something like this, 

> found USB scanner (vendor=[COLOR="blue"]0x04b8[/COLOR] [Language Error], product=[COLOR="blue"]0x083f[/COLOR]

just change the numbers with yours.

Then edit:

```
sudo gedit /etc/sane.d/epkowa.conf
```

# comment all usb entries and add this > usb [COLOR="Blue"]0x04b8 0x083f[/COLOR]

save and execute xsane

---

### Post by bluexrider on 2011-12-20
@BC59

This should be saved as a tutorial for future Epson issues. Good support

---

### Post by bordercot on 2011-12-21
@BC59
Thanks for the reply. Have installed "alien" from the Software Centre but, as a Ubuntu newbie,  I haven't a clue on how to open it !!! Could you please advise on how to open the program (or indeed any other program). I know this may sound ridiculous but would welcome your help till I get used to Ubuntu.

---

### Post by BC59 on 2011-12-21
You don't have to open alien. Just follow my steps on post#2. 

Means open a terminal with CTRL+ALT+T and paste the first command

```
alien iscan-2.10.0-1.c2.i386.rpm iscan-2.10.0-1.c2.i386.deb generated
```

Paste with right click or SHIFT+CTRL+V

---

### Post by bordercot on 2011-12-21
Have opened the terminal and pasted the first command and pressed enter, password requested which I entered and then the message can't find file  iscan-2.10.0-1.c2.i386.rpm, which has stopped me in my tracks. Why can't it find the file which is located in the downloads folder ?  Where do I go from here ?

---

### Post by BC59 on 2011-12-21
> **bordercot said:**
> Have opened the terminal and pasted the first command and pressed enter, password requested which I entered and then the message can't find file  iscan-2.10.0-1.c2.i386.rpm, which has stopped me in my tracks. Why can't it find the file which is located in the downloads folder ?  Where do I go from here ?

mmm ok move the downloaded file iscan-2.10.0-1.c2.i386.rpm to home directory and start again.

---

### Post by bordercot on 2011-12-22
Have moved file to home folder but still get can't find file message. Losing the will to live here ! Will have to come back to this after the holidays and start again by deleting iscan file and redownload another copy and start again. Have a good Christmas !

---

### Post by BC59 on 2011-12-22
It's not that difficult. When you have time we are here to help you.

---

### Post by bordercot on 2011-12-27
Thanks for your reply. Have had another go at your suggestions to install my Epson scanner but still get message can't find file, even when I moved it to /home folder as suggested. Clearly I am missing something along the way. If you have the patience I would welcome any suggestions you may have to get this thread going again.

---

### Post by Marller on 2011-12-28
On the avasys-website there are deb-packages, even for ubuntu-11.10, at least it claims they are. Are those buggy or something?

It seems everything gets installed but no working scanner.
No program can access the scanner (not even root).
Now i included this line in /lib/udev/rules.d/40-iscan.rules
```
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0131", MODE="664", GROUP="scanner"
```
Scanner is now in group scanner upon plug in but it is still "busy" (busy with nothing, ha)
Anyone an idea?

---

### Post by bordercot on 2012-01-03
Hi BC59, Back again after the holidays to try and install my Epson scanner again.Have gone back to #5 above and pasted alien iscan-2.10.0-1.c2.i386.rpm iscan-2.10.0-1.c2.i386.deb generated into a terminal and, after pressing Enter I get the message " must run as root to convert to deb format (or you may run as fakeroot)". Since I thought I was the root person why do I get this message ? How do I run as root ? Grateful for any reply.

---

### Post by Marller on 2012-01-03
Putting "sudo" before it should do the trick.

---

### Post by bordercot on 2012-01-05
Hi again, Since I'm making zero progress on a two  minute job I decided to go back to step 1 and start again. With the .rpm file in the home folder I copied and pasted the first line of code (with the sudo prefix) into a terminal window only to receive the following :- Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
iscan_2.10.0-2_i386.deb generated
File "iscan-2.10.0-1.c2.i386.deb" not found.
Since I am a Ubuntu newbie I've not yet learnt either how to interpret the message or where to go from here. Can anybody help and explain why even the first line of code is kicked back with an error message ?

---

### Post by pointym5 on 2012-01-07
I've got iscan installed, and I updated the sane.d files as directed in this thread, but xsane doesn't work. It finds the scanner, after a long long wait, but eventually xsane just dies (sometimes with an error dialog, sometimes not).

The odd thing is that under previous releases of the OS (that is, previous to oneiric), the scanner just worked without any sort of weird installation of additional software of any kind.  It just worked, and that's been the case for years.

(Mine's a Perfection 2450.)

---

### Post by tock on 2012-01-09
I got the same results following these instructions for v300 scanner. I re-installed using the .deb files already on the site. I went back and removed the config changes except for adding epkowa to sane.d and all started working.

---

### Post by tock on 2012-01-09
Your file name looks to be wrong.  You should use iscan_2.10.0-2_i386.deb.  Or better yet go back and download the .deb files instead of the rpm files.  Then make sure you pay attention to where the files are being downloaded to.  Normally it is /home/Downloads.  If your files are in the Downloads folder then:

> cd ./Downloads

> sudo dpkg -i <Name of first file you downloaded>

> sudo dpkg -i <Name of second file you downloaded>

Then add epkowa to /etc/sane.d/dll.conf as previously discussed

---

