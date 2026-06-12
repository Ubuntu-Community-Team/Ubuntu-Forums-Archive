---
title: "Toshiba NB 100 problem"
date: 2008-11-25
forum: Hardware
---

### Post by atlas95 on 2008-11-25
Hello ! 

I have just buy a new netbook, a Toshiba  NB 100 111 (Windows XP version)
I have buy the XP version for install directly linux on, i just choose it for big memory, bluetooth etc.

The 110 version with preinstall Ubuntu seems to work very well, all function keys work.

But for the moment, on my intrepid fresh install, I  can get working fan,screen for example.

I can't so enable cooling and my netbook is hot.

If someone buy the 110 version, i would be happy to have a feedback of all tweak and settings I must do.

Or if someone can simply say me where I can get the toshiba ubuntu ISO ?...

Thanks to help me :)

---

### Post by Cryptonome on 2008-11-26
> **atlas95 said:**
> Hello ! 

I have just buy a new netbook, a Toshiba  NB 100 111 (Windows XP version)
I have buy the XP version for install directly linux on, i just choose it for big memory, bluetooth etc.

The 110 version with preinstall Ubuntu seems to work very well, all function keys work.

But for the moment, on my intrepid fresh install, I  can get working fan,screen for example.

I can't so enable cooling and my netbook is hot.

If someone buy the 110 version, i would be happy to have a feedback of all tweak and settings I must do.

Or if someone can simply say me where I can get the toshiba ubuntu ISO ?...

Thanks to help me :)

You can install Ubuntu Remix with the NB100 options, the only thing I could not get to work  is the bluetooth sue the lack of a way to activate it.

The rest work perfectly, fans, suspend, etc.

---

### Post by jaureguiramirez on 2008-11-27
> **Cryptonome said:**
> You can install Ubuntu Remix with the NB100 options, the only thing I could not get to work  is the bluetooth sue the lack of a way to activate it.
'
The rest work perfectly, fans, suspend, etc.

I also have a toshiba nb100, i tried installing ubuntu eee but the install program couldn't find my main hard drive. So i made a fresh ubuntu 8.10 install but it was a pain to get the wireless lan working and the integrated mic on the notebook doesnt work either. it is also a little slow.

Where can i find the install for the ubuntu remix? thank you.

---

### Post by ispyamoose on 2008-11-27
> **jaureguiramirez said:**
> I also have a toshiba nb100, i tried installing ubuntu eee but the install program couldn't find my main hard drive. So i made a fresh ubuntu 8.10 install but it was a pain to get the wireless lan working and the integrated mic on the notebook doesnt work either. it is also a little slow.

Where can i find the install for the ubuntu remix? thank you.

[http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

Scroll to the bottom of the page for the download link, but I would read the page on the way down.

---

### Post by jaureguiramirez on 2008-11-27
> **ispyamoose said:**
> [http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

Scroll to the bottom of the page for the download link, but I would read the page on the way down.

Thank you but i was actually looking for the very same version that comes preinstalled in this notebook, i want the ubuntu drivers for this specific netbook.

---

### Post by sammyd on 2008-11-27
Hi, I too am looking for the Toshiba Ubuntu ISO.

jaureguiramirez can you point me in the direction of how you got the atheros wifi working - I am having no luck.

---

### Post by Cryptonome on 2008-11-27
To install a working version of Unbutu Remix you have to download and install on a USB drive, after installation of Ubuntu Remix all should be working except Bluetooth.

To add the fan control, the LCD control, OSD Display and toshiba customziations you have to add to your apt repositories the following 
deb [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main
```


and them install with
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install oem-config toshiba-conf toshiba-extras-bin toshiba-nb100-manual toshiba-osd-bin toshiba-osd-userspace toshiba-payson-unr

```

---

### Post by jaureguiramirez on 2008-11-27
> **sammyd said:**
> Hi, I too am looking for the Toshiba Ubuntu ISO.

jaureguiramirez can you point me in the direction of how you got the atheros wifi working - I am having no luck.

I used this tutorial: [http://www.ipako.net/2008/11/instalando-atheros-5007eg-enubuntu-intrepid-ibex/](http://www.ipako.net/2008/11/instalando-atheros-5007eg-enubuntu-intrepid-ibex/)

it's in spanish, but all you need to do is download the drivers and enter those simple commands.

---

### Post by Cryptonome on 2008-11-27
> **jaureguiramirez said:**
> I used this tutorial: [http://www.ipako.net/2008/11/instalando-atheros-5007eg-enubuntu-intrepid-ibex/](http://www.ipako.net/2008/11/instalando-atheros-5007eg-enubuntu-intrepid-ibex/)

it's in spanish, but all you need to do is download the drivers and enter those simple commands.

I do not recoment to install Ubuntu Intrepid, because you loose the cpu optimization and power management included in the lpa version of ubuntu remix based on 8.04-1.

WIth Ibex I got 2 hours on battery with UNR iI got 3 and a half. Btw all work with out issue with UNR including wireless.

---

### Post by jaureguiramirez on 2008-11-27
> **Cryptonome said:**
> To install a working version of Unbutu Remix you have to download and install on a USB drive, after installation of Ubuntu Remix all should be working except Bluetooth.

You mean that i can only run it from an USB drive? Can't it be installed in the main hard drive?

---

### Post by atlas95 on 2008-11-27
Taks , all is working, I have pass the day to reinstall all my fav program and more.
All is working, bluetooth too.
Just a little problem of "random" toggle wireless button : sometimes at start bluetooth and off but wlan on, sometimes they are on together....i must toggle off and toggle on on time too have a good sync of bt and wlan state.
for resume i think we can optimise hal,acpi script which control it but i have not find how to yet.

And another one, i have resize with gparted live usb my only / for make a SWAP.
Now I can hibernate but resume don't work !
I have set in /boot/grub/menu.lst resume=/dev/sda2 at end of kernel line.
I don't understand why resume on disk doesn't work, if you can help me...

I will help you if you have question if you want..

I go to sleep, it is 1am here and i have exam this afternoon :D

---

### Post by jaureguiramirez on 2008-11-27
> **atlas95 said:**
> Taks , all is working, I have pass the day to reinstall all my fav program and more.
All is working, bluetooth too.
Just a little problem of "random" toggle wireless button : sometimes at start bluetooth and off but wlan on, sometimes they are on together....i must toggle off and toggle on on time too have a good sync of bt and wlan state.
for resume i think we can optimise hal,acpi script which control it but i have not find how to yet.

And another one, i have resize with gparted live usb my only / for make a SWAP.
Now I can hibernate but resume don't work !
I have set in /boot/grub/menu.lst resume=/dev/sda2 at end of kernel line.
I don't understand why resume on disk doesn't work, if you can help me...

I will help you if you have question if you want..

I go to sleep, it is 1am here and i have exam this afternoon :D

What did you do? Did you install ubuntu 8.04?

---

### Post by atlas95 on 2008-11-27
I must turn off sound mail notification lol!
I have install ubuntu network remix based on hardy and add the payson ppa for add toshiba tools

;)

---

### Post by sammyd on 2008-11-27
> **atlas95 said:**
> 
Just a little problem of "random" toggle wireless button : sometimes at start bluetooth and off but wlan on, sometimes they are on together....i must toggle off and toggle on on time too have a good sync of bt and wlan state.
for resume i think we can optimise hal,acpi script which control it but i have not find how to yet.


I am experiencing the same issue, on installing UNR the first time round the atheros wifi card was detected and I could scan for networks. I think I hit the fn-F2 shortcut which I believe is linked to turning on-off wifi. Now I am having some problems detecting the card. 

I had read that turning wifi on/off in bios may help restart and will try that when I get home. 

Any other suggestions????

---

### Post by atlas95 on 2008-11-28
I have install install network-manager 0.7 from ppa ~network-manager, this is yet the same problem, i must play wuth toggle wireless button, but the difference with 0.6 is that the nm-applet wireless wlan toggle option doesn't switch on/off, I have install it for have a good support of my 3g usb.

I have see to think too, sometine at start when i do a dmesg just after the fully environement start, i have a segfault of nautilus and bluetooth-applet. :/

---

### Post by sammyd on 2008-11-28
Pleased to reply from my NB100 with 8.04 UNR on wireless. It seems that to get the wireless up and running I have to make sure bluetooth is toggled on. I also install WICD wifi manager which works far better than network-manager and allows connection to protected network.

---

### Post by atlas95 on 2008-11-28
Could you give me the repository to install wicd? (I have a svn version on my laptop debian the interface in python is very slow but work very good)

---

### Post by Cryptonome on 2008-11-28
> **atlas95 said:**
> Taks , all is working, I have pass the day to reinstall all my fav program and more.
All is working, bluetooth too.
Just a little problem of "random" toggle wireless button : sometimes at start bluetooth and off but wlan on, sometimes they are on together....i must toggle off and toggle on on time too have a good sync of bt and wlan state.
for resume i think we can optimise hal,acpi script which control it but i have not find how to yet.

And another one, i have resize with gparted live usb my only / for make a SWAP.
Now I can hibernate but resume don't work !
I have set in /boot/grub/menu.lst resume=/dev/sda2 at end of kernel line.
I don't understand why resume on disk doesn't work, if you can help me...

I will help you if you have question if you want..

I go to sleep, it is 1am here and i have exam this afternoon :D

Are you sure that Bluetooth is working, because as much as I check I can not get it working, the Hardy version install all and the driver is loaded but bluetooth is not working at all. On Windows Xp run perfectly.

---

### Post by atlas95 on 2008-11-28
Yes bluetooth works i'm sure ;)
I have  try somes files transfert, and it only work when the bluetooth applet is display.

---

### Post by Cryptonome on 2008-11-28
> **atlas95 said:**
> Yes bluetooth works i'm sure ;)
I have  try somes files transfert, and it only work when the bluetooth applet is display.

Ok, I will reinstall all, wuch version are you using? I mean wich iso are you using ?

Thanks

---

### Post by jaureguiramirez on 2008-11-28
Everything is working for me now, except for the microphone. Any ideas?

---

### Post by bernd.juchems on 2008-11-28
Hi all ...

I'm new here, and this is my first post.

I'm very glad to find some other users that are experiencing problems similar to mine with the combination of Toshiba NB 100 and Linux/Ubuntu.

I've gotten my NB 100 a week ago from my company. We've decided to get the Windows version for the obvious reasons (more RAM, BT and so on ...) and I wanted to install Ubuntu as second OS, as I thought "hey, they're shipping it with this OS, so it will work".

How stupid I was.


I had some calls to Toshiba hotline ... result: Very much support for Windows ... none for Linux.
I asked them for the "Original" Distribution they ship with their Ubuntu-Version of the NB 100 ... but this is not available to the outside world.
So I tried for myself.

First try:
- Kubuntu Intrepid (I used to prefer KDE over Gnome with KDE 3, but after having some insight into KDE4 on Netbooks I will overthink that). Result: installation worked fine, but no WLAN running!

Second try:
- Ubuntu-eee (non-Canonical offshoot of Intrepid, I think; Netbook Remix). Result: WLAN worked fine, but the OS did not recognize the Hard Discs, so no installation possible

Third try:
- Ubuntu Hardy ... installation worked fine, but no WLAN.
As I was desperating about this, I found THIS forum thread.
But I seem to have lost the track: What do I actually need to get my WLAN running? The thing Cryptonome wrote (=> get this Netbook Remix edition, which desktop I do not very like) and add the toshiba-packages?
I tried to add the toshiba-things (oem-config, toshiba-conf and so on) but I got lost in dependency chaos (there were always missing dependencies like "language-installer" or other)
Or is it the way jaureguiramirez wrote? (download the madwifi package, reinstall it)?
I tried this, too (I tried to guess the correct way, as I do not speak spanish), but it had no effect.

Or maybe it is a problem of Gnomes Network Manager applet? (I do not find Entries for my WLAN there).





Well, I seem to need help. I am a programmer myself, but still quite new to the Linux world, so this whole "compile the kernel"-stuff scares the **** out of me. Anyhow, I would be grateful to get a working (with all hardware options) NB100. Could someone please help me?

Maybe one could summarize all needed steps to get a working Linux on a NB 100 from steps like "download the ISO image here", "do this to make a bootable USB stick from it", "install to hard drive", "add these repositories" "get these packages" and finally "have fun with your WLAN"?

I'm completely lost and slightly frustrated ...

---

### Post by atlas95 on 2008-11-28
Hi all,

For install ubuntu on this netbook, use Ubuntu Network Remix, read this page, all is explain for install it :

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)


After, add in your source.list the payson repository :


deb [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main

Then do :

sudo aptitude update && sudo aptitude install toshiba-payson-unr

And all work :)


For me, i'm testing PHC undervolt on it for the moment...

---

### Post by Cryptonome on 2008-11-28
> **atlas95 said:**
> Hi all,

For install ubuntu on this netbook, use Ubuntu Network Remix, read this page, all is explain for install it :

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)


After, add in your source.list the payson repository :


deb [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main

Then do :

sudo aptitude update && sudo aptitude install toshiba-payson-unr

And all work :)


For me, i'm testing PHC undervolt on it for the moment...
I Check again and no Bluettoth, if I run windows XP, tem reboot and get into Ubuntu I got Bluetooth, but if i Turno off the NB1010 and boot into ubuntu no bluetooth, is the same for you?


Thanks, I just try t find a solution.

---

### Post by jaureguiramirez on 2008-11-29
So i got everything working, except for the front mic.

---

### Post by atlas95 on 2008-12-01
The front mic work, plz verify your sound settings, enable in prefs  all available option, and choose "Int DMic" in "Input Source" option tab.
;)

---

### Post by atlas95 on 2008-12-08
Hi,

How to remove this flood in Xorg.0.log ?

I think xorg.conf need some custom in screen or device part but i don't know what...

Could you help me? This make work the hard drive for nothing ...

cyril@cyril-netbook:~$ tail  /var/log/Xorg.0.log
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546


thanks

---

### Post by sandman652001 on 2008-12-11
I'm having a problem when I try to install toshiba-payson-unr

I getthis error

toshiba-payson-unr:
 Depends: topi  but it is not installable
 Depends: toshiba-google-eula  but it is not installable

does aanybody have any idea on how to solve this?
Thanks for you help

---

### Post by EGottlieb on 2008-12-11
Hi Everyone,

I notice that people are having varied results with the install of Ubuntu on the NB100 and wanted to tell how I was able to do this.

First of all, I purchased the Windows XP version of the NB100, but my end goal was to have a dual-boot system with both XP and Ubuntu.  I really wanted it to have the "official" Ubuntu install as if I had purchased it with this, and also get the benefits of the LPIA kernel, so I went with the UNR 1.0.1 deployment package.  I setup my system as follows:

1) Downloaded [http://oem-images.canonical.com/unr/unr-1.0.1.iso]("http://oem-images.canonical.com/unr/unr-1.0.1.iso") and burned the ISO image to a DVD

2) Booted from this and installed on the NB100.  Note that this installer is NOT like the standard Ubuntu installer and does not allow you to pick a partition.  It will wipe all partitions and do it's own install.

3) Downloaded gparted boot image and created a bootable CD for this.  Used this to shrink the Ubuntu partition to 10 GB and copy it to the 2nd partition.  Created a partition with the rest (about 100GB) for Windows.

To make it more clear -- after I was done booting the gparted CD and modifying the partitions, I had a 100 GB partition labeled as NTFS first (on the left in the gparted graph) and my 10 GB Ubuntu partition on the right side.

Note that it is REQUIRED for the Toshiba XP restore disk that Windows be on the first partition.  This move of Ubuntu to the new 2nd partition screws up grub, but we'll fix that later.

4) Now I booted from the XP restore CD that came in my NB100 box.  At the first screen I chose "advanced" or something like that at the bottom which brought up a dialog box to let me choose to either wipe the disk (NO!!) or install on a partition.  When I chose to install on an existing partition, it offered me the first partition (100GB).  If you did not move Ubuntu to the 2nd partition with gparted, it will want to overwrite it.

5) After restoring XP to the large partition, when I rebooted, I got only a message saying "Error 17".  This is grub complaining that it can't find the Ubuntu installation.  Now you need a regular Ubuntu 8.04 or 8.10 installation boot CD.  Boot into the live CD session, mount your Ubuntu partition, and edit the ./boot/grub/grub.conf file.

You need to make the following changes:
a) for both Ubuntu boot images, root (hd0,0) needs to change to root (hd0,1)

b) for both boot images, set the kernel boot line to include "root=/dev/sda2"

c) add the line for Windows XP as follows:
title	 Microsoft Windows XP Home
root	 (hd0,0)
makeactive
chainloader	+1

d) set the timout parameter as appropriate for the number of seconds you want before booting in to the default OS

e) load the changes in to the MBR as follows:
sudo grub
root (hd0,1)
setup (hd0)
quit

Now grub is all set and you just need to adjust your ./etc/fstab file to change the mounting of the root partition from /dev/sda1 to /dev/sda2

Note I am using ./boot/grub/menu.lst and ./etc/fstab because these are the ones located in the Ubuntu partition, NOT the ones on the current root directory (those are the live CD files and won't help you!).

6) Now you should be able to reboot and get the grub menu.  Test to be sure that you can boot into both XP and Ubuntu.

Finally, follow the directions in the earlier post about adding the payson sources to the source file and to the apt-get update; apt-get upgrade; apt-get install toshiba-payson-unr

Now you should be all set.

If anyone tries this and runs in to trouble, let me know and I can help or post my grub menu.lst file.

Good luck!

Eric

---

### Post by sandman652001 on 2008-12-11
> **sandman652001 said:**
> I'm having a problem when I try to install toshiba-payson-unr

I getthis error

toshiba-payson-unr:
 Depends: topi  but it is not installable
 Depends: toshiba-google-eula  but it is not installable

does aanybody have any idea on how to solve this?
Thanks for you help

Anybody have the same problem?

---

### Post by EGottlieb on 2008-12-11
> **sandman652001 said:**
> Anybody have the same problem?

I don't, sorry.  I also checked to see if I had either of those packages installed and no, I don't.

apt-get also cannot find them.

What distribution are you using?  Are you using the lpia UNR distribution?

---

### Post by sandman652001 on 2008-12-12
Followed the guide to the letter I installed the lpia UNR then added the payson repos
I also tried installing hardy and the adding every thing to it but I still get the same error. the only reference I can find on the internet to the missing dependency's is here [https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr]("https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr") 
thanks for your help

---

### Post by EGottlieb on 2008-12-12
> **sandman652001 said:**
> Followed the guide to the letter I installed the lpia UNR then added the payson repos
I also tried installing hardy and the adding every thing to it but I still get the same error. the only reference I can find on the internet to the missing dependency's is here [https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr]("https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr") 
thanks for your help

When I now do an sudo apt-get update; sudo apt-get upgrade, I can also see that it cannot find those dependencies.

Try installing the other packages instead of the whole payson pack:

toshiba-config
toshiba-nb100-manual
toshiba-osd-bin
toshiba-osd-userspace

my system updated these (except the manual, which must not have changed).

---

### Post by mustardseed on 2008-12-12
If you look at:

[https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr](https://code.launchpad.net/~canonical-fae-team/payson/toshiba-payson-unr)

at the recent changes for at the recent changes you can see that dependencies on the eula and topi were added recently.

I realise that this doesn't solve the problem but it does explain why this package is no longer installable whereas it worked in the past.

It also says the eula and topi packages are now available in payson repo.  Perhaps someone with more experience can decode this?

---

### Post by sandman652001 on 2008-12-12
Yes I installed the separate packages and everything seems to be working but it still annoys me to death ;) it's like having a messy room:D. I guess we will have to wait for a solution.

I am now wandering if there is a solution for the codecs(W32codecs, etc) I tried adding the medibuntu repos but nothing will install, I only managed to install skype but I had to download and install manually.

---

### Post by nb100.toshiba on 2008-12-14
Does anyone know where to download Toshiba NB100 Ubuntu recovery DVD (original ISO) or is willing to share it for download ? I'd be grateful since I can not find it anywhere.

----------------------------
Proud owner of Toshiba NB100

---

### Post by sandman652001 on 2008-12-15
Sorry I looked for it too but it seems that nobody shared it, is there any particular reason you need the original? this guide works quite well

---

### Post by sandman652001 on 2008-12-21
**INSTALLING UBUNTU NETBOOK REMIX ON A TOSHIBA NB 100**

**I would like to start by saying that this guide is not my doing! I just copied bits and pieces from many sources and cleaned it all up so it would be easier for people like me to install UNR on their Toshiba NB100.** At the bottom of the guide you will find links to the original posts or guides that I used.

**To install UNR on your Toshiba **

download the following image
[http://oem-images.canonical.com/unr/unr-1.0.1.img](http://oem-images.canonical.com/unr/unr-1.0.1.img)

From a Ubuntu PC

Download and install USB-Image writer 
[http://ppa.launchpad.net/ogra/ubuntu/pool/main/u/usb-imagewriter/usb-imagewriter_0.1-1~ppa1_all.deb](http://ppa.launchpad.net/ogra/ubuntu/pool/main/u/usb-imagewriter/usb-imagewriter_0.1-1~ppa1_all.deb) 

Plug in  a usb pen drive(at least 1 Gb)

Then run the Image Writer tool from the accessories menu, select the downloaded image, select the target device and click on "Write to device"..

From a windows command prompt
. 
1.Download flashnul from [http://shounen.ru/soft/flashnul/](http://shounen.ru/soft/flashnul/) 
2.At the command prompt run: 
flashnul -p 
3.Note the physical device number for the target USB disk. 
4.At the command prompt run: 
flashnul <number obtained in prior step> -L \path\to\unr-<version>.img
5.Answer "yes" after verifying the destination device. 

Once it finished unmount the usb drive and plug it in to your netbook

Start your NB100 press F12 at the initial screen and select USB Memory as the boot device.
Follow the instructions to install UNR.

[COLOR="Red"]**PLEASE BE AWARE OF THE FACT THAT THE INSTALLATION OF UNR WILL DELETE EVERYTHING ON YOU DRIVE! Including WINDOWS XP!**[/COLOR]

Once the install is finished open a command prompt and type

*sudo gedit /etc/apt/sources.list *

and add the following to the end of the file

[I]deb [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) hardy main[/I]

save and close it
then type 

*sudo aptitude update && sudo aptitude install toshiba-payson-unr*

if that does not work(at the moment of writing there seems to be a problem)

*sudo aptitude update && sudo aptitude install toshiba-config toshiba-nb100-manual toshiba-osd-bin toshiba-osd-userspace*


**TWEAK FOR BOOTUP SPEED (Optional):**

To decrease boot time, activate concurrency bootup: 

*sudo gedit /etc/init.d/rc* 

and replace the line: 

CONCURRENCY=none 
with 
CONCURRENCY=shell 

Install preload, it loads in to memory parts of the programs that you use most often**[COLOR="Red"](NEW)[/COLOR]**(I'm told that people that have less than 1 Gb of ram have problems with this)

*sudo aptitude install preload*

no configuration needed

**TWEAKS FOR POWERSAVING (Optional):**

Add the following to the /etc/rc.local file: 

[I]# As in the rc.last.ctrl of Linpus
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 20 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 5 > /proc/sys/vm/laptop_mode

#Decrease power usage of USB while idle
[ -w /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -w /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level[/I]

[COLOR="Red"]**(NEW)**[/COLOR]**Adding a swap file to solve suspend issues**
The following solved my suspend issues

Sample method of creating and using a swap file:

(The preceding hash (#) means that the command should be ran as root)

1) Create the file (2GB in this example):
```

# dd if=/dev/zero of=/swap bs=1024 count=2097152

```2) Make it usable as swap:
```

# mkswap /swap

```3) Edit fstab so it may be used on startup
```

# echo -e "/swap\tnone\tswap\tsw\t0 0" >> /etc/fstab

```4) Activate it for use immediately
```

# swapon -a

```
we owe this one to Rolcol


**Maximising screen real estate in Firefox:**

To take your screen saving netbook remix to the next level, you can do the following to maximise screen real estate in everyone's most used app - Firefox - 

Install the following addons 
Stop or Reload Button 
Personal Menu 
AutoHideStatusBar ([https://addons.mozilla.org/en-US/firefox/addon/1530](https://addons.mozilla.org/en-US/firefox/addon/1530)) 
Fission it combines address bar and progress bar (Safari style).
Install the following theme - 
Classic Compact 
Configure Personal Menu to include all the standard menus except History and Bookmarks (they get their own buttons) 
Disable the menu toolbar. You can always get it back by pressing Alt 
Use the top-bar icon tabs instead of firefox tabs. (options are in edit > preferences > tabs ) 

**Install Network Manager 0.7 (3g support)**

*sudo gedit /etc/apt/sources.list *

and add the following to the end of the file

[I]deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main[/I]

[I]sudo apt-get update

sudo apt-get upgrade[/I]

reboot

restart network manager alt+f or from a terminal:

*nm-applet*

blacklist the airprime driver

*sudo nano /etc/modprobe.d/blacklist*

Add this to the bottom of the file:

*blacklist airprime*

Remove the running driver:

*sudo modprobe -r airprime*

**Repackage i386 deb in to  lpia deb**

Really the i386 deb is a non issue. You can easily repackage any deb outside the repos into an lpia one. And really there aren't many. The reason you want lpia packages instead of forcing the i386, is that while the former will show up as an installed package on Synaptics, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for Skype into an lpia package:

1. Download the Ubuntu version of Skype
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the debian-binary file
6. Decompress control.tar.gz. There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: lpia"
9. Open the other archive data.tar.gz. There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files control.tar.gz and data.tar.gz
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.

[B]
Sources:[/B]
[https://wiki.ubuntu.com/UNR]("https://wiki.ubuntu.com/UNR")
[http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=3 ]("http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=3")
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")
[http://www.barq.org/blog/?p=50 ]("http://www.barq.org/blog/?p=50")
[URL="http://ubuntuforums.org/showthread.php?t=910487&page=55"]http://ubuntuforums.org/showthread.php?t=910487&page=55
[/URL][http://ubuntuforums.org/showthread.php?t=1059358&highlight=add+swap+partition]("http://ubuntuforums.org/showthread.php?t=1059358&highlight=add+swap+partition")

---

### Post by nb100.toshiba on 2008-12-23
I'd like to have an original image from Toshiba. Is there nobody willing to share in this X-mas time ?? :P

---

### Post by ubuntator on 2009-01-12
I am trying to build a dual-boot system with NB100, the XP version, and Easy Peasy 1.0 but I have not a working microphone.
 
How have you solved that starting from Ubuntu-UNR?
Which step of the previous procedure does produce a working microphone in Ubuntu on the Toshiba NB100?

Thanks

---

### Post by sandman652001 on 2009-01-15
I have no problem with the mic after installing UNR

---

### Post by bernd.juchems on 2009-01-15
Hi all ...

after a longer period I finally had the time trying to get Linux work on my Toshiba.

I was somehow reluctant to test the UNR image, as I could not see if it would delete my Windows partition, so I waited a bit.

Then someone came up with this Ubuntu-EEE distro, now painfully renamed to "Easy Peasy". (=> Ubuntu Intrepid)

That worked!
At least, on second try (first try didn't see the hard drive again).
On second try: Graphics. Input, Hard Drive, WLAN ... 
And, Oh happy days, without me having to mess around with hard driver installing work, for I still am not very secure in Linux at all.

So, now I am running a great working Linux on my new little toy and should be content, BUT ...


There still is no Blutetooth and no Webcam.

Has someone else this Distro and has these problems solved?

BTW: I tried to add these Payson repos to Synaptic, but I am not able to install these toshiba packages (and I have tried to change "hardy" to "intrepid") ...

---

### Post by ubuntator on 2009-01-16
> **bernd.juchems said:**
> Hi all ...


There still is no Blutetooth and no Webcam.

Has someone else this Distro and has these problems solved?

 ...

In order to have the NB100 webcam working in Easy Peasy 1.0 with cheese I put the setting to the lowest available resolution. And for me the webcam works natively with Skype. 
But  as you can se on my previous post #40 I have a not working microphone. Does your microphone work? If yes have you done some configuration for it? 
I have not tried the Bluetooth yet:(.

---

### Post by bernd.juchems on 2009-01-17
> **ubuntator said:**
> In order to have the NB100 webcam working in Easy Peasy 1.0 with cheese I put the setting to the lowest available resolution. And for me the webcam works natively with Skype. 
But  as you can se on my previous post #40 I have a not working microphone. Does your microphone work? If yes have you done some configuration for it? 
I have not tried the Bluetooth yet:(.

Ah, ok, it was my fault; I didn't know that cheese program. It works, as you told. Thank You. And I found the corresponding Skype setting as well ... 

BTW: Skype microphone doesn't work by me either.

---

### Post by bernd.juchems on 2009-01-17
Adendum: After I have installed some other software (not obliously linked to the matter), I now have a Bluetooth icon in the tray and can connect to my Nokia phone. It's a miracle, I think :P

---

### Post by ubuntator on 2009-01-17
> **bernd.juchems said:**
> 
BTW: Skype microphone doesn't work by me either.

I opened a bug report in:

[https://bugs.launchpad.net/ubuntu-eee/+bug/318239](https://bugs.launchpad.net/ubuntu-eee/+bug/318239)

---

### Post by markrfc1873 on 2009-01-20
I have the toshiba recovery disc for ubuntu netbook remix if anyone is interested in a trade for the xp version.

many thank's Markrfc:D

---

### Post by sqoo on 2009-01-21
> **bernd.juchems said:**
> Adendum: After I have installed some other software (not obliously linked to the matter), I now have a Bluetooth icon in the tray and can connect to my Nokia phone. It's a miracle, I think :P


yes that is a miracle, congratulations!!!!!

I am running with the original intrepid install and have tried various things to get bluetooth going but have had no success in getting it started :(

I am beginning to wonder if this machine actually has bluetooth.

I would love to do away with the cable between my nokia phone and this machine especially since my girlfriend sat on it while it was plugged in yesterday and the plug is now bent and unreliable, bah

so how **do** you get bluetooth running?????

---

### Post by bernd.juchems on 2009-01-22
Yeah, a miracle ...

When I booted Ubuntu two days ago, there was no Bluetooth again.
Miraculous ... ](*,)

Maybe some side effects running the original WinXP along with Ubuntu? Does the BT-adapter save some settings internally and gets confused on switching to another OS?

There is a parallel to my experiences on installing Ubuntu: When I first tried to install, the live system did not find any hard disk.
On second try, it did ...

---

### Post by bernd.juchems on 2009-01-22
> **markrfc1873 said:**
> I have the toshiba recovery disc for ubuntu netbook remix if anyone is interested in a trade for the xp version.

many thank's Markrfc:D

I have the XP-CD, I think ...

What about putting our CD's on Rapidshare? Or is there any copyright problem I didn't think of?

By the way: has anybody any experience with the recovery CD? Does it simply delete anything on the hard drive?

---

### Post by sandman652001 on 2009-01-22
For those having a disappearing Bluetooth try and switch your wireless adapter on and off mine reappears after I do that

I do not know about the UNR disk by Toshiba but sharing the XP one is a definite no-no from a license point of view, besides if you want to install XP on it you can use any XP disk and download the drivers from the Toshiba website, not only that, but if you do not have an external CDROM there is no way of using the restore disk anyway.

---

### Post by bernd.juchems on 2009-01-23
[QUOTE=sandman652001]
For those having a disappearing Bluetooth try and switch your wireless adapter on and off mine reappears after I do that
[/QOUTE]

YES! That's it. I managed to reproduce this. Thanx :D

[QUOTE=sandman652001]
I do not know about the UNR disk by Toshiba but sharing the XP one is a definite no-no from a license point of view
[/QUOTE]
Yeah, I had something like this in mind. I still wasn't sure, if there might be a possibility for sharing, as with the "Windows XP Netbook Edition"-thingy, that is already some sort of "limited" WinXP. But, I forgot, M$ does not want their products to be used unless explicitely allowed :(

[QUOTE=sandman652001]
, besides if you want to install XP on it you can use any XP disk and download the drivers from the Toshiba website
[/QUOTE]
Nothing more? Oh, that's nice from Toshiba. I think they have figured out, that it would be an extremely mess to provide the same courtesy for Linux (at least, that is, what the Toshiba Support in Germany told me ... what a shame).

Ok, with BT hopefully running, I will switch over to Ubuntu for main working duty, to get me out of my n00b-State in time :p

---

### Post by bernd.juchems on 2009-01-23
Oh, here another one:
I do have the german keyboard layout version ("QWERTZ") of the Toshiba. This layout has the nice anomaly, that the "Pipe"-Character ("|") lies on the "x"-key - and should be accessible via the "FN"-Command-Key (=> FN + x).
Problem is: it wouldn't. Neither in Windows XP nor in Ubuntu the FN + x combo would produce a proper "|"; Linux shells will produce a single ">>"-sign that would not really work as pipe in scripts :-(. 
With Windows, that would be ok for me, with Linux this is a big problem!

Has anybody else this problem?

---

### Post by sandman652001 on 2009-01-24
I do not have the problem but try and do a search for key remap on the forum
there should be a way to have the fn x combination work for you

---

### Post by mariopilar on 2009-01-25
hello all
i already tried unr install from bootable usb disk, made by dd from unr-1.0.1.img
it works ok however it wipes out my windows xp
since xp is paid for i see no arm in keeping it
besides i need it for my checkpoint vpn client

since XP recovery disk from toshiba allows me to create /dev/sda1 with variable size, for example 100 GB, i could live with ubuntu in my other 60 gb

as anyone tried to customize install.sh present in usb_boot image to "NOT" wipe the disk but to install only in /dev/sda2 ??

---

### Post by sandman652001 on 2009-01-25
It would be useful if UNR did not wipe ones disk, but I have not tried the modification you suggest. You can however find a way to install UNR with Xp in this post a couple of pages back

---

### Post by StrgAttractor on 2009-01-28
Hi!!
First of all, thanks you, all this information has been very usefull to install ubuntu in my new brand nb100.

All works fine except the fans. I have ubuntu intrepid (the problem is this?) , I put 
deb [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/payson/ubuntu](http://ppa.launchpad.net/payson/ubuntu) intrepid main
in the source list and I tried:
sudo aptitude update && sudo aptitude install toshiba-config toshiba-nb100-manual toshiba-osd-bin toshiba-osd-userspace

but there was erros. Brightness and wifie controls from keyboard works but the fun doesnt work (wathing a film the temperature is very high and fun still keep dead)

Do I have to use ubuntu hardly?...
Are the fun controls in this packages?  

Thanks!!!

---

### Post by atlas95 on 2009-01-28
Hi,
I have try yesterday intrepid too, and now, i will reinstall form unr.img tonight, the problem? Payson ppa doesn't provide yet their tweak for intrepid, there is any package for intrepid, so no osd for fan, toggle screen fn key working etc...

If anyone done the install of intrepid lpia with all tweak, key, osd working tell me it :)

:(

---

### Post by StrgAttractor on 2009-01-28
Aham, thx.

The point is that it doesnt matter that osd for fan not work, the problem is that when temperature is high, the fan doesnt start!!!!, so you cant use the netbook to watch video or something that requires intensive calculations.
Payson ppa is only for osd or controls the fan automatically also?

---

### Post by danieljezik on 2009-02-03
I bought Toshiba NB 100 with XP.Now I have instaled Ubintu 8.10. Microphone is not working and I could not ind any solution for fixing it...Pls help. Thanks, I dont want to switch back to XP, hope I will find solution...

---

### Post by bernd.juchems on 2009-02-04
Hi there ... 

Just in case it might help someone, I was able to remap the "|"-character to a key of my choice (doing this by editing the latin keymap of the X-server); if anybody needs to know how, I can go on the topic further.

Now I will try to do the same remapping for the basic Linux system below, as of course the remapping does not work on console, just with X.


BTW: does anybody know if those PPA guys are working on a solution for Intrepid, too?

---

### Post by atlas95 on 2009-02-04
Hi, could you explain how to remap please? What is the "|" on a azerty keyboard?
For me, I would like to remap the "function+²" which do nothing no? (on azerty keyboard this is the touch with seem to be the wwan key, but this nb100 havn't a wwan internal card...)

---

### Post by bernd.juchems on 2009-02-12
> **atlas95 said:**
> Hi, could you explain how to remap please? What is the "|" on a azerty keyboard?
For me, I would like to remap the "function+²" which do nothing no? (on azerty keyboard this is the touch with seem to be the wwan key, but this nb100 havn't a wwan internal card...)


Hi ... this is, what I sent as a PM to another User:


[INDENT]
I solved the pipe character-problem the following way:
For the X-server there are a lot of keymaps saved; plain text files that say which key or action is to be executed by pressing any key. These keymaps are organized in the filesystem under /usr/share/X11/xkb/symbols.

I wanted to map "|" to AltGr + x, as this way of remapping seemingly does not work with the Fn-Key.

Now you have to find out, what keymap you are using. For me, it is "de". The localized map itself won't help you, you must find, where the base map lies. In the "de" map there is an entry 'include "latin(type4)"'. That means, the base key mapping for "de" is found in the keymap "latin". Open this file (/usr/share/X11/xkb/symbols/latin) as root with a text editor.
The "type4" section is irrelevant; the mapping for the "x" key is found the "basic" section (=> 'kxb_symbols "basic" { ...').
Here is an entry 
"key <AB02> {[x, X, guillemotright, greater]}";
 maybe there are other entries for you. The first entry means "simply striking x key", the second entry means "shift + x", the third "AltGr + x", the fourth I don't know yet ;-)
As I wanted to map the Pipe to AltGr + x I replaced the third entry (guillemotright) with the code for the pipe ("bar"), so now my entry reads
"key <AB02> {[x, X, bar, greater]}".
(it might be wise to let the old line in the file and just comment it out with //).

Now you have to restart X server, or reboot. And you should have the Pipe character.

This way only works while working on the desktop, i.e. GNOME, KDE or other. It won't work if you go into console without any X server. But I'm sure, there is a similar solution here.

Of course you can reassign "bar" to any other key combination, and you have replace my keymap with the one that you use. Just make sure, you have a copy of the original keymap ;-)[/INDENT]



The "azerty"-Layout must be the "fr"-keymap, which is based on "latin" as well, so my solution should work for you as well.
But, alas ... as far as I know that kind of remapping does not work with FN-keys, as FN keys are some things that proprietary things from the manufacturer. There is a GNOME-tool that prints out all input events, so you have to find out what kind of event the FN-combo submits, but at the moment I do not know, what that tool's name was :-(.

---

### Post by bernd.juchems on 2009-02-12
By the way ... not a GNOME- Tool but a X tool: xev

---

### Post by Aikimox on 2009-02-16
Hi,
For those who still search for the microphone problem solution for Toshiba nb100 netbook , I have found one, I think.

Just run in terminal:

sudo gedit /etc/modprobe.d/alsa-base

and add a line at the bottom of the file:

options snd-hda-intel model=toshiba position_fix=1 enable=yes

reboot and then in skype change default snd devices to HDA intel (hw;intel,0)

Worked like a charm in my case. Sound in skype will be mono but really who cares. and there will be sudden issues with firefox. If you play a youtube movies, for example, skype has a audioplayback problem. So quit firefox for a sec, establish a call in skype and reload the browser. 
I spent a month on this, reinstalled ubuntu several times, but finally - everything works on toshiba nb 100 dual boot with xp/ubuntu 8.10
So if you have further questions, I'd be glad to help if I can.
And don't install kernel update 2.6.27-11 it ruins network. use program kernelcheck to install latest kernel , to this date it's 2.6.28-5. Then everything works fine but the wireless. For wireless i found a thread which works for my netbook, I'll try to find it again.

---

### Post by atlas95 on 2009-02-17
Hi !



@Aikimox:
-Could you share your .config for kernelcheck?
I will do this tonight, have you seen some speed improvement or other improvement while using the last kernel?What i must do for have wireless working after this upgrade?


-I havn't seen problem with my mic...i will try your fix

-Someone have try to replace the internal hard drive? is it difficult to open it ? I would like to replace it by a SSD hard drive...

@bernd.juchems:
Thanks for the tips !


Best Regards

Cyril

---

### Post by Tuliku on 2009-02-19
**Aikimox**, thanks, i will try this at home tonight.

**Atlas95**, i replaced in my nb100 the harddisk, from a 120 gb to a 320 gb. It was quite some work, but not impossible.
I found these steps on another forum, if you follow them carefully it is no problem to replace your hard disk:

1. Remove the battery, turn the unit over and press the power button for a few seconds to remove any residual power in the motherboard.

2. Turn the unit over and remove every screw you can see, there are 11 I think. There is also one under where the battery sits.

3. Turn the unit over and open up the screen, now prize up the cover where the power button is from either end.

4. There is one screw either side under this cover holding the keyboard down, remove them.

5. CAREFULLY lift up the keyboard from the top, under it you will see a ribbon cable in the lower centre, unclip the locking bar and gently pull out the ribbon from the motherboard. Now you will see the HDD on the left side under the cover, thats where you need to get.

6. Youll see in the lower right corner a small ribbon connector, for the touchpad, unclip and remove it gently.
There are two connectors in the centre with cables coming from the display, disconnect them and unhook the wiring.

7. Under an insulator strip at the top right of the motherboard there are two connectors for aerials, unclip them.

8. There are two screws, either side at the top holding the display, remove them and the display will be removeable.

9. Remove every screw you can find in the top cover of the lower half, and gently prise it from the underside, separating the two halves, if it wont separate, youve missed one, have a closer look.

10. You can now remove the two screws securing the HDD in (on the left of it) Unclip the HDD, turn it over and youll see four screws holding the HDD to the bracket, remove them, and refit the bracket to your new HDD.

11. Refitting is a complete reversal of removal, bearing in mind that some of the screws are different lenghts, you must replace them in their original positions.

---

### Post by atlas95 on 2009-02-19
@ Tuliku

Thanks for instructions ! BUT do you have the website with maybe somes pictures ?

I will try this tonigh, and maybe tomorrow i will by an HDD.

Do you know if I can change it by a SSD?

---

### Post by Tuliku on 2009-02-20
Hi, this is the place where i found those instructions:
[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=40112&tstart=0](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=40112&tstart=0)

No pictures there, and during my search didn't find anything else ten the above on the net.

Aboout changing it to a ssd, can't say. Never have seen on on the inside.
I assume there will be some special holder for it.
Would be cool if you could place a picture of the ssd holder ;-)

Good luck

BTW, the mic suggestion, does not work on my nb100 :-(

---

### Post by thanme on 2009-02-24
Hi Guys,

Got my NB100 last night, and had found this thread earlier in anticipation of getting Ubuntu on it first thing :D

So following the steps on page 4, I installed Ubuntu UNR from a USB stick with no dramas at all. Out of the box, everything seemed to work fine (as far as I can tell). I did have problems installing the payson package, but I went and installed the packages individually, and they all went on ok apart from the osd package. What does this actually do?
After reading other peoples problems, I have no idea about the fan, and I tested the webcam/mic with Skype and it works without any dramas.
Also, what app do people use for Bluetooth? As far as I can tell, it's installed and running, but I have no idea how to actually test it :P

Anyway, thanks a lot for the guide, and everyones input to this. It certainly made the whole process painless!

---

### Post by project_h20 on 2009-03-11
Hi ppl,

Does anyone here have problems with the display brightness resetting to full brightness on every reboot or whenever the display comes back on? Is there a fix to this?


Thanks
h20

---

### Post by pju123 on 2009-03-18
Kernel 2.6.27-11-generic stops the wired network connection working.

**You can get the wired network connection working again with the following from a terminal window**

sudo bash (enter your password when prompted)
cd /lib/modules/2.6.27-11-generic/kernel
mv net netx
depmod -a

reboot and when it comes back up the wired network now working properly.

Couldn't find that anywhere on google. I hopes that helps somebody.

---

### Post by xCannonballx on 2009-04-06
Hi everyone,

As several other people, I bought this laptop (the windows version) thinking of installing linux in it - the thing is, at least for now I wanted to keep windows as well, having both of them in dual boot. I installed Ubuntu 8.10, but it's been a real pain to try and get the wireless and some other stuff working, so I was wondering how I should do so that I could install the UNR without losing the windows installation - or even better, which is the easiest way to configure this without having to resort to a new installation of a OS at all.

---

### Post by sandman652001 on 2009-04-07
Your best bet is to install the Jaunty beta UNR it allows you to retain windows and dual boot, everything seems to work out of the box on my NB100

---

### Post by ubuntator on 2009-04-15
> **sandman652001 said:**
> Your best bet is to install the Jaunty beta UNR it allows you to retain windows and dual boot, everything seems to work out of the box on my NB100

I may confirm excellent result with Jaunty beta UNR on the NB100 in order to have a dual boot (XP e Ubuntu UNR) machine.
Comparing to EasyPeasy 1.0 I got big improvements: my microphone is working at last, I got also higher max sound emission and desktop-switcher and cheese work 'out the box'. 
Many thanks to Canonical and to the entire Ubuntu/Debian/Gnu/Linux community for these marvellous results.

PS microphone worked only during live session available by ubiquity but not after the hd install

---

### Post by sandman652001 on 2009-04-20
If anybody is interested in installing the lpia version of Jaunty UNR i created this guide
[http://ubuntuforums.org/showthread.php?p=7105900#post7105900](http://ubuntuforums.org/showthread.php?p=7105900#post7105900)

---

### Post by ville.peloton on 2009-05-07
> **Cryptonome said:**
> I do not recoment to install Ubuntu Intrepid, because you loose the cpu optimization and power management included in the lpa version of ubuntu remix based on 8.04-1....

I may confirm that you loose the CPU optimization with Ubuntu Intrepid, and the worse was that I could'nt get it back when I re-installed the original OS Hardy 8.04. My motherboard has been changed and now it works again !
I tried Ubuntu 9.04 Netbook Remix, and I still loose the CPU optimization. Is there anyone who could resolve this problem ?

---

### Post by sandman652001 on 2009-05-12
look here
> **sandman652001 said:**
> If anybody is interested in installing the lpia version of Jaunty UNR i created this guide
[http://ubuntuforums.org/showthread.php?p=7105900#post7105900](http://ubuntuforums.org/showthread.php?p=7105900#post7105900)

---

### Post by markosp on 2009-08-21
Hi!

I just want to share a few solutions in case someone meets the same problems as I did:

**Suspend/Hibernate didn't work after installing payson stuff**

I deleted the file /etc/pm/sleep.d/20toshiba or something similar

**To get powertop suggestions permanent for better power saving**

$sudo nano /etc/default/acpi-support
ENABLE_LAPTOP_MODE=true

then read /etc/laptop-mode/laptop-mode.conf and customize.

Then enable all the modules that you want to in /etc/laptop-mode/conf.d/ but at least:
_hal-polling_. *Change device to /dev/cdrom*
_intel-sata-powermgmt_

I hope someone finds these instructions usefull

---

### Post by project_h20 on 2009-12-08
Did anyone get the zoom and fan function keys working in Karmic?

---

### Post by Palko on 2009-12-11
I've just installed Ubuntu NB Remix 9.10 on my NB100. Everything is working really well. The only thing that doesn't work is the inbuilt Blue-tooth but that is ok because a Blue-tooth USB dongle works and I can live with that. :D

---

### Post by thanme on 2009-12-13
Yeah fan works good for me too.
Hibernate didn't seem to work out of the box, but I haven't really played with it yet.

---

### Post by xchip on 2010-01-04
this line wil fix your mic

amixer sset "Input Source" "Int DMic"

enjoy!!

---

### Post by Thameslink on 2010-01-06
Ha I spent ages messing about with this to no avail the i found | is mapped to <Alt-Gr>+` like it's supposed to be (UK Keyboard). I just couldn't see it tucked inbetween Esc and F1.

Still no bluetooth though.

---

### Post by Thameslink on 2010-01-07
Right after reinstalling Ubuntu from the supplied Toshiba disc, it is apparent that there is NO bluetooth device built into the nb100-11r all the bluetooth messages in dmesg must just be the bluetooth deamon starting up. 

Time to go shopping :)

---

### Post by Southernlights on 2010-07-29
If you have a NB100 with blue tooth built in, simply upgrade to 10.04 . To Get your bluetooth working after having installed just toogle the wireless key off so the wireless light turns off then toogle it back on again.  A bluetooth Icon will pop up at the top of the screen and your away :)  And with that going I think everything works in the NB100 works perfectly on 10.04 including the Mic :)

---

