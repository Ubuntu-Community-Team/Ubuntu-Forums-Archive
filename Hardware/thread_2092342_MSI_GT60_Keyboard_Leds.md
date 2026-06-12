---
title: "MSI GT60 Keyboard Leds"
date: 2012-12-07
forum: Hardware
---

### Post by Mr.EJ on 2012-12-07
I'm trying to get my MSI GT60 Keyboard Leds to work with linux, sure enough there is the capacitive button that switches the plain lights on or off but i'd love to have the additional functionality as exist in the KLM windows software.

I've located this [post]("http://www.insanelymac.com/forum/topic/284486-msi-gt6070780783-ge6070-gx780-keyboard-led-enabler/") that links to a [program]("http://www.insanelymac.com/forum/topic/284486-msi-gt6070780783-ge6070-gx780-keyboard-led-enabler/") that was created to do it but i'm unable to compile and install with the usual make  && make install procedure.

Can someone assist me with either modifying this little program so that it can compile or posting a howto so i can do the modification?

I'm also not too comfortable with not being able to compile that hid.c for myself hopefully someone could restructure the package so that it either uses a preinstalled library or provide the necessary additional files/framework that will allow compilation.

---

### Post by luxexcudo on 2012-12-21
Hi,

I tried the same and had a look over the sourcefiles (I'm not a programmer) but as far as i understand so far in the makefile a library is called

> LIBS=-framework IOKit -framework CoreFoundation

if i put it in Google i found:
[http://www.opensource.apple.com/source/IOKitUser/IOKitUser-376/IOKitLib.h?txt](http://www.opensource.apple.com/source/IOKitUser/IOKitUser-376/IOKitLib.h?txt)
where it says:

/*  * Copyright (c) 1998-2000 Apple Computer, Inc. All rights reserved.  *  * @APPLE_LICENSE_HEADER_START@  *   .....  */ /*  * HISTORY  *  */  /*  * IOKit user library  */

..... its a lib for the Mac kernel i didn't find any port for Ubuntu so the only hope is 

that someone rewrite the programm with Ubuntu libs provided in the essentials-build package.

---

### Post by Mr.EJ on 2012-12-21
hmm interesting....
hope someone helps out here

> **luxexcudo said:**
> Hi,

I tried the same and had a look over the sourcefiles (I'm not a programmer) but as far as i understand so far in the makefile a library is called

> LIBS=-framework IOKit -framework CoreFoundation

if i put it in Google i found:
[http://www.opensource.apple.com/source/IOKitUser/IOKitUser-376/IOKitLib.h?txt](http://www.opensource.apple.com/source/IOKitUser/IOKitUser-376/IOKitLib.h?txt)
where it says:

/*  * Copyright (c) 1998-2000 Apple Computer, Inc. All rights reserved.  *  * @APPLE_LICENSE_HEADER_START@  *   .....  */ /*  * HISTORY  *  */  /*  * IOKit user library  */

..... its a lib for the Mac kernel i didn't find any port for Ubuntu so the only hope is 

that someone rewrite the programm with Ubuntu libs provided in the essentials-build package.

---

### Post by PaNaVTEC on 2013-01-01
Hi guys,

luxexcudo called me to solve this fail in compilation for linux. This is the unix version of this app:

[https://dl.dropbox.com/u/5977601/MSI_GT_GE_Led_Enabler-master-unix.tar.gz](https://dl.dropbox.com/u/5977601/MSI_GT_GE_Led_Enabler-master-unix.tar.gz)

Also you need to:

sudo apt-get install build-essential libudev-dev libusb-1.0-0-dev libfox-1.6-dev autotools-dev

to get dependencies for compilation. I dont have ubuntu installed only Win7 and OSX so I can test it but luxexcudo says is working (with little problems). 

enjoy :)

---

### Post by Dani716 on 2013-01-09
Hi, I'm new to Ubuntu and I'm having problems installing the unix app.
I've followed some guides on compiling source files and I've installed the dependencies as suggested by PaNaVTEC, but when I type
./configure
in the terminal it tells me 
**bash: ./configure: No such file or directory**
Could someone help me please?

---

### Post by luxexcudo on 2013-04-21
Hi Dani716 [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1774745")

Yesterday, I just read your post. The attachment below is the msiledenabler from PaNaVTEC as a allready compiled binary (43K). Im also not so familiar with the compiling stuff, but i got a working on out ... If you want to use, here how i get it running:

Copy it to /usr/bin/ so every user reaches it, put the rights with chmod to a "555" and make it also "suid" (like passwd) because it require to be root. I read the code so far as i can understand it with a bit of logic and my old programming knowledge (when i was writing Programms i used linenumbers and GOTO ;-) . I understand that it sends a 8 byte array in hex to the keyboard in a special format which includes color and intensity, but the array isn't 100% correct jet.  

 I also put the init script beside just copy it to /etc/init.d/ and use update-rc.d to include it to your start process (the color you choose you have to edit in the init file)

I hope it helps you a bit :-)

Lux Excudo

---

### Post by Ludovic_Martin on 2013-09-16
Hi !

The [https://dl.dropbox.com/u/5977601/MSI_GT_GE_Led_Enabler-master-unix.tar.gz](https://dl.dropbox.com/u/5977601/MSI_GT_GE_Led_Enabler-master-unix.tar.gz) link seems to be broken...
Does anybody can help my to get this file ?

Thanks...

---

### Post by guy.labbe23 on 2013-12-15
Hi

Thank you for posting your code and instructions, very nice :) Have you had a chance to sort out the color encoding? I mean, when I request red it gives blue and so on...

Cheers
Guy

---

### Post by ubulindy2 on 2014-03-15
Hi, I found this on another thread, but Im unable to get to it, and from what I understand it's the precompiled binaries? It takes me to a board to login, ect, which I do, no idea whats wrong. I have the MSI GT60 OC-US trying desperately to get KLM/led manager working.: 
[COLOR=#000000][INDENT]
Hi Dani716 

Yesterday, I just read your post. The attachment below is the msiledenabler from PaNaVTEC as a allready compiled binary (43K). Im also not so familiar with the compiling stuff, but i got a working on out ... If you want to use, here how i get it running:

Copy it to /usr/bin/ so every user reaches it, put the rights with chmod to a "555" and make it also "suid" (like passwd) because it require to be root. I read the code so far as i can understand it with a bit of logic and my old programming knowledge (when i was writing Programms i used linenumbers and GOTO :wink: . I understand that it sends a 8 byte array in hex to the keyboard in a special format which includes color and intensity, but the array isn't 100% correct jet. 

I also put the init script beside just copy it to /etc/init.d/ and use update-rc.d to include it to your start process (the color you choose you have to edit in the init file)

I hope it helps you a bit :smile:

Lux Excudo[/INDENT][/COLOR]
[COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG] Attached Files
[LIST]
[*][IMG]http://ubuntuforums.org/images/attach/zip.gif[/IMG] [msiledenabler.zip]("http://ubuntuforums.org/attachment.php?attachmentid=241600&d=1366545032") (15.5 KB, 31 views)
[*][IMG]http://ubuntuforums.org/images/attach/zip.gif[/IMG] [msiledenbler.init.zip]("http://ubuntuforums.org/attachment.php?attachmentid=241601&d=1366546661") (536 Bytes, 26 views)
[/LIST]
[/COLOR]

---

### Post by leanid.chaika on 2014-06-21
Hi! I have 64 bit ubuntu and current binary not working for me. Please can sameone give me source of this program(linux version)

---

### Post by leanid.chaika on 2014-06-21
found: [https://www.dropbox.com/s/xtm1k0rm3d1rflw/MSI_GT_GE_Led_Enabler-master-linux.zip](https://www.dropbox.com/s/xtm1k0rm3d1rflw/MSI_GT_GE_Led_Enabler-master-linux.zip)

---

### Post by rayfenwindspear on 2014-08-22
I did this research a little while back and found [this question here]("http://askubuntu.com/q/284580/308852"). Read my answer to the question and follow the instructions. This is a completely different solution that uses node.js to activate and control the keyboard backlight. It works for me on Ubuntu 14.04 and can be customized however you want. It just requires some manual editing of individual profiles if you want more than one. Just create a file for each profile and run it to change the keyboard. You could create desktop icons to do it after setting it all up if you wanted to.

---

