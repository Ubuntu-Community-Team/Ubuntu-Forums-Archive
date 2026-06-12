---
title: "Cannot activate wireless networking"
date: 2010-07-27
forum: Hardware
---

### Post by silkworm2.5 on 2010-07-27
Hi.
When using my sisters Amilo laptop, I cannot activate the wi-fi on it. I have tried Ubuntu 9.10 and 10.04, as well as Kubuntu 10.04. It's a standard Fn + F1 key combo. Strangely, all other key functions work, like the volume and brightness controls.
Any ideas of what I can try?

---

### Post by roger_1960 on 2010-07-27
Hi

If it is a dual boot set up, or you are using wubi or Live CDs, boot an OS in which the wifi works and leave it on when you shut down.  Then try again with Ubuntu.

---

### Post by silkworm2.5 on 2010-07-27
I am using alive USB. Unfortunately, whenever it shuts down it turns of the wi-fi automatically. And it wont activate during POST or anything. Whenever it is used in windows however, a dialogue box opens with options of on or off with (I think it's called) radio buttons. (The round ones).

---

### Post by ultrageeky on 2010-07-27
Take a look at [http://ubuntuforums.org/showthread.php?t=1538766](http://ubuntuforums.org/showthread.php?t=1538766)

You will likely find the laptop has a WiFi kill switch that is activated via a function key (fn) and an F# key (e.g F2, F5 etc...).

If you're duel booting, try enabling wireless in Windows then rebooting to Linux. If that doesn't work, use the guide on page 2 of the above link. You probably won't need new firmware files but you will likely need to block out the 13th pin (pin six as counted from the front-left) of the card.

There's a link to an informative madwifi page on the first page of the above link.

---

### Post by silkworm2.5 on 2010-07-27
I am not dual booting.I am running from a live USB ([www.pendrivelinux.net](www.pendrivelinux.net)) and use that. I can't try the pin 13 sellotape thing because the laptop is not mine. I did follow that link to the mad wifi thing and got the drivers from there,but I don't know how to install them. can you help me with that at all?

---

### Post by ultrageeky on 2010-07-27
Post the link to the download. Different packages install in different ways; each usually includes an installation guide (readme/install). I'll take a look at the download file for you.

Covering pin 13 won't harm the laptop or network card. It does require a bit of skill to accomplish - I put a strip of tape over it then carefully used a stanley knife to cut around the section I needed to keep covered.

---

### Post by silkworm2.5 on 2010-07-28
Thanks ultrageeky. they are on this page: [HTML]http://www.knights-of-camelot.nl/?page_id=12[/HTML]

But I just can't do the pin thing. The Laptop isn't mine and I'm not allowed to open it up.

---

### Post by ultrageeky on 2010-07-28
O.K, these installation instructions might seem a bit longwinded to some people but if I can help you move around the Linux command line a little better I'll be helping you more in the longterm.

The download page includes installation instructions. They are,

```
tar -xzvf acerhk-current.tgz    * where current is version
cd acerhk-0.5.35
make && make install
 modprobe acerhk force_series=6805 autowlan=1

```

Those instructions are fine provided you know a little about installing Linux software. They fail to explain where you need to within your directory structure and how to enter the listed commands. Confusing and frustrating, I think.

To start, I'll assume you have already downloaded the compressed file (acerhk-0.5.35.tgz):


[LIST=1]
[*]Open a terminal (go to Applications>Accessories>Terminal),
[*]Type "**ls**" at the prompt (no quotes) to **l**i**s**t the files and directories beneath your current location,
[*]Unless changed by you, your sister or another user, the default download location will be "Downloads". You will see it listed (in blue) as "**[COLOR=Blue]Downloads[/COLOR]**". Type "**cd Downloads**". This instructs the terminal to **c**hange **d**irectory to **Downloads**. Linux is case sensitive i.e **downloads** is different to **Downloads** and **DOWNLOADS** so you must type it as it is listed.
[*]Again, type "**ls**" to list the files and folders in the **Downloads** directory. You will see one entitled "**[COLOR=Red]acerhk-0.5.35.tgz[/COLOR]**". Now type "**tar -xzvf** **[COLOR=Red]acerhk-0.5.35.tgz[/COLOR]**" to unpack the tgz archive file (zip file).
[*]Type "**ls**" and you will now see "[COLOR=Blue]**acerhk-0.5.35**[/COLOR]" listed. Change directory to it with "**cd acerhk-0.5.35**". Notice the colour differences - the Linux command line allows users to differentiate between files and directories as well as file types by displaying them in different colours.
[*]Type "**ls**" to list the files within the [COLOR=Blue]**acerhk-0.5.35**[/COLOR] directory. You will see one called "makefile". "makefile" is the one we're going to invoke to install the application.
[*]Type "**make**"
[*]Type "**make install**"
[*]Type "**modprobe acerhk force_series=6805 autowlan=1**"
[*]Restart the laptop.
[/LIST]

Here are some reference pages for you:


[LIST=1]
[*][http://www.linux.org/lessons/beginner/](http://www.linux.org/lessons/beginner/)
[*][http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-get-started.html.en_GB](http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-get-started.html.en_GB)
[/LIST]

Take a look at the links in my signature too.

---

### Post by silkworm2.5 on 2010-07-28
Sorry, but when I type 'Is' it says 'Is: Command not found'
What should I do?

EDIT - Damn, thats an L isn't it? My bad >.<

---

### Post by silkworm2.5 on 2010-07-28
Damn, When I try to download the file it saves it with 0 bytes and it cannot read it. I'll try again tomorrow. Maybe the website is having problems.

---

### Post by silkworm2.5 on 2010-07-29
Hay ultra. Imanaged to get the file now, but the instalation fails at the 'make' command.What should I do?

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ ls
acerhk-0.5.35  acerhk-0.5.35.gz
ubuntu@ubuntu:~/Downloads$ tar -xzvfacerhk-0.5.35.gz
acerhk-0.5.35/
acerhk-0.5.35/doc/
acerhk-0.5.35/doc/FAQ
acerhk-0.5.35/doc/IOCTL
acerhk-0.5.35/doc/acertm.def
acerhk-0.5.35/doc/md95400.def
acerhk-0.5.35/doc/keycodes
acerhk-0.5.35/NEWS
acerhk-0.5.35/INSTALL
acerhk-0.5.35/README
acerhk-0.5.35/COPYING
acerhk-0.5.35/AUTHORS
acerhk-0.5.35/Makefile
acerhk-0.5.35/acerhk.c
acerhk-0.5.35/acerhk.h
ubuntu@ubuntu:~/Downloads$ ls
acerhk-0.5.35  acerhk-0.5.35.gz
ubuntu@ubuntu:~/Downloads$ cd acerhk-0.5.35
ubuntu@ubuntu:~/Downloads/acerhk-0.5.35$ ls
acerhk.c  acerhk.h  AUTHORS  COPYING  doc  INSTALL  Makefile  NEWS  README
ubuntu@ubuntu:~/Downloads/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ubuntu/Downloads/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ubuntu/Downloads/acerhk-0.5.35/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ubuntu/Downloads/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
ubuntu@ubuntu:~/Downloads/acerhk-0.5.35$ make install
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ubuntu/Downloads/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ubuntu/Downloads/acerhk-0.5.35/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ubuntu/Downloads/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
ubuntu@ubuntu:~/Downloads/acerhk-0.5.35$ modprobe acerhk force_series=6805 autowlan=1
FATAL: Module acerhk not found.
ubuntu@ubuntu:~/Downloads/acerhk-0.5.35$ 

```

---

### Post by ultrageeky on 2010-07-30
Hi Silkworm (used to play the game on 8-bit, by the way). I apologise for my response delay, I had to resolve my accounts. I'm glad to see you realised that "ls" was "LS" in lowercase and not "IS".

I read the "install" document in the download's "doc" folder. It looks like you need to do this:

```
make
make acerhk.ko
make install
```

Then you will need to copy the file "acerhk" folder to **/usr/src/linux-headers-xxxx/drivers/** (where xxxx is a number). I don't know which linux-headers-xxxx you should put it into, I'd copy it into them all just to ensure the right one has them.

You need to read the documents in the "doc" folder to learn more about the driver's installation.

---

### Post by silkworm2.5 on 2010-08-02
Ah, sorry but I still can't get anything to work. Here's the results of trying the make "acerhk.o/ko" commands.

```
silkworm205@ubuntu:~/Downloads/acerhk-0.5.35$ make acerhk.o
cc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acerhk.ko acerhk.c
acerhk.c:39:26: error: linux/config.h: No such file or directory
acerhk.c:3100:2: error: #error This driver is only available for X86 architecture
make: *** [acerhk.o] Error 1
silkworm205@ubuntu:~/Downloads/acerhk-0.5.35$ 
silkworm205@ubuntu:~/Downloads/acerhk-0.5.35$ make acerhk.ko
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/silkworm205/Downloads/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/silkworm205/Downloads/acerhk-0.5.35/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/silkworm205/Downloads/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
silkworm205@ubuntu:~/Downloads/acerhk-0.5.35$ 

```

Sorry but I have no idea how to work with terminals and such. Or the technical side of Linux. 

PS, sorry for my late reply. I've been away over the weekend.
PPS, what game? :|

---

### Post by utilitytrack on 2010-08-03
> **silkworm2.5 said:**
> Thanks ultrageeky. they are on this page: [HTML]http://www.knights-of-camelot.nl/?page_id=12[/HTML]But I just can't do the pin thing. The Laptop isn't mine and I'm not allowed to open it up.

Oh, third party kernel module... It's bad think, because that's may be security hole

---

### Post by ultrageeky on 2010-08-03
That's a good point utilitytrack.

Silkworm, I really have no other answers for the installation. Sorry :(

You could try ndiswrapper (it's in the repositories) and use it to install the WiFi card's Windows WiFi driver which might have an override for the laptop's WiFi kill switch. Alternatively, tell your sister that Doc. Ultrageeky insists she let you use a bit of sticky tape on her WiFi card :)

BTW, The WiFi adapter is accessible from the underside of the laptop (it has a cover screwed over it). Once its cover is removed it will be held in place by two plastic arms, push them to the side and the card will slot out. Make a note of which pins the two aerial wires are connected to. Google for "<laptop name> disassembly instructions" or "<laptop name> wifi card replacement tutorial"

---

### Post by silkworm2.5 on 2010-08-03
Ok i got NDisWrapper and got it tolinkup with what I believe to be my windows wireless driver. How do I activate it? the FN key combo does nothing.

---

### Post by ultrageeky on 2010-08-04
> **silkworm2.5 said:**
> Ok i got NDisWrapper and got it tolinkup with what I believe to be my windows wireless driver. How do I activate it? the FN key combo does nothing.

The function key combination activates/deactivates the WiFi kill switch (which is controlled by pin 13, lolol).

Some WiFi card drivers install a control panel that allows you to deactivate the kill switch. Try installing the WiFi card's software using Wine or PlayOnLinux then see whether you can deactivate the kill switch with it.

I went through all of this with my nephew's laptop (Toshiba Satellite A30) and the only solution that worked was the "masking the pin" one. It took me 3 days to activate it (lots of messing around until someone pointed out how to hack the card).

It would be nice were there a laptop keyboard locale option. I don't think there is but you could Google for one.

I've just done a quick search and discovered a program called xev which can be used to determine key bindings. [Here are some instructions]("http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings")

[This might also help]("http://ubuntuforums.org/archive/index.php/t-83703.html").

[And so might this]("http://www.google.co.uk/#hl=en&q=ubuntu+xev+laptop+wifi&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=a53e9ae07f1cc2a8").

I know it's frustrating to nearly have everything installed only to be harassed by laptop manufacturers who insist on putting silly software WiFi kill switches into their laptop keyboards. They must know it causes problems for Linux users; I'm sure they do it to test our skill and resolve.

---

### Post by ultrageeky on 2010-08-05
In KDE there is an Acer Laptop keyboard layout (System Settings>General>Regional and Language>Keyboard Layout). Maybe there's a similar Keyboard Locale in Gnome. I suspect that the laptop layout will activate the FN key combinations.

---

