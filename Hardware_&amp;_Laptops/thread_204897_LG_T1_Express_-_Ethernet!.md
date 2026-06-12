---
title: "LG T1 Express - Ethernet!"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by murmlos on 2006-06-27
HELP!

And now for something completly different...

Nah just kidding, i do need help!

I got at LG T1 Express laptop that has a Agere et131x Gbit eth card.. It doesnt work under linux!

[http://dadams1969.googlepages.com/et131xkernelmodule](http://dadams1969.googlepages.com/et131xkernelmodule)

That is the ONLY site that acknowledges the problem.. And apparantly he has a fix for it.. Well, the thing is that i suck so i cant get it to work.. 

I also tried the live cd that is on that link and well.. That one do work.. But then the problem is to install Gentoo.. And lets face it, if i cant follow a simple instruction on his page im not very likely to succeed in installing Gentoo..
(I tried, but ended up with a Kernel Panic ;) )

Well, anyways.. Help.. In anyway you can..


et131x # make && make modules_install
#make -C /lib/modules/2.6.16-gentoo-r3/build M=/usr/src/linux-2.6.16-gentoo-r9/drivers/net/et131x modules
make: *** /lib/modules/2.6.16-gentoo-r3/build: No such file or directory. Stop.
make: *** [modules] error 2

Nice huh? Thats the error i recieved when trying to make && make modules_install the et131x module..  

Well.. I think you get my point..  

// Erik

---

### Post by murmlos on 2006-06-28
Well, a little update.

I tried using ndiswrapper with  the windows drivers ... But if i understoos it right, it failed to load or something.. So that didnt go that well either..

Anyone else who had anyluck with the Agere et131x card?

---

### Post by masterping on 2006-07-04
Hello!

I have a LG P1 with the same network card and I tried to fallow the instructions you refered and got the same errors. I tried to find something at Agere's website but with no sucess.
I didn't had much luck with the rest of the hardware...
- ATI Mobility Radeon X1400: didn't work but got the drivers from ATI and it's fine
- Intel Wireless card, not working
- Sound, not working
- SATA HDD, light is always On... I think this is not good!!
- PCMCIA, not working
- Got some problems with Synaptics touchpad... now are solved

Any help??

---

### Post by mhafren on 2006-07-06
Hello.

I have a T1 Express and am also sad to say that I haven't got the et131x network card working. Doesn't anybody here know how to get it working? Help would really be appreciated.

---

### Post by sml on 2006-07-10
How is the progress guys? I would like to buy one of these but obviously I am having second thoughts now.

What is the performance like?

---

### Post by Burkey on 2006-07-10
Wow more LG users!  My et131x works fine, I had to download the driver and build it myself every time the kernel changes.  Otherwise rock solid.  I forgot where I downloaded it from but I am using et131x_20060131_v1-2-2.tar.gz and new_ver_x86_3-10-06.patch

Search google, I bet you find it in 10 mins.

As for the sound on my P1 Express, it works well if you plug headphones in.  What I really want though is the speakers to make sound so if anyone has advice on that would really be appreciated.

It is an Intel 82801G (ICH7 Family) hooked to a Realtek ALC880 somehow.  I do not mean to hijack the thread, however I am betting all the LG people here have the same audio setup and same problem?

---

### Post by mhafren on 2006-07-11
That's good to know somebody has got it working. However when I apply the patch I get the following error:

mhafren@mhafren-laptop:~/et131x$ patch -p0 < new_ver_x86_3-10-06.patch
patching file et131x/ET1310_tx.h
patching file et131x/ET1310_rx.h
patching file et131x/ET1310_rx.c
patching file et131x/ET1310_address_map.h
mhafren@mhafren-laptop:~/et131x$ cd et131x/
mhafren@mhafren-laptop:~/et131x/et131x$ sudo make && make modules_install
#@make -C /lib/modules/2.6.15-26-386/build M=/home/mhafren/et131x/et131x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/mhafren/et131x/et131x/et131x_main.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_initpci.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_isr.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_netdev.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_supp.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_config.o
  CC [M]  /home/mhafren/et131x/et131x/et131x_debug.o
  CC [M]  /home/mhafren/et131x/et131x/ET1310_jagcore.o
  CC [M]  /home/mhafren/et131x/et131x/ET1310_tx.o
  CC [M]  /home/mhafren/et131x/et131x/ET1310_rx.o
/home/mhafren/et131x/et131x/ET1310_rx.c: In function &#8216;nic_rx_pkts&#8217;:
/home/mhafren/et131x/et131x/ET1310_rx.c:1476: error: &#8216;pShBufVa&#8217; undeclared (first use in this function)
/home/mhafren/et131x/et131x/ET1310_rx.c:1476: error: (Each undeclared identifier is reported only once
/home/mhafren/et131x/et131x/ET1310_rx.c:1476: error: for each function it appears in.)
/home/mhafren/et131x/et131x/ET1310_rx.c:1670: warning: unused variable &#8216;vlan_tag&#8217;
make[2]: *** [/home/mhafren/et131x/et131x/ET1310_rx.o] Error 1
make[1]: *** [_module_/home/mhafren/et131x/et131x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [modules] Error 2


Does anybody know what is wrong here? 
About the sound. I have the speakers working out-of-the box but I don't get my headphones or mic to work. I have gotten my headphones to work with a fix but the the speakers wouldn't work so I don't know if I can help you there. I have heard that getting the latest ALSA-drivers might help.

Murmlos: You should install the corresponding linux-headers to your kernel. uname -a gives you your kernel version and then you search for the corresponding linux-headers in synaptic.

---

### Post by xinel on 2006-07-12
Hey guys I have an S1 express dual and have all the same problems. I got the wireless networking to work without ndiswrapper, I gave up on ethernet after I got the wireless working. Have sound through headphones but not with the speakers. Ive installed and reinstalled the latest alsa drivers (realtech too) and followed the sound guide a few times over and haven't been able to solve the problem yet.

Anyways good luck to everyone and hopefully one of us solves one of the problems :P because these lappy's are pretty cool otherwise.

---

### Post by Wise Ferret on 2006-07-14
Hello Burkey,

I'm about to get a LG-S1, So I ask you in order to be absolutely sure: did you have to compile the entire kernel in order to get the ethernet support? Or did you have to only to apply the patches to the driver's source code, compile it (how exactly?) and use modprobe to stick it into the kernel?
Can you please list the steps you have taken in order to get this card working on Dapper, one by one? I, like many other rookies, will be very grateful.

---

### Post by Burkey on 2006-07-16
No need to recompile the kernel!  Also I did not have to supply any make arguments, make clean then make from memory.

I am sorry I am not that helpful right now, I was overseas for work and only checking on occasion.  I am nt home but done something evil on the flight back (hey 12hours nothing to do) and installed SuSE 10.1  It come on the cd withe the mag from the airport!  And I wanted to see if the sound would magically start working.. well, it does not.  So don't bother trying.

I intend to go back to Ubuntu 6.06.  Nothing bad about SuSE, I just personally find apt-get better.  If I was not on Dapper then I would be on Gentoo, RPM just does not work for me.

---

### Post by Wise Ferret on 2006-07-17
Thank you very much!

I succeeded in applying the 4 patches and compiling the source on my desktop ubuntu system (just to make sure I can do it when the laptop arrive). The order of applying the patches is important: first I had to apply the one titled "patch", and only then the ones titled "fix". I had to apt-get linux kernel headers, and then the compilation worked. The instructions from then on are in the README, so I guess it will work fine. Hurrah!

Do you know to whome we should go and nudge for speaker support? Is it the ALSA team? The ubuntu team also does such things when they are in the proper mood, but I cannot file a bug there without actually trying it on the laptop.

---

### Post by Burkey on 2006-07-17
And I really am stumped on the speakers too.  I do not fully understand where the problem lies so don't know if it is Alsa or who.  I saw lots of work was done on Alsa 1.0.11 for Intel High Def audio but those were all fixes for people getting no sound etc which makes me think our problem lies in the Mixer which I think is a Realtek ALC880.

I guess if we keep the forums brimming with these sorts of topics and more people are using the same or similar hardware we will be heard and might get help?

---

### Post by masterping on 2006-07-17
Wise Ferret, could you please detail (with all the commands line instructions) how did you proceed for applying the patches and compiling the Agere's driver?

I'm using an old pcmcia ethernet card which works fine or an Atheros chipset wireless card which also works fine... but it would be much better if I could use the hardware that is INSIDE the computer :)

Concerning the audio... I was testing some stuff and... I heard my speakers!! Unfortunatelly I turned off the computer and next day I could not repeat the stunt. I use some speech processing systems that mainly use sox and play. Some of these programs have solved something.

I also had some problems with aticonfig... after installing the drivers (from ATI) I try to make:

$sudo aticonfig --initial --force 

and it says that the fglrx?????.so is not found (cannot detail now ... running windows :( ) but I already located the file.

Any help??

---

### Post by Wise Ferret on 2006-07-17
Hello masterping,
I do not know if the drivers I compiled actually work. I do not have the laptop yet. However, for ubuntu the stepas are:
1. apt-get build-essential linux-headers-686 (get compilation tools and kernel header files necessary for the driver)
1. wget [http://dadams1969.googlepages.com/et131x-1.2.2-3.src.tar.gz](http://dadams1969.googlepages.com/et131x-1.2.2-3.src.tar.gz) (get the driver)
2. Make a new folder. Open the archive and extract the patch files (1 ending with .patch and 3 ending with .diff) to that folder. Then open the et131x-1.2.2.tar.bz2 file that lies within the archive, and extract its content too into the same folder. Open a console and go to that folder.
3. Enter following commands, in that order:
patch < new_ver_x86_3-10-06.patch
patch < fix-patch_et131x_x86_3-10-06.diff
patch < fix-get_mac_address_from_EEPROM.diff
patch < MODULE_PARM.diff
(This will apply the various patches to the code).
4. Then you can compile:
make

This is as far as I can get without the actual card, but the instruction in the README file in the archive are clear enough. Please keep us posted with your efforts, and good luck!

---

### Post by Burkey on 2006-07-17
For the ATI drivers.  There are drivers in the Ubuntu restricted-modules.  So there are 2 options:

1. Use the Ubuntu restricted-modules
2. Use newer ones from ATI's site.  If you do this you need to un-comment the blacklisted fglrx driver from (memory here) /etc/default/linux-modules

If you went route 1, make sure it is commented out.

---

### Post by Burkey on 2006-07-18
Fresh installed Dapper 6.06 from the desktop CD.  A few notes are:

On install none of the network interfaces work.  To make them work you have to install build-essential and the kernel headers, then download the et131x drivers (I used et131x_20060131_v1-2-2.tar.gz) I did not patch these but they built and installed fine.

To get build-essential you are going to have to add the Ubuntu CD as an apt source, otherwise you will not see it.

I got the et131 driver on by downloading on another PC and copying the tar.gz to a flash drive btw.

Not saying this is the right way but it is indeed one way that worked for me.  Next will be to upgrade and get my wireless working, thankfully that is in the repo's so should be easy.

Again, no sound though..

---

### Post by masterping on 2006-07-18
Good news and no news...

The ATI is now fully working (maximum res and 3D accel).
I copied libfglrx_pp.so.1.0 (that aticonfig could not find) to /usr/lib/ (was in /usr/X11R6/lib/)

Concernig the Agere's card I sucessfully applied the patches (according to Wise Ferret's instructions) and got the same error when trying to compile:

$ make
#@make -C /lib/modules/2.6.15-26-386/build M=/home/masterping/et131x-1.2.2-3.src modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

### Post by Wise Ferret on 2006-07-18
Hi masterping,

You get this error because you did not install the package "linux-headers-686". Once you get that installed, it should work.

---

### Post by masterping on 2006-07-19
Hello,

I have now successfully made:

$sudo make

and

$sudo make modules_install

with no errors (linux-headers-386 was missing and not 686)

I restarted the computer (because I don't know how to do it other way) and made: 

$lspci
(...)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145 --> but it works! and ATI Control panel is OK
0000:02:00.0 Ethernet controller: Agere Systems: Unknown device ed00 (rev 02)
0000:05:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:06:00.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:06:00.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:06:00.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:06:00.3 0805: Texas Instruments: Unknown device 803c

Also tried to find something new at "System Settings".

Any ideas? Sorry for not being very helpfull.

---

### Post by pepinto on 2006-07-20
Hello people!
First statement: i´m a linux newbie, working with Ubuntu dapper since 3 days ago.
I have a LG P1 and thanks to you the ethernet card is working! :D 
I have a problem: i upgraded the kernel to 686 SMP (to have the two cores working) after some time i noticed the computer was too slow, and voila, core one was under 100% load, the second core was working properly! 
Then i googled about that and found this: 
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/48395](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/48395)
Now i´m using de 386 kernel but dapper only sees one core (i have half processor :( )

Second question: the microphone seems not working. I checked the sound config, and selected the realtek controler. The volume selection is ok, SPDIF turns on and off but the microphone does not work. When i increase the "microphone volume" i hear a "buzz" from the speakers, but it seems not capturing any sound.

Did you noticed this?

---

### Post by masterping on 2006-07-20
Hello pepint!
I believe you've red what I've made to try to install the drivers. 
Till now, compiled and made "make modules_install"... I tried to find something new in "systems settings" but there's nothing. In the README file there's a description using "insmod" and other commands. 
Did you fallowed these? What did I missed?

---

### Post by masterping on 2006-07-20
Now I've made:
$sudo insmod et131x.ko
And
$ dmesg | grep -i Agere
[17179939.428000] 10/100/1000 Base-T Ethernet Driver for the ET1310, v1.2.2 01/31/2006 15:40:00 by Agere Systems, [http://www.agere.com](http://www.agere.com)

but lspci still says the same... "..unknown device.."

When I restart the computer I always have to make sudo insmod et131x.ko

I tried to find the "something.autoload" that dadams refers to but I think it's doesn't exist in Ubuntu.

How can I automatically have my card configured at startup?

---

### Post by pepinto on 2006-07-20
Hello!
masterping:
i had the same problems you have.

1 - patched the drivers
2 - compiled -> "make"
3 - "make modules_install"
* no ethernet card
4 - "insmod et131x.ko"
* ethernet card ok, but after system reboot it disapears
5 - "depmod" - update dependencies
6 - "modprobe et131x"
* after reboot i have eth card working properly

I hope works with you!
Now, regarding my last post, anything?

---

### Post by Wise Ferret on 2006-07-22
I found something in ALSA's site:


ALSA Changelog between 1.0.11 and 1.0.12rc1 releases

...

    - hda-codec - Add support for LG S1 laptop

...


So if any of you is willing to give the newest alsa version a try, it might help.

---

### Post by masterping on 2006-07-24
Thank you pepinto!!!
My ethernet card is now working!!

Concerning the audio... As other have related, I only have access to the headphones and I can't hear the speakers (although it happens once, I don't know how).

Maybe this question should be lauched in another thread?

---

### Post by mpmf on 2006-07-29
I've followed the instructions written here and, thanks to them, I've got my LG S1 ethernet card working. I tried the new ALSA drivers (1.0.12rc1), compiled them and installed them and I can confirm that the sound is working through speakers :-)

Thanks for all your help.

---

### Post by Burkey on 2006-07-30
Wow! SOUND?

mpmf how did you install them?  Did you have some guide to follow or some info as I want to try it on my P1 Express.

---

### Post by Burkey on 2006-07-30
Just installed using :

```

./configure --with-cards=hda-intel
sudo make
sudo make install

```

Then reboot and cat /proc/asound/version gives me 1.0.12rc1

Exactly the same, sound out the headphones but nothing from the speakers

Edit: running an LG P1 Express Dual

---

### Post by pepinto on 2006-07-31
mpmf, 
can you please explain how did you installed the drivers for the sound card?
I installed but do not have sound in the laptop speakers (LG P1)
I do not have the microphone working. Do you have the same problem?

---

### Post by chaosgeisterchen on 2006-09-25
> **pepinto said:**
> Hello!
masterping:
i had the same problems you have.

1 - patched the drivers
2 - compiled -> "make"
3 - "make modules_install"
* no ethernet card
4 - "insmod et131x.ko"
* ethernet card ok, but after system reboot it disapears
5 - "depmod" - update dependencies
6 - "modprobe et131x"
* after reboot i have eth card working properly

I hope works with you!
Now, regarding my last post, anything?

'Proud' user of a LG T1 Express Dual here.. great notebook, lots of power, lightweight and 1440x900 for crystal clear display.. I love it. 

Ethernet did not work up to now - but now it does. Thanks a thousand times :)

Sound issues should be moved to another thread, hm?

---

### Post by pyter on 2006-10-01
hello,

i have a P1 Dual Express and i'm having some problems to activate the ethernet card...

i patched the files, everything OK.
but when i executed make i got this:

```
bash: make: command not found
```

i found out that on my /usr/bin folder there is no make file!

help me please! thanks


edit: *sudo apt-get install linux-essential* isn't working either... :(

---

### Post by pyter on 2006-10-01
ok, make is working already :) 

now there is another issue...

> #@make -C /lib/modules/2.6.15-26-386/build M=/home/psemeano/linux/et131x
modulesmake[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [modules] Error 2


what does this means?

---

### Post by pyter on 2006-10-02
help me please! :( 

thanks in advance


ps: already tried "./configure" but nothing..

---

### Post by Wise Ferret on 2006-10-04
You do not have the kernel headers. Do the following:
sudo apt-get install linux-headers-2.6.15-27-686
(provided that you use dapper and 686 kernel). Now it should compile.

---

### Post by Wise Ferret on 2006-10-09
And by the way, on lg S1, with ubuntu edgy the internal sound works out of the box like a charm :)

---

### Post by quisoc on 2006-10-10
Hi everybody!
   I have a LG S1, and some problems too.
   I think that this post could be the "official post from LG P1 - S1 - T1". If you are agree, can anybody change the title?
   I installed ati's driver, and it's all ok. I had some trouble woth antialias fonts, but changing ```
.fonts.conf
``` with the next code, it looks very well now.

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Now I will try to update the alsa driver.

---

### Post by haggan on 2008-05-19
Hi all I have an LGR200 and I cant get the et131x to work. I have no problems compiling the latest driver and the system founds eth0 but I cant get an IP over DHCP and if I use static I cant get any connection. The network works in windows vista. When switching over to Ubunu 8.04 my LG sometimes floods the HP switch i got and all other connections is breaking, until I plug out the network cord. Any one got an LGR200 and the et131x working?

---

