---
title: "Can't make Realtek ALC880 HDA work"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2005-05-25
Hello All!
First of all, I'm a linux newbie so please excuse me for my silly questions. :smile:

I've got Asus P4GPL-X motherboard recently. It's all great about it except for one thing, it's TOO modern for the current software! :smile: One has to install drivers for Gigabit LAN and Sound in Linux and even Windows. I have installed Marvell Yukon Gigabit LAN drivers in Linux finally, and it works (overwise how could I write this post?) but I still have problems with my sound card! Please post step by step guide how to install this driver or tell me where do I find this information. I have tried many things yesterday, but came to a conclusion that I need a helping hand here. Thank you!

---

### Post by hostile on 2005-05-25
I'm curious about this myself.

I have an Asus Z7100 laptop, and everything works perfectly, except the sound...

Anyone with any ideas?

---

### Post by PryGuy on 2005-05-27
People seem to ignore us... :(

---

### Post by hostile on 2005-05-27
[QUOTE=PryGuy]People seem to ignore us... :([/QUOTE]


Apparently, at the time of our posts, the driver was not yet ready.

Here it is, hot off the press (posted to RealTek's site 05/26/05):

[Click.](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True)

Good luck!

---

### Post by PryGuy on 2005-05-28
Thanks, mate!
Downloading it, hope it will help!!!
Thanks again! I feel so lonely without my Pink Floyd! :)

EDIT: What do I do to make my poor little integrated sound card work?!
I download the damn driver, extract the alsa-driver-1.0.9rc4a folder from there,
./configure
make
make install
./snddevices
reboot

It compiles and installs like a breeze, not a single error message, I reboot and
NOW WHAT?! :mad:

---

### Post by hostile on 2005-05-28
[QUOTE=PryGuy]It compiles and installs like a breeze, not a single error message, I reboot andNOW WHAT?! :mad:[/QUOTE]


Well, I havent tackled yet myself, but I'm assuming you edit your modules.conf file to reflect the installed driver...

When I have some spare time this weekend, I'll look at it and report back.

Good to know it compiles though...

---

### Post by PryGuy on 2005-05-28
...and the question is: how do i know what module name to write there?

---

### Post by hostile on 2005-05-28
[QUOTE=PryGuy]...and the question is: how do i know what module name to write there?[/QUOTE]


Isnt it in the readme file?

---

### Post by PryGuy on 2005-05-28
There certainly is, and it says:> Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)So I refer to the attached modules.conf and here it is: > #alias sound-slot-0 via82cxxx_audio	//remark this line, this is default audio driver

#====== added those lines =============
alias char-major-116 snd
options snd major=116 cards_limit=1
# -- Azalia controller -----------------------------
alias snd-card-0 snd-azalia
options snd-azalia index=0 id="Azalia"
#--- Intel 8x0  , SiS 7012 and NVidia----------
#alias snd-card-0 snd-intel8x0
#options snd-intel8x0 index=0 id="ICH"
#--- Via8233 Via686a  -------------------------------
#alias snd-card-0 snd-via82xx
#options snd-via82xx index=0 id="VIA"
#--- ATI  -------------------------------
#alias snd-card-0 snd-atiixp
#options snd-atiixp index=0 id="ATI"
//=================================
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
#=================================
post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || :
 I have inserted it into /etc/modules.conf and tried experimenting with the Azalia and Intel8x0 modules but there's no luck though system starts with no errors :? Bet one has to do something else to make it work. Yet I've noticed that the esd demon says:> /dev/dsp: No such file or directory

---

### Post by hostile on 2005-05-29
[QUOTE=PryGuy]There certainly is, and it says:So I refer to the attached modules.conf and here it is:  I have inserted it into /etc/modules.conf and tried experimenting with the Azalia and Intel8x0 modules but there's no luck though system starts with no errors :? Bet one has to do something else to make it work. Yet I've noticed that the esd demon says:[/QUOTE]


Hrm... I guess an easy thing to do it maybe see a modules.conf which has another RealTek codec and go from there...

Maybe we should email RealTek directly?

I'm going to see if the Intel one works for me... I'll try it in a bit, or tomorrow if I run out of time tonight... 

I'll report back.

 :)

---

### Post by PryGuy on 2005-05-29
Thank you!
I don't think it will work for you if you really have ALC880 HDA of course. Hardware is the same. To tell you the truth I'm really lost in all these different HDA codec realizations. And I'm thinking of building yet another PC with my old Albatron 865PE mainboard especially for Ubuntu because it has a very typical AC'97 sound codec. Again, it seems that our hardware is too modern for Ubuntu. It's too modern for Windows as well, but I have to say one good word for Windows here (sorry, for that!), it has a very nice and simplified driver installation procedure.

---

### Post by hostile on 2005-05-29
[QUOTE=PryGuy]Thank you!
I don't think it will work for you if you really have ALC880 HDA of course. Hardware is the same. To tell you the truth I'm really lost in all these different HDA codec realizations. And I'm thinking of building yet another PC with my old Albatron 865PE mainboard especially for Ubuntu because it has a very typical AC'97 sound codec. Again, it seems that our hardware is too modern for Ubuntu. It's too modern for Windows as well, but I have to say one good word for Windows here (sorry, for that!), it has a very nice and simplified driver installation procedure.[/QUOTE]


If the driver compiles, it will work. We just have to figure out how to set up ALSA/OSS to use it properly...

---

### Post by PryGuy on 2005-05-30
I can't find any information so far. Does anybody have the same hardware on earth or we're just two customers I wonder? :)  Realtek suppoerts Linux really bad, shame on them. So, we'll have to sit and wait till the 5.10 version will be released. Hope the problem will be fixed there...
And gurus, help please!!!

---

### Post by hostile on 2005-05-30
[QUOTE=PryGuy]I can't find any information so far. Does anybody have the same hardware on earth or we're just two customers I wonder? :)  Realtek suppoerts Linux really bad, shame on them. So, we'll have to sit and wait till the 5.10 version will be released. Hope the problem will be fixed there...
And gurus, help please!!![/QUOTE]

Okay... I don't know if this helps or not, but I read on a RedHat forum that it's pretty easy to make this work, you just have to  recompile your kernel with all sound drivers removed, then install this driver using the examples in the included modules.conf.

---

### Post by PryGuy on 2005-05-30
[QUOTE=hostile]it's pretty easy to make this work, you just have to  recompile your kernel[/QUOTE]Well, it's not that easy for me! :) But I will RTFM! :) I like Ubuntu, probably the best Linux I've seen!

---

### Post by PryGuy on 2005-06-03
hostile, could you tell me which of the modules worked for you finally? I tried snd_intel8x0 but it doesn't work =( Other module names do not make sense at all :???:

---

### Post by hostile on 2005-06-06
[QUOTE=PryGuy]hostile, could you tell me which of the modules worked for you finally? I tried snd_intel8x0 but it doesn't work =( Other module names do not make sense at all :???:[/QUOTE]


=(

Nothing yet.

---

### Post by PryGuy on 2005-06-07
Well, I have solved this problem finally! :) One just had to look at the ./configure output more carefully, for some reason I had two kernels installed in my system and the link was on the other kernel, so I had everything installed in another kernel. I have reinstalled Ubuntu and it worked fine! Yet you don't even have to add anything to /etc/modules, just reboot your PC after the driver installation and it will automatically find your device! Guess that's what the "hotplug" is for! :)
Good Luck!

---

### Post by hostile on 2005-06-07
I was missing the correct kernel headers, so I installed them, configured, make, make install, snddevices, reboot, and it worked like a charm.

Glad we got it solved!

*high five*!

 :D

---

### Post by robio376 on 2005-06-22
Newb post but same hardware
Realtek ALC880
I have been following your post and I can't get past ./configure,
I've tried as root and an user Here is what I get:

root@thermdnetwork:~/linux_r32/alsa-driver-1.0.9rc4a# ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details

So how do I get that to install?

---

### Post by hostile on 2005-06-23
For some reason you don't have gcc installed. Fire up synaptic, install gcc, and try again.

---

### Post by Deomanh on 2005-07-04
Greets

I'm stuck with this chipset... bought a laptop (asus a6va) with Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04) and installed alsa with hda-intel and intel8x0 but none of them work. Well actually they do except i dont hear anything, even though i have the channels unmuted in alsamixer. Have tried several config combinations, recompiled the kernel, but nothing works. Any clues? I have also attempted to compile the kernel with sound support embedded instead of module...

thanx

EDIT: Fixed it! Here's my configs:

/etc/modules:
...
snd-pcm-oss
snd-seq-oss
snd-mixer-oss
...

/etc/modprobe.d/sound:
options snd-hda-intel model=w810 position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Notes:
 - the position_fix option is set to 1 because by default (0) it produces some clicks during playback (refer to alsa-driver-1.09b/alsa-kernel/Documentation/ALSA-Configuration.txt)
 - I forced the model to the closest i could find to my laptop (also in the same txt file above)
 - I also noticed that before, when i rebooted, the files /dev/dsp* and some others wouldn't appear, so i had to do ./snddevices again (/dev/dsp is a link to /dev/dsp0). Not sure if thats really necessary though, think thats just for OSS emulation

Works like a charm now!

---

### Post by LeTon on 2005-07-04
Dear Deomanh

If it isn't too much of a trouble...could you post step by step what things you did to get  sound from your asus -for total noobs like me?
I also have a asus laptop(z33a) with the same chipset...and i can't  get that sound working!
Thank you in advance!

P.S.

I even get this when trying alsamixer:

function snd_ctl_open failed for default: No such file or directory

Sure ,I've seen at least one post where our friend had the same return...and followed the instructions given to him...so far no  ](*,) luck

May be there is anybody in this forum who lives in NYC?
Would be glad to invite you for a cup of (insert necessary) and help me to config this mashine. :)

---

### Post by Varanger on 2005-07-08
Hi everyone!

I have alread made this soundcard work. However, I am getting a very scratch sound. I've tried with position_fix=1 and position_fix=2 but still getting the same scratchy output.

My mainboard is an Intel D915GEV and the lspci output for the soundcard is the following:

> 0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

I've tried with every version since Hoary's ALSA 1.0.8 up to 1.0.9b  (including the rc ones) and getting the same scratchy sound...

Did anyone have the same problem?

Thanks,
Varanger

---

### Post by GrootBrak on 2005-08-01
I've got the D915GEV motherboard as well. Got nowhere with sound. Got the same response from alsamixer as below. I still have only piece and quite. Got a chap on linuxquesteions trying real hard to help me out. We got to a point where he found my kernel is not correct. I am still trying to figure that bit out.

> I even get this when trying alsamixer:

function snd_ctl_open failed for default: No such file or directory

I still have only piece and quite. Got a chap on linuxquesteions trying real hard to help me out. We got to a point where he found my kernel is not correct. I am still trying to figure that bit out. How the heck do you change/update kernels? I am supposed to have the kernel in /usr/src, but there was nothing in that folder. 

If anyone here can add some info, please post it here. I am unable to ./configure without errors.

---

### Post by adrislayer on 2005-08-01
hi, I have the same mainboard as GrootBrak and after some tries I have now sound.

And it's not scratchy any more. Everthing just works fine !

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=345819&perpage=15](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=345819&perpage=15)

here is the post made bye GrootBrak with another nick on another forum.

[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

this worked for me without any problems.

```
uname -r
sudo apt-get install linux-header-x-x-x restricted
sudo apt-get install build-essential restricted
sudo apt-get install ncurses-dev

```
I have installed all this to compile without errors. You must replace x-x-x with what you got with uname -r.
PS: I don't know if "restricted" works, but this should install the proper linux-header and not another one.

for the next: goto [www.alsa-project.org](www.alsa-project.org) and download driver, lib, oss, utils or just copy this:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9b.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.9.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.9a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.9.tar.bz2

bunzip2 alsa-driver-1.0.9b.tar.bz2
tar -xvf alsa-driver-1.0.9b.tar
bunzip2 alsa-lib-1.0.9.tar.bz2
tar -xvf alsa-lib-1.0.9.tar
bunzip2 alsa-utils-1.0.9a.tar.bz2
tar -xvf alsa-utils-1.0.9a.tar
bunzip2 alsa-oss-1.0.9.tar.bz2
tar -xvf alsa-oss-1.0.9.tar

```
Now you have uncompressed all in differents folders.
go into the driver folder and execute this:
```
./configure --with-oss=yes --with-cards=hda-intel && make && sudo make install
```
now to all the other folders (lib, oss, utils) do this:
```
./configure && make && sudo make install
```

after execute
```
sudo alsaconf
```
select hda-intel and then ok

Reboot and now it should work fine. Well it worked for me so... But I don't know if I have installed other things...

---

### Post by WebbyBabe on 2005-08-21
I can't get passed ./configure

I get this error: 

checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I'm totally lost.  ](*,)

---

### Post by WebbyBabe on 2005-08-21
Ok, I found what the problem was. Linux-kernel needed to be renamed to linux.

But now I get this error

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.

---

