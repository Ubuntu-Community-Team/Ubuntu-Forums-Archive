---
title: "Lexmark X5150 Printer, Detected and Driver Installed, but won't Print"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by mayamaniac on 2006-06-28
Just installed Ubuntu, I went to add a new printer, and it does see my Lexmark X5150. It recommended I used the Lexmark X125 driver. Everything seems well because it shows the Lexmark printer was "Ready". I did a "Printe  a Test Page" and immediately in the printer job status window, it says: 
> Test Page    1    Owner   150.0K    Stopped: job-stopped

I looked in the Lexmark printer property window under General and it says:
> Status: Ready: /usr/lib/cups/filter/foomatic-rip failed

I saw another [thread]("http://www.ubuntuforums.org/showthread.php?t=111174&highlight=lexmark+x5150") where someone says to use the Lexmark Z55 driver. I'm trying to follow the [instruction]("http://www.ubuntuforums.org/archive/index.php/t-83456.html") to install that driver, but got stuck where it says to do the command:
```
sudo alien -t z600cups-1.0-1.i386.rpm
```

I get "sudo: alien: command not found". Does anyone what is the problem and how can I fix it. Maybe help me install the Z55 driver first and see if that work. I have the driver file "lexmarkz55-CUPS-1.0-1.gz.sh", what do I do with it?

---

### Post by Cygnus1 on 2006-06-28
Same problem with a Lexmark x73. Printing does seem a problem with Dapper.

---

### Post by patrickfromspain on 2006-06-28
sudo apt-get install alien to covert the package.

Or sudo sh filename.sh or maybe sudo ./filename.sh

---

### Post by patrickfromspain on 2006-06-28
[QUOTE=Cygnus1]Same problem with a Lexmark x73. Printing does seem a problem with Dapper.[/QUOTE]

Yeah.. printing is a problem. But not dapper's one. Not even linux' one. The problems is only from the vendors.. if lexmark refuses to offer a proper linux support, there's not much one can do.

Anyway.. your x73 seems to be supported, with the same driver as the z42. Which driver have you tried, also x125??

---

### Post by Cygnus1 on 2006-06-28
[QUOTE=patrickfromspain]Yeah.. printing is a problem. But not dapper's one. Not even linux' one. The problems is only from the vendors.. if lexmark refuses to offer a proper linux support, there's not much one can do.[/QUOTE]

I can appreciate that...Next time I wont buy a lexmark:mad: 

[QUOTE=patrickfromspain]
Anyway.. your x73 seems to be supported, with the same driver as the z42. Which driver have you tried, also x125??[/QUOTE]

Tried both x73 & x125, produces the same result.:(

---

### Post by patrickfromspain on 2006-06-28
maybe you could try to install cups 1.2.1, and see if it works:

[http://www.cups.org/software.php?VERSION=1.2.1&FILE=cups/1.2.1/cups-1.2.1-source.tar.bz2](http://www.cups.org/software.php?VERSION=1.2.1&FILE=cups/1.2.1/cups-1.2.1-source.tar.bz2)

It's very easy, just sudo ./configure, sudo make and sudo make install. If it doesn't work, just reinstall cups through synaptic.

---

### Post by chrism7 on 2006-06-29
[QUOTE=patrickfromspain]Anyway.. your x73 seems to be supported, with the same driver as the z42. Which driver have you tried, also x125??[/QUOTE]

I had no problems with my x73 using z42 in breezy, but haven't had success yet in Dapper - haven't been trying long admittedly.  I'll give cups 1.2.1 a try as you suggested.
Chris

---

### Post by mayamaniac on 2006-06-29
[QUOTE=patrickfromspain]sudo apt-get install alien to covert the package.

Or sudo sh filename.sh or maybe sudo ./filename.sh[/QUOTE]
Thank you for the command. That is actually in the installation instruction of the driver at the beginning, I don't know how I missed it. It was late, maybe I was tired. 8-[ 

Anyway, I got the z55 driver installed and the printer now works. Thanks for the help.

Now to get all the media codecs installed, I can't even play an MP3 at the moment, which is pretty lame, but I'm learning. :wink:

---

### Post by patrickfromspain on 2006-06-29
could you repeat??

X5150 now prints in linux?? I have one of those lying around. I changed because ink was way to expensive (75&#8364; both inks... for less than the half I get a new lexmark printer and the X5150 cost me 90&#8364;) and bought a canon (99&#8364; ip3000 with 4 ink cartriges..not bad, and less expensive). Will try If I get it to work :)

EDIT: BTW, how does it work? good quality? medium? only black and white?

EDIT2: for mp3.. automatix ;)

---

### Post by bernd on 2006-09-10
Hi, 
i have the same problem with Lexmark x73 and Dapper (worked fine in breezy). 
Installing cups 1.2.1 didnt work for me.
Has somebody fixed this ?

---

### Post by therawski on 2008-07-23
I'm new to linux (that's why I'm using ubuntu), please bear with me, I am trying to set up my Lexmark X5150 to print but when I get stuck in the instructions here:

therawski@ubuntu9:/etc/rc2.d$ ls
README S12dbus S20rsync S89cron
S01policykit S18avahi-daemon S24dhcdbd S98usplash
S05vbesave S20apmd S24hal S99acpi-support
S10acpid S20apport S25bluetooth S99laptop-mode
S10powernowd.early S20cupsys S25pulseaudio S99rc.local
S10sysklogd S20hotkey-setup S30gdm S99rmnologin
S10xserver-xorg-input-wacom S20nvidia-kernel S89anacron S99stop-readahead
S11klogd S20powernowd S89atd
therawski@ubuntu9:/etc/rc2.d$ sudo S20cupsys restart
sudo: S20cupsys: command not found

SEE!?! can anyone help? I'm obviously using the Z55 driver for this

I've also tried manually selecting the driver using the "Administration>Printing" thing

Can anyone help me out?

---

