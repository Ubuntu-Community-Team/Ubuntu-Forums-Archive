---
title: "Soungraph iMON VFD not working with LIRC 0.8.2"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by reclusivemonkey on 2007-10-18
Hello,

I had the Soundgraph iMON VFD working perfectly in Feisty. I moved it from my Desktop machine to my MythTV box and installed Gutsy; it no longer seems to work. The modules seem to load fine;

```

Oct 18 19:36:25 mythtv kernel: [   23.772000] lirc_dev: IR Remote Control driver
 registered, at major 61 
Oct 18 19:36:25 mythtv kernel: [   23.928000] /build/buildd/linux-ubuntu-modules
-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driv
er for Soundgraph iMON MultiMedian IR/VFD, v0.3
Oct 18 19:36:25 mythtv kernel: [   23.928000] /build/buildd/linux-ubuntu-modules
-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venk
y Raju <dev@venky.ws>
Oct 18 19:36:25 mythtv kernel: [   23.932000] /build/buildd/linux-ubuntu-modules
-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon
_probe: found IMON device
Oct 18 19:36:25 mythtv kernel: [   23.932000] lirc_dev: lirc_register_plugin: sa
mple_rate: 0
Oct 18 19:36:25 mythtv kernel: [   23.932000] /build/buildd/linux-ubuntu-modules
-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon
_probe: Registered iMON plugin (minor:0)
Oct 18 19:36:25 mythtv kernel: [   23.932000] /build/buildd/linux-ubuntu-modules
-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon
_probe: iMON device on usb<1:3> initialized
Oct 18 19:36:25 mythtv kernel: [   23.932000] usbcore: registered new interface 
driver lirc_imon

```

also, lsusb seems to report everything is OK;

```

monkey@mythtv:~$ lsusb | grep -i imon
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

```

However, when I try to get something from the remote, nothing appears. I've tried both irw with lircd running, and mode2 -d /dev/lirc0 but still nothing. The LED on the remote lights up and I've checked the battery. The correct lircd.conf  is present in /etc/lirc and the correct devices are being made;

```

monkey@mythtv:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2007-10-18 19:35 /dev/lirc0
srw-rw-rw- 1 root root     0 2007-10-18 19:35 /dev/lircd

```

Does anyone have any ideas?

---

### Post by Tom55 on 2007-12-18
Well I hope someone can help you because I have exactly the same problem.  I erased Fiesty and MythTv to upgrade to Gutsy (7.10) with the intention of using lirc.  along the way I discovered Mythbuntu and the ability to install the infra-red from within the Mythbuntu control centre.

I'm getting exactly the same information as you
dmesg
<snip>
[   30.844033] lirc_dev: IR Remote Control driver registered, at major 61 
[   30.845182] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   30.845186] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   30.845211] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   30.845216] lirc_dev: lirc_register_plugin: sample_rate: 0
[   30.845240] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   30.845285] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<1:3> initialized
[   30.845294] usbcore: registered new interface driver lirc_imon

<snip>
[ 6909.564000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[ 6930.592000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[ 7185.384000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[ 7228.200000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed

lsusb recognises the imon PAD

My Ubuntu/linux knowledge is almost zero... I'm a "monkey see.. monkey do" user 

Regards

Tom
[email]jonestejm@gmail.com[/email]

---

### Post by Tom55 on 2007-12-18
Humm... I just tried this and received a response from the remote

sudo mode2 -d /dev/lirc0

Then I pressed the keys on the remote and receved some code on the screen.

According to my idiots guide I need to configure the lirc daemon by copying the imon data into the lircd.conf file.  Well this has alread been done by the Mythbuntu control centre remote setup routine.

Supposed to start lircd manually

$ sudo lircd -d /dev/lirc0

Response is that lircd is already running with pid 3953.  Don't know what this means?

Check id it's running with
$ ps -e|grep lirc

response is 
3953 ?   00:00:00  lircd

Which appears to be missing a line (4841 ?  00:00:00 lirc_dev)

The manual tells me that I don't have lirc running.

Now I'm lost !!!!

Tom

---

### Post by Fopper on 2008-01-10
I have got kind of the same problem, I also get reaction on the mode2 command (see below), but when I change my remote to imon-pad in mythbuntu irw doesn't give any reaction on anything I do, also not the volume knob (which has the same codes as in the configuration file (the rest of the codes have different mode2 codes then what is in the config file))
```
sudo mode2 -d /dev/lirc_imon
code: 0x800f8408
code: 0x800f8408
code: 0x800f0412
code: 0x800f0412
code: 0x800f8413
code: 0x800f8413
code: 0x01000000
code: 0x00010000
```

BTW When I get the mode2 output of my mce device it gives a totaly different output, something like:
```
pulse 500
space 400
pulse 450
space 450
pulse 900
space 850
pulse 450
space 400
pulse 900
space 450
pulse 450
```

---

### Post by reclusivemonkey on 2008-03-19
As of right now, the iMON VFD works almost flawlessly in Mythbuntu 8.04. The "pad" on the remote doesn't work, but all of the other keys do and all of this with the default LIRC package. Just load the relevant modules (see the MythTV Wiki) and it all works. I understand there are patches to get the pad working but frankly I am so glad the remote "just works" I simply remapped some of the buttons around the pad to perform up/down/left/right. Also, installing lcdproc and editing the config to use the imon driver gets the LCD screen working. I'm very pleased this all now works, its a great bit of kit to use in a self build MythTV system. I should imagine by 8.10 the 2pad" patches will have made it into lirc and it will all work prefectly.

---

