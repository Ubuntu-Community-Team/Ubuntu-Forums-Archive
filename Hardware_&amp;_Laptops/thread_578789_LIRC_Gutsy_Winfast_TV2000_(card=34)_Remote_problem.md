---
title: "LIRC Gutsy Winfast TV2000 (card=34) Remote problems"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by davem2312 on 2007-10-17
Hello,

I just recently purchased a Winfast TV2000 TV Tuner Card, and I can use the card with tvtime in gutsy quite well.  Now, I would like to get my Remote working, but I can't seem to get it to work.

I followed this very simple guide

[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

but when I got to try

```
$ irw

```
The terminal appears to hang like it should, but no button presses are detected.  Can anyone try to help me diagnose what might be happening?  Thanks.

--dave

---

### Post by davem2312 on 2007-10-18
bump

---

### Post by teet on 2007-10-19
[http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html](http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html)

Check out my guide.  It may be of some help.  Although lirc stuff has changed quite a bit in gutsy as compared to feisty.  The lircd.conf and lircrc files should both still work though.

-teet

---

### Post by davem2312 on 2007-10-19
Thanks, I will check it out today after class, and I will let you know how it goes...

Dave

---

### Post by davem2312 on 2007-10-19
There were only two hiccups that I could see, but it seemed not to work...



This is an error I received part way through, which leads me to believe that a download of some source failed or something.

```
$ sudo rm /usr/src/lirc*deb
rm: cannot remove `/usr/src/lirc*deb': No such file or directory

```

When I tried to start the lirc daemon, this happened.

```

$ sudo /etc/init.d/lirc start
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

```


And last but not least, when I tried 

```
$ irw
```

the symptoms were exactly as above, and the terminal hung like it should, but no button presses were recorded.

---

### Post by Mfvane on 2007-10-20
Hi, 

I am experiencing similar problems with my lirc. What I found was that the kernel 2.6.22(presente in Gutsy)  cant handle the module lirc_gpio, so you'll need some workarounds, using the driver dev/input. Here are some workarounds:: 

[https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative](https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/125384](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/125384)

They didnt work for me though... but everyone says they work fine!

Let me know if I am the only one with bad luck!
Hope this works for you,
Matheus

---

### Post by Mfvane on 2007-10-21
Hi,
As I did before, DONT disable ir-common by editting the ir-keymaps.c and the copying the ir-common.ko... That was the difference between having lirc working and a total failure... 
At least for me, I followed those guides that I told you before and recompiled the ir-common module from source. After recompiling the modules, I substituted the modified ir-common.o for the original one and used irrecord --driver=dev/input --device=/dev/input/irdev /etc/lircd.conf... then, with a restart, and irexec my remote started to work again. 
Hope this works
Pease let me know of the outcomes!
Matheus
PS: kill lirc before running irrecord

---

### Post by merwizard on 2007-10-23
Matheus, please, give us more detailed instructions on how to achieve that, since, I too have a Winfast board, and the remote stopped working for me. Using dev/input doesn't work for me, either.

---

### Post by bastille on 2007-10-24
Hi,
same problem here. I tried to follow the instructions as they are described [here]("https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative") , but when i use ```
sudo irrecord -H dev/input -d /dev/input/event4 lircd.conf
``` it tells me to hold down an arbitrary button. Doing exactly this, this is the output: ```
Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event4'

```
I killed lircd before, so i don't know what went wrong here.
Basti

---

### Post by Mfvane on 2007-10-24
> **bastille said:**
> Hi,
same problem here. I tried to follow the instructions as they are described [here]("https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative") , but when i use ```
sudo irrecord -H dev/input -d /dev/input/event4 lircd.conf
``` it tells me to hold down an arbitrary button. Doing exactly this, this is the output: ```
Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event4'

```
I killed lircd before, so i don't know what went wrong here.
Basti

Hi, Bastilee, you need to check if event4 is you irdevice, by doing the command:

sudo cat /proc/bus/input/devices

here is the output part of mine:

I: Bus=0001 Vendor=1554 Product=4011 Version=0001
N: Name="bttv IR (card=72)"
P: Phys=pci-0000:02:06.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=100003
B: KEY=2c0814 100004 0 0 0 4 2008000 2090 2001 1e0000 4400 0 ffc

but, when I check my /dev/input, I dont have the event4 listed there, it is listed as irdev:

ls /dev/input

event0  event2  event5  irdev  mouse0
event1  event3  event6  mice   mouse1

Try using irrecord with /dev/input/irdev.

Also, make sure that you did not temper with any of the ir-keymap.c nor ir-common.c trying to get the IR-Common to stop working...

Then, it should work ok.
Tell me what are your next results.
see ya
Matheus

---

### Post by Mfvane on 2007-10-24
Hi merwizard, I am not sure what part you didnt understand... 

Do you have the dev/input driver installed? 
What is the output of your irrecord?
Does your remote works without lirc? volume,etc?

I need a little more detailed questions to help you. I just simply followed those guides, checked to see what was my card recognized as in and untempered with my ir-keymaps.c so that my ir-common would be original. 
See ya
Matheus

> **merwizard said:**
> Matheus, please, give us more detailed instructions on how to achieve that, since, I too have a Winfast board, and the remote stopped working for me. Using dev/input doesn't work for me, either.

---

### Post by bastille on 2007-10-25
Hi Matheus

thx for the quick answer :-)
When I use ```
sudo cat /proc/bus/input/devices
``` I get the output ```
I: Bus=0001 Vendor=107d Product=6609 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:02:03.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc

```

Output of ```
ls /dev/input
```
is ```
by-id    event0  event2  event4  event6  mice    mouse1
by-path  event1  event3  event5  event7  mouse0

```
So I guess ```
sudo irrecord -H dev/input -d /dev/input/event4 lircd.conf
``` is the right code to use, if I'm wrong please tell me, I'm relatively new to ubuntu.
Basti

---

### Post by Mfvane on 2007-10-25
Hi Bastille, 

I'm also relatively new to ubuntu, and even newer to lirc hehehe! Lirc has always been problematic for me.

From your output, I have one more question that I forgot to ask you yesterday. 
Can you operate your remote without lirc? 
what does it say when you type
```
 lircd -n
```
can you give me the output of your irw?

and your /etc/lirc/hardware.conf, which should be similar to this:

```
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="/dev/input/event4"
MODULES="lirc_dev"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF="" 
```

Did you install by apt-get or did you compile from source your lirc instalation?
and what about your dmesg output:

```
 dmesg | grep lirc 
```

There is one more thing that can help running the irrecord using ```
/dev/input/by-path/pci-0000:02:03.0--event-ir
```

Thanks
Matheus


> **bastille said:**
> Hi Matheus

thx for the quick answer :-)
When I use ```
sudo cat /proc/bus/input/devices
``` I get the output ```
I: Bus=0001 Vendor=107d Product=6609 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:02:03.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc

```

Output of ```
ls /dev/input
```
is ```
by-id    event0  event2  event4  event6  mice    mouse1
by-path  event1  event3  event5  event7  mouse0

```
So I guess ```
sudo irrecord -H dev/input -d /dev/input/event4 lircd.conf
``` is the right code to use, if I'm wrong please tell me, I'm relatively new to ubuntu.
Basti

---

### Post by bastille on 2007-10-26
Hi again,

```
sudo  lircd -n
lircd-0.8.2[5900]: lircd(userspace) ready
lircd-0.8.2[5900]: caught signal

```
irw doesn't give me any output, that's the reason why I'm trying to get this work with the irrecord-thing...
My /etc/lirc/hardware.conf:
```
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="dev/input/event4"
MODULES=""
LIRCD_CONF="leadtek/lircd.conf.RM-0010"
LIRCMD_CONF=""

```
So I need to set up a lircd.conf first? Because I tried to install ist exactly that way: [https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)
Until I get to the command irw, where it doesn't  give me any output, because of the gpio-problem.
```
dmesg | grep lirc
```
doesn't give me any output.
```
$ /dev/input/by-path/pci-0000:02:03.0--event-ir
bash: /dev/input/by-path/pci-0000:02:03.0--event-ir: Permission denied
$ sudo /dev/input/by-path/pci-0000:02:03.0--event-ir
sudo: /dev/input/by-path/pci-0000:02:03.0--event-ir: command not found

```
I think lirc downloads the preconfigured lircd.conf-file automaticaly. But I'll change the /etc/lirc/hardware.conf to your suggestion and tell you if it works.
See ya, Basti

PS: I can't use my remote control without lirc at all :-(

---

### Post by bastille on 2007-10-26
Ok, now I changed my hardware. conf several times, trying different things:
first I used only lirc_dev as MODULE, then I tried lirc_dev together with lirc_gpio and then only lirc_gpio. Nothing worked. The lircd.conf-file already exists. So currently my hardware.conf looks like that:
```
REMOTE="Winfast TV2000/XP (card=34)"
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="dev/input/event4"
MODULES="lirc_gpio"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
```

---

### Post by bastille on 2007-10-26
oO sry, I guess I misunderstood you; my hardware.conf looks like that:
```
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="/dev/input/by-path/pci-0000:02:03.0--event-ir"
MODULES="lirc_dev"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
```

And I used ```
sudo irrecord -H dev/input -d /dev/input/by-path/pci-0000:02:03.0--event-ir lircd.conf

```
but it still gives me the output ```
Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event4'
```
I also thought about trying to fix the bug with the [lirc-ubuntu1-ubuntu2.debdiff]("http://launchpadlibrarian.net/8452664/lirc-ubuntu1-ubuntu2.debdiff") but I didn't find anything about how to use debiff-files.
Basti

---

### Post by mazirian on 2007-10-26
@davem2312:  Have you resolved this? I have the same card and I'd be interested in how you were able to get it to work.

---

### Post by davem2312 on 2007-10-29
No, I haven't resolved this.  I have tried many things, but I am still waiting on some more advice.

---

### Post by Mfvane on 2007-10-30
Hi again!! Sorry for the delay in answering you. I was busy out of town.
Ok, let's see your outputs:
one thing that is not right is the lircd -n...
it should say something like:
```
 lircd-0.8.2[5900]: lircd(dev/input) ready 
```

That is the only thing that is different from my card. My card is the card number 72, but it worked somethings whenever I killed lircd... it worked volume from the regular kernel... it did not work when lirc was running...
so i just gave a 

```
 sudo killall lircd 
```

and then tried to run the irrecord whenever the volume was working. Then it stoped loading the preconf lircd.conf.

Try using 
```
 sudo irrecord -H dev/input -d /dev/input/by-path/pci-0000:02:03.0--event-ir /tmp/irrecord.0 
```
because of permission problems

Also, make sure that the hardware.conf is the last one that you showed me, where it loads the lirc_dev module.

see if that works, if that doesnt work, we will figure out a way of getting it to work hehe!
see ya
matheus


> **bastille said:**
> Hi again,

```
sudo  lircd -n
lircd-0.8.2[5900]: lircd(userspace) ready
lircd-0.8.2[5900]: caught signal

```
irw doesn't give me any output, that's the reason why I'm trying to get this work with the irrecord-thing...
My /etc/lirc/hardware.conf:
```
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="dev/input/event4"
MODULES=""
LIRCD_CONF="leadtek/lircd.conf.RM-0010"
LIRCMD_CONF=""

```
So I need to set up a lircd.conf first? Because I tried to install ist exactly that way: [https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)
Until I get to the command irw, where it doesn't  give me any output, because of the gpio-problem.
```
dmesg | grep lirc
```
doesn't give me any output.
```
$ /dev/input/by-path/pci-0000:02:03.0--event-ir
bash: /dev/input/by-path/pci-0000:02:03.0--event-ir: Permission denied
$ sudo /dev/input/by-path/pci-0000:02:03.0--event-ir
sudo: /dev/input/by-path/pci-0000:02:03.0--event-ir: command not found

```
I think lirc downloads the preconfigured lircd.conf-file automaticaly. But I'll change the /etc/lirc/hardware.conf to your suggestion and tell you if it works.
See ya, Basti

PS: I can't use my remote control without lirc at all :-(

---

### Post by Mfvane on 2007-10-31
I've googled around today, and found a patch that is needed in order to make this card work in kernels greater than 2.6.17. I am not sure if you need all that... anyways, here is the source to patch and tutorial: [http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000)

Also you can see if your remote works by using, with lirc killed:

```
 sudo evtest /dev/input/eventX 
```

where X is your event number. It should give something similar to this

```
Input driver version is 1.0.0
Input device ID: bus 0x1 vendor 0x1554 product 0x4011 version 0x1
Input device name: "bttv IR (card=72)"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 20 (Repeat)
  Event type 1 (Key)
    Event code 2 (1)
    Event code 3 (2)
    Event code 4 (3)
    Event code 5 (4)
    Event code 6 (5)
    Event code 7 (6)
    Event code 8 (7)
    Event code 9 (8)
    Event code 10 (9)
    Event code 11 (0)
    Event code 74 (KPMinus)
    Event code 78 (KPPlus)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 128 (Stop)
    Event code 141 (Setup)
    Event code 164 (PlayPause)
    Event code 167 (Record)
    Event code 173 (Refresh)
    Event code 207 (?)
    Event code 217 (?)
    Event code 226 (?)
    Event code 354 (Goto)
    Event code 372 (Zoom)
    Event code 386 (Tuner)
    Event code 388 (Text)
    Event code 395 (List)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 405 (Last)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)

Event: time 1159635067.701163, type 1 (Key), code 402 (ChannelUp), value 1
Event: time 1159635067.701165, type 0 (Reset), code 0 (Reset), value 0
Event: time 1159635067.705146, type 1 (Key), code 402 (ChannelUp), value 0
Event: time 1159635067.705148, type 0 (Reset), code 0 (Reset), value 0
Event: time 1159635077.129202, type 1 (Key), code 372 (Zoom), value 1
Event: time 1159635077.129204, type 0 (Reset), code 0 (Reset), value 0
Event: time 1159635077.133201, type 1 (Key), code 372 (Zoom), value 0
Event: time 1159635077.133203, type 0 (Reset), code 0 (Reset), value 0

```

Also, I found a lircd.conf preconfigured, which is attached, to use with Leadtek WinFast 2000XP, but I think that the one generated by irrecord is better... 

Tell me if that works...
see ya
Matheus

---

### Post by bastille on 2007-11-01
No worries, I'm very happy with anyone helping me at all :-)
The /etc/lirc/hardware.conf looks exacty like the last one I pasted above.
I killed lircd before trying if the remote works without lirc, but there is nothing happening after pressing the vol up/down button or any other button.
Usind the code ```
sudo irrecord -H dev/input -d /dev/input/by-path/pci-0000:02:03.0--event-ir /tmp/irrecord.0
``` the output still is  ```
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/by-path/pci-0000:02:03.0--event-ir'
```
Output of ```
sudo evtest /dev/input/event4
``` is ```
Input driver version is 1.0.0
Input device ID: bus 0x1 vendor 0x107d product 0x6609 version 0x1
Input device name: "bttv IR (card=34)"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 20 (Repeat)
  Event type 1 (Key)
    Event code 2 (1)
    Event code 3 (2)
    Event code 4 (3)
    Event code 5 (4)
    Event code 6 (5)
    Event code 7 (6)
    Event code 8 (7)
    Event code 9 (8)
    Event code 10 (9)
    Event code 11 (0)
    Event code 28 (Enter)
    Event code 52 (Dot)
    Event code 74 (KPMinus)
    Event code 78 (KPPlus)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 128 (Stop)
    Event code 139 (Menu)
    Event code 142 (Sleep)
    Event code 164 (PlayPause)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 208 (?)
    Event code 223 (?)
    Event code 226 (?)
    Event code 234 (?)
    Event code 355 (Clear)
    Event code 358 (Info)
    Event code 361 (Archive)
    Event code 363 (Channel)
    Event code 368 (Language)
    Event code 370 (Subtitle)
    Event code 372 (Zoom)
    Event code 377 (TV)
    Event code 385 (Radio)
    Event code 386 (Tuner)
    Event code 388 (Text)
    Event code 389 (DVD)
    Event code 392 (Audio)
    Event code 393 (Video)
    Event code 398 (Red)
    Event code 399 (Green)
    Event code 400 (Yellow)
    Event code 401 (Blue)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 405 (Last)
    Event code 407 (Play)
    Event code 412 (Previous)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)
```

Also i tried to use this [patch]("http://marc.info/?l=linux-video&m=116099140716390&w=2"), but this patch modifies the file bttv-input.c which seems not to be existing.

See ya
Basti

---

### Post by mazirian on 2007-11-01
I've struggled with lirc and this card for years now, first under gentoo and then under debian/ubuntu.  It's always taken cajoling and coaxing and been a hassle.  I used to enjoy tweaking things until I could get it to work, and I always did get it to work eventually.  I'm sure I could again.  But, now I'm starting to think I just want to solve this problem with a wireless keyboard or a new tv card. :)

---

### Post by Mfvane on 2007-11-01
Basti, during the evtest, did you try to press some keys on the remote?
Because everything seems right... I just dont understand why it is not working...
I still think that the problem is with the ir-common... My card had the same problem as yours... But I had messed up the ir-common module trying to disable it, since last ubuntu version needed this so whenever a button was pressed, it would not send a  command for lirc and a command for ir-common. So I messed up the ir-common so it would not load. After getting it unmessed up, and killing lirc, ir-common started to work again... showing some basic remote control functions(vol+ and vol-). So I reconfigured lirc the way that I told you, and it started to work fine under lirc.

But we will try to find something to make it work... Ive heard that the module ir-kbd-gpio might help, but I tested on mine when it didnt work and did not change a thing... and also, for these newer kernels, it is not needed. 
If it is something with the ir-common, it should state something in the dmesg output:

```
dmesg | grep bttv
```
```
dmesg | grep lirc
```

I will think more about it, and try to find what is different... 

see ya
matheus

---

### Post by Mfvane on 2007-11-01
Mazirian, 
We are trying to get bastille card working, if we can get it to work, we will make a how to and post it here. But dont buy a new tv card! hehe! It will be fixed for sure under newer lirc's or kernel! hehe!
If you want to help us, you are more than welcome!
we reconfigured the hardware.conf for lirc, as described in a previous message, so it would not load the lirc_gpio and load lirc_dev. Also, we are trying to use the driver dev/input as a workaround for gpio module.
But no luck so far... the system doesnt recognize his control, it's some configurantion... not lirc that is causing the problem. I think that might be the regular built-in kernel support for IR remotes.
Do you suggest something?
Thank you
Matheus

---

### Post by bastille on 2007-11-02
I tried to press a lot of buttons to test if there is a reaction, but indeed there isn't. So I interrupted with Crtl + C.
```
 dmesg | grep bttv
[   34.997768] bttv: driver version 0.9.17 loaded
[   34.997773] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   34.997854] bttv: Bt8xx card found (0).
[   34.997889] bttv0: Bt878 (rev 17) at 0000:02:03.0, irq: 17, latency: 32, mmio: 0xf2100000
[   34.997903] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   34.997906] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   34.997934] bttv0: gpio: en=00000000, out=00000000 in=003ff506 [init]
[   34.998314] bttv0: using tuner=5
[   34.998319] bttv0: i2c: checking for MSP34xx @ 0x80... <3>intel_rng: FWH not detected
[   35.484638] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   35.789708] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   35.842479] bttv0: i2c: checking for TDA9887 @ 0x86... <6>input: PC Speaker as /class/input/input3
[   36.533273] bttv0: registered device video0
[   36.533335] bttv0: registered device vbi0
[   36.533381] bttv0: registered device radio0
[   36.533404] bttv0: PLL: 28636363 => 35468950 .. ok
[   36.566010] input: bttv IR (card=34) as /class/input/input4

```
```
 dmesg | grep lirc
[   90.325713] lirc_dev: IR Remote Control driver registered, at major 61
```
To be honest, I had the mind to buy another TV-card as well, but then I thought about what might happen until the next kernel-release, and eventually then I would possess 2 cards which don't work:lol: Anyway, how do I replace the ir_common with the original one? I can't remember trying to disable it, but it can't be wrong to test if that works.
By the way linuxtv.org writes >  Setting up the remote

The notes below are for kernels <= 2.6.14. On recent kernels up to at least 2.6.17 the module ir_kbd_gpio is not needed anymore. However, you will need to apply this patch. Otherwise this card will not work unfortunately.


But I don't think that this can be the problem, because my tv-card worked with lirc on feisty without any patch.
See ya,
Basti

---

### Post by Mfvane on 2007-11-03
Everything seems working perfect... This is really odd though...But this time is a kernel thing, not a lirc problem...Lirc seems to be working. 
the ir_common I messed up like someone who I cant find the link anymore, told...
I oppened the ir-keymaps.c with an editor
took out the key codes and replaced it with a null command
rebuilded the modules for the kernel
copyied the now ir-common.ko to the location of the kernel in use.
To rebuild it, I redownloaded kernel sources and rebuilded the modules and substituted the messed up one for the original one. Then, after killing lirc, my remote started to work some basic commands... 
But I dont think that this is your problem, because in my case whenever I did dmesg it showed something like:
bttv IR key pressed unknown key
Maybe you can try to find if your card is listed in the ir-keymaps.c
I would check it for you, but I'm not in my machine with lirc. I am in a different machine, running slackware whose kernel is not updated.
Hope we can at least find where the trouble is... I will try to find someone with a card like yours to borrow to see if I can get IR to work. It is easier sitting in front of the PC than in a forum hehehe!
Let's see what marizian has to say too.
See Ya

---

### Post by mazirian on 2007-11-03
I've tinkered some more too, and had no luck.  After the gutsy upgrade I acquired a bunch of small but annoying and difficult to fix issues that might warrant a fresh install if I can't find the cruft that's causing them.  So, I'm holding off on investing any more time on lirc until I resolve them.  I'll keep an eye on this thread and keep my fingers croossed that you guys sort it out for me :)

Still, thinking about that wireless keyboard though! If only I could find one as small as my happy hacker)

---

### Post by mazirian on 2007-11-03
Ironically, while I was swapping drives in my box for a fresh install, I broke the tv card! Muahahahah.  I am sad to replace it, but glad that I can get maybe something else that will work. Ah the end of an era.

---

### Post by Mfvane on 2007-11-03
Oh man! That is not a good thing! hehehehe! There is no way of getting it back to work??
Well, since you are buying a new one, which one do you think is a good one?
Dont buy the pixelview mpeg2 (card=72). It works ok under linux... Remote works, but I faced the same problems as the winfast... But I found out later that it was the ir-common module that was broke... This card is not good for TV, everytime you change a channel, you have to switch it to stereo and then to mono if you want sound comming out of it. I dont recommend this card...

Basti, I found this site, where it has some a newer version of lirc. 
```
 http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lirc 
```
```
 Changelog

lirc (0.8.3~pre1-0ubuntu1) hardy; urgency=low

  * New upstream version.
    - Includes Iguanaworks IR Support (LP: #153457)
  * Update 03_extrafiles patch for gpio changes.
  * Update 05_fix_cmdir patch for command IR lirc.hwdb update.
  * Update 12_lirc_pvr150 patch for transmitting support under
    kernel 2.6.22.
  * Update 13-warning-cleanup patch for items that were already
    cleaned up upstream.
  * Drop 14_mceusb2 patch since now included upstream.
  * Drop 14_lirc-i2c patch since now included upstream.
  * Drop 15_macmini patch since now included upstream.
  * **Update 16_lirc-gpio patch for added changes upstream.**
  * Update 17_devinput patch for added changes upstream.
  * Drop 18_irman-fix patch since now included upstream.
  * Drop 19_serial_support patch since now included upstream.
  * Update 20_serial_igor patch for new serial support upstream.
  * Update 22_hauppauge_novat_500 patch for new support upstream.
  * Add 23_pad2keys patch for pad2keys imon support (LP: #153184).
  * Add 24_freecom_dvbt patch for NovaT 500 Remote (LP: #152539).
  * Clean up lintian warning for -$(MAKE).
  * Clean up lintian warning for ${source:Version}. 
```

What do you think? Might worth a try? 

see ya 
Matheus

---

### Post by bastille on 2007-11-04
wooohooo \\:D/
That IS definitely worth a try, mate! hrhr
To be continued...

---

### Post by bastille on 2007-11-04
Okay, now I tried everything I also tried with the 0.8.2-version, and the symptoms are exactly the same. I guess the only possible thing to do is to wait for an official new release of lirc, hopefully they'll have fixed the bug until then. I'll give it up. 
Thank you very much for your help, Matheus, I really appreciate that, but I'm tired of wasting so much time on this sh.., I'm sorry. I've got a lot of other things to do for university so I prefer switching to Windows XP (yep I still got dual boot for cases like this :-D) each time i want to watch TV than wasting hours and hours on lirc.

See ya,
Basti

---

### Post by mazirian on 2007-11-04
Well, I can't fix my card.  I've never actually broken a pci card before.  But I've re-evaluated what I need the tv card for and decided I mostly used the remote and I can get by without a tv card for a while.  I think I'm going to pick up a Stream Zap remote.  It's popular with the myth users and supported by lirc.

---

### Post by mazirian on 2007-11-06
Not to gloat but my Stream Zap arrived today and it was entirely painless to set up!  All i needed to do was adjust my .lircrc a bit and it was done.  :)  Totally recommended.

---

### Post by michwill on 2007-11-08
. . .but, but, but. . .I'm still stuuuuuuuuck  :'(  (yes I'd like cheese with that).


Hi All,

I've got the exact some problem.  So, for the remainder of us that weren't fortunate enough to break their card in order to justify a new one, please continue this thread.  I'm in dire need of assistance.

Regards.

---

### Post by mazirian on 2007-11-08
> **michwill said:**
> ... for the remainder of us that weren't fortunate enough to break their card in order to justify a new one, please continue this thread...

You'll be getting your hammer out soon...  (It really was an honest accident!)

---

### Post by bastille on 2007-11-08
Hey I accidently broke my card, too! And it felt great!
Just kidding 
If you find a solution to the problem please tell in this thread. I just don't have enough time at the moment to deal with this problem....

---

### Post by michwill on 2007-11-08
> **mazirian said:**
> You'll be getting your hammer out soon...  (It really was an honest accident!)

You *may* just be right.  :confused:  This really perplexes me.  Has anyone heard why they removed direct gpio support?  What was *supposed* to have been the benefit?

Regards.

---

### Post by michwill on 2007-11-09
Alright guys, I'm really about to break the hammer out.  This is frustrating.  "irw" works in 6.10, but doesn't work with 7.10 (I didn't try 7.04).  Why in the world would "irw" just *not* work?  The system recognizes my card, it just doesn't respond.

I have a USB IR receiver.  How would I go about getting that set up?  I'm going to Google for now, but if you guys have any pointers, lemme know.  Thx.

Regards.

---

### Post by bastille on 2007-11-10
@ michwill:
One possibility would be to find out which module your card needs. If that is the gpio-module you could do a kernel-downgrade. I thout about this but in the end i think it's too risky.
But you could try it; with Feisty my remote control works.
[http://ubuntuforums.org/showthread.php?p=3723818]("http://ubuntuforums.org/showthread.php?p=3723818")

---

### Post by michwill on 2007-11-16
Yeah, I know it worked with Feisty.  But I really like Gutsy.  It seems slightly snappier.  Not to mention I'm using Mythbuntu 7.10, and I fear what a kernel downgrade might do to it.  ;)  I've got a couple of e-mails out (including one to LIRC's maintainer), so I'll give it a few days and see what comes of it.

Thanks.

---

### Post by bastille on 2007-11-17
Okay,
now I installed the 2.6.20.16-Kernel and reinstalled lirc, but the problem is still the same. => We'll probably have to wait for a new lirc-version... That really sucks

---

### Post by Flandry on 2007-11-17
I'm back to WinXP while i wait for someone to report this is fixed.  That's easier to justify because after fiddling around with some of the suggestions here, i booted into Kubuntu today and the mouse stops working as soon as i log in.  I guess i'll just do a clean install when i want to try again.

I had planned on going completely linux on the new system i'm putting together, but this has been rather discouraging.  On WinXP i install a couple files completely painlessly and get TV, radio, remote, timeshifting, etc.  As much as i always stand up for linux, in 2007 this is just ridiculous.

Good luck, everyone!

---

### Post by mihaicj on 2007-11-30
Hey guys. I solved it for me with the help of a friend. I am posting my hardware.conf. Try making yours the same and tell me if it works.

REMOTE="Winfast TV2000/XP (card=34)"
LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER=""
DEVICE="/dev/lirc0"
MODULES="lirc_serial"
LIRCD_CONF="leadtek/lircd.conf.RM-0010"
LIRCMD_CONF=""

P.S. Don't forget to set your serial ports not to be used by the kernel:

dmesg | grep ttyS tells me that ttyS0 is use by the RM, so:

setserial /dev/ttyS0 uart none

All the best.

---

### Post by bastille on 2007-12-03
Hm doesn't work for me. Are you sure you used the serial-module?

---

### Post by spalVl on 2007-12-10
I too am having the same problems with this remote as bastille and michwill describe.  I'd be willing to test anything to get this remote working or brain storm ideas

I am now using Mythbuntu 7.10.  This card previously worked fine in Knoppmyth R5F1, but stopped woriking in Knoppmyth R5F27 (debain based distro) which is one of the reasons I switched to Mythbuntu.  Knoppmyth R5F27 introduced the change so this remote uses dev/input and depreciated lirc_gpio usage.

This post details my troubleshooting on Knoppmyth (mostly same steps as here) 

[http://www.knoppmyth.net/phpBB2/viewtopic.php?t=16928&highlight=leadtek](http://www.knoppmyth.net/phpBB2/viewtopic.php?t=16928&highlight=leadtek)

and this one details others troubleshooting on Mythbuntu 

[http://ubuntuforums.org/showthread.php?t=610426](http://ubuntuforums.org/showthread.php?t=610426)

It really looks like it is something with the bttv kernel module.  Here is a post at Fedora fourms about same issue. (Dr. Death post)

[http://forums.fedoraforum.org/showthread.php?t=162240&page=1&pp=15](http://forums.fedoraforum.org/showthread.php?t=162240&page=1&pp=15)

I also tried the changing to serial setup like mihaicj suggested but didn't work for me.

I have Leadtek Winfast TV2000XP Deluxe tuner (NTSC)

The best bet to me looks like applying bttv-input.c  (values may differ) and recompiling the bttv module, but not sure how to do this on Ubuntu.


Thanks in advance for any ideas.

---

### Post by silverdulcet on 2008-01-01
I also have the same card and am unable to get the ir reciever working on it. I attempted to use the patch you mentioned. The patch doesn't work. The output I get is:
```
Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|--- bttv-input.c.orig  2006-10-15 18:57:11.000000000 +0300
|+++ bttv-input.c       2006-10-15 18:28:08.000000000 +0300
--------------------------
Patching file bttv-input.c using Plan A...
Hunk #1 FAILED at 65.
Hunk #2 succeeded at 244 (offset -71 lines).
1 out of 2 hunks FAILED -- saving rejects to file bttv-input.c.rej
done

```

There is also a post regarding this card on Fedora where the user states he succeeds using a very similar patch file. link to post: [http://lists.atrpms.net/pipermail/atrpms-users/2007-November/008201.html]("http://lists.atrpms.net/pipermail/atrpms-users/2007-November/008201.html")
With that patch file I get the following output when I attempt to patch bttv-input.c
```
Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|--- bttv-input.c.orig 2007-07-08 19:32:17.000000000 -0400
|+++ bttv-input.c 2007-11-07 01:15:33.000000000 -0500
--------------------------
Patching file bttv-input.c using Plan A...
patch: **** malformed patch at line 4: (ir->mask_keyup && (0 == (gpio & ir->mask_keyup)))) {

```

I have applied 1 patch before so I worked out how to try this one from that. The steps are as follows:
```
sudo aptitude install linux-source-2.6.22
```

Then extract all of the files in the archive /usr/src/linux-source-2.6.22.tar.bz2 from the following directory:
/linux-source-2.6.22/drivers/media/video/bt8xx/

Finally use the command:
```
patch bttv-input.c --verbose --dry-run -i /usr/src/linux/bttv-input.patch
```

This needs to be changed to suit your file names and where you have the files. The basic gist o the command is patch targetofpatch --verbose --dry-run -i patchfilename
Verbose just means it will give you all available feedback on the command and --dry-run just tests the patch to make sure its valid without modifying anything. If it reports successful you can run it without that option. Unfortunately both patch files I tried were not. 

Anyone else have any ideas? Perhaps I made some error in my patching command? Any help would be greatly appreciated.

---

### Post by spalVl on 2008-01-02
@Sliverdulcet.

I basically patched the bttv-input.c file by hand.  Got same errors as you did before manually patching.

2 lines to edit add are...

Around like 65 add below line,  (Compare the patch to unmodified bttv-input.c file to figure out exactly where to insert)

> if (btv->c.type == BTTV_BOARD_WINFAST2000) ir_input_keydown(ir->dev,&ir->ir,data,data);

And the keycode line around line 315.  From what I read this can be one of 2 values depending on card variant.  

> ir->mask_keycode = 0x8f8;

or

> ir->mask_keycode = 0x0f8;

Theory is >  ir->mask_keycode = 0x1f8;  is NOT the correct value for this card.

I tried 0x8f8 value and still have not got it working.  But this is not my system and basically I work on it when the system's owner is around to test the remote.  I tried using a lircd.conf file from the Fedora thread, but my next step is to use IRRECORD to create a clean lircd.conf.  If that doesn't work I'll try the 0x0f8 value and recompile kernel again.  

I used these guides to recompile the kernel.

[http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/](http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/)
[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile)

Another gotcha, after using a custom kernel the "restricted" drivers do not work.  For me that meant installing Nvidia drivers from Nvidia's page.

I'll post as I progress.

---

### Post by silverdulcet on 2008-01-04
So it seems its not as simple as just recompiling a module/driver. The way to fix it is compiling recompiling the entire kernel? I've patched some wireless driver modules and recompiled those, but never compilied a custom kernel. 

Anyway, thanks for the reply. I would be very interested to find out if you succeed in getting the ir receiver to work. Otherwise I might just spend the 18 bucks and nab a serial IR receiver from [http://irblaster.info/receiver.html]("http://irblaster.info/receiver.html")

---

### Post by spalVl on 2008-01-12
:guitar: **FINALLY  RESOLVED **

That was a bitch,

I did so many things I can't be sure exactly what solved but this is what I did.

Downloaded the Kernel source and patched bttv-input.c (detailed in post #47), 

> sudo aptitude install linux-source-2.6.22

> ir->mask_keycode = 0x8f8; is value I used

Followed these 2 guides to recompile the Kernel

[http://symbolik.wordpress.com/2007/1...-gutsy-gibbon/](http://symbolik.wordpress.com/2007/1...-gutsy-gibbon/)
[http://www.beginlinux.com/index.php/...e_m/ub_compile](http://www.beginlinux.com/index.php/...e_m/ub_compile)

The lircd.conf file I found from above Fedora forum didn't work.  Because this not my system I didn't get to troubleshoot for few weeks.

<In the meantime>
I  unloaded bt878 module 
> rmod bt878
and overwrote  my new kernel bt878.ko 
> /lib/modules/2.6.22.9-with-bttv/kernel/drivers/media/dvb/bt8xx/bt878.ko
with this newly compiled module
> /usr/src/linux-source-2.6.22/debian/linux-image-2.6.22.9-with-bttv/lib/modules/2.6.22.9-with-bttv/kernel/drivers/media/dvb/bt8xx/bt878.ko

Reloaded new module
> insmod bt878
<I don't know what effect this had, I didn't get to troubleshoot unitl a few more weeks later...>

Obtained IR reciever still using /dev/input/event3,  by command 
> cat /proc/bus/input/devices

So still not getting any feedback from irw,  I tried to record a new lircd.conf file.

**STOP LIRC 1ST **
> sudo /etc/init.d/lirc stop

And record remote
> sudo irrecord -H dev/input -d /dev/input/event3 ~/lircd.conf
And it picks up the remote keypresses, and recorded my remote.

My **/etc/lirc/hardware.conf ** looks like this.


[COLOR="Blue"]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event3"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""[/COLOR]

My** /etc/lirc/lircd.conf ** looks like this.

[COLOR="Blue"]
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(dev/input) on Sat Jan 12 17:04:54 2008
#
# contributed by: Mike Treichler
#
# brand: LeadTek
# model no. of remote control: Y0400046 (bundled with Winfast 2000XP Deluxe)
# devices being controlled by this remote: LeadTek Winfast 2000XP Deluxe

# brand: Leadtek
# model: Y0400052 (bundeled with Winfast PVR2000 TV-card)
#
# Note: Only CH_UP, CH_DOWN, VOL_UP and VOL_DOWN will repeat. This
# seems to be a limitation of the remote control.

begin remote

name Leadtek-RM0010
bits 16
eps 30
aeps 100

one 0 0
zero 0 0
pre_data_bits 16
pre_data 0x8001
gap 423871
toggle_bit_mask 0x0

begin codes
POWER 0x0074
MTS 0x0188
TV/FM 0x0182
VIDEO 0x0189
DISPLAY 0x0166
CH_UP 0x0192
CH_DOWN 0x0193
VOL_DOWN 0x0072
VOL_UP 0x0073
FULLSCREEN 0x0174
TELETEXT 0x0184
SLEEP 0x008E
BOSSKEY 0x0163
MUTE 0x0071
RED 0x018E
GREEN 0x018F
YELLOW 0x0190
BLUE 0x0191
1 0x0002
2 0x0003

3 0x0004
4 0x0005
5 0x0006
6 0x0007
7 0x0008
8 0x0009
9 0x000A
0 0x000B
. 0x0034
FINETUNE+ 0x004E
FINETUNE- 0x004A
PIP 0x00E2
ENTER 0x001C
RECALL 0x0195
BACK 0x019C
PLAY 0x00A4
NEXT 0x0197
TIMESHIFTING 0x0169
STOP 0x0080
REC 0x00A7
SNAPSHOT 0x00EA
end codes

end remote
[/COLOR]

The difference in my lircd.conf between the one I used from Fedora forum mentioned in post #47 is the "toggle_bit_mask" field.
 
 
So now everything works fine.  Unfortunately this is not my machine or else I would blow it away and configure it from scratch to figure out exactly what fixed.

So given not knowing exactly what fixed and not being able to retry  is there a way to submit a bug to Ubuntu devs to get fixed in future releases?  
 
> **silverdulcet said:**
> So it seems its not as simple as just recompiling a module/driver. The way 
to fix it is compiling recompiling the entire kernel? I've patched some wireless driver modules and recompiled those, but never compilied a custom kernel.

Maybe?  I didn't know about that option and assumed full Kernel compile was only route.

---

### Post by 1337 on 2008-05-01
Is there any way to get this remote working in current version of Ubuntu (Hardy Heron) without kernel compilation?

Regards

---

### Post by thecrane on 2008-07-23
Bump.  Same question.  :)

---

### Post by mazirian on 2008-07-23
As much fun as it is to hack on lirc issues, there are more productive ways to tinker with systems. I honestly can't recommend the streamzap enough.  dpkg sets it up for you and you won't go through a bunch of baloney each time you upgrade your kernel.  It costs a little over $30.00 from amazon and that amount is certainly less than the value of the time you'll spend making the Winfast work.  I know, because before I broke mine, I spent hours and hours over three years constantly frigging with kernel sources and the lirc-modules-sources packages and everything else. The Winfast will still do what it is primarily intended to so: capture video.

---

