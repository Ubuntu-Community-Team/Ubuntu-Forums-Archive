---
title: "Snd-hda and Hw-Random"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by zoun on 2005-10-08
Hello
I have two critical problems with ubuntu (even the latest Breezy RC version) the boot sequence stop just after the Hotplug... Selecting safe mode in Grub permit me to see that two modules can't be loaded snd-hda-intel and hw-random. I have a recent computer (centrino 2 intel 915pm and radeon X700) This config seems to be very common but no site give an answer to this bug.
How can I add support for my soundcard in kernel (he tells me can't be loaded , missing kernel module and for hw-random :NRG not detected)


If someone has an answer or a meaning to ignore these errors and following the boot process.

                 Thanks A LOT

---

### Post by nooky59 on 2005-10-11
Hi,

I've a diffetent laptop but a Centrino Sonoma and I guess you have one.

In fact hw-random isn't responsible for the hotplug freeze at boot. This is snd-hda-intel.

In order to boot without problems, add this in /etc/hotplug/blacklist

snd-hda-intel

I suppose you are skilled enough to find the way to edit the file even if you can boot with Ubuntu (shortly, start on the Ubuntu install CD up to the network settings, switch to another console with CTRL + right arrow or CTRL + F2 for example, then

* Create a directory :

mkdir target

* Mount your Ubuntu partition (here is an example, find your correct partition number and if you hardrive is an hd or sd one)

mount -t ext3 /dev/sda5 /target

* Then you can edit the file with

nano /target/etc/hotplug/blacklist

Here the step to boot without problem. Then, if you want to try to have the sound, see this bug report :

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465)

I don't think installing the backport packages is necessary as the RC1 packages for Breezy are newest but you can get and compile the driver alsa 1.0.9.

Then you can remove snd-hda-intel from the /etc/hotplug/blacklist file.

For me, my soundcard is detected, alsamixer and Gnome see it but there is no sound at all.  I've reported it and try to find a solution but you can try, perhaps you'll be more lucky.

---

### Post by TRagiK on 2005-10-12
I think this thread will help you out. :)

[http://www.ubuntuforums.org/showthread.php?t=73175&highlight=tragik]("http://www.ubuntuforums.org/showthread.php?t=73175&highlight=tragik")

---

### Post by zoun on 2005-10-12
Just to tell you that your instructions work perfectly and now ubuntu start without problem (just a bug in xorg.conf but others people who have the Ati X700 say there is just one line to add so it's cool)

   Again THANkS A LOT

---

### Post by nooky59 on 2005-10-13
Hi,

No problem for the help.

Have you tried to compile the sound driver after ?

I still get no sound from the speakers or headphone output even if my soundcard is detected.

It's very frustrating :???:

---

### Post by zoun on 2005-10-22
Hello
I have take time to answer because I haven't got time.

I succeed to start ubuntu without snd-hda-intel blacklisted but it last to 'make sound'

For this I activated Universe for synaptic (easyubuntu put a good sources.list)

# apt-get install linux-headers-2.6.1xxxx-686(if you use this kernel 686=optimisation for new processor)
# apt-get install kernel-package 
# apt-get install ncurses-dev 
# cd /usr/src
# tar jxf alsa-driver.tar.bz2
Là je me suis rendu dans le dossier d'alsa-driver et j'ai fait 
./configure
make
make install

The version on alsa-project (1.0.10rc2... bugged during make). Using the one provided by Universe is OK, no bug

nano /etc/hotplug/blacklist to remove snd-hda-intel

The boot is ok

After if you are in kde usr the small icon kmix to enable pc speaker... up the level.
Else use alsamixer in console for gnome also.

SO everyhting seems to be good but at the final always no sound. I believe it's  a few better, maybe it's just the module snd-hda-intel that isn't registered in /etc/modules.conf 

I tell you if I have succeeded. Try this and tell me 
1.) If you can start with snd-hda-intel authorized
2.) Success to unmute
3.) Sound ...I hope for you

---

### Post by t.rei on 2005-12-15
I have tried all those hints - I got the modules loaded on boot and I can adjust any volume I want: cant hear a sound. :/

is there Anything I might have missed?

---

### Post by zoun on 2005-12-15
As I said Booting Ok with snd-hda enabled, but always silence .

I have tried at each release version of alsa 1.0.10 even final but too buggy to compile.

Today I'll try the Dapper Flight 2 If I have time. I'll post a message if things are better in this new version of ubuntu. With Breey I have tried all hints but unsuccessful.

I expect that corrections have benn done for Flight 2 (flight 1 it's the same : needs to blacklist and silence)


Great Hopes for dapper :rolleyes:

---

