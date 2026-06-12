---
title: "Easy Canon PIXMA MX700 printer install"
date: 2011-05-02
forum: Hardware
---

### Post by gamecraziness on 2011-05-02
Hello,

I made an easy install script for the Canon PIXMA MX700 printer. This should work on 64-bit (x64) and i386. Most of the credit goes to Menthu_Rae from here: [http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363), I just automated it. :D

Download: [http://dl.dropbox.com/u/3925366/mx700.zip](http://dl.dropbox.com/u/3925366/mx700.zip)

Hope this helps someone, and feel free to ask any questions if you encounter any problems!

---

### Post by Ichido on 2011-06-03
Will your *.zip file work with/in Ubuntu 10.04 i386?
Thanks.

---

### Post by gamecraziness on 2011-06-03
Yes, it should. It uses i386 packages, in fact, but works on x64 as well because the architecture check is removed.

---

### Post by Ichido on 2011-06-04
Thanks!
I hope to run it next week on my Sister-in-Law's PC.

---

### Post by ghl on 2011-06-27
Hi new to this forum, not new to Ubuntu but I am not a programmer and do use both WinXP and Ubuntu (native and virtually via Virtualbox)....

Firstly many thanks for the script, made life so much easier.

The script works fantastically on my home laptop (which is on 10.10), the only problem I've found is that I had issues with 11.04 (broadcom wireless) so stayed with 10.10 on this.

I have a desktop machine that currently is running 10.04 LTS, again the script worked fantastically on this - I tried 11.04 and all was fine except I hit a problem with the script.

I installed it and all appeared fine however for some reason it always tried to print from the rear tray regardless of the settings for the tray/paper.

Has anyone else hit this problem or can anyone provide any suggestions on how to resolve it as I would like to move the latest release if possible.

---

### Post by gamecraziness on 2011-07-13
Sorry, I don't have this problem on Ubuntu 11.04.

Does this problem occur on all applications?

---

### Post by ghl on 2011-07-16
tbh, didn't test with multiple apps, just did the test page at the end of installation.

Hit a problem now where I've updated 10.04 with security patches etc (via update manager) and now my scanning has stopped, as it can't be found by sane/xsane - so thinking of trying again with 11.04 and seeing how it goes.

Not sure if there are other ways of 'reloading' the scanning properties - i tried reinstalling the drivers by your install.sh script but it didn't help - assuming it's something more underlying.

---

### Post by ghl on 2011-07-16
ok, now have more info...

I have updated to 11.04 (10.04 LTS goes to 10.10 on initial upgrade then to 11.04). Now I tried to print/scan - here's what I got.

XSane shows, "no devices available" still.


if I print a test page, it always comes out of the rear tray regardless of the setting in the printer options tab but prints correctly.

If I try to print from LibreOffice, I can select the tray but either way the print job goes into the queue and I can see it go to Processing but when looking on the printer properties, the status goes from 'Idle - Ready to print' to 'Processing - Failed to read side-channel request!', then back to 'Idle - Ready to print'.
At the same time the job enters the print queue, shows as Processing then just disappears.

During this time the printer doesn't change, that is, no aligning, movement or sound from the printer.

I don't know if this matters at all, it's connected via ethernet, now on 11.04 (32 bit).

It almost feels like a permissions thing, otherwise I wouldn't be able to print a test page albeit only off the rear tray.

Using Eye of GNOME 2.32.1, also doesn't print. I did a Diagnose but it doesn't make sense to me :D. The system didn't find anything automatically either.

Any ideas/pointers??

Cheers

---

### Post by gamecraziness on 2011-07-16
Hmmm, it may indeed be a permissions issue.

Try entering these commands (they were in the bash file, but try them anyways):

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

---

### Post by ghl on 2011-07-16
ok, getting further - i think!
as well as the cmds you gave me I did;
sudo ldconfig -v followed by 
sudo service cups restart

These were from a different thread relating to the printer error. Not really sure what the ldconfig does but it seemed to relink some config files to versions, by the looks of the response.

After also doing your cmds, now I no longer get the processing - 'Processing - Failed to read side-channel request!' error. Now the printer status stays in Idle Ready to Print, then says there was a error processing and the state changes to Stopped.
Test Page still OK though.

Sorry didn't make a note of the file ownership before typing your commands in, but now are;
ghl:/usr/lib/cups$ ls -la
total 120
drwxr-xr-x  10 root root  4096 2011-02-11 13:10 .
drwxr-xr-x 248 root root 81920 2011-07-16 17:24 ..
drwxr-xr-x   2 root root  4096 2011-07-16 16:31 backend
drwxr-xr-x   2 root root  4096 2011-07-16 15:23 backend-available
drwxr-xr-x   2 root root  4096 2011-07-16 15:23 cgi-bin
drwxr-xr-x   2 root root  4096 2011-07-16 15:23 daemon
drwxr-xr-x   2 root root  4096 2011-07-16 15:38 driver
drwxr-xr-x   2 root root  4096 2011-07-16 16:31 filter
drwxr-xr-x   2 root root  4096 2011-07-16 15:23 monitor
drwxr-xr-x   2 root root  4096 2011-07-16 15:23 notifier

I must admit, I've been trying to switch over to Linux since about Ubuntu 8.04 but the printing/scanning and also previously Skype were the things that got in my way (as I used to have a box that routed skype from the pc through to my landline phone). I have now got one of them dualphone things for skype and thought I'd got the printing/scanning sorted with your script. Looks like a mixture of buying a printer designed for windows and no support in drivers from Canon still gives me grief.

Thanks for your ideas up till now. Any further suggestions/ideas greatly received :D

---

### Post by gamecraziness on 2011-07-18
Sorry, I honestly have no idea. You might have a better chance of solving the problem if you open up a new thread about it.

It is unfortunate that Canon doesn't provide Linux drivers. I probably would have bought another model if I knew it required so much setup.

Good luck!

---

### Post by ghl on 2011-07-18
many thanks anyway. Will have a bit more of a dig and let you know if I find anything - good for info if nothing else.

---

### Post by horseshoe on 2011-07-27
thanks for the script, worked like a charm w/ USB. unplugged USB and attached to router, then switched the device URI to the network IP address and no issues whatsoever on desktop and netbook. (netbook would not print via shared printer from USB connected desktop)

---

### Post by bootedguy on 2011-07-30
Thank you gamecraziness!  You deserve a medal for this.

---

### Post by MyR on 2011-07-31
Wow thanks for the script!

Would you submit a [review of the printer]("http://linuxdeal.com/add-printer.php")?

---

### Post by amalasuintha on 2011-08-04
> **gamecraziness said:**
> Hello,

I made an easy install script for the Canon PIXMA MX700 printer. This should work on 64-bit (x64) and i386. Most of the credit goes to Menthu_Rae from here: [http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363), I just automated it. :D

Download: [http://dl.dropbox.com/u/3925366/mx700.zip](http://dl.dropbox.com/u/3925366/mx700.zip)

Hope this helps someone, and feel free to ask any questions if you encounter any problems!

You are wonderfull, you solve our problem very easily. Works with 32 and 64bits right away! Thank you!

---

### Post by woo10jw on 2011-08-10
After 1 yr of trying, 6 mos sending MB back & forth to Calif, then the ink dried on printer head, finally got everything ready, just ran the script on Ubuntu 10.10 everything worked perfect. Felt really lucky, have 2nd part with 11.04, ran the script, installed fine but it did swithch to top tray to print. I love this forum and all the guy that help the less knowledgeable.    Thanks very much Gamecraziness

---

### Post by andrew_wilson on 2011-09-04
Thanks!

---

### Post by gamecraziness on 2011-09-04
I'm glad it helped a lot of people! Menthu_Rae deserves most of the credit though.

---

### Post by ghl on 2011-10-20
Hi, just trying to get this to work with 11.10 64bit (actually with the  xubuntu version as I'm not keen on the Unity interface, but that's a  different discussion). Did get it going on 11.04 in the end, but can't  recall what I needed to do.

When I run sudo ./install.sh, this is  what I get - any ideas at all on what I need to do. I've run this a few  times hence why it thinks things are already at the latest version.

$ sudo ./install.sh 
[sudo] password for ghl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcups2' instead of 'libcupsys2'
Note, selecting 'libcups2-dev' instead of 'libcupsys2-dev'
libcups2 is already the newest version.
libcups2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcups2' instead of 'libcupsys2'
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libcairo2 is already the newest version.
libfontconfig1 is already the newest version.
libglib2.0-0 is already the newest version.
libgtk2.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libpng12-0 is already the newest version.
libpopt0 is already the newest version.
libtiff4 is already the newest version.
libx11-6 is already the newest version.
libxcursor1 is already the newest version.
libxext6 is already the newest version.
libxfixes3 is already the newest version.
libxi6 is already the newest version.
libxinerama1 is already the newest version.
libxml2 is already the newest version.
libxrandr2 is already the newest version.
libxrender1 is already the newest version.
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(Reading database ... 148994 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 2.80-1 (using cnijfilter-common_2.80-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
Setting up cnijfilter-common:i386 (2.80-1) ...
(Reading database ... 148994 files and directories currently installed.)
Preparing to replace cnijfilter-mp520series:i386 2.80-1 (using cnijfilter-mp520series_2.80-1_i386.deb) ...
Unpacking replacement cnijfilter-mp520series:i386 ...
Setting up cnijfilter-mp520series:i386 (2.80-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
cups-bjnp-0.5.5/
cups-bjnp-0.5.5/configure
cups-bjnp-0.5.5/NEWS
cups-bjnp-0.5.5/config.h.in
cups-bjnp-0.5.5/bjnp-debug.c
cups-bjnp-0.5.5/bjnp-io.c
cups-bjnp-0.5.5/Makefile.am
cups-bjnp-0.5.5/TODO
cups-bjnp-0.5.5/missing
cups-bjnp-0.5.5/depcomp
cups-bjnp-0.5.5/README
cups-bjnp-0.5.5/COPYING
cups-bjnp-0.5.5/Makefile.in
cups-bjnp-0.5.5/configure.ac
cups-bjnp-0.5.5/aclocal.m4
cups-bjnp-0.5.5/bjnp.c
cups-bjnp-0.5.5/INSTALL
cups-bjnp-0.5.5/ChangeLog
cups-bjnp-0.5.5/AUTHORS
cups-bjnp-0.5.5/cups-bjnp.spec
cups-bjnp-0.5.5/install-sh
cups-bjnp-0.5.5/bjnp-runloop.c
cups-bjnp-0.5.5/bjnp.h
cups-bjnp-0.5.5/conf/
cups-bjnp-0.5.5/conf/norpm
cups-bjnp-0.5.5/conf/rpmbuild
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for cupsDoRequest in -lcups... yes
found Cups backend directory /usr/lib/cups/backend
checking for rpmbuild... no
checking for library containing strerror... none required
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/socket.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking cups/backend.h usability... yes
checking cups/backend.h presence... yes
checking for cups/backend.h... yes
checking cups/http.h usability... yes
checking cups/http.h presence... yes
checking for cups/http.h... yes
checking for sys/types.h... (cached) yes
checking for netinet/in.h... (cached) yes
checking for arpa/nameser.h... yes
checking for netdb.h... (cached) yes
checking for resolv.h... yes
checking for size_t... yes
checking for ssize_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint8_t... yes
checking for ftime... yes
checking for gethostbyaddr... yes
checking for gethostname... yes
checking for inet_ntoa... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for getifaddrs... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/home/ghl/Desktop/mx700/cups-bjnp-0.5.5'
gcc -DHAVE_CONFIG_H -I.     -g -O2 -MT bjnp.o -MD -MP -MF .deps/bjnp.Tpo -c -o bjnp.o bjnp.c
bjnp.c: In function ‘main’:
bjnp.c:92:11: error: ‘stderr’ undeclared (first use in this function)
bjnp.c:92:11: note: each undeclared identifier is reported only once for each function it appears in
bjnp.c:130:6: warning: incompatible implicit declaration of built-in function ‘printf’ [enabled by default]
bjnp.c:142:7: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
bjnp.c:286:3: warning: incompatible implicit declaration of built-in function ‘sprintf’ [enabled by default]
bjnp.c:290:7: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
bjnp.c:295:3: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
make[1]: *** [bjnp.o] Error 1
make[1]: Leaving directory `/home/ghl/Desktop/mx700/cups-bjnp-0.5.5'
make: *** [all] Error 2
./install.sh: line 10: ./bjnp: Permission denied
gcc -DHAVE_CONFIG_H -I.     -g -O2 -MT bjnp.o -MD -MP -MF .deps/bjnp.Tpo -c -o bjnp.o bjnp.c
bjnp.c: In function ‘main’:
bjnp.c:92:11: error: ‘stderr’ undeclared (first use in this function)
bjnp.c:92:11: note: each undeclared identifier is reported only once for each function it appears in
bjnp.c:130:6: warning: incompatible implicit declaration of built-in function ‘printf’ [enabled by default]
bjnp.c:142:7: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
bjnp.c:286:3: warning: incompatible implicit declaration of built-in function ‘sprintf’ [enabled by default]
bjnp.c:290:7: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
bjnp.c:295:3: warning: incompatible implicit declaration of built-in function ‘fprintf’ [enabled by default]
make: *** [bjnp.o] Error 1

seems  to be the make and make install that's giving the trouble - tried by  changing the ./bjnp to sudo ./bjnp but it looks like I break the script  before then!

Any assistance greatly received!
Thanks

---

### Post by schase02 on 2011-10-25
there's got to be something with 11.10 that's doing it.  I've installed it no problem with 11.04.

---

### Post by schase02 on 2011-10-25
yeah, it's 11.10.

I just formatted and installed 11.04 again.  the printer installs no problem at all - bam right away.

with 11.10 I get either the errors ghl mentions, or if installing bjnp 1.0 than it gives the side channel error.

Going to try upgrading to 11.10 see if it holds.

---

### Post by schase02 on 2011-10-25
confirmed.

At least for me.  install ubuntu 11.04 - install mx700 - upgrade to 11.10

---

### Post by basil0 on 2011-11-05
Ubuntu 11.10 Oneiric:

Network connected Canon printer (MX700 for me)

Enter device URI:  bjnp://192.168.1.113:8611

Change IP to address for your printer, 8611 is port required by CUPS

Works beautifully - thanks to turboprint for finding the URI, which is not documented for newbies like me.

---

### Post by ashikaga on 2011-11-06
> **ghl said:**
> Hi, just trying to get this to work with 11.10 64bit (actually with the  xubuntu version as I'm not keen on the Unity interface, but that's a  different discussion). Did get it going on 11.04 in the end, but can't  recall what I needed to do.

When I run sudo ./install.sh, this is  what I get - any ideas at all on what I need to do. I've run this a few  times hence why it thinks things are already at the latest version.

...snip...


I had the same problem on 11.10. Here's how to work around the issue:

- Unzip and run the install script, wait for it to error out as above
- Add ```
#include <stdio.h>
``` to the top of mx700/cups-bjnp-0.5.5/bjnp.c and bjnp-runloop.c.
- Comment out (or delete) all lines of the install script up to and including "tar xvzf cups-bjnp-0.5.5.tar.gz" by placing a # at the front of each
- Run the install script again
- Winning.

---

### Post by Docaltmed on 2011-11-13
Rats. No win here, though I'm not sure I put the ```
#include <stdio.h>
``` in the right place, the directions were a little unclear. I'm not sure why adding a commented-out line to this file would make any difference anyway.

---

### Post by gamecraziness on 2011-11-13
Edit: see below

---

### Post by gamecraziness on 2011-11-13
I updated the script, thanks ashikaga! Hope it works for everyone.

---

### Post by benmoreassynt on 2011-11-25
Great script. Thank you.

Quick note in case it's useful to anyone, which I picked up over at the Mint forums.

If you are trying to connect by SMB over a LAN to a printer connected to a Windows machine, check that the Windows Printer Share name does not have any spaces in it. If it does, it appears that the printer settings dialog box on Ubuntu will add '20' in every space (some sort of messed up space escaping) and the connection will never work. Simple fix, but very non-obvious when you're doing the setup.

---

### Post by schase02 on 2011-12-06
works on Linux Mint 12.

btw - if you wanted to include scanning install (sane) on your script.

Download the latest release version; click snapshot for the download.
[http://git.debian.org/?p=sane/sane-backends.git](http://git.debian.org/?p=sane/sane-backends.git)

You do need the above libusb-dev or this will not produce errors - it just will not work

Extract above Sane-Backends archive


cd into the sane-backends directory:

```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```


then compile (this takes a considerable amount of time)


```
make
```

followed by:

```
sudo make install
```


Now you need to set new permissions. 

```
sudo vi /etc/udev/rules.d/40-scanner-permissions.rules
```

paste the following into it.

```
# usb scanner
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE:="0666"
SUBSYSTEM=="usb_device",MODE:="0666"

```

You can then test with scanimage -V  (version) scanimage -L (list scanner)  scanimage -T (test)

and install xsane if you wanted to.

---

### Post by cdshan on 2011-12-27
> **basil0 said:**
> Ubuntu 11.10 Oneiric:

Network connected Canon printer (MX700 for me)

Enter device URI:  bjnp://192.168.1.113:8611

Change IP to address for your printer, 8611 is port required by CUPS

Works beautifully - thanks to turboprint for finding the URI, which is not documented for newbies like me.

I tried your suggestion on 11.10 but I get the following error:

Cups Server Error: There was an error during the CUPS operation: 'client-error-not-possible'.

When I tried installing using the cups on the browser I got the following error:

Unable to add printer:

Bad device-uri scheme "bjnp".

Could you please help me out.

---

### Post by thpierre on 2012-01-20
Hi,

I have got the same message, it was due to a bad backend directory specify at compile time.

---

### Post by lelandsam on 2012-02-18
Thanks so much for all your work. It looks like the script is working well for most people. I've had a couple errors when I try to install on 11.04. 

This is the end of the terminal output:

```

dpkg: error processing cnijfilter-common_2.80-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_2.80-1_i386.deb
dpkg: error processing cnijfilter-mp520series_2.80-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-mp520series_2.80-1_i386.deb
/home/likusasa/mx700/install.sh: line 6: cd: cups-bjnp-0.5.5/: No such file or directory
sudo: ./configure: command not found
make: *** No targets specified and no makefile found.  Stop.
/home/likusasa/mx700/install.sh: line 9: ./bjnp: No such file or directory
make: *** No rule to make target `install'.  Stop.


```

I'm not proficient enough with terminal to know what to make of this.
I think it may be due to trying a bunch of other things before I found this thread, such as installing MX860 drivers in the hope that they might work for the MX700. 
Any ideas?
Thanks

---

### Post by aroundtown on 2012-05-07
> **gamecraziness said:**
> Hello,

_I made an easy install script for the [[COLOR="Black"]Canon PIXMA MX700[/COLOR]]("http://www.tonermax.com/model/PIXMA-MX700/11542") printer_. This should work on 64-bit (x64) and i386. Most of the credit goes to Menthu_Rae from here: [http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363), I just automated it. :D

Download: [http://dl.dropbox.com/u/3925366/mx700.zip](http://dl.dropbox.com/u/3925366/mx700.zip)

Hope this helps someone, and feel free to ask any questions if you encounter any problems!

Is it possible to substitute the script to work for any other canon printer then mx700? I have a canon pixma mp495 and I want to make one for it , thanks!

---

### Post by twigginsga on 2012-09-08
Many thanks for this; makes life much easier!

---

### Post by aikishugyo on 2012-09-10
> **aroundtown said:**
> Is it possible to substitute the script to work for any other canon printer then mx700? I have a canon pixma mp495 and I want to make one for it , thanks!

The SANE software (CVS version only) has experimental support (meaning no-one has yet tested it) for the MP495. If you are willing to compile SANE locally (really easy), I'll be happy to help you, and your feedback will ensure that support is completed if it does not work as-is.

Regards,
Gernot Hassenpflug

---

