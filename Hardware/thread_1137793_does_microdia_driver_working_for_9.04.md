---
title: "does microdia driver working for 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by Erdem on 2009-04-25
Hi

i have usb webcam and lsusb output down here:

```

erdem@pc:~$ lsusb
[COLOR="Red"]Bus 001 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878[/COLOR]
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

i search about how to install it and i found this link:
[http://ubuntuforums.org/showpost.php?p=5165181&postcount=9](http://ubuntuforums.org/showpost.php?p=5165181&postcount=9)

but it doesn't work for me...
can anyone help me?

Thank you

---

### Post by Erdem on 2009-04-26
can anyone help?

---

### Post by raix0r on 2009-04-28
I tried the same.

My cam is a

```

Bus 001 Device 005: ID 0c45:613b Microdia Win2 PC Camera

```So I followed these instructions:

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1)

But instead of the mentioned messages in dmesg I get these after plugging the cam in

```

[ 1363.665933] usbcore: registered new interface driver sn9c20x
[ 1363.665941] sn9c20x: SN9C20x USB 2.0 Webcam Driver v2009.01 loaded
[ 1380.925060] usb 1-4.4: USB disconnect, address 4
[ 1380.925775] usb 1-4.4: Disconnecting SN9C1xx PC Camera...
[ 1380.925782] usb 1-4.4: V4L2 device /dev/video0 deregistered
[ 1386.244180] usb 1-4.4: new full speed USB device using ehci_hcd and address 5
[ 1386.337131] usb 1-4.4: configuration #1 chosen from 1 choice
[ 1386.337526] usb 1-4.4: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[ 1386.387396] usb 1-4.4: OV7660 image sensor detected
[ 1386.574767] usb 1-4.4: Initialization succeeded
[ 1386.574876] usb 1-4.4: V4L2 device registered as /dev/video0
[ 1386.574881] usb 1-4.4: Optional device control through 'sysfs' interface disabled
[ 1386.622471] usb 1-4.4: usb_submit_urb() failed, error -28

```

I think some module is getting access to the cam, before the new driver module can take control.
And of course programs like camorame are reporting an error when trying to read /dev/video0.
Any hints?


x

---

### Post by paulsans on 2009-06-14
> **Erdem said:**
> Hi

i have usb webcam and lsusb output down here:

```

erdem@pc:~$ lsusb
[COLOR=Red]Bus 001 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878[/COLOR]
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```i search about how to install it and i found this link:
[http://ubuntuforums.org/showpost.php?p=5165181&postcount=9](http://ubuntuforums.org/showpost.php?p=5165181&postcount=9)

but it doesn't work for me...
can anyone help me?

Thank you

Just follow this. Bye.

Preamble
--------

1. "Gentlemen" of Conceptronic, to which I wrote a couple of years ago, asking for a solution to my problem, were absolutely
absent in this. My source was the following:

[http://ubuntuforums.org/showthread.php?t=982471&page=1](http://ubuntuforums.org/showthread.php?t=982471&page=1)

This source, suitably revised, permitted me to write the following solution.

2. This solution was tested on an Ubuntu 9.04 AMD64bit, but also works on 32bit systems. Let me know if it works also with previos releases (it should)!

3. Perhaps the solution proposed, although functional, is not optimized. That is, some instruction is redundant or even useless. But would not cause any damage.

START
-------

Let's verify that our microdia sn9c20x based webcam is connected to our PC and is recognized by the system.
Open a terminal window and type the following (without the dollar, it is used to indicate the prompt):

$ lsusb|grep Microdia

The result should be something like this:

Bus 002 Device 003: ID 0c45:627b Microdia PC Camera (SN9C201)

Remember: everything should work with SN9C20x chip based webcam.

Now, to install webcam kernel module (aka driver),
open a terminal window and type the following:

# This will install kernel source. If you already have, it does nothing. If in doubt, run it.
$ sudo apt-get install linux-headers-`uname -r` linux-source

# This install other software, needed by our procedure.
$ sudo apt-get install ubuntu-dev-tools
$ sudo apt-get install exuberant-ctags
$ sudo apt-get install git

# Now I go to my home directory.
$ cd

# Download and clone microdia source folder.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

# Compile kernel module.
$ cd microdia
$ make

# Install and load it.
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x

# This is to clean microdia folder from installation files generated during the make process.
$ make clean

Let's try it with software cheese 
$ sudo apt-get install cheese
$ cheese

Of course I also tried it with skype and works fine.

Be carefull about what follows:

To re-install kernel module after a system update that changes the kernel,
just open a terminal window and type the following :

# I go to my home directory.
$ cd
# If there is no microdia folder, I download it.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
# otherwise, I simply move to that folder.
$ cd microdia

$ make clean
$ make
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x
$ make clean

THE END
-----
Send me your smiling webcam shot! :p

---

### Post by blissfulpenguin on 2009-06-16
That's an incredibly great set of instructions!  I would really like to try this, and I am considering grabbing the previous kernel to work with.  But, the problem I have encountered in the past with installing modules comes into play with the extra modules I need to ensure internet connectivity (madwifi) and graphics (nvidia-glx-180).
It looks like you're describing just compiling modules, but I am so not familiar with this.  I know it is a sensitive procedure.  Where can I learn more about what is being done in general here?

Thanks again for the awesome post!
(...)
Oh, wow, I understand now that I was not compiling the kernel.  Big difference!  So, I've attached pictures as you asked!  Yay for Linux!

---

### Post by restless on 2009-06-19
THANK YOU SO MUCH paulsan!!!!!!!

it has been a while since i had my webcam working and i tried all the tutorials i could find around, always without success...

I upgraded to 9.04 a couple of days ago, and i just tried your instructions..
and IT WORKS!!!!

thanx a lot!!!

Lorenzo

---

### Post by bzr on 2009-06-24
I had used your method and it worked great, though the color from my cam is still a little "not right". I just had a kernel update and Skype wouldn't recognize the cam again so I followed the last part of the instructions and got the cam to work, again!

Thanks, man! You rock!!!

---

### Post by chrisj26 on 2009-06-24
I was using it fine under Ubuntu 8.04 but ever since I upgraded I to 9.04 I haven't been able to install it. I am not on my Ubuntu box now but will post back exact results.

---

### Post by chrisj26 on 2009-06-25
[ 1919.452156] sn9c20x: Unknown symbol video_unregister_device
[ 1919.452340] sn9c20x: disagrees about version of symbol video_device_alloc
[ 1919.452343] sn9c20x: Unknown symbol video_device_alloc
[ 1919.452432] sn9c20x: disagrees about version of symbol video_register_device
[ 1919.452435] sn9c20x: Unknown symbol video_register_device
[ 1919.452951] sn9c20x: disagrees about version of symbol video_device_release
[ 1919.452955] sn9c20x: Unknown symbol video_device_release
when I try insmod I get "insmod: error inserting 'sn9c20x.ko': -1 Unknown symbol in module"
Anyone? I installed it once and it worked fine (about 3 days ago) then I shut down my computer and as I left the room I saw a fleeting glimpse of error messages regarding the cam ( I remotely remember seeing power somewhere)! Can anyone help? It's still going fine in Vista but the quality was much better in Ubuntu 8.04.

---

### Post by jhahoneyk on 2009-08-07
As the Microdia driver we're downloading from the repo is licensed under GPL, can't we ask kernel.org people to make it a part of the Linux kernel?
If not that, at least can't it be made a part of the ubuntu repositories?
So that it can be installed and configured using dkms ( e.g sudo apt-get install microdia-driver ). My dad has this camera and he finds it really confusing when I tell him "You have to recompile the kernel module each time you get a new kernel upgrade through the ubuntu repos".

---

### Post by Ashrael on 2009-08-26
There are a few things in Ubuntu/linux that bug me... Webcam support is one of them. And, yeah, I know, it's the manufacturer that should support it's own hardware. But shouldn't Mark Shuttleworth use some of his vast wealth and resources to get manufacturers to deliver a working linux driver or open up the source code? Or maybe pay those guys from MXHAARD to develop a free open source driver? I don't know what's best...

My webcam (ID 0c45:613c Microdia PC Camera (SN9C120)) used to work, not that well, but it worked... Now, well, it does work, but even worse then before... I am not even gonna give you guys a screenshot, you can imagine an almost white screen I guess...

And, YEAH, this stuff should be included in Ubuntu repo's! I am a bit of a nerd, and I do not even want to go and recompile sh*t every kernel update... This stuff happens way too often to make this usable for a n00b / simple user...
I have been horsing around with different webcams since 2003, and this is one of the (few) issues that keep many of my customers from using Ubuntu/linux. They want this kinda stuff, they're used to this stuff working in w*nd*ws. Also installing a scanner and getting it to work is not straightforward / easy enough for an end-user. 

Well I hope something happens, because after upgrading to jaunty things have not improved across the line... I am not downgrading again, because on average I am still content, but, I am surprised how the problems have shifted....

---

### Post by jeffvader on 2009-08-29
Greetings,

Who knows!?

The repository quoted above:

# I go to my home directory.
$ cd
# If there is no microdia folder, I download it.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
# otherwise, I simply move to that folder.
$ cd microdia


... does not seem to be working any longer. It is now virtually impossible to follow the instructions above, as the microdia.git driver is nowhere to be seen any more.

I upgraded to Jaunty in the hope that many shortcomings in the previous versions of Ubuntu would be solved. NAH!

I have been a great supporter of Ubuntu locally, but I have to say that Ubuntu still fails to make it easy for users to just plug and play devices.

Not only one has to go through endless outdated posts to find a solution, but sometimes - like in this situation - there is no solution!

So much for criticising MS windows! 

At least that system has a true plug and play facility. You buy the darn device, plug it (or get the driver), and voila!

I have to say, as much as I like Ubuntu, it still remains a great disappointment.

I cannot get my webcams to work, and there is NOTHING by way of help to overcome this issue.

FREE? Dudes, I have spent more on UBUNTU by way of books, new devices that do not work and time than I would ever spend on windows!

I don't like windows, but given the weaknesses of Ubuntu, it is a necessary evil I have to live with if I want things done without the complications of this system.

Yes, I am very frustrated now.

---

### Post by davidpodhola on 2009-10-03
> **paulsans said:**
> Just follow this. Bye.

Preamble
--------

1. "Gentlemen" of Conceptronic, to which I wrote a couple of years ago, asking for a solution to my problem, were absolutely
absent in this. My source was the following:

[http://ubuntuforums.org/showthread.php?t=982471&page=1](http://ubuntuforums.org/showthread.php?t=982471&page=1)

This source, suitably revised, permitted me to write the following solution.

2. This solution was tested on an Ubuntu 9.04 AMD64bit, but also works on 32bit systems. Let me know if it works also with previos releases (it should)!

3. Perhaps the solution proposed, although functional, is not optimized. That is, some instruction is redundant or even useless. But would not cause any damage.

START
-------

Let's verify that our microdia sn9c20x based webcam is connected to our PC and is recognized by the system.
Open a terminal window and type the following (without the dollar, it is used to indicate the prompt):

$ lsusb|grep Microdia

The result should be something like this:

Bus 002 Device 003: ID 0c45:627b Microdia PC Camera (SN9C201)

Remember: everything should work with SN9C20x chip based webcam.

Now, to install webcam kernel module (aka driver),
open a terminal window and type the following:

# This will install kernel source. If you already have, it does nothing. If in doubt, run it.
$ sudo apt-get install linux-headers-`uname -r` linux-source

# This install other software, needed by our procedure.
$ sudo apt-get install ubuntu-dev-tools
$ sudo apt-get install exuberant-ctags
$ sudo apt-get install git

# Now I go to my home directory.
$ cd

# Download and clone microdia source folder.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

# Compile kernel module.
$ cd microdia
$ make

# Install and load it.
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x

# This is to clean microdia folder from installation files generated during the make process.
$ make clean

Let's try it with software cheese 
$ sudo apt-get install cheese
$ cheese

Of course I also tried it with skype and works fine.

Be carefull about what follows:

To re-install kernel module after a system update that changes the kernel,
just open a terminal window and type the following :

# I go to my home directory.
$ cd
# If there is no microdia folder, I download it.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
# otherwise, I simply move to that folder.
$ cd microdia

$ make clean
$ make
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x
$ make clean

THE END
-----
Send me your smiling webcam shot! :p
Great tutorial. I am able to use my camera now. Only 2 things in today's kernel (linux-headers-2.6.28-15-generic):

1. to install git i needed to use 'sudo apt-get install git-core'
2. I needed to create file bounds.h in /sr/src/linux-headers-2.6.28.15-generic/include/linux. The code in bounds.h is from [http://groups.google.com/group/microdia/browse_thread/thread/e10ef9376f2a19f4](http://groups.google.com/group/microdia/browse_thread/thread/e10ef9376f2a19f4)

---

### Post by jhahoneyk on 2009-10-03
> **jeffvader said:**
> Greetings,

Who knows!?

The repository quoted above:

# I go to my home directory.
$ cd
# If there is no microdia folder, I download it.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
# otherwise, I simply move to that folder.
$ cd microdia


... does not seem to be working any longer. It is now virtually impossible to follow the instructions above, as the microdia.git driver is nowhere to be seen any more.

I upgraded to Jaunty in the hope that many shortcomings in the previous versions of Ubuntu would be solved. NAH!

I have been a great supporter of Ubuntu locally, but I have to say that Ubuntu still fails to make it easy for users to just plug and play devices.

Not only one has to go through endless outdated posts to find a solution, but sometimes - like in this situation - there is no solution!

So much for criticising MS windows! 

At least that system has a true plug and play facility. You buy the darn device, plug it (or get the driver), and voila!

I have to say, as much as I like Ubuntu, it still remains a great disappointment.

I cannot get my webcams to work, and there is NOTHING by way of help to overcome this issue.

FREE? Dudes, I have spent more on UBUNTU by way of books, new devices that do not work and time than I would ever spend on windows!

I don't like windows, but given the weaknesses of Ubuntu, it is a necessary evil I have to live with if I want things done without the complications of this system.

Yes, I am very frustrated now.

Why is it Ubuntu's shortcoming if a certain device manufacturer doesn't provide drivers for Linux? Thats how Windows 'supports' more hardware because they bribe hardware vendors to make their hardware run smoothly on windows only.

I have the same camera and it works fine, and I've checked it again and the link is working fine this very moment.

And please define "true plug and play".

And I'm sorry but you don't know what free means, please consult a dictionary or visit [www.fsf.org](www.fsf.org) to find that free also means as in "to become free" (or freedom). Free means you can play with system (e.g. in this case you have to insert a module into the kernel for the camera) and make it do what you wish. YOU are free, the user is the central point for Free Software. If you only installed Ubuntu because its free of cost, you're missing a lot.

And by the way, next time pick a Logitech one, they rock dude. Also, try the link once again, its working. All the best and be free :P

P.S. Check out this too [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by ukripper on 2009-11-13
> **paulsans said:**
> Just follow this. Bye.

Preamble
--------

1. "Gentlemen" of Conceptronic, to which I wrote a couple of years ago, asking for a solution to my problem, were absolutely
absent in this. My source was the following:

[http://ubuntuforums.org/showthread.php?t=982471&page=1](http://ubuntuforums.org/showthread.php?t=982471&page=1)

This source, suitably revised, permitted me to write the following solution.

2. This solution was tested on an Ubuntu 9.04 AMD64bit, but also works on 32bit systems. Let me know if it works also with previos releases (it should)!

3. Perhaps the solution proposed, although functional, is not optimized. That is, some instruction is redundant or even useless. But would not cause any damage.

START
-------

Let's verify that our microdia sn9c20x based webcam is connected to our PC and is recognized by the system.
Open a terminal window and type the following (without the dollar, it is used to indicate the prompt):

$ lsusb|grep Microdia

The result should be something like this:

Bus 002 Device 003: ID 0c45:627b Microdia PC Camera (SN9C201)

Remember: everything should work with SN9C20x chip based webcam.

Now, to install webcam kernel module (aka driver),
open a terminal window and type the following:

# This will install kernel source. If you already have, it does nothing. If in doubt, run it.
$ sudo apt-get install linux-headers-`uname -r` linux-source

# This install other software, needed by our procedure.
$ sudo apt-get install ubuntu-dev-tools
$ sudo apt-get install exuberant-ctags
$ sudo apt-get install git

# Now I go to my home directory.
$ cd

# Download and clone microdia source folder.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

# Compile kernel module.
$ cd microdia
$ make

# Install and load it.
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x

# This is to clean microdia folder from installation files generated during the make process.
$ make clean

Let's try it with software cheese 
$ sudo apt-get install cheese
$ cheese

Of course I also tried it with skype and works fine.

Be carefull about what follows:

To re-install kernel module after a system update that changes the kernel,
just open a terminal window and type the following :

# I go to my home directory.
$ cd
# If there is no microdia folder, I download it.
$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
# otherwise, I simply move to that folder.
$ cd microdia

$ make clean
$ make
$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32 # Just needed on a 64bit System. Not necessary on x86 32bit.
$ sudo insmod ./sn9c20x.ko
$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install sn9c20x.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a
$ sudo modprobe sn9c20x
$ make clean

THE END
-----
Send me your smiling webcam shot! :p

Perfect instructions for Jaunty 9.0464bit, my panther GX 4 megapixel camera working great with your instructions.

Only one thing different to install git it is git-core now in repos.

---

### Post by thedutchrockstar on 2010-02-07
unfortunatly it did not work for me :( I followed all your instructions and everything worked fine yet no webcam pic shows up :( when starting cheese my webcam led lights up and then after a little bit of waiting it turns off again...
I use ubuntu 9.10 karmic koala, the info on my cam is : trust 16430
lsusb gives me:
> Bus 002 Device 003: ID 0c45:613e Microdia PC Camera (SN9C120)

Any help would be awesome
Thanks in advance
Vincent

---

### Post by ukripper on 2010-02-08
> **thedutchrockstar said:**
> unfortunatly it did not work for me :( I followed all your instructions and everything worked fine yet no webcam pic shows up :( when starting cheese my webcam led lights up and then after a little bit of waiting it turns off again...
I use ubuntu 9.10 karmic koala, the info on my cam is : trust 16430
lsusb gives me:


Any help would be awesome
Thanks in advance
Vincent

can you post output of the following:
```
lsmod 
```

ubuntu 9.10 kernel already detects and load modules for this chipset SN9C1xx. It should be working right out of the box in karmic.

Have you tried cheese?

---

### Post by thedutchrockstar on 2010-02-08
> **ukripper said:**
> can you post output of the following:
> lsmod 

ubuntu 9.10 kernel already detects and load modules for this chipset SN9C1xx. It should be working right out of the box in karmic.

Have you tried cheese?

this is what I get when using lsmod
> Module                  Size  Used by
sn9c20x                73136  0 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
gspca_sonixj           20796  0 
gspca_main             22812  1 gspca_sonixj
iptable_filter          3100  0 
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
sn9c102               139268  0 
videodev               36736  3 sn9c20x,gspca_main,sn9c102
v4l1_compat            14496  1 videodev
snd_usb_audio          84224  2 
snd_usb_lib            16284  1 snd_usb_audio
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
parport_pc             31940  1 
fglrx                1989532  32 
agpgart                34988  1 fglrx
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
rt2860sta             522456  1 
snd_seq_dummy           2656  0 
i2c_nforce2             6784  0 
k8temp                  4188  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  21 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
usb_storage            52576  1 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
floppy                 54916  0 
forcedeth              54152  0

I do use cheese to test my webcam =D yet noe results (as mentioned in my earlier post :()

---

### Post by ukripper on 2010-02-09
> **thedutchrockstar said:**
> this is what I get when using lsmod


I do use cheese to test my webcam =D yet noe results (as mentioned in my earlier post :()

When you run cheese what error you getting?

---

### Post by gcheckmail@gmail.com on 2011-02-13
Hello mates.. everything worked with Cheese.. but still unable to get it working on Skype.. any help is appreciated...

9.04, Frontech cam.. 32 bit..

---

