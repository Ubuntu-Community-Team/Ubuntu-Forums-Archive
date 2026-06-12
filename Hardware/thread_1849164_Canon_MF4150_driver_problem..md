---
title: "Canon MF4150 driver problem."
date: 2011-09-23
forum: Hardware
---

### Post by latvian on 2011-09-23
Hello everyone,

I am trying to install the drivers of Canon MF4150 multifunction printer on Ubuntu 11.04 but I couldn't for mysterious reasons. I downloaded the Linux drivers from the official website of Canon. I contacted Canon's support about how to install their Linux driver on Ubuntu and their answer was that they does not support Linux anymore because there are many distributions out there and they can not test every driver on every single distro and that the drivers I have downloaded are from a third-party and never been tested!

I have partially solved the problem by running Win XP on a virtual machine and installed the drivers on the Win XP but this was not the perfect solution for me...

Any idea or suggestion to this dilemma? 

Thanks in advance...

---

### Post by latvian on 2011-09-28
Anyone?

---

### Post by Tibs1 on 2011-10-17
I have problems as well with a 4410:(

---

### Post by mikekab on 2011-10-18
Installing the drivers:

1. Extract them
2. If they are .rpm, convert to .deb with the alien program.
3. You can install .deb packages by double clicking them.
4. The printer manager should now be able to find the drivers.

---

### Post by JimmyC4 on 2011-10-21
If your system is 64 bit, you'll need to install the dependencies 
- libc6-i386
- lib32z1
- ia32-libs
before installing the 64 bit RPM packages as mikekab mentioned.

32 bit is slightly trickier - the Canon UFR2 i386 Debian install files depend on gs-esp, which is no longer in the repositories. You can try installing [**[COLOR="Blue"]this[/COLOR]**]("https://launchpad.net/ubuntu/natty/i386/gs-esp/9.01~dfsg~svn12047-0ubuntu1") first or you can replace the dependency gs-esp with ghostscript-x in the package control file.

---

### Post by joemiah on 2011-10-23
Hi all,

I have the same problem with my Canon MF-4150 on Oneiric 64bit. Considering I have had the same problems each distribution upgrade since Feisty, you'd think I'd have learnt by now.

Could anyone point me in the right direction please? I have done the following:

a. Downloaded latest drivers from Canon website;

b. Installed libc6-i386, lib32z1 and ia32-libs;

c. Installed the 64bit driver rpms using alien:
sudo alien -ik cndrvcups-common-2.20-1.x86_64.rpm
sudo alien -ik cndrvcups-ufr2-uk-2.20-1.x86_64.rpm

d. Added my printer (usb) by clicking on the cog, printers, add printer;

e. The printer is detected and a little icon appears.

Now, when I print a test page I get a print error stating: "Stopping job because the scheduler could not execute a filter". I click Diagnose and the dialog advises that I'm missing "/usr/lib/cups/filter/pstoufr2cpca".

After locating the filter under /usr/lib64/cups/filter and creating a link, I try printing again. This time, there's no error message, but nothing is printed.

I checked the error log under /var/log/cups and there's no error; the access log shows three entries:

localhost - - [23/Oct/2011:21:17:16 +1100] "POST /printers/Canon-MF4150 HTTP/1.1" 200 205787 Print-Job successful-ok
localhost - - [23/Oct/2011:21:17:20 +1100] "POST / HTTP/1.1" 200 341 Create-Printer-Subscription successful-ok
localhost - - [23/Oct/2011:21:17:21 +1100] "POST / HTTP/1.1" 200 152 Cancel-Subscription successful-ok

I'm out of ideas, and really need my printer back.

Can anyone suggest what to try next?

---

