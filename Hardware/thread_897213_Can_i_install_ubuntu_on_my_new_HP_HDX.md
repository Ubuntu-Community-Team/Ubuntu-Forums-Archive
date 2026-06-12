---
title: "Can i install ubuntu on my new HP HDX"
date: 2008-08-21
forum: Hardware
---

### Post by lawrencep93 on 2008-08-21
Intel(R) Core(TM)2 Extreme Processor X9000 (2.80GHz)
	20.1" diagonal WUXGA High-Definition HP Ultra Brightview Widescreen (1920x1200)-"True HD" 1080p res
        4GB DDR2 System Memory (2 Dimm)
	512MB NVIDIA GeForce 8800M GTS
        640GB 5400RPM SATA Dual Hard Drive (320GB x 2)
        Webcam + Fingerprint Reader
	Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
	Blu-Ray ROM with SuperMulti DVD+/-R/RW Double Layer
	Integrated HP HDTV Hybrid TV Tuner and 4 Altec Lansing speakers +the HP Triple Bass Reflex subwoofer


will ubuntu work, I know that to get my graphic card working i run that program which installs the correct drivers. But I need to install the drivers for my wifi but will everything else work?

---

### Post by Afkpuz on 2008-08-22
That looks like a sweet comp!  The good news is that you can test ubuntu without making changes to your computer.  Download a live cd and boot from it.  If it boots up and you can play around in ubuntu, then it will work when you install.  Please note that this does not install anything to your computer.  It only boots from the CD.  

Some things might not work well though.

blue ray support for linux is in it's infancy.  From what I understand, you'll have to rip any blue rays before you can watch them.  I've heard that it's doable, but will be harder than straight dvds.

Webcam support has gotten alot better, but you might have trouble with yours. Same thing with finger print reader.  Might work, might not have software, but could work.

My advice is to try the live CD and test it out.  Make sure you check the System>Administration>Hardware Drivers to see if your wireless card has a driver.  If it doesn't, there may still be a driver out there, but that's the easy way to get the driver.

Also, bluetooth should work.

---

### Post by lawrencep93 on 2008-08-22
Ok thank you :).
I have installed a a similar wifi on my friends new HP but i guess if i dual boot I will not need blue ray but will my CD drive still work just to burn normal DVD's or do I need to find a blue ray driver?

Also will the screen be fine as it is big and full HD?

And what sound driver will I need or will my sound work just fine?

---

### Post by Afkpuz on 2008-08-23
If your drive can burn dvds in windows, it will be able to in linux.  That should be fine.  I don't see your sound card listed, so I can't say for sure.  You should try to google it like "soundcard name and ubuntu".

Graphics: Ubuntu can set the resolution as high as your video card and monitor allow.  You will be able to get the full resolution size (might need some tweaking, but prolly not), I just don't know if it will be progessive scan or interlaced (1080p vs. 1080i).  If you try the live cd (which I recommend), realize that your graphics won't be up to par because you can't install the graphics driver in a live boot.  But you can test your sound card and dvd burner in the live mode.  Also wifi if you've got it.  

Hope that helps

---

### Post by polkaguy6000 on 2008-10-29
Did that ever work I'm thinking about getting an HDX for Vista/Ubuntu use. My only fear is I will have issue with the wireless (HP + Ubunut gave me trouble in the past) If it works I'm sold.

---

### Post by schuylerv on 2008-11-03
I'm not the original poster but I am running ubuntu on an HDX with pretty much the same configuration(different processor) and everything works as far as I can tell. The only problems I have had were that when I first installed it all the speakers were muted but the volume control didn't act like it was. Also the second headphone jack, the remote, a few of the quickplay buttons(which I didn't expect to work), and the button that turns off the touchpad don't work but those problems might just be me not knowing how to get them to work. Everything else that I tried which I think was everything worked without any problems including the wireless card.

---

### Post by Benitlu on 2008-12-07
No!! the sound does not work and there is no driver yet for it.

---

### Post by Xytis2000 on 2008-12-29
I've got a brand new hp hdx 16. Now trying to get everything working. Yet I have major problems with fingerprint scanner. It appears it is not Autentech product. I have no idea how to make it working. Any help would be appreciated.

---

### Post by noyb on 2009-01-07
Open Volume Control.
Device should read HDA Intel (Alsa mixer).
Go Preferences.
Add Surround.
Close Preferences.
You should now see a Surround channel.
Make sure mute (at the bottom of the channel) is off.
Crank up the volume on the Surround channel.
Now try it.

You should now have sound. Volume is a bit sensitive and only kicks in at the high end but system sounds pretty much as good as it does under Vista.

---

### Post by bit_jammer on 2009-01-09
> **lawrencep93 said:**
> Intel(R) Core(TM)2 Extreme Processor X9000 (2.80GHz)
	20.1" diagonal WUXGA High-Definition HP Ultra Brightview Widescreen (1920x1200)-"True HD" 1080p res
        4GB DDR2 System Memory (2 Dimm)
	512MB NVIDIA GeForce 8800M GTS
        640GB 5400RPM SATA Dual Hard Drive (320GB x 2)
        Webcam + Fingerprint Reader
	Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
	Blu-Ray ROM with SuperMulti DVD+/-R/RW Double Layer
	Integrated HP HDTV Hybrid TV Tuner and 4 Altec Lansing speakers +the HP Triple Bass Reflex subwoofer


will ubuntu work, I know that to get my graphic card working i run that program which installs the correct drivers. But I need to install the drivers for my wifi but will everything else work?
Well. I have installed the x64 version for mine HDX and works fine. The only non working stuff are the TV tunner and the webcam but I haven't done any research about'em.

---

### Post by logic++ on 2009-01-31
> **bit_jammer said:**
> Well. I have installed the x64 version for mine HDX and works fine. The only non working stuff are the TV tunner and the webcam but I haven't done any research about'em.

Hi, is your irda recognised?

---

### Post by davidpasto on 2009-06-08
Hey,

I tried to follow the steps, but I don't have any "Surround" case, where did you get it ? At the same nivel as Master for example ?

Anyway, Ubuntux64 working fine on HDX 16 ! Sound and mic are the last problems I have ..

Thx


> **noyb said:**
> Open Volume Control.
Device should read HDA Intel (Alsa mixer).
Go Preferences.
Add Surround.
Close Preferences.
You should now see a Surround channel.
Make sure mute (at the bottom of the channel) is off.
Crank up the volume on the Surround channel.
Now try it.

You should now have sound. Volume is a bit sensitive and only kicks in at the high end but system sounds pretty much as good as it does under Vista.

---

### Post by ale.f76 on 2009-06-17
Hi there from Italy!

I have the same model of lawrence

> Intel(R) Core(TM)2 Extreme Processor X9000 (2.80GHz)
	20.1" diagonal WUXGA High-Definition HP Ultra Brightview Widescreen (1920x1200)-"True HD" 1080p res
        4GB DDR2 System Memory (2 Dimm)
	512MB NVIDIA GeForce 8800M GTS
        640GB 5400RPM SATA Dual Hard Drive (320GB x 2)
        Webcam + Fingerprint Reader
	Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
	Blu-Ray ROM with SuperMulti DVD+/-R/RW Double Layer
	Integrated HP HDTV Hybrid TV Tuner and 4 Altec Lansing speakers +the HP Triple Bass Reflex subwoofer

I was happy with 8.10  but wated to try 9.04 but couldn't manage to have the audio working...

Do you have the same problem? Have you find a solution?

Thx
Ale

---

### Post by pmalmsten on 2009-07-16
Hi there,

I had the same problem where the speakers didn't seem to work on my HP HDX 16. However, I came across this solution which worked for me:

[https://answers.launchpad.net/ubuntu/+question/74675]("https://answers.launchpad.net/ubuntu/+question/74675")

According to those instructions, just add the following line to /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=hp-m4
```

After restarting, my speakers worked fine.

Good luck,
~Paul Malmsten

---

### Post by josephellengar on 2009-07-19
> **pmalmsten said:**
> Hi there,

I had the same problem where the speakers didn't seem to work on my HP HDX 16. However, I came across this solution which worked for me:

[https://answers.launchpad.net/ubuntu/+question/74675]("https://answers.launchpad.net/ubuntu/+question/74675")

According to those instructions, just add the following line to /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=hp-m4
```

After restarting, my speakers worked fine.

Good luck,
~Paul Malmsten

Anybody got the TV tuner to work?  I'm going to buy one of these and I'm wondering if it's worth it to purchase the TV tuner.  I know that the included HP software has a cool Tivo-like experience.  Is there similar software in ubuntu?  Otherwise, everything works other than blu-ray, correct?  I was just attracted to this computer because it now has ddr3 ram and quad-core processors.

---

### Post by Benitlu on 2009-11-09
Yes on the HDX 9300 (9494nr) 20" screen

No problem encounter with Ubuntu 9.10 (32 bit), but does not boot with the (64 bit) I don't know why.

Amazingly fast, that change from Vista

So far everything work great except the sound from the loudspeaker, but from the headphone connector work fine.

Wifi work great! without any extra installation (from the Box)

Video full resolution

Blu-Ray did not try yet and did not look for any software so far, but it does read CD & DVD normally.

Enjoy your new OS, just intall it on an empty partition and will create a Dual Boot menu automatically, so that will keep your Vista as well intact... Just in case you need it later  ;)

---

### Post by bit_jammer on 2010-02-10
> **logic++ said:**
> Hi, is your irda recognised?

Yes. Using lirc and using the HP Pavillion lirc config I managed to make it work (almost). Here is the output of **/etc/lirc/lircd.conf**
```
begin remote

  name  HP_Pavilion
  bits            8
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2740   860
  one           482   420
  zero          482   420
  pre_data_bits   29
  pre_data       0x37FF07B
  gap          110890
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_POWER                0xF3
# DVD MENU
          KEY_DVD                  0xDB
# 'Q' key
          KEY_MEDIA                0x7F
# MONITOR SWITCH
          KEY_DISPLAYTOGGLE        0x7E
# Windows Media Center
          KEY_PROG2                0xF2
# PAGE DOWN
          KEY_PAGEUP               0xED
# PAGE UP
          KEY_PAGEDOWN             0xEC
# STOP
          KEY_STOPCD               0xE6
# REWIND
          KEY_REWIND               0xEA
# PLAY / PAUSE
          KEY_PLAYPAUSE            0x91
# FF
          KEY_FASTFORWARD          0xEB
# SKIP BACK
          KEY_PREVIOUSSONG         0xE4
# (up)
          KEY_UP                   0xE1
# SKIP FWD
          KEY_NEXTSONG             0xE5
# (left)
          KEY_LEFT                 0xDF
# OK / ENTER
          KEY_ENTER                0xDD
# (right)
          KEY_RIGHT                0xDE
# BACK / UNDO
          KEY_ESC                  0xDC
# (down)
          KEY_DOWN                 0xE0
# 'i'
          KEY_INFO                 0xF0
# VOL +
          KEY_VOLUMEDOWN           0xEE
# MUTE
          KEY_MUTE                 0xF1
# VOL -
          KEY_VOLUMEUP             0xEF
      end codes

end remote

```

And here the output of **/etc/lirc/hardware.conf**
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ENE KB3926 B/C/D (ENE0100) CIR port"
REMOTE_MODULES="lirc_dev lirc_ene0100"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS="-d /dev/lirc0"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

---

### Post by dimmo7 on 2010-05-21
installed on my hdx and the only dramas are with tv tuner and dvd player and braserio, would love to get the tuner going though

---

