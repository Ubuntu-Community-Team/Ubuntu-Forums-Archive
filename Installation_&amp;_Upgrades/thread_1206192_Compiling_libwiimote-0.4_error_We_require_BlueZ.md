---
title: "Compiling libwiimote-0.4 error: We require BlueZ"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by marshmallow1304 on 2009-07-06
I'm trying to compile libwiimote-0.4 on 64-bit Jaunty, but I keep running into this:

```
benn@system76-pc:~/Desktop/Wii/libwiimote-0.4$ autoconf
benn@system76-pc:~/Desktop/Wii/libwiimote-0.4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for hci_remote_name in -lbluetooth... no
configure: error: We require BlueZ
```

Any ideas?  bluez is installed.

---

### Post by taurus on 2009-07-06
You probably need the libbluetooth-dev package as well.

---

### Post by marshmallow1304 on 2009-07-06
I installed libbluetooth-dev, retried, and got the same result.

---

### Post by mc4man on 2009-07-07
Only gave this a quick glance, read thru and see (#9

[http://ubuntuforums.org/showthread.php?t=933332](http://ubuntuforums.org/showthread.php?t=933332)

---

### Post by marshmallow1304 on 2009-07-07
> **mc4man said:**
> Only gave this a quick glance, read thru and see (#9

[http://ubuntuforums.org/showthread.php?t=933332](http://ubuntuforums.org/showthread.php?t=933332)

Unfortunately, I already tried that.  However, I did my initial setup with

[https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

I shall try the setup described by

[http://ubuntuforums.org/showthread.php?t=535659](http://ubuntuforums.org/showthread.php?t=535659)

even though it seems very similar.  If it doesn't work after that, I'll go back and try post #9 on

[http://ubuntuforums.org/showthread.php?t=933332](http://ubuntuforums.org/showthread.php?t=933332)

---

### Post by mc4man on 2009-07-07
Must be a 64 bit and or greater than 8.04 'issue', configured and built fine on a 8.04 i386 install. (libbluetooth 3.29

Gonna boot up a jaunty 64 bit live cd and take a look

---

### Post by marshmallow1304 on 2009-07-07
I got it working.  Thanks.

It turns out I must have done the editing to replace hci_remote_name after I did autoconf.  I deleted and restarted from the tarball.

---

### Post by mc4man on 2009-07-07
> I got it working

Good to hear, the edits are pretty straightforward. noting you don't get a configure script to edit till you run autoconf

(used the edits from the linked post 9, for anyone else

replaced all instances of hci_remote_name with hci_read_remote_name in configure
replaced the 1 instance in wiimote_link.c (not wii[COLOR="Blue"]re[/COLOR]mote_link.c
edited the src makefile to use -fPIC

---

### Post by marshmallow1304 on 2009-07-07
> **mc4man said:**
> 
used the edits from the linked post 9, for anyone else

replaced all instances of hci_remote_name with hci_read_remote_name in configure
replaced the 1 instance in wiimote_link.c (not wii[COLOR="Blue"]re[/COLOR]mote_link.c
edited the src makefile to use -fPIC

Also for anyone else who has to use the fix above:

I also needed to perform similar actions in order to configure and compile cwiid-0.5.03.  I had to replace hci_remote_name with hci_read_remote_name in wiimote/bluetooth.c

Thought I'd include it since the two are often used together and are both used in the installation section of the [CWiiD documentation]("https://help.ubuntu.com/community/CWiiD").

---

### Post by faabiioo on 2009-07-22
> **mc4man said:**
> 
used the edits from the linked post 9, for anyone else

replaced all instances of hci_remote_name with hci_read_remote_name in configure
replaced the 1 instance in wiimote_link.c (not wii[COLOR="Blue"]re[/COLOR]mote_link.c
edited the src makefile to use -fPIC

Hello,
i've done right what you suggested, then [FONT="Courier New"]autonconf[/FONT] again and [FONT="Courier New"]./configure[/FONT] again: still getting the same error ```
configure: error: We require BlueZ
```

:confused:

---

### Post by marshmallow1304 on 2009-07-22
Stupid question maybe, but do you have libbluetooth-dev?

---

### Post by TheUnwiseman on 2009-09-19
Thanks for the help, marshmallow!  I'm running 64-bit Jaunty, and this fixed my problem as well.

---

### Post by Argard on 2012-07-02
> **taurus said:**
> You probably need the libbluetooth-dev package as well.

Thanks, this solved the problem.

---

