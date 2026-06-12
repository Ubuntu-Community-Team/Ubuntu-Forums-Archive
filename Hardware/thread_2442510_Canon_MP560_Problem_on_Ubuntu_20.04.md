---
title: "Canon MP560: Problem on Ubuntu 20.04"
date: 2020-05-04
forum: Hardware
---

### Post by belaw on 2020-05-04
Hello,

I try to get a Canon MP560 printer running on Ubuntu Focal Fossa. I have .deb files provided by Canon. But these need i386 support. I could not install ia32-libs which are needed. Is there a workaround?
I also got source files (cnijfilter-4.10) from which i tried to compile the driver. I tried this
```
./autogen.sh --program-suffix=mp560 --enable-libpath=/usr/lib/bjlib/
$ make

```
Here i got an error: ```
gcc  -O2 -L../..//libs_bin64  -o cif bjferror.o bjfilter.o bjfimage.o bjfoption.o bjfpos.o bjfrcaccess.o getipc.o bjflist.o -lcnbpcmcm -lcnbpess -lm -ldl -lcnbpcnclapi -lcnbpcnclbjcmd -lcnbpcnclui -lpopt 
/usr/bin/ld: -lcnbpcmcm not found
/usr/bin/ld: -lcnbpess not found
collect2: error: ld returned 1 exit status
```
I have the libraries which are needed. But I don't know where to place them to make the driver. Can somebody pleas assist me to either install the driver from the .dep file or compile from sources.
Thanks

---

### Post by teejay687 on 2020-05-08
I have the exact same printer, and I'm running Ubuntu  20.04 LTS. After literally days of trying to get the printer working, I  managed to do it with the following two commands in Terminal:

```
apt-cache search bjnp
sudo apt-get install cups-backend-bjnp

```

Then go to Settings, Printers, Add, click on "Network Printer" and it  should popup. Now just click forward to the end and you should be able  to print a test page.

Best of luck!

---

### Post by zon14 on 2020-05-09
And by the way, the above commands also helped me get the correct driver for a Canon PIXMA MP160 installed.  All the previous versions of Ubuntu I used always had it available, but not this time.  Even using the web browser set to [http://localhost:631](http://localhost:631) only brought up a partial list, which didn't include the model I was using.

---

### Post by belaw on 2020-05-10
Thanks teejay687 this is a big step forward. 
I tried several printers (generic, different recommend Canon BJ printers) but I was not able to print a test page. 
I also provided a Canon MP 560 ppd file which I extracted from a original .deb package provided by Canon. Here I got an error that a file pstocanonij is missing. 
I used a file provided in the .deb file and copied it to /usr/lib/cups/filter where it should be, but still no success.

Which printer did you select in the installation process?
Thanks

---

### Post by CelticWarrior on 2020-05-10
.deb files are Debian/Ubuntu installation packages, just double-click and they should open the assigned utility or app store or you can install them manually in the terminal. In no case they are to be copied anywhere.

---

### Post by belaw on 2020-05-10
> **CelticWarrior said:**
> .deb files are Debian/Ubuntu installation packages, just double-click and they should open the assigned utility or app store or you can install them manually in the terminal. In no case they are to be copied anywhere.

Basically you are right. But the .deb files i have are compiled for previous ubuntu versions and with i386 support which is not longer supported in ubuntu 20.04.

---

### Post by CelticWarrior on 2020-05-10
Yes, it may need updates but so do you. The mention of 'ia32-libs' is the reason. It isn't used that way for many years now.

You may try ```
sudo dpkg --add-architecture i386
```
This is how users add 32-bit support for a 64-bit Ubuntu since ~8 years ago.

Please note the Canon drivers/software may need dependencies that are no longer available. That said, please pay attention to post #2 where the user explicitly says they didn't install anything from Canon directly so, supposedly, the printer is already supported with the additional software mentioned in said post.

---

### Post by belaw on 2020-05-10
> **CelticWarrior said:**
> Yes, it may need updates but so do you. The mention of 'ia32-libs' is the reason. It isn't used that way for many years now.

You may try ```
sudo dpkg --add-architecture i386
```
This is how users add 32-bit support for a 64-bit Ubuntu since ~8 years ago.

Please note the Canon drivers/software may need dependencies that are no longer available. That said, please pay attention to post #2 where the user explicitly says they didn't install anything from Canon directly so, supposedly, the printer is already supported with the additional software mentioned in said post.

I appreciate your help. As you noted there are unfulfilled dependencies as I wrote in my first post. Do you know a solution for this (ia32-libs)?
Can you tell me which printer to select from the installation dialog? The requested Canon MP560 is not in the list. But you can provide a manual ppd which can be extracted from the .deb file. This ppd needs a library (pstocanonij) which can be compiled from sources. Unfortunately it still does not work.
I would be happy if you can provide a solution or way to work.

---

### Post by CelticWarrior on 2020-05-10
Sadly, you're still missing the point. So, again, the purpose of 'ia32-libs' was to provide 32-bit support/libraries to 64-bit OSes for software that needs 32-bit libraries. The way users add said support now was explained in post#7. The 'ia32-libs' package no longer exist, at least since 2012!! Forget it, it isn't and can't be the solution, period. Please don not insist in dead-ends, especially after being told why that's a dead end.

Here's the problem for which you need a rational and realistic approach:
Your hardware is ancient; Canon stopped supporting it a long time ago for all but especially for Linux OS which was an afterthought anyway since the beginning.
Everything you can do now is a workaround, a 'best effort' attempt in keeping it working (but there will be a time, much sooner than later, when even those efforts will be in vain) by using ~10 years old drivers that never supported 64-bit, reason with we need to add that architecture.

In a nutshell, this answer from 5 years ago already required some unorthodox "moves" to make it work but in any case there were and there aren't because it can't be any involvement of the old 'ia32-libs' package:
[https://askubuntu.com/a/675217](https://askubuntu.com/a/675217) (Important note: The PPA mentioned is long gone; if you want to try then please follow the instruction from the part saying "alternatively download the original drivers from Canon Asia website")
It's clearly mentioned the drivers were for 32-bit OS only therefore users need to add 32-bit support (i386) before installing them and they show how to do that exactly as I told you in post #7.

---

### Post by frostschutz on 2020-05-11
I have a similar printer (MP630). It does not work out of the box with 20.04 which makes me want to buy a new one :-)

For the cnij driver there used to be a PPA by Michael Gruz [https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)

And this PPA is forked by Ordissimo / Thierry Huchard [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz)

There you can find .deb for Ubuntu 19.04, that's the latest I could find. The 20.04 side only has driver for a different set of printers that won't work for the old stuff.

direct link: [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+sourcepub/9870078/+listing-archive-extra](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+sourcepub/9870078/+listing-archive-extra)

> 
steps from memory:

- download the .deb you need for your printer (cnijfilter-common_*1904, cnijfilter-mp###series_*1904)
- install with dpkg -i
- if that was a i386 package, dpkg --add-architecture i386
- to pull missing dependencies, apt update, apt --fix-broken install

- settings, printers, remove previously added stuff, add new printer
- should now detect your ancient usb printer
- print test page \o/


There is also a commercial driver (Turboprint, free 30 day trial) and I used those under 16.04 with great success, but as of yet they don't have packages meant for Ubuntu 20.04 specifically.

It's also possible to install Qemu/KVM or Virtualbox and pass the USB printer device through to a virtualized Windows, and then print using Windows drivers. Huge waste of resources for a printer driver but it works.

EDIT: the bjnp should be fine for network printers, unfortunately my model is USB only

---

### Post by belaw on 2020-05-11
Thanks frostschutz, 
i followed your advice and it worked very well (this was my frustschutz)> **frostschutz said:**
> I have a similar printer (MP630). It does not work out of the box with 20.04 which makes me want to buy a new one :-)

For the cnij driver there used to be a PPA by Michael Gruz [https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)

And this PPA is forked by Ordissimo / Thierry Huchard [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz)

There you can find .deb for Ubuntu 19.04, that's the latest I could find. The 20.04 side only has driver for a different set of printers that won't work for the old stuff.

direct link: [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+sourcepub/9870078/+listing-archive-extra](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+sourcepub/9870078/+listing-archive-extra)
steps from memory:

- download the .deb you need for your printer (cnijfilter-common_*1904, cnijfilter-mp###series_*1904)
- install with dpkg -i
- if that was a i386 package, dpkg --add-architecture i386
- to pull missing dependencies, apt update, apt --fix-broken install

- settings, printers, remove previously added stuff, add new printer

---

### Post by teejay687 on 2020-05-12
Edit: sorry, I just noticed frostschutz's reply, leaving this here if it can help any one.

 I apologize for never replying.  All I did was kept clicking next, and Ubuntu picked up the printer and it displayed it as Canon MP560. I should point out that this method worked with **printing **over WiFi. I never plug directly into my printer, and I do not use the scan function (I scan to USB). I know people will say you need to install the 32bit architecture, but I assure you, I never had to that.  Also the  Michael Gruz PPA method mentioned here worked great for 18.04, but once I updated to 20.04, I could never get that PPA to work properly. 

I just enter the following **two** commands **separately **into terminal after updating my machine:

```
apt-cache search bjnp
sudo apt-get install cups-backend-bjnp
```

 Then go to printer set up and click add printer. You do have to wait a few moments after you click "Network Printer" for the printer to show up. Ubuntu then picks up my printer (Canon MP560), every time. I never did anything else, no 32bit architecture or anything like that, no downloading packages from Canon. Since my initial response I have used this exact method successfully on MX Linux 19.1 (64bit), and Debian 10.3 (64bit). Sorry for replying to a solved thread (was it even solved?), but I really hope this helps you. Getting this printer to work was such a hassle. Please feel free to message me if you still have issues.

---

### Post by belaw on 2020-05-12
Thanks teejay687 for your detailed post and your help. I followed your advice closely but no Canon MP560 showed up in the printer installation dialog. There where many other canon printers listed but not any mp560. I tried several BJ printers but non worked.
The solution frostschutz gave me worked very well. So yes this issue is solved.

---

### Post by CelticWarrior on 2020-05-12
> **belaw said:**
> I followed your advice closely but no Canon MP560 showed up in the printer installation dialog. There where many other canon printers listed but not any mp560. I tried several BJ printers but non worked.


No, you probably didn't. Or you did but then missed some error during the installation of 'cups-backend-bjnp' (BTW, although the user mentioned 2 commands the first does nothing, the second one is all it needs to install the package that provides support for additional model). If you had it installed correctly the correct model would be available.

---

### Post by frostschutz on 2020-05-14
> **belaw said:**
> The solution frostschutz gave me worked very well. So yes this issue is solved.

Either solution should work, the confusion is because one (bjnp) only works for (wifi or lan) network printers, while for USB printer you are stuck with the Canon driver, .deb or PPA.

If your printer is network capable and your network is trustworthy, do set it up (wifi / ip address on the printer, same subnet as PC) and try bjnp first before going with the USB one which unfortunately does not have proper opensource drivers.

---

