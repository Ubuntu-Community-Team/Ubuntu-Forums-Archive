---
title: "How to install dvb-t card based on Realtek chip in kernel 3.0.0 &amp; 3.1.0 &amp; 3.2.0"
date: 2012-01-05
forum: Hardware
---

### Post by s1hr on 2012-01-05
Due that plenty of well written modification of realtek rtl2831 and realtek rtl2832 driver on internet and even on this forum, that not work past Ubuntu 10.04 LTS, and very few work in relases after but just for exact card model..
I choose to post here this procedure which work under actual Ubuntu releases for almost all dvb-t cards based on Realtek chip.
Thanks list is down under.

There is NOW very simple way to make RTL2832U driver working in Ubuntu with kernel 3.0.0 ,kernel 3.1.0 and even kernel 3.2.0(with small edit),that means a lot of dvb-t cards,regardless USB dvb-t or PCI dvb-t with Realtek chip will work under Ubuntu 11.10 and even under Ubuntu 12.04 LTS which have to arive soon.
"Not Only TV" -LifeView LV5TDLX is just one of those cards.
Personally i test it with "Not Only TV LV32TDLX"(two tuners) on Ubuntu 11.10 with kernel 3.0.0 and work fine.
List of codes(PID & VID) of supported manufacturer and models of cards i will add too,but that list constantly growing..as 10tuners are supported.

Original Realtek RTL2832U chipset (DVB/DAB) Linux 2.6.x driver rel. 2.2.2 , "full" version

Thanks to Realtek (as company)
Thanks to Xgazza
Thanks to Skaman
Thanks to Gennar1
Thanks to Ambrosa

This procedure is valid for kernel 3.0.0 and kernel 3.1.0
That means you can use it in Ubuntu 11.10
just copy & paste, line by line in terminal following by ENTER  --> newbie friendly

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install git
git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*)
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0
cd RTL2832-2.2.2_kernel-3.0.0
make clean
make
sudo make install
```
now its time to make restart of Your computer or just type in terminal
```
sudo reboot
```
thats it! end of story.

if You wish to check if driver is loaded type
```
lsmod | grep dvb
```
You should get someting like..
> dvb_usb_rtl2832u 341269 0 
dvb_usb 23788 1 dvb_usb_rtl2832u
dvb_core 94826 1 dvb_usb
what means that driver rtl2832u is loaded and working.

All your dvb-t aplication now will recognize your dvb-t card.
Next to do is to scan for available dvb-t chanels.
As player Kaffeine can use also your dvb-t card,and show you tv and have scan for dvb channels built in,i recommend it for use.

This driver depends of particular model of card will open fm radio and DAB radio if your card have support for it.Mine do.

Enjoy watching & recording dvb-t..:popcorn: .. and listening & recording FM radio or DAB radio.

Bad luck,here in my place in Croatia,there is no DAB signal,whatever..sorry if i miss-spell something,english is not my native language..
enjoy in dvb-t):P
...Buntu...to all

---

### Post by gamx on 2012-01-06
I have tried your instructions and they do not work for me (I use oneiric so my kernel is 3.0.0-14). According to lsusb my device is:

Bus 001 Device 007: ID 0bda:2831 Realtek Semiconductor Corp. RTL2831U DVB-T

which should work according to your instructions. I compile, run "sudo make install" and get no error message. However, when I do "lsmod|grep dvb" nothing happens. And, of course, the dvb-t card does not work...
Any ideas?
Thanks,

Gamx

---

### Post by dlpl on 2012-03-03
With your solution my GIGABYTE U7300 DVB-T dongle works great on freshly installed ubuntu 11.10
Thanks from Poland!

---

### Post by EddyMontoto on 2012-04-07
Works fine with NPG Real DVB-T Plus, thank you

---

### Post by Leo H on 2012-04-22
@s1hr

I followed your instructions successfully until the "make" command where I get my first error message.  I presume that all subsequent error messages are a consequence of this first one.  I am copying the terminal window output, starting from the "make clean" command.  (The commands I entered are in [COLOR=Red]red[/COLOR], the first error message I can detect is in [COLOR=Blue]blue[/COLOR].)


-------------------------------------------------------------------------------------------------------

~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ [COLOR=Red]sudo make clean[/COLOR]

rm -f  *.o  *.ko *.mod.c .*.o.cmd  .*.o.d  .*.ko.cmd Module.symvers Module.markers modules.order
rm -rf .tmp_versions

~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ [COLOR=Red]sudo make[/COLOR]

make -C /usr/src/linux-headers-`uname -r` SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-17-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
[COLOR=Blue]make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [default] Error 2[/COLOR]

~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ [COLOR=Red]sudo make install[/COLOR]

cp dvb-usb-rtl2832u.ko /lib/modules/`uname -r`/kernel/drivers/media/dvb/dvb-usb/ 
cp: cannot stat `dvb-usb-rtl2832u.ko': No such file or directory
make: *** [install] Error 1

~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ [COLOR=Red]modprobe dvb_usb_rtl2832u[/COLOR]

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module dvb_usb_rtl2832u not found.

------------------------------------------------------------------------------------------------------


The system is a rock-standard Xubuntu 11.10 32-bit (fully up to date).  Let me know if you need any more info.

What can I do to resolve this and to get my DVB-T dongle going?

Thanks, Leo

---

### Post by BirdOfPrey on 2012-05-03
Thank you so much s1hr! The usb dvb-t dongle is working fine now! 
For reference, it's a chinese one with no brand, with a rtl2832, an E4000 tuner and remote support.
The usb id is:
Bus 001 Device 002: ID 0bda:2838 Realtek Semiconductor Corp.
dmesg reports :
[  109.831561] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)
[  110.897542] RTL2832U usb_init_bulk_setting : USB2.0 HIGH SPEED (480Mb/s)

lsmod | grep dvb:
dvb_usb_rtl2832u      403933  0
dvb_usb                24444  1 dvb_usb_rtl2832u
dvb_core              110616  1 dvb_usb
rc_core                26963  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb

---

### Post by hornetster on 2012-05-04
Trying to do this on Opensuse 12.1 x64 (uname -r = 3.1.10-1.9-desktop).
The standard linux headers in suse are: */usr/src/linux-3.1.10-1.9/* and a symbolic link of */usr/src/linux* points to this.
Thus I had to rename */usr/src/linux-3.1.10-1.9/* to */usr/src/linux-headers-3.1.10-1.9-desktop/* as /usr/src + uname -r doesn't equal the correct path.
This seemed to fix my main problem, but then running make, I got this:
```
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=/Temp/NewREaltek/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.1.10-1.9-desktop'

  WARNING: Symbol version dump /usr/src/linux-headers-3.1.10-1.9-desktop/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD [M]  /Temp/NewREaltek/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/dvb-usb-rtl2832u.o
/bin/sh: scripts/mod/modpost: No such file or directory
make[2]: *** [/Temp/NewREaltek/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/dvb-usb-rtl2832u.o] Error 1
make[1]: *** [_module_/Temp/NewREaltek/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.1.10-1.9-desktop'
make: *** [default] Error 2
```

This was the second run.... but gave the same errors.
How to fix?
Thanks, John.

---

### Post by codixxxl on 2012-05-07
Hello,
I have the same problem that [gamx]("http://ubuntuforums.org/member.php?u=196952"). 
--------------
My distro is 
> lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

>uname -r
3.2.0-24-generic
------------------

My dvb-t card is
Bus 002 Device 006: ID 0bda:2831 Realtek Semiconductor Corp. RTL2831U DVB-T

into  Zaapa DVBUSB 

I have compiled without error messages, but the device not work. And when I typed 
> lsmod |grep dvb
shows noghing

Even when I load the module explicity whith
>sudo modprobe dvb_usb_rtl2832u
and shows
>lsmod |grep dvb

dvb_usb_rtl2832u      408029  0 
dvb_usb                24490  1 dvb_usb_rtl2832u
dvb_core              110619  1 dvb_usb
rc_core                26412  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb


and

>dmesg

...
[  453.922787] IR NEC protocol handler initialized
[  453.933871] IR RC5(x) protocol handler initialized
[  454.024610] usbcore: registered new interface driver dvb_usb_rtl2832u
[  454.034368] IR RC6 protocol handler initialized
[  454.049090] IR JVC protocol handler initialized
[  454.050856] IR Sony protocol handler initialized
[  454.053068] IR MCE Keyboard/mouse protocol handler initialized
[  454.056727] lirc_dev: IR Remote Control driver registered, major 249 
[  454.057487] IR LIRC bridge handler initialized


My dvb-t card doesn't work. 

Thanks

---

### Post by hornetster on 2012-05-08
Just wondering what the "small edit" for kernel 3.2 is? Couldn't find it in the thread.
Thanks,

---

### Post by Javierin on 2012-05-26
Hi.

STEP 5:

cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0

  there you can see a file named README, open it and read:


       Main thread about OpenPli project: [http://openpli.org/forums/topic/20899-rtl2832u-chipset-support-proposal/](http://openpli.org/forums/topic/20899-rtl2832u-chipset-support-proposal/)

  goto that url. There, ambrosa 0n #18 says:

    - edit Makefile and remark include file about kernel 320... bla bla bla

STEP 6

cd RTL2832-2.2.2_kernel-3.0.0

AND EDIT Makefile

# kernel 3.0.0 / 3.1.0
[COLOR="red"]#[/COLOR]INCLUDE_EXTRA_DVB := include-300

# kernel 3.2.0
[COLOR="Red"]INCLUDE_EXTRA_DVB := include-320[/COLOR]

save Makefile and try again for kernel 3.2.0

STEP 7, 8 and 9:

make clean
make
sudo make install

GOOD LUCK

---

### Post by hornetster on 2012-05-26
Yeah, sorry, had already worked that one out.... :oops:
Thanks.

---

### Post by teledyn on 2012-08-04
ok, I have the dongle installed, and the lsusb says the module is installed, and dmesg doesn't say anything isn't work.

now what??

what software do I use to actually put the device to use, and how do I operate that software?  I ran VLC and it appeared to like the device, but there was no means to search channels; I've heard of a scan utility but no instructions on how to use this outside of the UK -- I should explain that I live in a remote and technologically disavantaged country (Canada) and I'm not likely to experience digital TV in my lifetime, but all I really wanted from this thing was to tune in FM radio (which we do have, although all the stations suck so I run my own broadcast from a FM-transmitter dongle in another room)

Should xine simply recognize this thing?  Is there other code elsewhere i need to install or build and install? Did I miss something in the tutorials? I never expected the last step to be so hard to find :( -- any and all patient advice is very much appreciated.

---

### Post by Bucky Ball on 2012-08-05
I know this is an old thread so thought I'd get in before anyone notices and it gets closed.

I have the DVB-T up fine and crystal clear TV. Is anyone using this for DAB? If so, what software are you using to listen? I can't find, or maybe work out, how to check for DAB stations or listen to them in Linux and have spent ages searching. I gave up for about a week then found this thread. 

Works out of the box in Win 7 so I know DAB is working. (EZCap 646 USB dongle.)

---

### Post by DutchDude on 2012-08-09
> **teledyn said:**
> ok, I have the dongle installed, and the lsusb says the module is installed, and dmesg doesn't say anything isn't work.

now what??

what software do I use to actually put the device to use, and how do I operate that software?  I ran VLC and it appeared to like the device, but there was no means to search channels; I've heard of a scan utility but no instructions on how to use this outside of the UK -- I should explain that I live in a remote and technologically disavantaged country (Canada) and I'm not likely to experience digital TV in my lifetime, but all I really wanted from this thing was to tune in FM radio (which we do have, although all the stations suck so I run my own broadcast from a FM-transmitter dongle in another room)

Should xine simply recognize this thing?  Is there other code elsewhere i need to install or build and install? Did I miss something in the tutorials? I never expected the last step to be so hard to find :( -- any and all patient advice is very much appreciated.

Same problem here. 

In addition: After restarting, lsusb no longer says the module is installed...

On the Dutch ubuntu forum there are currently 2 people who have the same problem. I'm one of them. No solution yet. :( But I´ll communicate between the two forums in case anybody finds a sollution :-)

(or should I open a new thread??)

---

### Post by Bucky Ball on 2012-08-09
Me-TV. The latest version has auto-scan. In the repos.

You need to create a channels.conf file for the others, as far as I know. (VLC, Xine). Do this by installing DVB-apps and using w_scan. You'll need to research this. You then put that in the apps folder (eg xine is /home/youruser/.xine

Put the channels.conf in there. Boot xine and you're set to go.

---

### Post by puigpuig on 2012-09-04
Excellent. The instructions given in post #1 work fine with Linux Mint 12 (Kernel 3.0.0), except for the line:

 git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*)

that does not work. The link I think is not correct.

Instead, I have used:

 git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0)

and it worked well. 

Thank you!

---

### Post by puigpuig on 2012-09-04
With Linus Mint 13 (Kernel 3.2.0) I have an error: 

make -C /usr/src/linux-headers-`uname -r` SUBDIRS=/home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  (...)
/home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/rtl2832u.c: In function &#8216;rtl2832u_frontend_attach&#8217;:
/home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/rtl2832u.c:704:15: error: &#8216;struct dvb_usb_adapter&#8217; has no member named &#8216;fe_adap&#8217;
home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/rtl2832u.c: At top level:
/home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/rtl2832u.c:858:24: error: unknown field &#8216;num_frontends&#8217; specified in initializer
/home/puig/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/rtl2832u.c:858:24: warning: excess elements in struct initializer [enabled by default]

etc...

The solution I found is in: [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0) : 
 after the two 
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0 cd RTL2832-2.2.2_kernel-3.0.0  you have to edit Makefile, option INCLUDE_EXTRA_DVB (choose which include file set): 
you have to comment with # the version for kernel 3.0.0 and uncomment the version for kernel 3.2.0. 

The complete instructions are: 
**** UBUNTU FRESH INSTALL ****  - install compile kit sudo apt-get install build-essential  - install linux headers sudo apt-get install linux-headers-$(uname -r)  - install git sudo apt-get install git  - clone this repo using git git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git)   - goto into source dir cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0 cd RTL2832-2.2.2_kernel-3.0.0  - edit Makefile, option INCLUDE_EXTRA_DVB (choose which include file set)  - compile code make clean make  - install module sudo make install  - reboot

And it works well tith a dvb trust 16738 in Linux Mint 13 with kaffeine. 
In kaffeine I have gone to Television + Configure Television and refreshed the corresponding device and put the location I am. 
It works fine. 
Thank you!

---

### Post by fmcgorenc on 2012-09-05
Thank you. It works on Ubuntu 12.04. Except I can't get the remote to work. I've tried everything I could find on the internet nothing seems to work. Any ideas? 

If I type:
```

lsmod | grep dvb
```
I get this:
```

dvb_usb_rtl2832u      345365  0 
dvb_usb                23826  1 dvb_usb_rtl2832u
dvb_core               94814  1 dvb_usb
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb
```

EDIT: sory could'n find the attachments option at first

---

### Post by Bucky Ball on 2012-09-05
@ [fmcgorenc]("http://ubuntuforums.org/member.php?u=1001633"): Could you please make your photograph in post #18 an attachment by clicking the attachment icon and uploading and remove the huge photo in the body of your post, please? 

To all: Please make huge photos like the one above attachments, *not* huge pics pasted in the body of your posts, please. Unwieldy, waste of space and inconvenient. Thanks. ;)

---

### Post by kdim2637 on 2012-12-26
> **s1hr said:**
> Due that plenty of well written modification of realtek rtl2831 and realtek rtl2832 driver on internet and even on this forum, that not work past Ubuntu 10.04 LTS, and very few work in relases after but just for exact card model..
I choose to post here this procedure which work under actual Ubuntu releases for almost all dvb-t cards based on Realtek chip.
Thanks list is down under.

There is NOW very simple way to make RTL2832U driver working in Ubuntu with kernel 3.0.0 ,kernel 3.1.0 and even kernel 3.2.0(with small edit),that means a lot of dvb-t cards,regardless USB dvb-t or PCI dvb-t with Realtek chip will work under Ubuntu 11.10 and even under Ubuntu 12.04 LTS which have to arive soon.
"Not Only TV" -LifeView LV5TDLX is just one of those cards.
Personally i test it with "Not Only TV LV32TDLX"(two tuners) on Ubuntu 11.10 with kernel 3.0.0 and work fine.
List of codes(PID & VID) of supported manufacturer and models of cards i will add too,but that list constantly growing..as 10tuners are supported.

Original Realtek RTL2832U chipset (DVB/DAB) Linux 2.6.x driver rel. 2.2.2 , "full" version

Thanks to Realtek (as company)
Thanks to Xgazza
Thanks to Skaman
Thanks to Gennar1
Thanks to Ambrosa

This procedure is valid for kernel 3.0.0 and kernel 3.1.0
That means you can use it in Ubuntu 11.10
just copy & paste, line by line in terminal following by ENTER  --> newbie friendly

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install git
git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*)
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0
cd RTL2832-2.2.2_kernel-3.0.0
make clean
make
sudo make install
```now its time to make restart of Your computer or just type in terminal
```
sudo reboot
```thats it! end of story.

if You wish to check if driver is loaded type
```
lsmod | grep dvb
```You should get someting like..

what means that driver rtl2832u is loaded and working.

All your dvb-t aplication now will recognize your dvb-t card.
Next to do is to scan for available dvb-t chanels.
As player Kaffeine can use also your dvb-t card,and show you tv and have scan for dvb channels built in,i recommend it for use.

This driver depends of particular model of card will open fm radio and DAB radio if your card have support for it.Mine do.

Enjoy watching & recording dvb-t..:popcorn: .. and listening & recording FM radio or DAB radio.

Bad luck,here in my place in Croatia,there is no DAB signal,whatever..sorry if i miss-spell something,english is not my native language..
enjoy in dvb-t):P
...Buntu...to all

in my case not working any help kostaslaptop@ubuntu:~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ make clean
rm -f  *.o  *.ko *.mod.c .*.o.cmd  .*.o.d  .*.ko.cmd Module.symvers Module.markers modules.order
rm -rf .tmp_versions
kostaslaptop@ubuntu:~/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0$ make
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=/home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/demod_rtl2832.o
In file included from /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/include-320/dvb-usb.h:19:0,
                 from /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/foundation.h:19,
                 from /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/dvbt_demod_base.h:289,
                 from /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/demod_rtl2832.h:72,
                 from /home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/demod_rtl2832.c:13:
/home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/include-320/dvb_frontend.h:49:33: &#963;&#966;&#940;&#955;&#956;&#945;: field ‘parameters’ has incomplete type
/home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/include-320/dvb_frontend.h:313:28: &#963;&#966;&#940;&#955;&#956;&#945;: array type has incomplete element type
make[2]: *** [/home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0/demod_rtl2832.o] Error 1
make[1]: *** [_module_/home/kostaslaptop/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/RTL2832-2.2.2_kernel-3.0.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [default] Error 2

---

### Post by kdim2637 on 2012-12-26
> **s1hr said:**
> Due that plenty of well written modification of realtek rtl2831 and realtek rtl2832 driver on internet and even on this forum, that not work past Ubuntu 10.04 LTS, and very few work in relases after but just for exact card model..
I choose to post here this procedure which work under actual Ubuntu releases for almost all dvb-t cards based on Realtek chip.
Thanks list is down under.

There is NOW very simple way to make RTL2832U driver working in Ubuntu with kernel 3.0.0 ,kernel 3.1.0 and even kernel 3.2.0(with small edit),that means a lot of dvb-t cards,regardless USB dvb-t or PCI dvb-t with Realtek chip will work under Ubuntu 11.10 and even under Ubuntu 12.04 LTS which have to arive soon.
"Not Only TV" -LifeView LV5TDLX is just one of those cards.
Personally i test it with "Not Only TV LV32TDLX"(two tuners) on Ubuntu 11.10 with kernel 3.0.0 and work fine.
List of codes(PID & VID) of supported manufacturer and models of cards i will add too,but that list constantly growing..as 10tuners are supported.

Original Realtek RTL2832U chipset (DVB/DAB) Linux 2.6.x driver rel. 2.2.2 , "full" version

Thanks to Realtek (as company)
Thanks to Xgazza
Thanks to Skaman
Thanks to Gennar1
Thanks to Ambrosa

This procedure is valid for kernel 3.0.0 and kernel 3.1.0
That means you can use it in Ubuntu 11.10
just copy & paste, line by line in terminal following by ENTER  --> newbie friendly

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install git
git clone [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*)
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0
cd RTL2832-2.2.2_kernel-3.0.0
make clean
make
sudo make install
```now its time to make restart of Your computer or just type in terminal
```
sudo reboot
```thats it! end of story.

if You wish to check if driver is loaded type
```
lsmod | grep dvb
```You should get someting like..

what means that driver rtl2832u is loaded and working.

All your dvb-t aplication now will recognize your dvb-t card.
Next to do is to scan for available dvb-t chanels.
As player Kaffeine can use also your dvb-t card,and show you tv and have scan for dvb channels built in,i recommend it for use.

This driver depends of particular model of card will open fm radio and DAB radio if your card have support for it.Mine do.

Enjoy watching & recording dvb-t..:popcorn: .. and listening & recording FM radio or DAB radio.

Bad luck,here in my place in Croatia,there is no DAB signal,whatever..sorry if i miss-spell something,english is not my native language..
enjoy in dvb-t):P
...Buntu...to all

> **Javierin said:**
> Hi.

STEP 5:

cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0

  there you can see a file named README, open it and read:


       Main thread about OpenPli project: [http://openpli.org/forums/topic/20899-rtl2832u-chipset-support-proposal/](http://openpli.org/forums/topic/20899-rtl2832u-chipset-support-proposal/)

  goto that url. There, ambrosa 0n #18 says:

    - edit Makefile and remark include file about kernel 320... bla bla bla

STEP 6

cd RTL2832-2.2.2_kernel-3.0.0

AND EDIT Makefile

# kernel 3.0.0 / 3.1.0
[COLOR=red]#[/COLOR]INCLUDE_EXTRA_DVB := include-300

# kernel 3.2.0
[COLOR=Red]INCLUDE_EXTRA_DVB := include-320[/COLOR]

save Makefile and try again for kernel 3.2.0

STEP 7, 8 and 9:

make clean
make
sudo make install

GOOD LUCK
not work for me

---

### Post by Bucky Ball on 2012-12-26
[I][B]Thread Closed

Reason:[/B][/I] Necromancy.

Please post a new thread with any issues you have rather than resurrecting an old and inactive one. This will improve your chances of help.

---

