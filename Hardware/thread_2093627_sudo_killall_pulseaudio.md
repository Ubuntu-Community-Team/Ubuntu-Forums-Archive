---
title: "sudo killall pulseaudio"
date: 2012-12-11
forum: Hardware
---

### Post by em wai zee on 2012-12-11
Hi everyone! Recently, I've upgraded Ubuntu from 10.04 to 12.10, and this little audio problem keep bugging me since day one I've upgraded it. I've followed all the tips from this [blog]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/") to solve my audio problem. I think I've solved it. But, everytime start my machine, I've to insert "killall pulseaudio" to reset my Dummy Output to normal ones. Tips anyone to overcome this pesky bug? Thanks!

---

### Post by NightsShadeQueen on 2012-12-11
If running killall pulseaudio at startup works, consider just putting that in startup scripts?

Two ways to do so:

1. Go to Startup Applications. Click add. 
2. Add it to the end of ~/.bash_login

**Edit:** I'm stupid, this is a sudo command, of course it won't work this easily.

How much do you like external volume controls? You might be able to just uninstall pulseaudio completely.

sudo apt-get autoremove pulseaudio and then reboot.

**Edit: **I really should stop giving advice after not sleeping. Getting rid of pulseaudio won't work.

You *can* give your local user the ability to run killall on pulseaudio without sudo. 

See here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

And then put it startups.

---

### Post by dannyboy79 on 2012-12-11
have you read through these solutions?
[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

---

### Post by em wai zee on 2012-12-12
> **NightsShadeQueen said:**
> If running killall pulseaudio at startup works, consider just putting that in startup scripts?

Two ways to do so:

1. Go to Startup Applications. Click add. 
2. Add it to the end of ~/.bash_login

**Edit:** I'm stupid, this is a sudo command, of course it won't work this easily.

How much do you like external volume controls? You might be able to just uninstall pulseaudio completely.

sudo apt-get autoremove pulseaudio and then reboot.

**Edit: **I really should stop giving advice after not sleeping. Getting rid of pulseaudio won't work.

You *can* give your local user the ability to run killall on pulseaudio without sudo. 

See here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

And then put it startups.

Okay, maybe you've to much caffeine! :popcorn: BTW, Thanks ... will follow-up your tips!

---

### Post by em wai zee on 2012-12-12
> **TacheDeChoco said:**
> After so many many attempts to solve my audio problems when upgrading to Karmic, I finally found a working solution  :p !

First, let me decribe what the problem was:
1) no audio card was detected at all
=> cat /proc/asound/cards returned an empty content
=> cat /proc/asound/devices did not include any audio devices
=> 'Hardware' tab in sound preferences was empty
2) the audio tray indicated a "dummy output"


SOLUTION
========

For those who do not have a fresh Karmic install (in other words those who have upgraded their Jaunty install), you should update your Grub BEFORE applying the 2 steps described hereunder:

sudo update-grub



**Step1: make the sound card being recognized**

=> _Purge _alsa-base and pulseaudio, eg:

sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload


Now, reboot, you shoud now SEE (but maybe not yet hear) your soundcard.
Give a try to:
cat /proc/asound/cards
and see if any card is listed...


**Step2 : If the sound is crapy, you MAY have to edit the alsa config file:**

sudo gedit /etc/modprobe.d/alsa-base.conf

a) comment (#) the following line:
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N

b) Add a new line
options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen]**hp**[/COLOR]

Replace "[COLOR=DarkGreen]**hp**[/COLOR]" with appropriate computer model. See [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt")

Good luck !

Bernard.

I believe I've followed all the tips above, & yet, I still have to force reload my sound card at each machine starts! 1 thing for sure after scouring the threads; my Acer TravelMate 6292 has a modem, so that could be THE problem. Question, how I tackle the modem problem. Some said in the thread, the modem software should be disabled, so, how do I disable it?

---

### Post by em wai zee on 2012-12-12
Ok, I think this is the time where I cry for help for breaking my sound system ... This is the output of running the script from ALSA


!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Wed Dec 12 15:01:13 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      Acer, inc.
Product Name:      TravelMate 6292 
Product Version:   Not Applicable
Firmware Version:  v1.3401


!!Kernel Information
!!------------------

Kernel release:    3.5.0-19-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
	Subsystem: 1025:011b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T 1 root audio 116,  1 Dec 12 22:48 /dev/snd/seq
crw-rw---T 1 root audio 116, 33 Dec 12 22:48 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
ipt_MASQUERADE
xt_state
ipt_REJECT
xt_tcpudp
iptable_filter
nf_nat_h323
nf_conntrack_h323
nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre
nf_nat_proto_gre
nf_nat_tftp
nf_conntrack_tftp
nf_nat_sip
nf_conntrack_sip
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_conntrack_ftp
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
ip_tables
x_tables
bnep
rfcomm
dm_crypt
binfmt_misc
arc4
uvcvideo
btusb
videobuf2_core
iwl4965
videodev
bluetooth
option
usb_wwan
videobuf2_vmalloc
usbserial
videobuf2_memops
iwlegacy
pcmcia
mac80211
yenta_socket
pcmcia_rsrc
pcmcia_core
coretemp
soundcore
joydev
kvm_intel
cfg80211
kvm
lpc_ich
acer_wmi
irda
psmouse
serio_raw
mac_hid
sparse_keymap
microcode
crc_ccitt
ppdev
parport_pc
lp
parport
usb_storage
hid_generic
usbhid
hid
firewire_ohci
firewire_core
crc_itu_t
sdhci_pci
sdhci
i915
tg3
wmi
drm_kms_helper
drm
i2c_algo_bit
video


!!ALSA/HDA dmesg
!!--------------

---

### Post by em wai zee on 2012-12-12
I believe I've solved my problem. Thanks people, thanks Google!

---

### Post by 6541984 on 2013-01-16
I did the following as stated above,

[I]sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload[/I]

I added the following,

*sudo apt-get update*

I restarted twice, then it worked.  This problem is the same since Ubuntu 10+, now I am on 12.04LTS yet we still have this same problem.  Any chance this can be fixed permanently?

---

