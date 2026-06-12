---
title: "Ubuntu Netbook Remix Jaunty + Acer Aspire One D250"
date: 2009-04-28
forum: Hardware
---

### Post by suomaf on 2009-04-28
Hey everyone,

I recently bought a new Acer Aspire One D250. I downloaded the Ubuntu Netbook Remix Jaunty and I installed it. Everything seems to work right out of the box except for 3 things.

01. The ethernet does not seem to work
02. The wifi led does not seem to come on
03. The front mic also does not work

I have looked at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and they seem to be talking about a different model, I tried following the instructions but I am not getting any positive results.

Can anyone point me in the right direction? 

Cheers

Suomaf

---

### Post by suomaf on 2009-04-28
This is my lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

Would really  appreciate it if anyone can give me a clue on what to do next.

suo

---

### Post by suomaf on 2009-04-29
Hello All,

Another update, I swapped in my windows hardisk and found out that the ethernet card is Atheros AR8132 but under ubuntu it shows as 03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

Is there anyway to "blacklist the Attansic.." and manually add Atheros AR8132?

Cheers,

Suomaf

---

### Post by suomaf on 2009-04-29
Hey guys,

I was looking at this [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/341183](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/341183) and I found out that they added the support for my AR8132.

I am not sure on how to continue, Is there a kernel module I have to download, and after that how do i load the module?

Any help would be much appreciated. Thanks

Suo

---

### Post by suomaf on 2009-04-29
Anyone? Bueller?:(

---

### Post by suomaf on 2009-04-29
Ok I went over to [https://bugs.launchpad.net/ubuntu/+bug/363691](https://bugs.launchpad.net/ubuntu/+bug/363691) and I followed the instructions to head over to [http://partner.atheros.comDrivers.aspx](http://partner.atheros.comDrivers.aspx) to download the drivers for the ethernet card. There were 2 drivers to download there

AR813X-linux-v1.0.0.8.tar.gz  and ..
AR81Family-linux-v1.0.1.0.tar.gz 

not sure which one to get I got both and unzipped them and had a look, it seems that the AR813X was a little newer. So I went ahead and did a 

make in ./src

then a 

make install

I then went into the install directory using superuser

sudo su
cd /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e
insmod ./arl1e.ko

This seem to load it and then i did a 

ifconfig

then network manager picked up the eth0 card

Sweet 1 down and 2 more things to go..

Regarding the sound, when i plug in a mic, I can record, but I am not sure how to get the front mic going.

Also the LED for the wifi is still not working.. the instructions says to "load linux-backports-modules-jaunty" does this mean apt-get install linux-backports-modules-jaunty and then reboot?

Any help would be appreciated, cheers

Suo

---

### Post by ddrichardson on 2009-04-29
I wouldn't bother with the backport for the LED - it's not on constantly rather it flickers on TX/RX and it needs manually reloaded on resume. You also need to add some keys, let me know if you want to try it.

The front mic is a known issue and is being worked on - I can't see the bug number at the moment.

---

### Post by stchman on 2009-04-29
> **suomaf said:**
> This is my lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

Would really  appreciate it if anyone can give me a clue on what to do next.

suo

Everything should work OOB but wireless on that netbook usgin Jaunty.

To get the wireless to work do the following:

```
sudo apt-get install linux-backports-modules-jaunty 
```

Then enable the restricted driver in Hardware Drivers.  The LEDs even work.

---

### Post by stchman on 2009-04-29
> **suomaf said:**
> Hello All,

Another update, I swapped in my windows hardisk and found out that the ethernet card is Atheros AR8132 but under ubuntu it shows as 03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

Is there anyway to "blacklist the Attansic.." and manually add Atheros AR8132?

Cheers,

Suomaf

The Attansic(manufactured by Atheros) card is the WIRED ethernet, the Atheros is the WIRELESS ethernet card.

---

### Post by suomaf on 2009-04-29
Thanks Stchman,

Really appreciate the answer, lspci picked up the ethernet card as Attansic but on windows it actually is Atheros AR8132, but thats sorted out. Thanks for the tip on the WIRELESS card, I'll try it out.

Cheers

Suo

---

### Post by suomaf on 2009-04-29
Yeap just tried it, the madwifi driver did not work and the led still won't come on. I deactivated it and went back to the original drivers. Is there any other way?

Suo

---

### Post by suomaf on 2009-04-29
Hey ddrichardson,

Thanks for the reply. Could you point me in the right direction of getting the led lights to flicker? I would probably try it once just so I know how to do it and then leave it. 

Noted about the front mic, so I just have to carry a microphone around when I want to skype. All in all this netbook was relatively painless.

Thanks again for the reply, appreciate it.

Cheers

Suo

---

### Post by ddrichardson on 2009-04-30
[https://help.ubuntu.com/community/AspireOne110L#WLan%20LEDs/Switch](https://help.ubuntu.com/community/AspireOne110L#WLan%20LEDs/Switch)

---

### Post by suomaf on 2009-04-30
Hey ddRichardson,

Thanks very much for the link. Currently I am using the ath5k method, if I were to use madwifi , would you know if there is anything i need to blacklist? Because I did try to use madwifi before and wireless was not working so I swapped back to arth5k.

Thanks again for the help

suo

---

### Post by ddrichardson on 2009-04-30
There was a need to blacklist acer_wmi prior to Jaunty.

---

### Post by suomaf on 2009-05-01
Thanks ddRichardson I think I will pass off on the wifi led for now. Thanks for your help.

Suomaf

---

### Post by suomaf on 2009-05-09
Hey Putrid,

I think I had the same problem when i downloaded the AR813X-linux-v1.0.0.8.tar.gz driver. Try again. I eventually got one that was workable.

I did a gunzip first before i untarred it. I had the output of 

gzip: stdin: decompression OK, trailing garbage ignored

as well.

PM me your email and I will send the one i downloaded to you.

Cheers

Suo

```

sso@aspirenova:~/Downloads/linux-files/test$ ls
AR813X-linux-v1.0.0.8.tar.gz
sso@aspirenova:~/Downloads/linux-files/test$ gunzip AR813X-linux-v1.0.0.8.tar.gz 
sso@aspirenova:~/Downloads/linux-files/test$ tar xvf AR813X-linux-v1.0.0.8.tar 
sso@aspirenova:~/Downloads/linux-files/test$ cd src
sso@aspirenova:~/Downloads/linux-files/test/src$ make
sso@aspirenova:~/Downloads/linux-files/test/src$ sudo su
[sudo] password for sso: 
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# make install
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# cd /lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e/
root@aspirenova:/lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e# insmod ./arl1e.ko

and thats it it should make the network manager see the network card. I believe that you have to do this each time your kernel updates.. i am guessing until 2.6.30 where i believe this driver will then be supported.

```

---

### Post by putrid on 2009-05-09
> **suomaf said:**
> Hey Putrid,

I think I had the same problem when i downloaded the AR813X-linux-v1.0.0.8.tar.gz driver. Try again. I eventually got one that was workable.

I did a gunzip first before i untarred it. I had the output of 

gzip: stdin: decompression OK, trailing garbage ignored

as well.

PM me your email and I will send the one i downloaded to you.

Cheers

Suo

```

sso@aspirenova:~/Downloads/linux-files/test$ ls
AR813X-linux-v1.0.0.8.tar.gz
sso@aspirenova:~/Downloads/linux-files/test$ gunzip AR813X-linux-v1.0.0.8.tar.gz 
sso@aspirenova:~/Downloads/linux-files/test$ tar xvf AR813X-linux-v1.0.0.8.tar 
sso@aspirenova:~/Downloads/linux-files/test$ cd src
sso@aspirenova:~/Downloads/linux-files/test/src$ make
sso@aspirenova:~/Downloads/linux-files/test/src$ sudo su
[sudo] password for sso: 
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# make install
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# cd /lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e/
root@aspirenova:/lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e# insmod ./arl1e.ko

and thats it it should make the network manager see the network card. I believe that you have to do this each time your kernel updates.. i am guessing until 2.6.30 where i believe this driver will then be supported.

```

Thank you suomaf!! Now I can finally enjoy my Gb ethernet! Keep up the good work with the guides:)
[IMG]http://appleanimation.com/dance5.gif[/IMG]

---

### Post by suomaf on 2009-05-09
no worries man, if you get the front mic, wireless LED or sd card readers working.. remember to tell me how.. cheers

suo

---

### Post by suomaf on 2009-05-09
Hey DDRichardson,

Sorry to bother again, but do you know the bug report number for the front mic issue for the acer aspire one D250? I would really like to be able resolve the mic and not have to carry a microphone for a netbook around just to use skype.

Thanks for any help I can get.

---

### Post by ddrichardson on 2009-05-09
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620)

There's a solution posted too but YMMV:
> Check System->Preferences->Sound->Sound Capture is set to "HDA Intel ALC268 Analog(ALSA)" not "ALSA"

---

### Post by suomaf on 2009-05-09
Thanks I will check out the bugs number but the only way i had any relative success is to use the 2.6.30-rc4 kernel but there were problems with display that is not present in 2.6.28-generic kernel.

---

### Post by gastur on 2009-05-11
Downloaded fresh alsa-driver-1.0.20.tar.bz2 from alsa-project.org.

Bult it (./configure --with-cards=all).

**Built-in microphone works now!**

But suspend still effectively kills sound subsystem. options snd-hda-intel model=acer-aspire in /etc/modprobe.d/alsa-base.conf doesnt help.

---

### Post by electricshoes on 2009-05-21
Have you been able to get fan control to work on you D250? My fan runs max constantly, acerhdf does not detect the hardware and lm-sensors does not find it.

---

### Post by suomaf on 2009-05-23
Same here can't get anywhere with the fans

---

### Post by cparata on 2009-05-24
I solved the problem of led in wireless connection.
I installed madwifi driver madwifi-hal-0.10.5.6-r4016-20090429.tar.gz from this link:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

I followed all the steps explained here to install madwifi driver with the patches for led:
[https://help.ubuntu.com/community/AspireOne110L#WLan%20LEDs/Switch](https://help.ubuntu.com/community/AspireOne110L#WLan%20LEDs/Switch)

and then I added ath5k in the blacklist.
In particular I replaced the file /etc/modprobe.d/blacklist-ath_pci.conf with a new file called /etc/modprobe.d/blacklist-ath5k.conf and with these lines of code:

# Load madwifi driver instead ath5k 

blacklist ath5k

):P

---

### Post by sc0g on 2009-05-24
I can confirm that the built-in microphone does not work on the Aspire One D150 either. Allegedly, there is a fellow that installed the linux-image-2.6.30 kernel and claims that it is working... However I am not going to do this since it is not a stable release yet.

---

### Post by cparata on 2009-05-25
[FONT=Times New Roman][SIZE=2]I was able to get working the front mic after suspend/resume process but I still have problems after standby/resume process.
I just installed hda-intel driver of alsa (this takes less time than compile all cards driver).
So I downloaded alsa-driver-1.0.20.tar.bz2 from 

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

I unzipped the package, I entered into the main directory of the package and then I typed:

[/SIZE][/FONT][I][I]sudo apt-get install build-essential ncurses-dev
[/I][/I][I][I]./configure --with-cards=hda-intel
[/I][/I][I][I]make
[/I][/I][I][I]sudo make install

[/I][/I][FONT=Times New Roman][SIZE=2]The[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]n I edited /etc/modprobe.d/alsa-base.conf and I added at the end of file the line:
*options snd-hda-intel model=acer-aspire*

After the reboot I adjusted the audio preferences in this way:

Device: HDA Intel (Alsa mixer)
Preferences: The first 3 items and last 2 items (Front Mic is disabled!!!)
Input Sources is set as default at Mic (not Front Mic!!!).

Finally check that [/SIZE][/FONT][FONT=Times New Roman][SIZE=2]**System->Preferences->Sound->Sound Capture** is set to "**HDA Intel ALC272 Analog(ALSA)**" not "**ALSA**"

I hope this can be useful.

Cheers
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]

[/SIZE][/FONT]

---

### Post by cparata on 2009-05-26
To try solving the problem of standby/resume process,  I found this post:
[http://ubuntuforums.org/showthread.php?t=426081](http://ubuntuforums.org/showthread.php?t=426081)

Now I have not time to try.
But we could try to edit /etc/default/acpi-support and replace

MODULES=""

with

MODULES="snd_hda_intel"

I'll try this patch this evening and I will let you know.

Cheers

---

### Post by suomaf on 2009-05-26
So far the tally on the D250 with UNR Jaunty is

Webcam works out of box
wireless work out of box no LED if need LED use madwifi drivers
sound work out of box not internal mic
internal mic works with a compile of new alsa driver and small patch
function keys work out of box
Bluetooth work out of box (I can send stuff to my nokia, I cannot receive but not something I cannot live without)
Ethernet works with installed driver
External Display have not tested.

I guess the last thing on my list is that CPU fan that is draining the battery.

Thanks to all the D250 owners, really appreciate it.

Suo

---

### Post by suomaf on 2009-05-26
Hey cparata,

I was not able to get the led's working for my machine, is yours a D250? is there anything i can check?

Suo

---

### Post by cparata on 2009-05-26
Yes, I have a AA1 D250.
I got the led working following all the instructions of madwifi method installation you can find here:

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

with also these tricks explained in the link above:

1) Add **ath_hal** to the **DISABLED_MODULES=** stanza in **/etc/default/linux-restricted-modules-common** (i.e. 'DISABLED_MODULES="ath_hal"')  
 
2) suspend/resume with madwifi 

If you want to suspend and resume and have your wifi working you will need the following script: 

# Adapted from AbtZ on [http://ubuntuforums.com/showthread.php?p=5564900](http://ubuntuforums.com/showthread.php?p=5564900)
# Enable wireless after a suspend/hibernate
# For my Acer Aspire One running Ubuntu Intrepid and Madwifi (madwifi-hal-0.10.5.6-r3879-20081204)
# This needs to be executable (chmod +x) and placed in the /etc/pm/sleep.d/ folder
case $1 in
    # We go into hibernate
    hibernate)
    ;;
    # We go into suspend
    suspend)
    ;;
    # We come out of hibernate
    thaw)
        /sbin/ifconfig wifi0 up
    ;;
    # We come out of standby
    resume)
        /sbin/ifconfig wifi0 up
    ;;
    # catch all
    *)
    ;;
esac

Save this file as **/etc/pm/sleep.d/10-wifi** and run **sudo chmod +x /etc/pm/sleep.d/10-wifi**

3) Wlan/LEDs Switch

WLAN can be turned off with the switch on the front side of the Aspire One, although you don't get a visual notification in the GUI. The Wireless LEDs DO work, with the addition of these lines to **/etc/rc.local** 

# Make wifi lights blink
sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1Make sure those lines appear before **exit 0**. 

I installed the last available version in the madwifi snapshot: [madwifi-hal-0.10.5.6-r4016-20090429.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4016-20090429.tar.gz").

Finally, I replaced the file /etc/modprobe.d/blacklist-ath_pci.conf with a new file called /etc/modprobe.d/blacklist-ath5k.conf and with these 2 lines of code:

# Load madwifi driver instead ath5k 

blacklist ath5k

Let me know if it works for you. For me it worked.

Cheers

---

### Post by cparata on 2009-05-27
I tested the fix for audio problems after suspend/resume. It  did not work for me. Audio problems persist after resume.

---

### Post by suomaf on 2009-05-28
Thanks apprecaite the answer, Will test it out tonight

---

### Post by cparata on 2009-05-28
After last update of acpid package, I got audio working after suspend/resume without any tricks. It needs to install only last version of alsa-driver. Great!!!

Cheers.

---

### Post by mustatommi on 2009-06-17
I'm a full noob, and as long as i didn't make it to do anything you wrote, i guess i should wait the update version (hoping they'll pop out soon) to have wifi, wifi led, mic, etc working properly
about the fans i found this that is used on a distro made for aspire (linux4one)
[http://piie.net/index.php?section=acerhdf](http://piie.net/index.php?section=acerhdf)

maybe you can make it work...

btw you can find the Linux4One distro here
[http://www.linux4one.it/index.php?pid=1#inglese](http://www.linux4one.it/index.php?pid=1#inglese)

hope that someone of you will make something i can just click and make it work...
cheers!

---

### Post by Oreo on 2009-06-23
What happens when I upgrade to a new kernal?

Upgrading to /2.6.28-13-generic caused me to lose my Ethernet again.

When I tried to follow the instructions for compiling the driver using sudo in your thread, I now get:

....stuff/AR813X Ethernet Driver/src$ sudo make install

make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/oreo/stuff/AR813X Ethernet Driver/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** No rule to make target `Ethernet'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

Do I need to download a new version of the driver? Or have I just forgotten something easy?

---

### Post by cparata on 2009-06-25
You have to just recompile all the package.
After have loaded the new kernel,  try to type:

# make clean
# make
# sudo make install

If make clean does not work try with make distclean.

Cheers,

Carlo

---

### Post by utonto on 2009-07-09
hi guys i really need your help please...
i have an aspire one with netbook remix installed.
i have tried to use skype but my external microphone (using the jack) did not work. i have tried to fix the problem editing the settings of the mixer. nothing worked... 
the thing is that i have seen a lot of pleople writing post in which they claim that the external microphone works well by default.
so i think that maybe it is my fault because i altered the correct settings.
i just want to use skype using my external microphone and headset... what are the correct settings of the pc/skype ? is there someone who could help me in a simple way?
thanks in advance

---

### Post by flattop1 on 2009-07-09
> **cparata said:**
> [FONT=Times New Roman][SIZE=2]

After the reboot I adjusted the audio preferences in this way:

Device: HDA Intel (Alsa mixer)
Preferences: The first 3 items and last 2 items (Front Mic is disabled!!!)
Input Sources is set as default at Mic (not Front Mic!!!).

Finally check that [/SIZE][/FONT][FONT=Times New Roman][SIZE=2]**System->Preferences->Sound->Sound Capture** is set to "**HDA Intel ALC272 Analog(ALSA)**" not "**ALSA**"



[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]

[/SIZE][/FONT]

I have the exact same problem with my D250 although luckily my wireless worked out of the box..The only problem I have is the mic..

I compiled the latest alsa driver and edited the /etc/modprobe.d/alsa-base.conf file....
But cant for the life of me find where to change" front mic" to "mic".
Can you help me out as to where this setting is?

---

### Post by cparata on 2009-07-10
The audio preferences should be in the system settings.
Now I don't have the precise path because I don't have my AAO D250 here with me.
The input instead should be set from audio icon on the panel. Push right button on the audio icon and then set all the values. Check also if mic volume is enable.

Cheers.

---

### Post by utonto on 2009-07-10
i'm not able to read your private messages :(
i always receive my previous message quoted

---

### Post by flattop1 on 2009-07-10
> **cparata said:**
> The audio preferences should be in the system settings.
Now I don't have the precise path because I don't have my AAO D250 here with me.
The input instead should be set from audio icon on the panel. Push right button on the audio icon and then set all the values. Check also if mic volume is enable.

Cheers.

Thanks for the reply cparata

Thats where I've been looking..But to no avail..I'd appreciate it if you would get back to me with the precise path when you have your computer.
Its driving me nuts.

---

### Post by LewRockwell on 2009-07-10
Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

---

### Post by flattop1 on 2009-07-10
bump..

---

### Post by flattop1 on 2009-07-11
> **LewRockwell said:**
> Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

Well good for you...But does your mic work?

---

### Post by suomaf on 2009-07-12
My mic works both for external and internal after compiling the latest alsa drivers. I just followed the very clear instructions layed out in this thread. 

Suo

---

### Post by jpmeijers on 2009-07-12
I had problems getting the Atheros Ethernet working on my Aspire D250 as Atheros' new driver version 1.0.0.9 do not want to compile. I managed to find the old 1.0.0.8 version somewhere on the internet and mirrored it at [http://web.ee.sun.ac.za/~15312704/linux/AR813X-linux-v1.0.0.8.tar](http://web.ee.sun.ac.za/~15312704/linux/AR813X-linux-v1.0.0.8.tar)

This one does compile and work for me.

---

### Post by flattop1 on 2009-07-12
> **suomaf said:**
> My mic works both for external and internal after compiling the latest alsa drivers. I just followed the very clear instructions layed out in this thread. 

Suo



I compiled the latest alsa driver as layed out in this thread but had been messing around with sound settings prior to finding this thread so as a result I need to tweak my settings to get it working.I've tried all sorts of stuff but cant get it working.
I can tell the internal mic is actually working now but it only records a hissing sound.

So basically I'm looking for someone to share their alsa/sound settings that work for them..
Everyone says change "front mic" to "mic" but
I can find no reference to "mic" in my sound settings...only "front mic" and "front mic boost"..??Help would be greatly appreciated.

---

### Post by cparata on 2009-07-13
flattop1,
I think you have not selected the right audio settings.
Go to Preferences item of the main menu list. Then go to Audio item.
Now check only the first 3 items and the last 2 items of the Preferences in the audio settings (I think that front mic and front mic boost should be unchecked).

Cheers

---

### Post by suomaf on 2009-07-13
Does this help? I can take screenshot of all the other settings if you need?

cheers
suo

---

### Post by flattop1 on 2009-07-13
> **suomaf said:**
> Does this help? I can take screenshot of all the other settings if you need?

cheers
suo

Yeah that helps alot suomaf...It lets me know I waslooking in the right place !!!,but for some reason the "mic" option is not there on my computer??
Does anyone know why that might be?

---

### Post by suomaf on 2009-07-13
Before I compiled the new alsa drivers, I was not able to select the mic, but after i compiled the alsa drivers the mic/front mic option showed up. Perhaps you can try to recompile the alsa drivers and show us the output here?

Suo

---

### Post by cparata on 2009-07-14
I think that flattop1 have not checked the right audio preferences.
I don't have my AAO D250 here to show a snapshot of my audio settings.
Suomaf could you show to flattop1 also a snapshot of audio settings you can find in the Preferences menu? If I well remember, it needs to check "Capture" item and not "Front Mic" item in the Preferences. Could you confirm that?
If nobody can show the snapshot of audio settings, tomorrow I show the mine.

---

### Post by suomaf on 2009-07-14
These are the screenshots might take a more than 1 post.. bear with me

This is from preferences - audio

Suo

---

### Post by suomaf on 2009-07-14
these are the ones from volume control on the top right corner

---

### Post by flattop1 on 2009-07-15
> **suomaf said:**
> these are the ones from volume control on the top right corner

THanks Suomaf....Thats exactly what I was looking for.

Its hard to beat screenshots for clarity!
I re-compiled alsa and followed your screehshots and the mic option is now available...Now I'm going to test it with a Skype call.

---

### Post by suomaf on 2009-07-16
sweet! enjoy your D250 and NBR, it is a good mix and does everything i need to do on the move

suo

---

### Post by sc0g on 2009-07-16
I followed the routine instructions on compiling the latest alsa drivers, yet the internal mic still does not work.

**Is this because I am still using Kernel 2.6.28-13-generic? I'm thinking the answer is yes... ** :( 

My procedure:
[i]
su -
apt-get install build-essential
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
tar xvjf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
./configure --with-driver=hda-intel
make
make install
echo "options snd-hda-intel model=acer-aspire" >> /etc/modprobe.d/alsa-base.conf
[/i](REBOOT)
(MADE ALL CHANGES IN SETTINGS ACCORDING TO SCREENSHOTS ABOVE)

Still no worky :( I fail

---

### Post by cparata on 2009-07-17
Very strange...
However I don't have the same audio settings of suomaf and my internal mic anyway works perfectly. Actually I don't use pulseaudio in the audio preferences but only alsa HDA-Intel audio device. You could try with my audio settings, but at the moment I'm not able to post the screenshots of my audio preferences. I'll try to post them next week.

Cheers

---

### Post by alexwd on 2009-07-17
Dear All,
A question from a complete newbie to Ubuntu...
I installed Ubuntu NBR on my Acer Aspire one D250 but once the fan turns on it just continues running (draining the battery). Is there an easy fix for this yet?
Many thanks in advance for any help!

---

### Post by suomaf on 2009-07-17
Hey Sc0g,

When you said it failed, do you mean the compile failed? Were you able to see the mic/front mic ?

Suo

Hey Alex, 

I dont know that there is anything that will "fix" the fan for D250. I am not too sure but I have tried to plug in my win xp hardisk and it seems to behave the same way in that it does not switch off. Can anyone else confirm this?

---

### Post by cparata on 2009-07-17
Yes, I can confirm that. I have noticed that fan control performances are more or less the same in Windows XP and Ubuntu 9.04.

---

### Post by sc0g on 2009-07-17
> **suomaf said:**
> When you said it failed, do you mean the compile failed? Were you able to see the mic/front mic ?


By failed, I am talking about the results of actually recording audio, or people hearing me in Skype. There were no errors during the whole process, everything compiled and installed correctly. Its just that the mic doesn't pick up any sound. :confused:

**My audio settings are identical to suomaf's screen shots. You don't think this has to do with my kernel version (2.6.28-13-generic)?**

Cparata, I would greatly appreciate seeing how your settings are configured! :D

---

### Post by asolbap on 2009-07-17
Hey guys,

I've just installed the UNR Jaunty, and I think that my wifi switch is not working (the wifi led neither, as usual), is this normal?

Thank you so much.

---

### Post by cparata on 2009-07-18
scOg, these are my audio settings (excuse me but they are in italian).
These are the first 5 screenshots.

[ATTACH]121467[/ATTACH]

[ATTACH]121468[/ATTACH]

[ATTACH]121469[/ATTACH]

[ATTACH]121470[/ATTACH]

[ATTACH]121471[/ATTACH]

---

### Post by cparata on 2009-07-18
And these are the last 3 screenshots.

I hope to have helped you.

Cheers

[ATTACH]121472[/ATTACH]

[ATTACH]121473[/ATTACH]

[ATTACH]121474[/ATTACH]

---

### Post by rhk on 2009-07-21
Hi there!

My sister gota D250.. planning to install UNR/Jaunty:

Have I understood correctly that the following don't work ootb:
-internal mic (but external works)
-ethernet
-wlan light
-fan speed control

To make internal mic work, one needs to recompile alsa drivers - or use external mics.Any ideas how to make the alsa drivers work also in the case of kernel update? The laptop will travel to other continent, I'd like it to work smoothly :)

Etherned requires some hacking of the drivers?

Wlan light.. don't really care (except that wlan can't be turned off?)


Thanks!


(if external mic works and I'm able to fight ethernet to work, I think I'll just leave it, maybe a future upgrade will fix the audio stuff later, maybe also the wlan light..)

---

### Post by cparata on 2009-07-21
After every kernel update, you generally must recompile all driver you compiled at the beginning (ethernet, alsa and eventually madwifi).

---

### Post by sc0g on 2009-07-22
> **cparata said:**
> And these are the last 3 screenshots.

I hope to have helped you.

Cheers

[ATTACH]121472[/ATTACH]

[ATTACH]121473[/ATTACH]

[ATTACH]121474[/ATTACH]

That was the last piece I was missing. I had the wrong 'Capture Device' selected; once I changed it to ALSA Mixer, the mic started cooperating.

Thanks for all your help.

---

### Post by Oreo on 2009-07-22
Is anyone else having trouble with WiFi or Ethernet with the newer 2.6.28-13 kernal?
I lost my Ethernet with the kernal update. I still have it if I use the *28-11 kernal.  
If I use 28-13, I did have my WiFi, but it's broken now. It can see networks, but fails to connect. This only recently happened. I tried recompiling madwifi, but still have something wrong. What am I forgetting?
Or, since it sees networks, is it broken in another way?
Do I need to blacklist something?

**Ethernet: **

The old download location link doesn't work. The link to the Bug site and the link there to Atheros works:
[http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx")

But the 813X file refuses to unzip:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

Should I try the older AR81 instead?

---

### Post by cparata on 2009-07-23
Oreo, for ethernet driver try to uncompress it with this command:

tar zxvf <file_name>

For WiFi, I use madwifi driver and everything works fine. After every kernel update I recompile the driver. If you want to use madwifi you should follow the steps explained in this thread some posts above. 

I suggest you save the source code of the drivers (ethernet, alsa, madwifi) in a folder of your pc, so when there is a kernel update you can recompile them. It takes about 5 minutes.

Cheers

---

### Post by Oreo on 2009-07-25
My Ethernet is back and working. Thanks for your help!

_BUT I am still having problems with madwifi._ It was working with the newest kernel until four days ago. I don't know why it would have stopped. At the time I was experiencing trouble with our wireless router. The newest kernal was installed on my system on July 2. I don't remember, but I probably recompiled the driver on that day and it worked. 

[new comment: I think my problem may come from interference with having followed another thread on the Acer One, probably the earlier model, not the 250 which I have now.]

So July 24-25, I went back and read the whole 7 pages of this thread, and made text notes I could use if I didn't have an Internet connection. I followed the instructions on p4.
1. I added ath_hal to DISABLED_MODULES.
2. I installed the resume script.
3. I installed the lines in rc.local to make the wifi light to blink. _So far I haven't seen the LED light come on._
4. I installed madwifi-hal.....20090429.tar.gz.
5. And here may be the problem: The instructions say to _replace_ blacklist-ath_pci.conf with ...blacklist-ath5k.conf. I renamed the file instead of replacing it. I commented out the one line [without reading it!] that was [supposed to be] blacklisting ath_pci. I added the two lines given (one commented out) and the other to blacklist ath5k. And saved the file. [Now I discover that the line I commented out was also blacklisting ath5k. It must be some other instruction list just says to change this line.]

When I tried to activate madwifi from Hardware drivers, it complained that I had removed blacklist-ath_pci.conf. I believe at this point I rebooted and tried to activate madwifi again. Madwifi refused to be activated. I would click on the button, it would ask my password, but would never change the left icon to the activated state. So I changed the name back to blacklist-ath_pci.conf, which still has blacklist ath5k. 

Here's my symptoms now:  If I have madwifi activated, Ubuntu acts as if I didn't have a wireless card at all. Nothing appears in Network Manager. The Hardware Drivers screen says madwifi is activated "but not in use." Each time I have tried something new that didn't work, I have tried the wifi switch on the front. (If the switch was the off, would the wireless start without having to reboot?) If I deactivate madwifi in Hardware Drivers and reboot, I can see wireless networks but can't connect.

I've tried recompiling the driver. I think one of my earlier problems was that the driver won't compile if I have introduced spaces in the name of the folder. This time "make" seems to end correctly, but after "sudo make install," I get this error message:
[INDENT]man -c -P'cat > /dev/null' atl1e || true
man: 
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.[/INDENT]
However the atl1e.ko driver was written afresh to /lib/modules.../atl1e.



What have I done wrong?

---

### Post by Gas-one on 2009-07-26
Hi all.

With the new ethernet driver you have to add to /etc/modules file the line:

atl1e

try it!

---

### Post by pugopugo on 2009-07-27
I am running Ubuntu on an D250 with the Atom N280 processor. I have issues with the speedstep functionality and the detected maximum CPU speed. Linux only seems to detect 1.33 GHz as maximum speed, not 1.66 GHz as it should be. 

When I run [FONT="Courier New"]cpufreq-info[/FONT] I get: 
[FONT="Courier New"]available frequency steps: 1.33 GHz, 1.07 GHz, 800 MHz[/FONT]

This problem seems to be new with the N280 CPU and is discussed some on other sites, but there seems to be no solution available at this point.

Do other D250 owners here have this problem? Have anyone heard of any solution?

---

### Post by Oreo on 2009-07-27
Thanks! I'm glad you noticed my reply.

I added that in /etc/modules. My file now has two active lines:
[INDENT]lp
atl1e[/INDENT]

When I booted up with that change this morning, Network Manager is still not recognizing any Wifi networks. Under Hardward Drivers madwifi is still activated. It talks about the free "ath5k" instead of atl1e. I suppose that is OK, right?
The file installed under /lib/modules.... says atl1e.ko. (That is in the atl1e folder.)

If I do not activate madwifi under Network Manager, my D250 will still see networks but can't connect.
PROBLEM NOT YET SOLVED.

[edit: My processor is the N270 and I am showing cpufreq stats as 1.60 GHz, 1.33, etc.]

---

### Post by cparata on 2009-07-28
Oreo, if you already used madwifi before kernel update, you should already have the right configuration of the madwifi driver.

So after any kernel update you should just do:

tar zxvf madwifi-hal.....20090429.tar.gz
cd madwifi-hal.....20090429/
make
sudo make install

and reboot your netbook.

Probably with the new ethernet driver you have a conflict with the network interfaces. Try to temporarily get the ethernet interface down and then try to type:

modprobe ath_pci

in order to check if madwifi works correctly.
However I use the old ethernet driver and the madwifi driver and everything looks working fine.

Cheers

---

### Post by greenfrog on 2009-07-28
Upgrade to kernel 2.6.30.-2-generic 

It fixed all my problems with my Aspire One D150

Mic and Wifi leds work with no problem.

---

### Post by bluerags on 2009-07-29
this also worked on my eeepc 1101. thanks!

---

### Post by irober02 on 2009-07-31
Within a week after having improved the performance of my original AAO (Ubuntu 9.04 NBR) by adding RAM and moving /home (for Firefox caching), /tmp & /var/log to my left-hand SSD due to the poor performance of the motherboard-mounted solid state storage I found my AAO experience seriously degraded after putting a chair leg on the unit. :-(

Note to self: don't leave little computers on the floor.

So, now I have new AAO but had to buy a D250: larger screen (same resolution); real, spinning HD, etc & I have a spare battery (battery from old AAO works).

In many respects this unit is much superior but there are a few annoying things. As reported elsewhere the ethernet device was not functioning out of the box. I had to download and compile the AR813x to get it working. Fortunately the WiFi *did* work out of the box so I could download the necessary sources.

Because of a WiFi problem at work, I need to use up-to-date madwifi drivers too and haven't succeeded in protecting these installs across kernel upgrades.

I do find an unexpected interaction between the two drivers and seem to need to compile and install the ethernet drivers first and *then* the wifi drivers if I want both to work. I haven't investigated any further.

I find I can't use the fancy display modes. I suspect I need a better graphics driver but it's not a priority for me.

I do have a persistent problem remaining. If I leave my AAO D250 unused for several hours I find that it's hung and I need to hard reboot it. The first hint of trouble in the syslog appears to be as follows.

Any suggestions?

bye

ian

Aug  1 00:32:21 tiddlywinks kernel: [ 8422.725097] ACPI: EC: missing confirmations, switch off interrupt mode.
Aug  1 00:32:22 tiddlywinks kernel: [ 8423.224085] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
Aug  1 00:32:22 tiddlywinks kernel: [ 8423.225149] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.LPC_.BAT0._BST] (Node f6c16f18), AE_TIME
Aug  1 00:32:22 tiddlywinks kernel: [ 8423.225302] ACPI Exception (battery-0359): AE_TIME, Evaluating _BST [20080926]
Aug  1 00:40:02 tiddlywinks /USR/SBIN/CRON[18974]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  1 00:47:23 tiddlywinks NetworkManager: <info>  (ath0): supplicant connection state:  completed -> group handshake 
Aug  1 00:47:23 tiddlywinks NetworkManager: <info>  (ath0): supplicant connection state:  group handshake -> completed 
Aug  1 00:47:23 tiddlywinks NetworkManager: <info>  (ath0): supplicant connection state:  completed -> group handshake 
Aug  1 00:47:23 tiddlywinks NetworkManager: <info>  (ath0): supplicant connection state:  group handshake -> completed 
Aug  1 00:50:02 tiddlywinks /USR/SBIN/CRON[6159]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  1 01:00:02 tiddlywinks /USR/SBIN/CRON[25723]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug  1 01:00:02 tiddlywinks /USR/SBIN/CRON[25722]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  1 01:01:25 tiddlywinks kernel: [10161.653347] lid.sh invoked oom-killer: gfp_mask=0x80d0, order=0, oomkilladj=0
Aug  1 01:01:26 tiddlywinks kernel: [10161.653359] Pid: 32336, comm: lid.sh Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug  1 01:01:26 tiddlywinks kernel: [10161.653366] Call Trace:
Aug  1 01:01:26 tiddlywinks kernel: [10161.653381]  [<c04fde46>] ? printk+0x18/0x1a
Aug  1 01:01:26 tiddlywinks kernel: [10161.653392]  [<c01916b5>] oom_kill_process+0x75/0x210
Aug  1 01:01:26 tiddlywinks kernel: [10161.653400]  [<c0191d93>] ? select_bad_process+0xc3/0x100
Aug  1 01:01:27 tiddlywinks kernel: [10161.653408]  [<c0191e72>] out_of_memory+0xa2/0x140
Aug  1 01:01:27 tiddlywinks kernel: [10161.653416]  [<c01944e0>] __alloc_pages_internal+0x450/0x490
Aug  1 01:01:27 tiddlywinks kernel: [10161.653425]  [<c0194571>] __get_free_pages+0x21/0x40
Aug  1 01:01:27 tiddlywinks kernel: [10161.653433]  [<c01265fd>] pgd_alloc+0x1d/0xe0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653440]  [<c0500078>] ? _spin_lock+0x8/0x10
Aug  1 01:01:27 tiddlywinks kernel: [10161.653448]  [<c01d1dd6>] ? dup_fd+0x1d6/0x330
Aug  1 01:01:27 tiddlywinks kernel: [10161.653456]  [<c0137c1e>] mm_init+0xae/0xf0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653463]  [<c01383e9>] dup_mm+0x79/0xf0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653471]  [<c0138b32>] copy_process+0x6a2/0xcf0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653478]  [<c01391e2>] do_fork+0x62/0x300
Aug  1 01:01:27 tiddlywinks kernel: [10161.653487]  [<c02cde06>] ? copy_to_user+0x36/0x120
Aug  1 01:01:27 tiddlywinks kernel: [10161.653495]  [<c01023e3>] sys_clone+0x33/0x40
Aug  1 01:01:27 tiddlywinks kernel: [10161.653503]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
Aug  1 01:01:27 tiddlywinks kernel: [10161.653508] Mem-Info:
Aug  1 01:01:27 tiddlywinks kernel: [10161.653512] DMA per-cpu:
Aug  1 01:01:27 tiddlywinks kernel: [10161.653517] CPU    0: hi:    0, btch:   1 usd:   0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653522] CPU    1: hi:    0, btch:   1 usd:   0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653527] Normal per-cpu:
Aug  1 01:01:27 tiddlywinks kernel: [10161.653532] CPU    0: hi:  186, btch:  31 usd: 132
Aug  1 01:01:27 tiddlywinks kernel: [10161.653537] CPU    1: hi:  186, btch:  31 usd: 156
Aug  1 01:01:27 tiddlywinks kernel: [10161.653541] HighMem per-cpu:
Aug  1 01:01:27 tiddlywinks kernel: [10161.653546] CPU    0: hi:   42, btch:   7 usd:  10
Aug  1 01:01:27 tiddlywinks kernel: [10161.653551] CPU    1: hi:   42, btch:   7 usd:  13
Aug  1 01:01:27 tiddlywinks kernel: [10161.653560] Active_anon:12538 active_file:1902 inactive_anon:12941
Aug  1 01:01:27 tiddlywinks kernel: [10161.653563]  inactive_file:9068 unevictable:2 dirty:0 writeback:0 unstable:0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653567]  free:7608 slab:202882 mapped:6498 pagetables:644 bounce:0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653577] DMA free:3504kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15764kB pages_scanned:0 all_unreclaimable? yes
Aug  1 01:01:27 tiddlywinks kernel: [10161.653586] lowmem_reserve[]: 0 861 990 990
Aug  1 01:01:27 tiddlywinks kernel: [10161.653600] Normal free:3744kB min:3720kB low:4648kB high:5580kB active_anon:20468kB inactive_anon:20852kB active_file:8kB inactive_file:160kB unevictable:0kB present:881880kB pages_scanned:18912 all_unreclaimable? no
Aug  1 01:01:27 tiddlywinks kernel: [10161.653610] lowmem_reserve[]: 0 0 1034 1034
Aug  1 01:01:27 tiddlywinks kernel: [10161.653623] HighMem free:23184kB min:128kB low:264kB high:404kB active_anon:29684kB inactive_anon:30912kB active_file:7600kB inactive_file:36112kB unevictable:8kB present:132416kB pages_scanned:0 all_unreclaimable? no
Aug  1 01:01:27 tiddlywinks kernel: [10161.653633] lowmem_reserve[]: 0 0 0 0
Aug  1 01:01:27 tiddlywinks kernel: [10161.653641] DMA: 0*4kB 0*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3504kB
Aug  1 01:01:27 tiddlywinks kernel: [10161.653663] Normal: 26*4kB 3*8kB 0*16kB 3*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3744kB
Aug  1 01:01:27 tiddlywinks kernel: [10161.653685] HighMem: 458*4kB 1259*8kB 311*16kB 85*32kB 40*64kB 8*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 23184kB
Aug  1 01:01:27 tiddlywinks kernel: [10161.653707] 27697 total pagecache pages
Aug  1 01:01:27 tiddlywinks kernel: [10161.653712] 7936 pages in swap cache
Aug  1 01:01:27 tiddlywinks kernel: [10161.653717] Swap cache stats: add 53898, delete 45962, find 37394/38771
Aug  1 01:01:27 tiddlywinks kernel: [10161.653722] Free swap  = 2795472kB
Aug  1 01:01:27 tiddlywinks kernel: [10161.653726] Total swap = 2971984kB
Aug  1 01:01:27 tiddlywinks kernel: [10161.664038] 259840 pages RAM
Aug  1 01:01:27 tiddlywinks kernel: [10161.664046] 33538 pages HighMem
Aug  1 01:01:27 tiddlywinks kernel: [10161.664052] 5613 pages reserved
Aug  1 01:01:27 tiddlywinks kernel: [10161.664057] 57296 pages shared
Aug  1 01:01:27 tiddlywinks kernel: [10161.664062] 220490 pages non-shared
Aug  1 01:01:27 tiddlywinks kernel: [10161.664072] Out of memory: kill process 2966 (x-session-manag) score 75994 or a child
Aug  1 01:01:27 tiddlywinks kernel: [10161.664141] Killed process 3091 (ssh-agent)
Aug  1 01:01:27 tiddlywinks kernel: [10162.477432] lid.sh invoked oom-killer: gfp_mask=0x80d0, order=0, oomkilladj=0

---

### Post by Oreo on 2009-08-02
[INDENT]
«I do find an unexpected interaction between the two drivers and seem to need to compile and install the ethernet drivers first and *then* the wifi drivers if I want both to work. I haven't investigated any further.»[/INDENT]

So maybe this is my problem. I am not sure what order I have done these, but the last time, I think I stated with the Ethernet.

I upgraded to the new 28-14 generic driver this week.

I suspect that I may just have a broken wireless card. Please someone answer these questions:
1) I don't remember anyone saying in the thread that they activated Madwifi in System > Administration > Hardware Drivers. Is that necessary after one compiles the driver? 
2) Does it make any difference if the driver is activated when one compiles the driver?
3) When I do NOT have madwifi activated in Hardware Drivers, I can see wireless networks but not connect. Is that normal? Having compiled the driver, once I  activate madwifi in Hardware Drivers, I see no wireless networks at all.

And Cparata, you said «Probably with the new ethernet driver you have a conflict with the network interfaces. Try to temporarily get the ethernet interface down and then try to type:   modprobe ath_pci »
4) How do I temporarily turn off the Ethernet and keep the wireless active?

---

### Post by cparata on 2009-08-03
Oreo, if you type on the shell:

sudo ifconfig

you can see all the network interfaces active on your netbook.
Now if you type:

sudo ifconfig <interface> down

you can get down whatever interface you want.
On my netbook, ethernet interface is marked as eth0. So in order to get down ethernet interface I type:

sudo ifconfig eth0 down

Cheers

---

### Post by Tokomitsu on 2009-08-03
> **jpmeijers said:**
> I had problems getting the Atheros Ethernet working on my Aspire D250 as Atheros' new driver version 1.0.0.9 do not want to compile. I managed to find the old 1.0.0.8 version somewhere on the internet and mirrored it at [http://web.ee.sun.ac.za/~15312704/linux/AR813X-linux-v1.0.0.8.tar](http://web.ee.sun.ac.za/~15312704/linux/AR813X-linux-v1.0.0.8.tar)

This one does compile and work for me.

suo, I am very sorry.I am so tired that I didn't look serious for the 1.0.0.8
Now I find it in the posts.

---

### Post by Tokomitsu on 2009-08-03
Don't care that, plug the lan, I got it.

---

### Post by Tokomitsu on 2009-08-04
when i reboot,:( lan lost anyway

---

### Post by Tokomitsu on 2009-08-04
OK I know it.When you finish the make install.
you find the folder atl1e /lib/modules/2.6.28-11-generic/kernel/drivers/net/
cd /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e
and insmod atl1e.ko
pm: I am using ubuntu netbook remix
if you are using other system, read the ReadMe first.

---

### Post by Tokomitsu on 2009-08-04
:(
i insmod the .ko
reboot 
Lan is there
set pppoe
ok i can connect to lan
and reboot
i lost the lan again:(:(:(

---

### Post by Tokomitsu on 2009-08-04
I find the method to resolve that.just config eth0 up everytime I boot my coputer:(

---

### Post by Oreo on 2009-08-04
Here is my ifconfig results if I boot up with madwifi activated:
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:23:5a:7f:0c:1c  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe7f:c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30896 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:38335177 (38.3 MB)  TX bytes:9494103 (9.4 MB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1948 (1.9 KB)  TX bytes:1948 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:07:9a:f6  
          inet6 addr: fe80::224:2cff:fe07:9af6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:488 (488.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-07-9A-F6-61-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/INDENT]

With eth0 down, ifconfig yeilds this:
[INDENT]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1948 (1.9 KB)  TX bytes:1948 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:07:9a:f6  
          inet6 addr: fe80::224:2cff:fe07:9af6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:226 (226.0 B)  TX bytes:729 (729.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-07-9A-F6-61-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/INDENT]

**The wifi refused to connect with eth0 down.**

---

### Post by Tokomitsu on 2009-08-05
when I boot up
the ifconfig show that I didn't have eth0

---

### Post by woodybrando on 2009-08-06
hey,
trying to get my aao d250 working with linux mint 7.0 and this seems to be the only thread returned by google's search that's actively talking about the d250. So I've got linux mint 7.0 installed on my friends d250. I've got skype working after compiling the new alsa drivers. And I have the network cable working by installing the drivers linked on the ubuntu aspire one community page. (had to unzip the driver in puppy linux to get it to unzip wouldn't work in mint not sure why.) Now the only problem I have left is getting the suspend to work when I close the lid of the netbook. I chose in power management to suspend on close whether plugged or unplugged, but it still won't suspend. Anyone have any ideas what I need to do to get this working? thx, jayson
lostvalley.org

also, for folks trying to get nebook remix to work. i installed the nightly karmic koala unr and that had wireless working out of the box as well as the ethernet but suspend still wouldn't work when I closed the lid.

---

### Post by cparata on 2009-08-07
In my AAO D250 with Ubuntu Jaunty Remix the suspend option started to work after some automatic updates. But it does not work when I close the lid of the netbook. It works only when I select suspend option into the shut down menu.

---

### Post by woodybrando on 2009-08-07
thanks for the info cparata. yeah fn f4 is working for me to suspend in linux mint 7 and unr. still having trouble getting the mic fixed, had it working after doing the alsa compile but now it's not working again and i even tried to recompile alsa 1.20 and no luck. gonna try moblin's latest release tomorrow and hope that fixes my problems. anyone confirming a working skype mic on the d250. thx, jayson

---

### Post by cparata on 2009-08-07
My mic works fine after I compiled alsa 1.20 driver. Unfortunately, I'm obliged to recompile alsa driver after any kernel update. Woodybrando, did you check your audio settings? I have posted the mine some posts above and they work for me.

Cheers

---

### Post by woodybrando on 2009-08-08
Hey cparata, 
yeah i recompiled the alsa drivers and matched my settings to yours (yours were the italian ones right?) then i tested skype and i could hear the womans voice but my playback was just white noise. :( 
my moblin download keeps dropping out so maybe i'll just start over with a fresh install of linux mint 7 and/or unr and see if i can get it working again. I'll let you know how it goes. 
jayson
lostvalley.org

---

### Post by ramoj02 on 2009-08-10
This thread solved EVERY problem I had on my D250! Everything works now.

- Mic
- WLAN/WiFi Indicator (MadWiFi driver)
- Ethernet

Thank you everyone!

---

### Post by Oreo on 2009-08-10
I still have questions that I wonder if you could answer:

[INDENT]I suspect that I may just have a broken wireless card. Please someone answer these questions:
1) I don't remember anyone saying in the thread that they activated Madwifi in System > Administration > Hardware Drivers. Is that necessary after one compiles the driver?
2) When I do NOT have madwifi activated in Hardware Drivers, I can see wireless networks but not connect. _Is that normal?_ Having compiled the driver, once I activate madwifi in Hardware Drivers, I see no wireless networks at all.[/INDENT]

Thanks,
Oreo

---

### Post by InfectedWithDrew on 2009-08-14
Following the community guides on getting the microphone to work, I have managed to completely break alsa.

Now I have to either reinstall UNR or just kill it and stick with Windows.

Lovely.

---

### Post by brownb2 on 2009-08-17
That's why it's *free *community support. If you need paid for you should probably contact Canonical directly.
[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)
(Note I'm not affiliated and don't know if they can sort your problem, although I'd guess they would or raise it as a priority fix*).

TBH it sounds like you might be better with Windows for the moment because getting UNR working on new hardware usually requires more effort and perseverance than with mass market Windows, for which companies' hardware developers primarily target and stay up to date with for obvious reasons.

Good luck getting your Aspire working again.

*Side note: Do Microsoft do this?

BTW I have one of the (probably final generation) new 3G integrated A110s which is not currently supported by UNR (Option 3G and Atheos Wifi are broken, so I'm sitting happy with Linpus until these are resolved - I've commented on relevant bugs in bugzilla).

> **InfectedWithDrew said:**
> Following the community guides.... I have managed to completely break alsa.

Now I have to either reinstall UNR or just kill it and stick with Windows.

Lovely.

---

### Post by JKugel on 2009-08-17
> **ddrichardson said:**
> I wouldn't bother with the backport for the LED - it's not on constantly rather it flickers on TX/RX and it needs manually reloaded on resume. You also need to add some keys, let me know if you want to try it.

The front mic is a known issue and is being worked on - I can't see the bug number at the moment.
Hi there. Has the microphone bug been resolved? I cant get my Microphone to work on my Aspire One D250.

---

### Post by Gas-one on 2009-08-28
Hi! I have a Acer Aspire One D250 and I have some trouble with the VGA exit. Infact after few minutes (almost 10) a monitor connect by VGA way become black, and stay black until a reboot (Or the end of the session). Its not a savescreen problem because I disable that, and there is no problem when I return to the internal monitor.   (Sorry for my english). Thanks.

---

### Post by Gas-one on 2009-08-30
> **Gas-one said:**
> Hi! I have a Acer Aspire One D250 and I have some trouble with the VGA exit. Infact after few minutes (almost 10) a monitor connect by VGA way become black, and stay black until a reboot (Or the end of the session). Its not a savescreen problem because I disable that, and there is no problem when I return to the internal monitor.   (Sorry for my english). Thanks.

 I have resolved it passing to a newer kernel (2.6.30.5).

---

### Post by wpierce on 2009-09-20
Hey guys, I'm new (both to Ubuntu and the forums) and am looking for some help. 

I've recently purchased the Acer Aspire D250, and after I got fed up with windows xp, I decided to set it up for dual-boot. Install for UNR went fine, and everything I've tested works, except:

1) Ethernet. This is obviously a problem people have been experiencing, and I've been looking for the recommended driver to install (AR813X-linux-v1.0.0.8.tar.gz), but it seems to have been removed from [http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx"). A quick google search turns up nothing. Any ideas on where I could find it?

2) Sleep and/or hibernate. When I close my netbook, the screen goes off, but it's still running. I've checked the power settings, and it *should* be hibernating when closed, but it isn't. I'll bet the answer is somewhere here, but if someone could quote/summarize the solution, I'd be highly appreciative. 

3) It runs hot, and by hot, I mean really hot. This is compounded by the problem with it not hibernating properly, and I've had a few scares putting it in my bag while it's still running. Again, I bet there's an answer to this somewhere, but I'd love it if someone could summarize.

Thanks in advance!

---

### Post by rhk on 2009-09-21
> **wpierce said:**
> Hey guys, I'm new (both to Ubuntu and the forums) and am looking for some help. 

1) Ethernet. This is obviously a problem people have been experiencing, and I've been looking for the recommended driver to install (AR813X-linux-v1.0.0.8.tar.gz), but it seems to have been removed from [http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx"). A quick google search turns up nothing. Any ideas on where I could find it?



it's OK to use newer version of the drivers: [http://partner.atheros.com/Download.aspx?id=103](http://partner.atheros.com/Download.aspx?id=103)

For the rest, sorry, can't help, don't have the laptop any more..

[/QUOTE]

---

### Post by chuangt2u on 2009-09-23
G'day all, my first post in these forums, and my first 48 hours as a Linux user.

2 days ago I installed Ubuntu / XP dual boot on my desktop after a power outage caused a serious windows crash - went perfectly, all is fine and dandy, I like the OS and haven't used Windows since installing Ubuntu.

So, I decided to install the same on the wife's laptop as a precautionary measure, (we get a lot of power cuts here).

Wubi install of Ubuntu 9.04 / XP dual boot to an Acer Aspire 1 D250.

Everything looks good except I've found the same problems as are listed in this thread.
I'm not bothered about the microphone or the LED issues, but the lack of internet is a deal killer with Mrs C. We have a wireless router in the house, but run lines to weak signal areas - neither work with this 9.04 installation.

I've read through all 11 pages of this thread and seen things explained in many different ways, and every word was completely over my head as I'm a 2 day old virgin with Linux.

Is there anyone here who has enough time and patience to write up a step-by-step idiot's guide to addressing the wifi/wired connectivity problem for the AA1 D250 - taking account of the fact that I'm a complete novice and need things spelling out in sparklingly clear, plain English?

Many thanks in advance.

C

---

### Post by wpierce on 2009-09-23
Hi chuangt2u!

I was in the same situation as you 2 days ago, and made a post asking much the same. Basically, you should download [http://partner.atheros.com/Download.aspx?id=103]("http://partner.atheros.com/Download.aspx?id=103"), and the enter what's quoted below line by line into terminal. 
This page ([https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")) should help you get to the correct directories. Obviously your ability to do this depends on you computer-savviness (for finding directories, changing the terminal commands to suit your system/kernel, etc), and hopefully this is the info you need. 

I'm sure someone else could explain better then I can, because as I said before,  only learned this a few days ago. But anyways, I hope this sets you in the right direction. 

-Will

> **suomaf said:**
> 
```

sso@aspirenova:~/Downloads/linux-files/test$ ls
AR813X-linux-v1.0.0.8.tar.gz
sso@aspirenova:~/Downloads/linux-files/test$ gunzip AR813X-linux-v1.0.0.8.tar.gz 
sso@aspirenova:~/Downloads/linux-files/test$ tar xvf AR813X-linux-v1.0.0.8.tar 
sso@aspirenova:~/Downloads/linux-files/test$ cd src
sso@aspirenova:~/Downloads/linux-files/test/src$ make
sso@aspirenova:~/Downloads/linux-files/test/src$ sudo su
[sudo] password for sso: 
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# make install
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# cd /lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e/
root@aspirenova:/lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e# insmod ./arl1e.ko

```

---

### Post by chuangt2u on 2009-10-01
Many thanks wpierce, I'll give it a go this weekend...

---

### Post by Oreo on 2009-10-03
My wireless used to work following the instructions here, then it stopped.
I thought for a long time that it was my fault that it stopped, and explored various settings suggested earlier.
I think now that the problem is just that something is broken in the wireless on my Aspire One.

**So, if anyone else has wireless difficulties,** I want to share that the LinkSys USB N wireless donggle works great. (Dual Band Wireless-N Network Adaptor) This seems to work with and without MadWifi activated. It also gives greater range and snappier connections.

First I borrowed the adaptor made by LinkSys and found that it worked. Trying to be frugal, I tried cheaper USB N wireless adaptors made by other manufacturers, and found that they did not work.

---

### Post by suomaf on 2009-10-11
Hey guys,

I sold my D250 then decided to buy it again.. long story but not important. I have decided to install UNR again and so far the ethernet is working. I think the mic should be too. However I seem to have lost the wireless. It used to work out of the box but this is not the case anymore.

I did a lspci and this is what i got 
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Any ideas anyone?

Cheers

---

### Post by suomaf on 2009-10-11
So I reread most of this thread and I was able to fix the wireless by loading jaunty backports. For the life of me, I cannot seem to be able to get the front mic working.. still trying but thats the fun of it i guess

Ok just an update.. everything worked out and as a bonus I was able to get my brand new phs100 hsdpa modem working as well...

---

### Post by suomaf on 2009-10-25
So 9.10 is just around the corner, has anyone tried to run it with their D250s? Would appreciate feedback and comments.

Thanks guys

Suomaf

---

### Post by dragon76 on 2009-10-26
Tested UNR 9.10RC on my brand new D250.

I booted from a live usb stick so no updates have been done.

The only thing that doesn't work out of the box is the led's for the wireless.

The sound including internal mic work oob
The wireless switch works oob, just not the LED
Ethernet works oob
webcam works oob
wireless works oob
suspend works oob
cpu speed stepping and fan appear to work oob, the fan runs very ocasionaly and the system does not get hot

I have not tested the VGA out, card reader, or hibernate (no swap space with live running off of usb stick).

I am waiting to get a new enclosure for my dvd drive so I can burn the factory backup discs before trashing windows and installing some linux distro's, so I can not test hibernate at this time.

---

### Post by suomaf on 2009-10-26
Sweet! thanks for the reply quick dragon

---

### Post by Oreo on 2009-10-29
Dragon, 
Did you use Netbook Remix or just the plain Ubuntu version with those results?

Using the network Update via the Update Manager, I have Ethernet,
but no longer have Wifi, even with the Linksys donggle.

So I tried compiling MadWifi, but got this error:
CC [M]  /home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.o
cc1: warnings being treated as errors
/home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.c: In function 'skb_print_message':
/home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.c:132: error: the frame size of 1072 bytes is larger than 1024 bytes
make[3]: *** [/home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429/net80211/ieee80211_skb.o] Error 1
make[2]: *** [/home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429/net80211] Error 2
make[1]: *** [_module_/home/oreo/stuff/AspireOne250/madwifi-hal-0.10.5.6-r4016-20090429] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2

Please help!

---

### Post by suomaf on 2009-10-30
Hey guys,

Do you know of any way to upgrade from Jaunty UNR to Karmic UNR using apt-get or synaptic. Or is the install from iso the only way to go?

Suo

---

### Post by Oreo on 2009-10-31
I think that using the Update Manager (which I used) would be the same as using the Synaptic.

My sound output is not working. Compiling the driver did not seem to help.

Madwifi also does not show up.

I think I will try reinstalling from the Desktop CD next.

---

### Post by bobsfougarakhs on 2009-10-31
Just installed 9.10 on my AOD 250. Everything seems to be working fine so far.

Webcam is ok
Card reader works fine
WiFi works out of the box (Even after the system comes back from suspend)
Ethernet haven't tested yet
The only issues I have come from the microphone. There is a LOT of background noise when I use sound recorder. No experimenting with the mixer seems to be solving that completely. Plus, skype doesn't seem to work at all. I'm gonna use the alsa driver trick again. Hope that will help. I just wonder why it wasn't included in the package on the first time.

---

### Post by cparata on 2009-11-01
I solved the internal mic problem with skype on UNR 9.10 using the version 2.0 of skype indicated in the thread below and using alsa instead pulseaudio in the audio settings of skype

[http://ubuntuforums.org/showthread.php?t=1306561](http://ubuntuforums.org/showthread.php?t=1306561)

I confirm that everything works OOB with UNR 9.10 on AOO D250 except for the wifi LED.
Did anyone find a workaround for the wireless LED?

Cheers

---

### Post by bobsfougarakhs on 2009-11-03
Indeed it worked! While I believe Ubuntu has to be compatible with the latest version of skype, installing Skype 2.0 worked! Sound is crisp and clear! Thanks cparata

---

### Post by cparata on 2009-11-06
I have solved the wifi led problem on UNR 9.10 patching the ath5k driver.
In practise ath5k driver has not mapped the pin and polarity of AAO D250 wireless card led.
If you want to try, download the source code of ath5k driver from this link:

[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

Add to the file compat-wireless-yyyy-mm-dd/drivers/net/wireless/ath/ath5k/led.c these two lines in the list of ath5k_led_devices:

/* Acer Aspire One D250 */
{ ATH_SDEVICE(PCI_VENDOR_ID_FOXCONN, 0xe00d), ATH_LED(3, 0) },

then compile and install the driver in this way:

cd compat-wireless-yyyy-mm-dd
./scripts/driver-select ath5k
make
sudo make install

Cheers

---

### Post by cparata on 2009-11-08
I checked the last tarball available in linux wireless web site and I found that they already added the patch for AAO D250 led problem on UNR 9.10.
So now it just needs to download the last tarball from:

[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

and then install ath5k without any other patch.
In order to install ath5k driver you can type:

cd compat-wireless-yyyy-mm-dd
./scripts/driver-select ath5k
make
sudo make install

Cheers

---

### Post by vexorian on 2009-11-09
Hey, did anyone get ethernet to work out of the box in the D250?

I cannot get my static IP LAN connection to work and want to know if it is a problem with the ethernet support or a problem with the manager.

I do ifconfig and it does show eth0

Edit: Actually, ethernet and static IP work out of the box in the D250, I just messed up when configuring the static IP and accidentally set the IP6 part as (automatically detect) instead of (ignore) .. and to think I just wasted my whole morning trying to figure that out...

---

### Post by Donfof on 2009-12-03
LED WiFi now working,

Thank you

---

### Post by manolo_asdf on 2009-12-22
hi,

how is the hibernate function working (both manual trigger and when closing netbook). is somebody working with UMTS usb-stick modems?

---

### Post by dgilperez on 2009-12-23
Hi there !

the link to the atheros driver site is broken since last two days at least. Do you know somewhere else where I could get the driver?

Many thanks

---

### Post by vexorian on 2009-12-23
> **manolo_asdf said:**
> hi,

how is the hibernate function working (both manual trigger and when closing netbook). is somebody working with UMTS usb-stick modems?
hmnn hibernate works OOB for me. Are you sure it doesn't?

---

### Post by Marcelo Santos on 2010-01-01
Confirmed: Wifi led is working now.

Marcelo.

I forgot to mention: Using UNR 9.10.

---

### Post by suomaf on 2010-04-29
Hey guys,

Just downloaded UNE 10.04 and going to install it now. Will  update and let yous know how it goes.

Cheers

---

### Post by suomaf on 2010-04-29
okie.. quick notes version.. going to go back and play with it some more.. most of the stuff i need is OOB, only need to check if skype works.

Download UNE.iso to fileserver 10 mins
Transfer UNE.iso to desktop 30 mins
Fiddle around with usb-creator-gtk 10 mins
palm face 10 seconds.. too early 
got a coffee 2 mins
Rmembering how to use usb-creator-gtk 5 mins
Installing UNE onto usb 45 seconds
------- Installation starts -----
08:15:20 wow funky icons
08:16:20 splash and mouse appears
Tried to click on country.. does not work use drop down instead
08:18:13 install begins
its creating ext4 filesystem.. nice but no choice
08:19:17 jumped to 15% 
08:20:19 Moving fast up to 40% already
really digging this no fuss install
08:21:10 just hit 50%
Evolution is a bigger part .. should I change over from thunderbird?
Did not like empathy in 9.10 but lets see how they are doing with 10.04
With 9.10 I had to recompile the alsa to get the mic working and also the recompile the ethernet drivers.. hope that its not the case now
08.23.50 just hit 80%
08.24.00 hit 93% configuring hardware
08.27.00 just used the function keys to make the screen brighter and it works?
08.28.30 and its done ! not too shabby.. restart now
08.29.30 it popped up.. wow purple
wireless works
webcam works
ethernet works
Just opened up music player and it tells me to install mp3 plugins .. nice
sound works using the example content
movie player just crashed on me .. haha i can crash anything
recording works using sound recorder
function key works
need to test skype later
...

---

### Post by suomaf on 2010-04-30
skype needs to be 2.0 and mono channel but otherwise relatively painless upgrade

---

### Post by cparata on 2010-05-01
What about standby and hibernation function?
WiFi led and WiFi switch off button work oob?
Obviously in UNR 10.04.

Cheers

---

### Post by suomaf on 2011-05-01
Wassup guys,

In the process of installing Natty 11.04 onto the D250. So far it seems that the wifi is not being detected. Might need to plug in the eth for the install to work.. Will update as install finishes or hiccups

---

### Post by suomaf on 2011-05-01
ok.. sound card seems to work, but have not tested the internal mic, wireless seems not to be working out of the box.. downloading the kernel headers is very annoying..

for some reasons the apt-get is taking a very long time, unable to make the driver, this version seems very hard to use...

---

### Post by suomaf on 2011-05-01
so ok after wasting the whole day trying to reinstall drivers, I gave up and reinstall the whole os again. This time, I left the eth0 cable in... now it seems that both the wireless and eth is working. Sound card is working, webcam is also working.. internal mic is working

---

### Post by obazsm on 2011-05-26
i also have an acer aspire one d250 running 10.04, do you feel 11.04 is worth the upgrade?

---

