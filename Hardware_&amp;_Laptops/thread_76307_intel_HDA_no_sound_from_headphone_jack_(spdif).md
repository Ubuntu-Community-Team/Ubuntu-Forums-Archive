---
title: "intel HDA no sound from headphone jack (spdif)"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by kbuel on 2005-10-14
Hey All,

I have an Asus z71v laptop with an intel HDA sound card.  Sound works fine through the speakers, but I can not get any sound out of the headphones.  The headphone jack seems to be a spdif jack.  I works under windows fine.

Any help would be awesome.

Thanks a lot,
-K

---

### Post by kbuel on 2005-10-15
what property/configuration files should i be playing with?

---

### Post by psp on 2005-10-15
Hi,

I don't know the exact specs of your laptop but i've seen that same result on a Asus A6V laptop with a Realtek ALC880 soundcard. It seems that the ALSA v1.0.9 driver has several bugs concerning the Intel HDA soundcards. The newest driver from realtek should fix that. You can get it [here]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True")

Hope this helps.

PSP.

---

### Post by kbuel on 2005-10-15
HI,

Thanks for the idea.  I downloaded and am trying to install those drivers, but i'm getting this error.  I'm not sure what to do:

make[2]: Leaving directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/a lsactl'
make[1]: Leaving directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/a lsactl'
Making install in alsaconf
make[1]: Entering directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/ alsaconf'
Making install in po
make[2]: Entering directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/ alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/a lsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/tmp/realtek-linux-audiopack-3.4/alsa-utils-1.0.9a/a lsaconf'
make: *** [install-recursive] Error 1
Remove Folder.....
./install: line 45: alsaconf: command not found


Is this because i don't have alsaconf?  I can't figure out what to install to get alsaconf.  I have alsa-utils installed.

Thanks,
-K

---

### Post by kbuel on 2005-10-16
has anyone seen this problem before?  And is this how you resolved it?

---

### Post by kbuel on 2005-10-17
I finally got the sound working through the headphones.  I used the drivers that psp mentioned.  I had to do the manual install of them (there is an automatic method that didn't work).  If anyone has this problem and needs some help, let me know. ( Just PM me) and i'll get back to you.

-K

---

### Post by teb on 2005-11-22
I've got a Fujitsu Siemens S7020 laptop and got Ubuntu Breezy running on it easily. As I observed the same problems as kbuel I followed the steps as described in this thread. 

I performed the ./configure, make, make install and snddevices commands on the ALSA v1.0.9b driver (as downloaded from the link), but then I didn't know how to add this latest driver to /etc/modules.conf as running on Ubuntu we don't have it that way. 

kbuel or somebody else, how do I add the new alsa  sound driver to my system? Thanks in advance!

regards, Wouter

---

### Post by kbuel on 2005-12-28
Hey all,

This is what I did:

I downloaded the file that psp posted, which is [here:]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True")

The file should be:
realtek-linux-audiopack-3.5-2.tar.bz2

Extract it
tar xvf realtek-linux-audiopack-3.5-2.tar.bz2

Go into the directory it created and untar the file named: alsa-driver-1.0.9b_22.tar.bz2
tar xvf alsa-driver-1.0.9b_22.tar.bz2


Compile and Install:
before you do this you may need to do an sudo apt-get install build-essential
You WILL need your Linux kernel headers also, you can get these from the package manager also. 

Look for:
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386

linux-headers-2.6.12-10 is the newest version.. and is probably the version you have (if you've been doing the automatic updates).  Base breezy install had linux 2.6.12-9, but there was an update to 2.6.12-10.  Basically get the version you have because it will compile it as a module for that kernel.  I think there is a way to specify what version when doing the configure, but i'm not sure how, so to get it to work for the version i'm using I removed the linux-headers-2.6.12-9, so I just had version linux-headers-2.6.12-10.


1) cd alsa-driver-1.0.9b_22
2) ./configure
3) sudo make
4) sudo make install
5) sudo ./snddevices

Then I updated a few files:
I may have updated more files then needed.... but the documentation was vague and so I put the following in a more files than were probably needed....

options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I put the above lines in the BOTTOM of the following files:
/etc/modutils/alsa-base
/etc/modprobe.d/alsa-base
/etc/modprobe.d/aliases
/etc/modprobe.d/sound

(I believe I created the file /etc/modprobe.d/sound)

Again, those lines may not need to go into all those file, but that is what I did, and it worked.

I also added the following lines to the bottom of /etc/modules
snd-hda-intel
snd-ALC880

Restart the computer and then it should work.  There should be a new slider for Headphone in the volumn control (next to PCM).  By default it will be muted, so unmut it before trying anything.


Lemme know if you have anymore questions.
-kbuel

---

### Post by Mastakey on 2006-01-14
Thanks kbuel, I followed everything you said and now my headphones work! I can finally listen to music in the library :D thanks again.

---

### Post by hawking on 2006-01-16
I did exactly what you did in my asus a3500e laptop and it worked! :)
thanks!

---

### Post by inovermyheadd on 2006-02-21
ok I guess I'm kind of confused...I'm new to linux...

I downloaded that file to my desktop and go to about

./configure and got this

checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/inovermyheadd/Desktop/realtek-linux-audi opack-3.5-6/alsa-driver-1.0.9b_26
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h d oes not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


and now I have no clue what I am doing, hehe

am I in over my head?

---

### Post by dhalgren on 2006-02-21
kbuel: thank you, thank you, thank you. :-)  I now have sound from the laptop and via the speaker jack. Prior to finding your post, i had no sound at all.
  Might i suggest that you put what you did on the appropraite wiki page as your instructions have been easyier to follow than others, and they worked!
  Thank you again! cheers!!

---

### Post by inovermyheadd on 2006-02-22
ok so I think part of my problem is that the realtek drivers are up to 3.5-6 which is only for kernel version 2.2.14

I tried to find the old realtek driver on opendrivers.com and other sites like it but none of the links work.

Does anyone know where I can either find the new drivers or update my kernel?

I appreciate it:) 

Donald

---

### Post by 0x_ on 2006-02-22
inovermyheadd, it think you need to install the kernel header files (linux-headers-"your_kernel_version"). find out what kernel you are using and then install the appropriate kernel header files with apt-get. also make sure to have the "build-essential" (sudo apt-get install build-essential) package installed.

---

### Post by inovermyheadd on 2006-02-22
Hey Ox,

My build essential is up to date...but I can't say I understand the linux headers thing...I'll look it up though thanks!

---

### Post by 0x_ on 2006-02-23
No worries, learn how to use "apt-get" then check what linux kernel you are using (you can see the linux kernel version at boot up - grub does display it or do a "uname -a"). then install the linux-header package via apt-get.

---

### Post by DarrenB on 2006-03-01
I followed some of the earlier instructions in this thread and had to re-install (completely lost all sound...which was working through the internal speakers).
 This page [http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)

worked fine on  a clean install. (although watch the lines: 
   [I]  Install lsb-base

    * sudo dpkg -i lsb-base_3.0-14_all.deb[/I] 
This should read :[I]
Install lsb-base

    * sudo dpkg -i lsb-base_3.0-1[COLOR="Red"]5[/COLOR]_all.deb[/I] 

Otherwise , completely sorted my Fujitsu-siemens S7020....

---

### Post by inovermyheadd on 2006-03-02
Hey, I actually got kbuel's code to work, but still no success w/ the headphone jack.


DarrenB,

I did what you suggested and it also did not fix my headphone jack.  It was, however, awesome that I could run my volume with just the keyboard controls.

Maybe my problem lies in the fact that I all ready have sound.  My speakers work fine with the Realtek ALC880 but no sound at all comes out of my headphones.  I have no clue what to do...can anyone help?

Another problem is that I may have entered something in incorrectly like:

[PHP]options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss[/PHP]

My model is not the z71v...I actually don't know what it is...MW1 I think...but what should I put in there?  I'm confused

---

### Post by al-yazir on 2006-04-22
[QUOTE=inovermyheadd]Hey, I actually got kbuel's code to work, but still no success w/ the headphone jack.


DarrenB,

I did what you suggested and it also did not fix my headphone jack.  It was, however, awesome that I could run my volume with just the keyboard controls.

Maybe my problem lies in the fact that I all ready have sound.  My speakers work fine with the Realtek ALC880 but no sound at all comes out of my headphones.  I have no clue what to do...can anyone help?

Another problem is that I may have entered something in incorrectly like:

[PHP]options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss[/PHP]

My model is not the z71v...I actually don't know what it is...MW1 I think...but what should I put in there?  I'm confused[/QUOTE]

I still have the same problem.

I'm using Dapper Beta, and sound worked with [this](http://www.ubuntuforums.org/showpost.php?p=791304&postcount=164) instruction through speakers, but not through the headphone jack.

The one kbuel posted earlier totally messed my sound up.

I also tried [this](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy) instruction, but it didn't change anything. Still only he speakers work, from headphone jack, there's only silence. 

Is it maybe a problem with Dapper and will be solved, when Dapper is final?
Someone has any ideas, how i might solve the problem?

---

### Post by akshaydua on 2006-05-14
It seems that the alsa installation required the program GNU 'msgfmt', which can be installed by:

apt-get install gettext

After this things should proceed smoothly. Also, if the installation cannot find test.wav.bz2 add the following (marked) lines to the install script:
...
## sample wave
if [ -d /usr/share/sounds/alsa ]; then
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav                           <-- new at line number 77
     rm -rf test.wav
else
     mkdir /usr/share/sounds/alsa
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav                            <-- new at line number 83
     rm -rf test.wav
fi
...

hope this helps

---

### Post by JeanJean on 2006-06-08
I have the same problem on my asus A6Vc laptop
This is the output from lspci:

**Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De finition Audio Controller (rev 04)**

Does I have to install the Realtec drivers or alsa 1.11 ? (I use ubuntu dapper)

JeanJean

---

### Post by mhafren on 2006-07-09
Hi.
The configure stage goes fine but when I run sudo make I get the following error.

make dep
make[1]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[4]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[4]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[3]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Entering directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[2]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[1]: Leaving directory `/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make -C /lib/modules/2.6.15-25-386/build SUBDIRS=/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.o
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:749: error: field 'pdev' has incomplete type
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:762: error: 'platform_bus_type' undeclared here (not in a function)
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:763: warning: initialization from incompatible pointer type
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:764: warning: initialization from incompatible pointer type
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c: In function 'snd_generic_device_register':
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:797: warning: implicit declaration of function 'platform_device_register'
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c: In function 'snd_generic_device_unregister':
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:807: warning: implicit declaration of function 'platform_device_unregister'
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c: In function 'snd_generic_suspend':
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:817: error: 'SUSPEND_DISABLE' undeclared (first use in this function)
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:817: error: (Each undeclared identifier is reported only once
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:817: error: for each function it appears in.)
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:820: warning: type defaults to 'int' in declaration of '__mptr'
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:820: warning: implicit declaration of function 'to_platform_device'
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:820: warning: initialization makes pointer from integer without a cast
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c: In function 'snd_generic_resume':
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:832: error: 'RESUME_ENABLE' undeclared (first use in this function)
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:835: warning: type defaults to 'int' in declaration of '__mptr'
/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:835: warning: initialization makes pointer from integer without a cast
make[3]: *** [/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.o] Error 1
make[2]: *** [/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore] Error 2
make[1]: *** [_module_/home/mhafren/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [compile] Error 2


Does anybody know what might be wrong? Help would really be apreciated.

---

### Post by stromgren on 2006-08-01
I have exactly the same problem with the same kernel and a fresh install of Ubuntu Dapper. Looks like there's a problem whit this kernel, the one used in the HOWTO was an older version.

Looking some rows above in the make output it looks like the problem appers when compiling "sound.o".

```
  
CC [M]  /home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.o
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.c: In function "snd_register_device":
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.c:247: varning: passing argument 2 of "class_device_create" makes pointer from integer without a cast
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.c:247: varning: passing argument 3 of "class_device_create" makes integer from pointer without a cast
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.c:247: varning: passing argument 4 of "class_device_create" from incompatible pointer type
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/sound.c:247: varning: passing argument 5 of "class_device_create" discards qualifiers from pointer target type
  CC [M]  /home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.o
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:749: error: field "pdev" has incomplete type
/home/andreas/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/init.c:762: error: "platform_bus_type" undeclared here (not in a function)

```

I'd really appreciate some help on this problem.

---

### Post by stromgren on 2006-08-03
Now it's working for me. I didn't have to install the driver in order to make it work, I just followed this thread.

[http://www.ubuntuforums.org/showthread.php?t=168793&highlight=alc880+spdif](http://www.ubuntuforums.org/showthread.php?t=168793&highlight=alc880+spdif)

---

### Post by Chiro on 2006-09-02
I have an Asus A6000 and had problems with listening through the headphone jack. I followed these instructions and now everything works like a charm! Thank's a lot:D

---

### Post by LostAndFound on 2006-09-23
Hi,

Many thanks for user "kbue's" post on page one. The instructions worked for me on a MSI S271 Megabook laptop with HDA ATI SB
and Realtek ALC883. I just had one further suggestion. After a kernel upgrade, I again lost the headphone output. It took me some time to get it back. 

What finally worked was to remove the alsa-driver-1.0.12-4.05b (installation) folder, untar the folder again, and then start from scratch with ./configure etc.
Possibly the configure process was not 'renewing' before this.
I also had to 'apt-get install linux-headers-xxxx'.

Maybe this will help someone out after a kernel upgrade.

---

### Post by baserg on 2006-11-28
This is working
[http://dev-board.com/?p=16](http://dev-board.com/?p=16)

---

### Post by blew on 2006-11-28
Hi all.

I had the same problem (lots of people seem to have it - just search for "headphones" in ubuntu forums: lots of results!).

Anyway, i tried all sorts of solutions mentioned in all the threads i could find, except the ones where i had to actually compile something. Not that i was afraid of it, but i just couldn't believe the solution for this had to be so "complicated".

I eventually gave up, as none of the solutions worked out for me. So i decided to just upgrade alsa to the latest version, something mentioned in some of those threads i read.

So, bottom line, i just wanted to tell you that getting the latest alsa files and doing exactly what this page says ([http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel)) solved my problem.

I still don't have a "headphones sense" option anywhere, but now i have a volume control for the built in speakers and another one for the headphones.

So, if you're getting desperate by now (like i was just until a few minutes ago), just give it a try at getting/compiling/installing the latest alsa drivers. If you run into trouble (i did have one or two issues with the instructions on that page, but easily solved) just ask here. I'll try to keep an eye on this topic.

I hope this helps you solve this annoying problem.

---

### Post by simple on 2006-12-17
I've tried so far the manual method from the above link from the alsa guide, manually with the alc880 linux driver 4.05b and r3.56, also the auto install scripts and every time the results are the same. No audio coming from the headphone jack, just output through the speakers though the headphones are plugged in. Also no headphone option for audio or volume, can you help me out blew? What was the two little problems you ran into? I made the /etc/modutils/alsa file and modules-updated, no dice..

---

### Post by W3ird_N3rd on 2006-12-30
Hey Simple, I tried zolero's tip because I felt there shouldn't be any need to compile anything.

[http://www.ubuntuforums.org/showthread.php?t=168793](http://www.ubuntuforums.org/showthread.php?t=168793)

This was it:

> With Dapper all hardwares works (almost) perfectly. Only the SPDIF OUT must be configured for listen music on headphones. For do this U need to insert this line at the bottom of file /etc/modprobe.d/alsa-base, and then make a restart

options snd-hda-intel model=z71v position_fix=1

It worked and I run 6.06 (Dapper) on an Asus A6Va :). Now listening!

---

### Post by simple on 2006-12-31
> **W3ird_N3rd said:**
> Hey Simple, I tried zolero's tip because I felt there shouldn't be any need to compile anything.

[http://www.ubuntuforums.org/showthread.php?t=168793](http://www.ubuntuforums.org/showthread.php?t=168793)

This was it:



It worked and I run 6.06 (Dapper) on an Asus A6Va :). Now listening!

Well, when I was running Ubuntu I also tried that little tip, but it didn't work. I'm running arch now and still nothing is working, so I don't know... I have a compaq so I forfeit my right to have a smooth operating computer. sr1318nx is the model number so if you have same comp and have this working, I not only commend you but I recommend you help me out :p Thanks for reply W3ird_N3rd.

---

### Post by W3ird_N3rd on 2006-12-31
I don't buy Compaqs.. I build every computer myself, I only buy complete laptops (like my Asus A6Va I mentioned).

Your Compaq has a different PCB I think. Open /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz and read the textfile inside of it. z71v is the 3-jack with shared SPDIF setup.

Ooooooohw.. You don't even have a laptop! Is it onboard sound? Hmm it has to be. You have an Asus mainboard. You do still have the ALC880. You can try the following models instead of z71v:

> 	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  6stack	6-jack in back, 2-jack in front
	  6stack-digout	6-jack with a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)
	  asus		3-jack
	  uniwill	3-jack
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20 laptop
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)
(that's a copypaste from alsa-configuration.txt). I'd say at least one of these models should get you a working headphone-out.

---

### Post by W3ird_N3rd on 2007-01-08
Well simple I'm really curious if you have sound now?

---

### Post by Cisto on 2007-02-03
> **kbuel said:**
> Hey all,

This is what I did:

I downloaded the file that psp posted, which is [here:]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True")

The file should be:
realtek-linux-audiopack-3.5-2.tar.bz2

Extract it
tar xvf realtek-linux-audiopack-3.5-2.tar.bz2

Go into the directory it created and untar the file named: alsa-driver-1.0.9b_22.tar.bz2
tar xvf alsa-driver-1.0.9b_22.tar.bz2


Compile and Install:
before you do this you may need to do an sudo apt-get install build-essential
You WILL need your Linux kernel headers also, you can get these from the package manager also. 

Look for:
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386

linux-headers-2.6.12-10 is the newest version.. and is probably the version you have (if you've been doing the automatic updates).  Base breezy install had linux 2.6.12-9, but there was an update to 2.6.12-10.  Basically get the version you have because it will compile it as a module for that kernel.  I think there is a way to specify what version when doing the configure, but i'm not sure how, so to get it to work for the version i'm using I removed the linux-headers-2.6.12-9, so I just had version linux-headers-2.6.12-10.


1) cd alsa-driver-1.0.9b_22
2) ./configure
3) sudo make
4) sudo make install
5) sudo ./snddevices

Then I updated a few files:
I may have updated more files then needed.... but the documentation was vague and so I put the following in a more files than were probably needed....

options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I put the above lines in the BOTTOM of the following files:
/etc/modutils/alsa-base
/etc/modprobe.d/alsa-base
/etc/modprobe.d/aliases
/etc/modprobe.d/sound

(I believe I created the file /etc/modprobe.d/sound)

Again, those lines may not need to go into all those file, but that is what I did, and it worked.

I also added the following lines to the bottom of /etc/modules
snd-hda-intel
snd-ALC880

Restart the computer and then it should work.  There should be a new slider for Headphone in the volumn control (next to PCM).  By default it will be muted, so unmut it before trying anything.


Lemme know if you have anymore questions.
-kbuel

well, i used the "model=z71v" line for a long time, then i discovered that the best way to make all things working without having stupid problems in mixing control is using the "model=w810" instead.

---

### Post by nisbus on 2007-02-12
Thanks KBuel, 

I downloaded the Realtek drivers and unpacked it.
from the terminal I went to the unpacked directory 

```
sudo sh install
```

After the installation finished I added all of your additions to the files and restarted.

I finally have sound on my ASUS W1Vc laptop (and I kept the z71v as the model after trying to use asus-w1v before)

---

### Post by salvo1 on 2007-02-17
great!

Thanks you very much!

It works with my MSI S262 notebook.

---

### Post by simple on 2007-03-17
> **W3ird_N3rd said:**
> Well simple I'm really curious if you have sound now?

Ahhh! So simple. All I had to do was use "6stack" as the model and the headphone jack worked. It still plays music through the speakers but I can just turn them down. Thanks W3ird_N3rd~

---

### Post by arbitrabbit on 2007-05-07
I have got 6 jacks at the back, a digital in and and adigital out at the back again and 3 jacks in the front. Will that be 6stack-digout or is there any model number not listed in here?

---

### Post by vigyani on 2007-09-08
Hi I have Acer Aspire 4710 running Ubuntu Feisty (updated). There was no sound from headphone jack, built in speakers worked. It has Intel HDA ICH7 and some Realtek chipset (probably Realtek ALC 268, that is what I see in volume control preferences after finishing install).
I downloaded the latest driver (Other version 4.06b) from Realtek site from the link [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") 

I uncompressed and executed the install script:
tar xvf realtek-linux-audiopack-4.06b.tar.bz2 
cd realtek-linux-audiopack-4.06b/
sudo ./install

It executed but came out with the error:
"alsaconf not found"

Anyway I rebooted and sound works from the headphone jack.:)

I observed that there is problem with sound in vlc. Speaker is mute and I cannot make it unmute!! Sometimes though speaker icon shows mute but there is some sound with noise.:confused:

I have no idea what went wrong.
In "Movie Player" it works fine.

DO look at this post [http://ubuntuforums.org/showthread.php?t=558069&highlight=aspire+4710]("http://ubuntuforums.org/showthread.php?t=558069&highlight=aspire+4710")
Every thing related to sound works.

Thanks for the post and for help in advance.:lolflag:

regards
Vig

---

### Post by ciaranjdunphy on 2008-01-04
I have an Acer Travelmate 5720 with a realtek HDA soundcard. I have the same problem with playback (plays only through the integrated speakers, even when something is connected to the headphone jack), and I have tried to install the Realtek drivers to rectify the problem. Unfortunately I don't have the technical know-how to do a manual install, and the current drivers are different to the ones mentioned in the previous post. If someone could possibly post some kind of *really* simple and easy to follow solution to the problem, that would be fantastic.

---

### Post by ciaranjdunphy on 2008-01-04
Ahem, a generous friend of mine found a solution and everything now appears to be working. Hurrah. Thanks all the same!

---

