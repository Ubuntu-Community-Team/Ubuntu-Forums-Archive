---
title: "P150SM-A and weird sound issues + guide for exotic drivers"
date: 2015-09-04
forum: Hardware
---

### Post by hickscorp on 2015-09-04
Hi,


I recently purchased a P150SM-A (Same mobo as in the Sager NP8268 i think), and have been spending a little time on getting things to correctly work with the version of Ubuntu i have installed on it. Right now, I'm using a 15.04 with an XFCE desktop, it looks great!

My main problem right now is a horrible sound support. Basically, all sounds are kind of "dimmed", almost like they would be when coming out of a phone from the 80's. The volume is very low, even when i crank all the mixers all the way to the top. With some other operating systems everything is just fine, but with 15.04 it just doesnt sound right.

Here is an output of lspci, maybe someone with the same brand (It says Sound Blaster X-Fi MB3 on the computer box):

```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
03:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] (rev 01)
04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] (rev 01)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
05:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
06:00.0 Network controller: Intel Corporation Wireless 7260 (rev c3)

```

I have close to no experience with sound systems, so if anyone could give me hints on how to solve this, i would be grateful.
In the meantime, i am going to write a small guide below for those who are looking for solutions to the problems i ran into.

Cheers!

[EDIT]
Forgot to ask about something else. When i'm using the Integrated Intel HD4000 GPU, everything is OK. However when i switch to the NVidia one, something really weird occurs. If i move my mouse to the top edge of the display, the pointer disapears :D
Ive looked it up online, but havnt found anything exactly like these symptoms. Did this happen to anyone please?
[/EDIT]

[SUPER-TIRED 2AM EDIT]
Side question: im running the vanilla BIOS on this computer. **Any advice on a more Linux-tolerant one?**
[/SUPER-TIRED 2AM EDIT]


--------

**Fingerprint Detection**

Most of the drivers / utilities that i have found in the default ubuntu repos dont work. Instead, here is what i have done:

- Go to [this page]("https://launchpad.net/~fingerprint/+archive/ubuntu/fprint").
- Their instructions are pretty accurate. The important part is to queue the PAM library correctly by issuing a ```
pam-auth-update --force
``` as root.

So basically as root:

```

sudo add-apt-repository ppa:fingerprint/fprint && sudo apt-get update && sudo apt-get upgrade
# The last package is optional, but it's fun to play with. If you are using GNOME or KDE, you might need some other things (GKSU, etc).
sudo apt-get install libfprint0 libpam-fprintd fprint-demo
sudo pam-auth-update --force

```

At this point, you should be able to register your fingerprint minutaes. Do so by running ```
fprintd-enroll
``` and by scanning your finger 5 times.

The only problem with this are applications that are not using PAM facilities to authenticate sudo attempts... Eg. Sublime Text, if you open a file that you dont own and try to save it, Sublime will freeze until the PAM module times-out, and then you will be able to type your sudo password... **Any idea about a workaround?**



**Backlit keyboard**

This one was a real nightmare. Either the repositories cannot be cloned because some files are corrupted, or the code is of so poor quality that i wouldnt dare leave the module getting insmod'ed.

I ended up using [the one here]("https://github.com/sonnym/clevo-xsm-wmi").

Here are the steps:

```

git clone https://github.com/sonnym/clevo-xsm-wmi && cd clevo-xsm-wmi
cd module && make && sudo cp clevo-xsm-wmi.ko /lib/modules/$( uname -r )/kernel/lib/ && sudo depmod -a

```

At this point, you should be able to manually load the module by issuing ```
sudo insmod clevo-xsm-wmi
```. If successfull, then hitting some of the Fn + Backlight keys on the numpad should give you some fancy results (Mine started blinking randomly).

[edit]
For those who are interested into getting the backlit keyboard to work, i just have forked the source code repository and created DKMS / tutorial readme, so the module automatically gets compiled automatically when you have a kernel update:
[https://github.com/hickscorp/clevo-xsm-wmi](https://github.com/hickscorp/clevo-xsm-wmi)
The README.md file explains how to use this.
[/edit]

Past this point, you should be able to compile the application from the same git repo. It's in the `utility` folder. I didnt try myself, because im pretty happy with the files i got in `/sys/devices/platform/clevo_xsm_wmi`. But i guess to compile the app in `utility` you would have to:
- Install Qt: `sudo apt-get install qt4-dev-tools`
- Build makefiles: `qmake`
- Build the program: `make`.
Maybe i will try that another day.

From there, i would really love to find a precompiled deb file... **Any idea on how i could do it myself?** Last time I build packages for debian was back in 2002... I have pretty much forgotten everything since then.

---

### Post by Yellow Pasque on 2015-09-04
For nvidia driver, you probably want to try the latest version: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

For audio, check:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by hickscorp on 2015-09-05
Hi Temujin, and thank you for helping,

I will install the nVidia drivers you're pointing out this afternoon (I have a very poor internet connection right now).
Regarding ALSA, [here is]("http://www.alsa-project.org/db/?f=ee78855daa046ac3105bee8e24715a1b17c1d92e") the link to the information the script had gathered.

Could you please tell me what im looking for exactly?

[edit]
Oh i think i understand where we're going. So basically the only kernel modules related to sound that are loaded are:
```
snd_hda_intel
snd_hda_intel
```
These probably only handle the sound card that is integrated to my CPU (It's a core i7 with an integrated GPU / Audio chip). But the sound blaster card isn't being supported by any of those, is it?
[/edit]

---

### Post by Yellow Pasque on 2015-09-05
I don't see anything obviously wrong with your info, but based on your description, it might need a code fix for EAPD (the amp). Do headphones work okay?

> But the sound blaster card isn't being supported by any of those, is it?

What Sound Blaster card? You have the HDMI audio built into the GPU and a Realtek ALC892 codec.
As best I can tell, this is what you're referring to: [http://www.creative.com/oem/products/software/x-fimb3.asp](http://www.creative.com/oem/products/software/x-fimb3.asp)
It's just a DSP software that runs on Windows and it works on non-Creative codecs.

---

### Post by hickscorp on 2015-09-05
> **Temüjin said:**
> I don't see anything obviously wrong with your info, but based on your description, it might need a code fix for EAPD (the amp). Do headphones work okay?
Ok, will google for EAPD code fix then. Thanks :)
No idea about the headphones... I dont have any right now to test. Will test and report back ASAP.
Is this what you are talking about?: [https://wiki.sabayon.org/index.php?title=HOWTO:_Resolve_Problems_with_HDA-Intel_Sound_Cards](https://wiki.sabayon.org/index.php?title=HOWTO:_Resolve_Problems_with_HDA-Intel_Sound_Cards) They list some Clevo laptops, i will try.

Aren't those two different things?
```

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

```

Regarding the nVidia advice: i have upgraded to the latest version of the drivers, no joy... The mouse is still disappearing when on top of the screen... Only when using the nVidia card.

Thanks Temujin!

---

### Post by hickscorp on 2015-09-05
After googling a little bit more, i think the problem i'm observing is clearly these ones:

[http://lists.freedesktop.org/archives/pulseaudio-discuss/2011-June/010344.html](http://lists.freedesktop.org/archives/pulseaudio-discuss/2011-June/010344.html)
[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-November/046109.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-November/046109.html)

I think the sub-woofer isnt getting any sound out, hence the "dimmed" sensation i was describing... Looking at what these guys are talking about, i have no solution for this?
Im having a hard time understanding what they are talking about, would you know about some resources i can read that might be more accessible for unexperimented users please?

---

### Post by hickscorp on 2015-09-05
@Temujin: Since i have identified that the problem is the subwoofer not outputing anything, i have found many resources online that im going to try, so don't bother looking into this anymore as i might find the fix. I will keep you posted and update the guide in my original post for other people to use.

**Im however still on the lookout** regarding the mouse glitch when using the nVidia card, and also I discovered that the fingerprint scanner fails in some circumstances (No error in syslog, the device is present and used by fprintd when it occurs, no clue yet).

Thanks for your help!

---

### Post by Yellow Pasque on 2015-09-05
> Is this what you are talking about?: [https://wiki.sabayon.org/index.php?t...el_Sound_Cards](https://wiki.sabayon.org/index.php?t...el_Sound_Cards) They list some Clevo laptops, i will try.

No. That's old advice (and for a different codec). The snd-hda-intel driver now automatically applies fixes.

> I think the sub-woofer isn't getting any sound out, hence the "dimmed" sensation i was describing...
Hmm. I wouldn't think that would cause you to not be able to hear sounds well at full volume. I'm not sure though.

> would you know about some resources i can read that might be more accessible for unexperimented users please? 
I don't know any comprehensive documentation aimed at users. I've just gleaned some bits here and there, though I wish I understood more.

---

### Post by Yellow Pasque on 2015-09-05
Just one more thing:
You may want to try hdajackretask to see if you can get the subwoofer
```
sudo apt-get install alsa-tools-gui
sudo hdajackretask
```

---

### Post by hickscorp on 2015-09-05
@Temujin You rock. I have played with the hdajackretask tool with no joy. After looking online for the same problem (And really, trust my hear: no subwoofer), i found a dead thread giving some alsa commands to try. Look at this one:

```

aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA Intel HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA Intel HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA Intel HDMI, HDMI 2
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Hardware device with all software conversions
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions

```

As you can see, the PCH (Can't help myself... Im so happy that i have a pacific coast highway sound card XD ) device exposes this surround21 thingy, but i have no idea how to rewire the pins to use it. Any advice please? We're almost there :)


[edit]
I changed alsa's daemon.conf with these lines:
```

 default-sample-channels = 3
enable-lfe-remixing = yes

```

Now, my sound properties panel offers me the Suround Analog 2.1 option, when i choose it the volume control offers one more silder named "Subwoofer". However nothing happens when i move it around... What should i rewire with the hdajack tool? I need to know if i need to rewire an unconnected pin or not, and if i need to rewire it to the Speaker LFE or Speaker Back... What is the most likely to work choice? It's way too many possibilities to try them all :D
[/edit]

---

### Post by Yellow Pasque on 2015-09-07
I'm not too sure when it comes to Pulseaudio and surround sound stuff. (I don't use either one). This is about the closest thing I've found: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/1286021](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/1286021)

---

### Post by hickscorp on 2015-09-08
I have just installed Windows and the Realtek drivers + the Creative Soft mixer... No output from the Subwoofer.
I'm wondering if it might be a physical connection problem... Will try to see with my reseller.

---

