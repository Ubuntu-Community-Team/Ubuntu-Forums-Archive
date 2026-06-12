---
title: "AO521 Battery Not Detected"
date: 2010-08-22
forum: Hardware
---

### Post by KellyLSB on 2010-08-22
EDIT: Found the solution (on page 2 or click here [http://ubuntuforums.org/showthread.php?p=10126099#post10126099](http://ubuntuforums.org/showthread.php?p=10126099#post10126099) )

Hola peoples

Just managed to get Ubuntu UNR 10.04 on my AO521 Netbook and it works amazingly (im starting to wonder why i have been dissing ubuntu [been a fedora user for years]) this has been by far the best linux build i have ever used so let me first start by saying. I'm sorry to anyone who has ever heard me diss ubuntu this truly is an amazing distribution.

Now down to the dirty.

By battery is not detected by the system. It works if i unplug the machine it stays on. but it is not giving out any data on its percentage. in fact it doesnt even have a battery tab in the power managment its almost as if it doesnt know there is a battery.

anyone have any ideas. its something i can deal with if i have to but it would be nice to have a battery power profile.

---

### Post by peter_b on 2010-08-23
Hello,

How did you manage to install ubuntu 10.04 on an AO521?

I tried it myself and it does not seem to work.
I tried to put the os on an usb memory stick. 
The installation itself was successful and the syetm boots, but as soon as i try to use the mouse or keyboard the system blocks.
The mouse cursor disappears and it is not possible to enter something w. the keyboard.

Did you have the same and how were you able to fix this?

---

### Post by KellyLSB on 2010-08-23
I used unetbootin to put the i386 ubuntu netbooks remit on a sdcard. I then used the WUBI application from Windows. Once I restarted it completed installation. It booted normally. The only thing that doesn't work is the battery status, and the Ethernet port. However I heard the Ethernet port has a kernel module somewhere or has one coming out soon.

---

### Post by thedud on 2010-08-25
I have had two of these netbooks so far. The first one is actually doing the same exact thing with the battery status. That one died completely after about 3 weeks and I RMAed it then received this one. 

I'm not sure if ACER has changed their hardware in the netbooks or what, but I now have the same issue as the latter of you two. IE my keyboard and mouse are not working. I have tried several other distros and haven't had any luck with them so far.

The main issue is that they must be using some type of newer hardware that isnt' yet supported by the linux kernel.

I hope they fix this soon because it runs really nicely with Xubuntu on it.
If either of you find a fix let me know and I'll do the same.

Oh yeah the battery status DOES work on the latest netbook just not the touchpad and keyboard. You may hook up a usb mouse and keyboard to do things if you need to.

---

### Post by KellyLSB on 2010-08-25
> **thedud said:**
> 
I'm not sure if ACER has changed their hardware in the netbooks or what, but I now have the same issue as the latter of you two. IE my keyboard and mouse are not working. I have tried several other distros and haven't had any luck with them so far.

The main issue is that they must be using some type of newer hardware that isnt' yet supported by the linux kernel.

I hope they fix this soon because it runs really nicely with Xubuntu on it.
If either of you find a fix let me know and I'll do the same.

Well i got ubuntu running on mine. i had issues with installing the regular versions but i just install the Netbook Remix with the WUBI installer on the windows start included with windows and it installed fine. im just missing battery status and microphone...

---

### Post by DoktorFuchs on 2010-10-02
I know this may be abit old, but the information's still relevant.

If you're having the lockup issue, it's actually related to the video driver.  If you pass the nomodeset option to the livecd/usb/whatever, you'll disable the Kernel Mode Setting that ubuntu started using.  This is how i solved that issue, though the current beta/rc (10.10) seems to have fixed this somehow...

In other news, the battery is still not detected, but this is a kernel issue apparently as i've tried gentoo with the unstable branch and I'm still getting the same issue.:(

---

### Post by KellyLSB on 2010-10-04
The ubuntu netbook remix also works as i said above.

Bit of a shame about the battery though.

---

### Post by jbluzb86 on 2010-10-21
I would like ask if the ubuntu 10.10 resolved the problem in installation for ao521 acer aspire one; i have bios 1.03

---

### Post by KellyLSB on 2010-10-21
I actually found that the rc installed for 10.10 but the release wont install.

---

### Post by jbluzb86 on 2010-10-21
I have solved my problem with 10.4 distro install; but i have problem installing 10.10; is it worth it? any suggestions

---

### Post by KellyLSB on 2010-10-21
i been really enjoying the RC of it.
the network card works thats a huge plus.

im still trying to figure out how to install the release now also realize i have all 64bit operating systems on this computer.

also just random stupid question
ok i installed the RC of 10.10 now that 10.10 is out will it upgrade to automatically or do i need to fresh install?

---

### Post by mrehorst on 2010-10-23
I loaded 10.10 netbook remix on my AO521 using a USB flash drive.  It went in easily and booted reliably.  It did not recognize the bluetooth hardware, mic did not work, camera refresh was only about 2-3 fps, did not recognize the battery, and closing the lid did not suspend/hibernate.  Touchpad works with 1 finger but goes nutz if you put two fingers on it.  I did not mess with it long enough to test the keyboard suspend/hibernate, and I have no way to test the hdmi out.  Wired and wireless g networking worked fine without any messing around.  I ultimately decided I'd wait for someone to iron out the bugs and uninstalled using the bootitng utility.

BTW, this 2 GB memory module works fine in my AO521:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231214&Tpk=F3-10666CL9S-2GBSQ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231214&Tpk=F3-10666CL9S-2GBSQ")

---

### Post by KellyLSB on 2010-11-11
Well i just install 11.04 Natty 64-bit Alpha over the distribution upgrade. and the headphone port works now! and most graphics glitches went away! battery still isnt showing up. sad day :( but it seems to be running much better. i also like the new themeing.

---

### Post by KellyLSB on 2010-11-16
SOLUTION TO BATTERY NOT SHOWING!

and a couple months later i found the solution (patch attached, and patching instructions below)
[https://bugzilla.kernel.org/show_bug.cgi?id=19602](https://bugzilla.kernel.org/show_bug.cgi?id=19602)

how to build your own kernel on ubuntu
[http://blog.gnu-designs.com/building-custom-kernels-for-ubuntu](http://blog.gnu-designs.com/building-custom-kernels-for-ubuntu)

after you have downloaded the kernel source of your preference
extract the attached file into the "linux-?" (kernel source) folder then run
```
patch -p1 < ./ao521-acpi.patch
```
Note: if the patching errors read the error then look in the source files where it is erroring. It may be possible to patch it by hand if the kernel source your using may have changed since this patch was made. (When I installed i had to modify one of the files manually a bit.)

Then compile the kernel and install (make sure you dont uninstall any other kernels in case this one crashes or refuses to boot! i will not take responsibility for bricked installs!)

---

### Post by stanlick on 2010-12-23
> **KellyLSB said:**
> SOLUTION TO BATTERY NOT SHOWING!

and a couple months later i found the solution (patch attached, and patching instructions below)
[https://bugzilla.kernel.org/show_bug.cgi?id=19602](https://bugzilla.kernel.org/show_bug.cgi?id=19602)


Greetings, unfortunately I badly understand in LINUX, therefore I ask you to help.
After abortive attempt to launch a kernel 2.6.33 by your example, I began to suspect wrong adjustment of a configuration.
I ask you to give me a file of a configuration for a kernel - .config .
My computer: AO521-12Dcc Ubuntu 10.10 Kernel 2.6.33
Thanks.

---

### Post by KellyLSB on 2010-12-23
to get the config just copy your current one via
```
cat /boot/config-`uname -r` > config.new

```

i also know there is a line of code that changed since i uploaded this in the file the patch patches so you will have to go in and manually update the patch... i plan on updating this thread when i get around to recompiling my own kernel again. i been really busy lately though and havent had the time.

---

### Post by stanlick on 2010-12-24
The matter is that at me the working version of a kernel 2.6.35-24. And I should work with a configuration of a kernel 2.6.35, I use it for 2.6.33 :(

---

### Post by KellyLSB on 2010-12-24
Ok those last two posts did not make any sense.

---

### Post by stanlick on 2010-12-29
I have done some abortive attempts to collect a kernel with a patch for ACPI :(
The kernel after compilation doesn't boot.
- There is a possibility to collect a ready packet.deb???

---

### Post by KellyLSB on 2010-12-29
The patch need to be modified a bit. For the latest kernel update.

---

### Post by Hack.The.Pow. on 2010-12-30
I just tried applying this patch to kernel linux-2.6.36.2

I get this output from the command

```
patching file drivers/acpi/ec.c
Hunk #1 succeeded at 731 (offset -50 lines).
Hunk #2 succeeded at 746 (offset -50 lines).
Hunk #3 succeeded at 761 with fuzz 1 (offset -49 lines).
Hunk #4 succeeded at 785 (offset -48 lines).
Hunk #5 FAILED at 871.
1 out of 5 hunks FAILED -- saving rejects to file drivers/acpi/ec.c.rej

```

Can anybody tell me how to manually apply the 5th hunk patch?

Or if that is too complicated with this kernel can you suggest the most recent kernel this works with?

---

### Post by KellyLSB on 2010-12-30
> **Hack.The.Pow. said:**
> I just tried applying this patch to kernel linux-2.6.36.2

I get this output from the command

```
patching file drivers/acpi/ec.c
Hunk #1 succeeded at 731 (offset -50 lines).
Hunk #2 succeeded at 746 (offset -50 lines).
Hunk #3 succeeded at 761 with fuzz 1 (offset -49 lines).
Hunk #4 succeeded at 785 (offset -48 lines).
Hunk #5 FAILED at 871.
1 out of 5 hunks FAILED -- saving rejects to file drivers/acpi/ec.c.rej

```

Can anybody tell me how to manually apply the 5th hunk patch?

Or if that is too complicated with this kernel can you suggest the most recent kernel this works with?

Using the latest ubuntu patched linux sources (linux-source-2.6.35) availible via
```
sudo apt-get install linux-source
```
i managed the patch works with no problems.

If you are using the kernel in the torvalds repository listed in the blog post. you have to make some modifications to the patch to get the final hunk to work. if you post the ```
./drivers/acpi/ec.c.rej
``` and the ```
./drivers/acpi/ec.c
``` file i will post another patch for people using that kernel source.

---

### Post by Hack.The.Pow. on 2010-12-30
> **KellyLSB said:**
> Using the latest ubuntu patched linux sources (linux-source-2.6.35) availible via
```
sudo apt-get install linux-source
```i managed the patch works with no problems.

If you are using the kernel in the torvalds repository listed in the blog post. you have to make some modifications to the patch to get the final hunk to work. if you post the ```
./drivers/acpi/ec.c.rej
``` and the ```
./drivers/acpi/ec.c
``` file i will post another patch for people using that kernel source.

Im using the kernel I downloaded from [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/) 

Here are the files you wanted.

Thanks for the help

---

### Post by KellyLSB on 2010-12-30
Ok this patch should do the trick... Im not used to writing patches  so i cant guarentee if it will...

if it doesnt heres the manually patched c file as well...
the .rej file is not important so i did not re attach it.

note: if you decide to run my patch file use a fresh kernel source!

if you decide to use the attached c file just overwrite your ./drivers/acpi/ec.c file. with the file in the archive.

best of luck.

---

### Post by Hack.The.Pow. on 2010-12-30
Wow thanks a ton man.  I'll update soon to let you know if it worked

---

### Post by Hack.The.Pow. on 2010-12-31
SUCCESS!!!!!!

....well sort of.

After I compiled and installed the kernel the battery module worked perfectly!!

However on boot I recieved the following error message(Not exact message but pretty close)

```
Firmware bug: PCI MMConfig at (Mem 0xe0000000-0xe03fffff) not resolved in ACPI motherboard resources
```

However it booted fine and everything seemed normal.  Then when I went to install the proprietery ATI/AMD video Drivers I experienced some problems.  Instead of just the video drivers being there, there was a ton of other ones such as mouse, ethernet, usb, etc.  Some are activated and some are not. Whenever I try and activate one that isn't activated I get a message that the installation failed and to check /var/log/jockey.log for error messages.  (file is attached in archive)

Then when I try to install the video drivers I get the error message SystemError: installArchives() failed.  

I have also noticed that whenever I try and install(or uninstall) a package from the software center it tries to install fglrx as well and gives an error message that it failed to install(the package i intended to install actually did install).  I get this error message.

```
Error! Bad return status for module build on kernel: 2.6.36.2 (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
```

This file is also attached.

If you can give me any help with it I'd be super appreciative.

Thanks

---

### Post by KellyLSB on 2010-12-31
Hmm im gonna guess its because you are compiling a un modded kernel. Try applying the orginal package to one of the ubuntu pre patched sources. You can download a ubuntu pre patched kernel source by running
```
sudo apt-get install linux-source
```
The source package will then be downloaded to /usr/src

---

### Post by Hack.The.Pow. on 2011-01-04
Soooooo just an update.

After trying to compile over 10+ kernels I've finally figured out a way to make it work.  

A couple of them compiled successfully but failed to load and froze on the startup screen.  A couple failed to compile because of random error with the kernel.  And some that did boot successfully for some reason made my netbook launcher screen disappear.  

After booting one of those last kernels made the launcher disappear on all other stock kernels as well I decided to reinstall.

After I reinstalled and compiled yet another kernel the launcher disappeared again.  So after a little investigation I discovered that for some reason it saved my xorg.conf as xorg.conf.old so i essentially had no xorg.conf.  After I restored that everything seemed to be fine.

So i just wanted to thank ya for your help.  I'll give a link to this thread in my own thread which nobody replied too......

---

### Post by stanlick on 2011-01-06
Greetings, seem to me at me the head will burst :(
That Mahlo that I communicate with you through a translator, and in Linux isn't strong.
Has collected already many kernels, from them one more hasn't earned.
The order of my actions:
1. I load the last kernel under your link.
2. I unpack it in ```
/usr/src/
```
3. I copy your patch in a folder with a kernel ```
/usr/src/linux-source-2.6.35
```
4. ```
patch -p1 < ./ao521-acpi.patch
```5. ```
make mrproper
```6. ```
cat /boot/config-`uname -r` > config.new
```7. ```
make oldconfig
```On the last kernel of questions &#1085;&#1077;&#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080; &#1085;&#1077;&#1073;&#1099;&#1083;&#1086;, and here on 33 was nearby 15, I always answered Y or M/
8. ```
make bzImage modules modules_install install
```9. update-grub
10. reboot
:confused:

---

### Post by stanlick on 2011-01-09
Thank you for your help. I found a detailed description of the process on the Russian site. Made for the core 2.6.35! - works:)
[http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/](http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/)

---

### Post by KellyLSB on 2011-02-14
Hey peoples was searching, and i found a headphone port fix, and he claims hes got a way to fix bluetooth too. but i havent tried...

[http://ubuntuforums.org/showthread.php?t=1621437](http://ubuntuforums.org/showthread.php?t=1621437)

---

### Post by kuld on 2011-05-10
Hi all!
what about 11.04 and 2.6.38 kernel?
does patch work?

---

### Post by KellyLSB on 2011-05-10
I made it work once. but i have not since tried again.

---

### Post by Bah-Ripple-Phi on 2011-07-23
> **kuld said:**
> Hi all!
what about 11.04 and 2.6.38 kernel?
does patch work?

This patch, which i found at [http://glotych.ru/ustanovka-ubuntu-11-04-na-acer-aspire-one-521/](http://glotych.ru/ustanovka-ubuntu-11-04-na-acer-aspire-one-521/) will work for 2.6.38

---

### Post by caledvwlch on 2011-08-07
Alright, I am attempting to follow the directions given at [http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/](http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/) as close as I can.  
However, once I get to the part where I enter ```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
```in the terminal I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-2.6.35-22-generic'
E: Unable to find a source package for linux
```I figure this must have something to do with the source.list file, but I'm not sure what to add to it.
Any help would be appreciated :)

---

### Post by dadopap on 2011-09-06
I have recompiled the Kernel for 11.04 64 bit, everything works perfectly!

thanks folks!

Since it takes time to do I decided to upload it. You can find it at:

[http://www.megaupload.com/?d=3A2ZZL30](http://www.megaupload.com/?d=3A2ZZL30)

you have to bunzip and untar it and then install both deb packages doing:

```

tar xvfj linux-2.6.38-x64-acpipatched_ao521.tar.bz2

sudo dpkg -i linux-image-2.6.38.8-dpap_2.6.38.8-dpap-10.00.Custom_amd64.deb

sudo dpkg -i linux-headers-2.6.38.8-dpap_2.6.38.8-dpap-10.00.Custom_amd64.deb

```

---

### Post by Spackotus on 2011-10-31
I got tired of Windows on this netbook so I got Ubuntu...
After some research I installed the graphic driver, but I still have no idea, how to fix the "Battery Not Detected" problem!
I have the newest Kernel.

Can someone help me because I am a new Ubuntu user!

---

### Post by kuld on 2012-01-26
does anybody use 11.10 and kernel 3.0.XX with AO521?
battery not detected :(
old patch don't resolve this problem :(

---

### Post by melT4 on 2012-02-03
Can't help you. But I confirm it's also doesn't work for me. (Ubuntu 11.10 or Lubuntu 11.10).

---

### Post by djk1o on 2012-02-28
i had the same problem, BUT i have the solution!!!
please read here: [ubuntu 11.10 on ao521]("http://djk1o.blogspot.com/2012/02/number-two.html")

---

