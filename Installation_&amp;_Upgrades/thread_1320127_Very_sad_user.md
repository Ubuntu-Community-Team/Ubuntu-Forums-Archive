---
title: "Very sad user"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by dahldk on 2009-11-08
Hi there
I am having a miserable time after upgrading to 9.10
actually it started after I got a new processor,a Athlon64 X2 5200+
+ 2G memory + 640G hard drive + motherboard
After a clean new install of the 64 bit system the machine was MUCH slower then with the old hardware and 32 bit system, and it was VERY hard to get things to work like before
watch DVD for instance, but I did succeed 
The other day I upgraded to 9.10
 WHAT a MISTAKE now the machine is barely working
system monitor uses 5-40% of the processor power if it is the ONLY thing running
opening Firefox takes 50-100% even if you do Nothing! and surfing is as slow as in the old dial up days (I have a 10 Meg Dsl line)
trying to watch Youtube takes opening a second window to get it started, and
it takes 50-100% processor power and it still freezes and stops randomly 
I have tried to Google these problems, but to no avail
trying to find new programs takes a programmer to figure out, there are about 100 different programs for Flash and Java on the lists, and NO way to figure out which to use or which I NEED
Before I was very happy about Ubuntu, but now I am thinking about spending 1000$ for a computer with Windows preinstalled, I guess that will solve my problem for the next 6 months or longer if Windows no longer needs to be reinstalled every 6 months 

I am sorry about my rantings  
if anybody has an idea I will be very happy  
Thanks   Jesper Dahl

---

### Post by scout4536 on 2009-11-08
Have you tried a "clean install".  I have heard of things going quite bad on "upgrades".  But other than that sounds like you got some good hardware there.

Just make sure you backup your stuff before you do a clean install.

---

### Post by AnarchyLinux on 2009-11-08
[B]Download a Fresh copy of Ubuntu 9.10 and make sure its 64 bits (works better with your processor)


if you dont want to loose data just simply do a backup of all you need!

ubuntu 9.10 comes with a very very powerfull embebed firewall (try to check it also) theres many things that might been hapening to make your computer that slow.
remeber 2 firewalls running (example router+ubuntu)=Horrible internet and Computer performance as they try to kill each other so to speak.
[/B]

---

### Post by lavinog on 2009-11-08
> **dahldk said:**
> Hi there
I am having a miserable time after upgrading to 9.10
actually it started after I got a new processor,a Athlon64 X2 5200+
+ 2G memory + 640G hard drive + motherboard
After a clean new install of the 64 bit system the machine was MUCH slower then with the old hardware and 32 bit system, and it was VERY hard to get things to work like before

What are the make and models of your components.  There may be something specific to your setup.  Also what video card are you using?
Did you change anything in BIOS?  Some motherboards have bios set for compatibility rather than performance, such as SATA drives might be running in IDE compatibility mode instead of AHCI.

What does dmesg say?



> 
The other day I upgraded to 9.10
 WHAT a MISTAKE now the machine is barely working

Did you upgrade or do a clean install?

> 
system monitor uses 5-40% of the processor power if it is the ONLY thing running

This is a bug with system monitor.  If you slow the graph speed down, it should come down.

> 
opening Firefox takes 50-100% even if you do Nothing! and surfing is as slow as in the old dial up days (I have a 10 Meg Dsl line)

There are various tweeks to improve firefox performance.  Your hd being in IDE mode could cause this also.
try a speed test and see what your dl and ul speeds are: [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)
It might not be a connection issue.  It could be a dns issue, or ipv6 issues...etc.
Who is your isp?  AT&T's fastest is 6mb.

> 
trying to watch Youtube takes opening a second window to get it started, and
it takes 50-100% processor power and it still freezes and stops randomly 

Yes it does.
This is because the flash that is installed by default is a 32bit flash with a wrapper program.  The 64bit flash is much better, but because it is in a alpha stage, it isn't part of the ubuntu repos.  There is a sticky that explains how to install it in the 64bit forum.

> 
I have tried to Google these problems, but to no avail
trying to find new programs takes a programmer to figure out, there are about 100 different programs for Flash and Java on the lists, and NO way to figure out which to use or which I NEED

The forums are a great resource.
if you use google, use the site field to limit your searches to ubuntuforums.org
for example for finding information on 64bit flash in ubuntu use this in google:
site:ubuntuforums.org flash 64bit
also take advantage of the ubuntu documentation and community documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

> 
Before I was very happy about Ubuntu, but now I am thinking about spending 1000$ for a computer with Windows preinstalled, I guess that will solve my problem for the next 6 months or longer if Windows no longer needs to be reinstalled every 6 months 

I am sorry about my rantings  
if anybody has an idea I will be very happy  
Thanks   Jesper Dahl
If you feel you must switch to windows, it would be cheaper to buy windows 7, instead of buying a new computer.

---

### Post by dahldk on 2009-11-09
Thank you very much

especially lavinog!!

the 64 bit flash solved a LOT of problems as did slowing system monitor down
[LEFT]but I have not found anything about Ahcl mode in my Bios, the choices are ide and raid 
the Dsl-test showed 6 Mb I guess I do not have 10 Mb after all!!
about dmesg, I do not know what to look for it is all gibberish to me, I can c&p it but it is 
a Big document to post
but now the computer is certainly usable, and quite fast
I will use this forum in the future, it ROCKS

Thanks    Jesper Dahl
[/LEFT]

---

### Post by lavinog on 2009-11-09
> **dahldk said:**
> Thank you very much

especially lavinog!!

It was my pleasure
> 
but I have not found anything about Ahcl mode in my Bios, the choices are ide and raid 

Is this hd a SATA drive?
What model motherboard is this.  Maybe it enabled by default.

> 
the Dsl-test showed 6 Mb I guess I do not have 10 Mb after all!!

Sometimes they advertise both up and down rates combined, and they also advertise the maximum possible rate.
The actual rate may vary with line conditions, distance, and network overhead.

> 
about dmesg, I do not know what to look for it is all gibberish to me, I can c&p it but it is 
a Big document to post

when posting the output of commands you have a couple of options.
you can redirect the output to a file and attach the file:
```

dmesg > dmesg.txt

```
the **>** redirects the output to dmesg.txt

instead of attaching the file you can post it inside [noparse]```

```[/noparse]
see this for an example: [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)
You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button to do this too.

Whenever you start having a problem, it is good start to post the output of dmesg.  With practice, you will start noticing what is normal and abnormal.  Many times if you find an error message, you can google it and find better information on it.

Some other information that can be handy to post would be:
lshw - gives detailed information about the hardware detected.
lspci - gives information about pci devices installed.
lsusb - usb devices

/var/log/Xorg.0.log (text file, not a command) - Log of X, handy for troubleshooting graphics, mouse, keyboard issues.

One thing I like about linux OSes is that there is plenty of information for troubleshooting.  I have been troubleshooting some windows issues, and all I have to use are generic error messages that can be caused by a wide variety of issues.

---

