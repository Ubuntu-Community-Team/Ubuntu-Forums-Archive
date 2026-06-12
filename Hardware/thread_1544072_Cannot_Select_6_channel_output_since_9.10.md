---
title: "Cannot Select 6 channel output since 9.10"
date: 2010-08-02
forum: Hardware
---

### Post by linuxyogi on 2010-08-02
Hi, 
The problem is after installing 9.10 I found that the option to select 2/4/6 channel output via pulse audio mixer is no longer available.

In short there is no option to change the speaker configuration.
Therefore the only remaining option is listening to stereo output (default).

Currently I am using lucid but the problem is still there.

Sound Card: Integrated sound card.

lspci prints -------------

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

aplay -l prints--------------

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

head -n 1 /proc/asound/card*/codec#* --------------

Codec: Realtek ALC662 rev1


Please help.

---

### Post by linuxyogi on 2010-08-02
dpkg -l | grep "alsa"

ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library

---

### Post by linuxyogi on 2010-08-03
No one?

---

### Post by AHD on 2010-08-03
Hi

As i already said, i spent endless hours getting rid of distortions, mute gstreamer sound after a about 30 minutes and other issues. 

imho there are several frontends fighting for the backend.

Someone mentioned that there are alsa driver problems with certain onboard cards. I also have this one, but i switched it of after an hour because it made nearly deaf.

I mentioned that I use Maverick 10.10 since it was released and I'm quite happy with it. Lynx was released to soon. So much regressions and mini-bugs which add up to a mantis.

Also using the "unstable" pulse did the rest. 

I don't know the current 10.4 version state, but i assume that you won't get these bugs fixed until 10.10. One example: I like my windows burn down und beam up :). But a regression made it impossible to select the mouse cursor properly. This is a gnome bug. Compiz unstable has an option to fix this without spending hours searching for a solution.
The developer reply to this bug report was that you should stop using compiz or live with it. ....What about the nearly blind ones. ;)

Just another thing: There's a gstreamer 0.10.30 available. Libcanberra is also a buggy. Perhaps this fixes your problem. 
But you have to update all other components. 

Regards,
Alex.

---

### Post by AHD on 2010-08-03
[SIZE=1]Forgot this alsa output thingy.[/SIZE]

trying to attach... done. 

Alex.

---

### Post by AHD on 2010-08-03
:KS

just as I hacked in my last message there came another update. Pulse + Alsa. The only setback is the icon for the Pulse manager. The normal icon seems to be not found and there's only an X with white background....

There's also a tool that can do a snapshot. Ailurus.

Alex.

---

### Post by utilitytrack on 2010-08-03
[SIZE=3][COLOR=#8A8A8A][B][SIZE=3][COLOR=#000000]to linuxyogi[/COLOR][/SIZE]
[/B][/COLOR][/SIZE]
[COLOR=#8A8A8A][SIZE=3][COLOR=#000000]put here[/COLOR][/SIZE]
[/COLOR] [SIZE=3][COLOR=#8A8A8A]
[/COLOR][/SIZE][COLOR=#8A8A8A][SIZE=3][COLOR=#000000]```
# hwinfo --sound
```[/COLOR][/SIZE]
[/COLOR] [SIZE=3][COLOR=#8A8A8A]
[/COLOR][/SIZE]

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> [SIZE=3][COLOR=#8A8A8A][B][SIZE=3][COLOR=#000000]to linuxyogi[/COLOR][/SIZE]
[/B][/COLOR][/SIZE]
[COLOR=#8A8A8A][SIZE=3][COLOR=#000000]put here[/COLOR][/SIZE]
[/COLOR] [SIZE=3][COLOR=#8A8A8A]
[/COLOR][/SIZE][COLOR=#8A8A8A][SIZE=3][COLOR=#000000]```
# hwinfo --sound
```[/COLOR][/SIZE]
[/COLOR] [SIZE=3][COLOR=#8A8A8A]
[/COLOR][/SIZE]


hwinfo --sound
17: PCI 07.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55c
  Unique ID: M71A.uqJCkV9DszA
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: sound
  Model: "nVidia MCP67 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055c "MCP67 High Definition Audio"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8290 
  Revision: 0xa1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdfff8000-0xdfffbfff (rw,non-prefetchable)
  IRQ: 21 (373 events)
  Module Alias: "pci:v000010DEd0000055Csv00001043sd00008290bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown



Thanks a lot.

---

### Post by utilitytrack on 2010-08-03
ok, next please

```
$ cat /etc/modprobe.d/alsa-base.conf | grep intel
```

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> ok, next please

```
$ cat /etc/modprobe.d/alsa-base.conf | grep intel
```

cat /etc/modprobe.d/alsa-base.conf | grep intel
options snd-intel8x0m index=-2

---

### Post by utilitytrack on 2010-08-03
ok, add it to the end of file [FONT=Courier New]/etc/modprobe.d/alsa-base.conf[/FONT]

```
options snd-hda-intel index=0 model=3stack-6ch
```
save and reboot. next open alsamixer, check the volume levels and test sound

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> ok, add it to the end of file [FONT=Courier New]/etc/modprobe.d/alsa-base.conf[/FONT]

```
options snd-hda-intel index=0 model=3stack-6ch
```
save and reboot. next open alsamixer, check the volume levels and test sound

Done ........
Front channel are playing.
Rear channels are still silent.

I am testing sound with a 2 channel mp3 file.
Is that okay ?

---

### Post by utilitytrack on 2010-08-03
No, It's can be check with [FONT=Courier New]speaker-test[/FONT] utility

 ```
$ speaker-test -Dplug:surround51 --channels 6
```

Check that you make physical connections correctly

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> No, It's can be check with [FONT=Courier New]speaker-test[/FONT] utility

 ```
$ speaker-test -Dplug:surround51 --channels 6
```

Check that you make physical connections correctly

Same result.
No sound from Rear channels.


For testing I am unplugging the front channels.
At present only the rear channels are connected.

Note : I have a 4.0 speaker setup.
Front channels are connected to a 2.1 speaker system while the rear channels are connected to a audio system
Center & LFE are not connected.

Therefore, speaker-test -Dplug:surround51 --channels 4

Correct ?

Same result. Rear channels are silent.

Sorry for not mentioning this before,
Sorry:lolflag:

---

### Post by utilitytrack on 2010-08-03
try it in that case

```
speaker-test -Dplug:surround40 --channels 4
```

Play some DVD with really 5.1 sound track (use e.g VLC fot that) and post result. Probable you need custom signals routing... Hint: if you can would make this, connect your speakers in standard 5.1 configuration.

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> try it in that case

```
speaker-test -Dplug:surround40 --channels 4
```

Play some DVD with really 5.1 sound track (use e.g VLC fot that) and post result. Probable you need custom signals routing... Hint: if you can would make this, connect your speakers in standard 5.1 configuration.

Tried "speaker-test -Dplug:surround40 --channels 4" but the same thing again.

Just played a 5.1 channel vob file using both vlc & smplayer. Rear channels remain silent.
Note: I have already selected 4.0 speaker configuration in smplayer's audio configuration page.

I can think of buying a proper 5.1 speaker setup only after I am able to get 6 channel audio from this pc. 

With 9.04 I used to listen to 6 channel audio via 4 channels with this very setup, with no problem. But from 9.10 its only 2.0 that's all I can get.

"custom signals routing" What is that? How do I do that?

---

### Post by utilitytrack on 2010-08-03
ok, I'm not forcing you to walk in shop now for buying speakers :))
I suppose that you need edit [FONT='Courier New'].asoundrc[/FONT] file for setting up surround sound (and that's be a signals routing). Sorry but I don't help you in this case. My ability is ended :) On this sites you'll find further info:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc) 
[http://alsa.opensrc.org/index.php/SurroundSound](http://alsa.opensrc.org/index.php/SurroundSound)
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)


good luck!

---

### Post by linuxyogi on 2010-08-03
> **utilitytrack said:**
> ok, I'm not forcing you to walk in shop now for buying speakers :))
I suppose that you need edit [FONT='Courier New'].asoundrc[/FONT] file for setting up surround sound (and that's be a signals routing). Sorry but I don't help you in this case. My ability is ended :) On this sites you'll find further info:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc) 
[http://alsa.opensrc.org/index.php/SurroundSound](http://alsa.opensrc.org/index.php/SurroundSound)
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)


good luck!

Alright, thanks a lot for your sincere efforts.
I will visit those links you have mentioned.
Thanks again.

---

### Post by linuxyogi on 2010-08-03
Anyone who wants to help please mention if I need to undo this step -----

I have added this line ------------ 
options snd-hda-intel index=0 model=3stack-6ch

to the end of file /etc/modprobe.d/alsa-base.conf.

Do I need to remove this line before following the your procedures ?

Also I am confused with what exactly am I running here Pulseaudio or Alsa ? How to determine this?

---

### Post by linuxyogi on 2010-08-04
**uname -a**

2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux


**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 

**dpkg -l | grep "alsa"**
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library


**head -n 1 /proc/asound/card*/codec#***
Codec: Realtek ALC662 rev1


About my motherboard : [http://reviews.cnet.com/motherboards/asus-m2n68-am-motherboard/4507-3049_7-33311626.html?tag=mncolBtm;rnav]("http://reviews.cnet.com/motherboards/asus-m2n68-am-motherboard/4507-3049_7-33311626.html?tag=mncolBtm;rnav")

This describes my speaker setup : [http://ubuntuforums.org/showpost.php?p=9673978&postcount=14]("http://ubuntuforums.org/showpost.php?p=9673978&postcount=14")

---

### Post by lidex on 2010-08-05
First upgrade your alsa install using the link in my sig. When done use pavucontrol (pulse audio volume control) to adjust your volume levels after selecting the correct profile in hardware tab of 'Sound Preferences'

To install pavucontrol:
```
sudo apt-get install pavucontrol
```

References:
[http://ubuntuforums.org/showthread.php?t=1491347](http://ubuntuforums.org/showthread.php?t=1491347)

```
Configuring Surround Sound with Pulseaudio

First off please remember. PULSEAUDIO DEFAULTS TO ONLY TWO CHANNELS!

This is something to remember because most likely it is very easy to get surround to work with one file change instead of trying to mess around with asoundrc or something like that.

Okay, we are going to copy over the config file to your home directory. This way it will be per user basis.

Open up the terminal and lets copy that file over.

cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/

Setting Up Surround Sound

Okay, there are two ways to do this based off of your speaker configuration. The Easy Way and The Hard(er) Way. I know all of you would like to use the easy way but here is the deal. if your speaker setup is any of the following it's pretty simple.

2.0, 4.0, 5.0, 5.1, 7.1

Any other setup and it's a bit more complicated with various hackish type stuff. If your speaker layout is anything other then what is listed above please proceed to The Hard(er) Way.
The Easy Way

Okay good. This will be simple and to the point.

Open up terminal and lets get to work shall we?

sudo gedit ~/.pulse/daemon.conf

You are going to look for the following lines of code.

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

Un-comment the line that says default-sample-channels (by taking away the ;) and change the 2 to output how many channels you need. If you have a 4.0 then put 4. If you have 5.1 then put 6 etc.

Save and exit. Now you need to reboot. Once Ubuntu boots back up you should have surround!
The Hard(er) Way

Okay, if you're here then you have a different setup then what was listed above.

So, lets get to this thing shall we?

Open up your terminal and lets get to work.

gedit ~/.pulse/default.pa

Down around line 32 is what you're looking for. It will look like this.

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
.endif

Now, you need to uncomment “load-module module-alsa-sink” and change it to something that looks like this. NOTE: It will have to be tweaked to reflect your speaker setup.

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)

### Manual config for configuring surround sound. Comment out line below to revert to defaults.
load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

#load-module module-alsa-source device=hw:1,0
.endif

This layout is what a 4.1 system looks like. The reason why you can't use the 5.0 layout is a 5.0 uses FL FR BL BR CEN. the *.1 is a sub-woofer setup. Just tweak the settings to reflect what you have.

Here is the template that you will use for getting this setup.

load-module module-alsa-sink device_id=X channels=X channel_map=x,x,x,x,x,x,x

device_id - This is of course the id of your card. If you have one sound card, this is likely to be 0, but might be different if you have more than one card. channels=X - The X should be replaced by the total number of channels you wish to use channel_map=x,x,x,x,x,x,x - This is a comma separated list of values that tell pulseaudio which channels to use. It's probably a good idea to stick to the same order that pulseaudio uses (listed at the beginning of the guide) but skip out which channels you don't want. Here is an exhaustive list of valid channel names: The currently defined channel names are: left, right, mono, center, front-left, front-right, front-center, rear-center, rear-left, rear-right, lfe, sub-woofer, front-left-of-center, front-right-of-center, side-left, side-right, aux0, aux1 to aux15, top-center, top-front-left, top-front-right, top-front-center, top-rear-left, top-rear-right, top-rear-center, (Default depends on the number of channels and the driver) It's probably best to stick to some combination of the following: front-left, front-right, front-center, rear-center, rear-left, rear-right, lfe, side-left, side-right

For a sub-woofer you will use lfe instead of sub or sub-woofer. lfe means “Low Frequency Effects” and that is what we will use for the sub-woofer.

Okay! Save and exit the editor and you're finished. Reboot your system and it should work! If the channels are mixed up then listen for what channels are swapped and fix the order. Also, if you are not getting sound you will want to check alsamixer to make sure that nothing is muted.

sudo alsamixer

If your system is totally messed up there is a simple fix to reset it.

cp /etc/pulse/default.pa ~/.pulse/default.pa && cp /etc/pulse/daemon.conf ~./pulse/daemon.conf

Reboot the system and it should be back the way it was when you started! 
```

---

### Post by linuxyogi on 2010-08-05
> **lidex said:**
> First upgrade your alsa install using the link in my sig. When done use pavucontrol (pulse audio volume control) to adjust your volume levels after selecting the correct profile in hardware tab of 'Sound Preferences'

To install pavucontrol:
```
sudo apt-get install pavucontrol
```

References:
[http://ubuntuforums.org/showthread.php?t=1491347](http://ubuntuforums.org/showthread.php?t=1491347)

```
Configuring Surround Sound with Pulseaudio

First off please remember. PULSEAUDIO DEFAULTS TO ONLY TWO CHANNELS!

This is something to remember because most likely it is very easy to get surround to work with one file change instead of trying to mess around with asoundrc or something like that.

Okay, we are going to copy over the config file to your home directory. This way it will be per user basis.

Open up the terminal and lets copy that file over.

cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/

Setting Up Surround Sound

Okay, there are two ways to do this based off of your speaker configuration. The Easy Way and The Hard(er) Way. I know all of you would like to use the easy way but here is the deal. if your speaker setup is any of the following it's pretty simple.

2.0, 4.0, 5.0, 5.1, 7.1

Any other setup and it's a bit more complicated with various hackish type stuff. If your speaker layout is anything other then what is listed above please proceed to The Hard(er) Way.
The Easy Way

Okay good. This will be simple and to the point.

Open up terminal and lets get to work shall we?

sudo gedit ~/.pulse/daemon.conf

You are going to look for the following lines of code.

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

Un-comment the line that says default-sample-channels (by taking away the ;) and change the 2 to output how many channels you need. If you have a 4.0 then put 4. If you have 5.1 then put 6 etc.

Save and exit. Now you need to reboot. Once Ubuntu boots back up you should have surround!
The Hard(er) Way

Okay, if you're here then you have a different setup then what was listed above.

So, lets get to this thing shall we?

Open up your terminal and lets get to work.

gedit ~/.pulse/default.pa

Down around line 32 is what you're looking for. It will look like this.

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
.endif

Now, you need to uncomment &#8220;load-module module-alsa-sink&#8221; and change it to something that looks like this. NOTE: It will have to be tweaked to reflect your speaker setup.

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)

### Manual config for configuring surround sound. Comment out line below to revert to defaults.
load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

#load-module module-alsa-source device=hw:1,0
.endif

This layout is what a 4.1 system looks like. The reason why you can't use the 5.0 layout is a 5.0 uses FL FR BL BR CEN. the *.1 is a sub-woofer setup. Just tweak the settings to reflect what you have.

Here is the template that you will use for getting this setup.

load-module module-alsa-sink device_id=X channels=X channel_map=x,x,x,x,x,x,x

device_id - This is of course the id of your card. If you have one sound card, this is likely to be 0, but might be different if you have more than one card. channels=X - The X should be replaced by the total number of channels you wish to use channel_map=x,x,x,x,x,x,x - This is a comma separated list of values that tell pulseaudio which channels to use. It's probably a good idea to stick to the same order that pulseaudio uses (listed at the beginning of the guide) but skip out which channels you don't want. 

Reboot the system and it should be back the way it was when you started! 
```

Success !!! :D
Upgraded Alsa using the script you mentioned.
Then the "Hard(er) Way" worked.
I am getting sound from all channels now.
There's only a minor problem, the volume control has stopped working.
When I click it says (after a long pause) "Waiting for sound to get ready" or similar. Actually this message too is not appearing anymore.
I am controlling volume using alsamixergui. 


Just one question :

The script you provided upgraded my alsa installation to ver. 1.0.23-2.
Now suppose there is an update available (ubuntu repos), will it be possible for update manager to update/upgrade it further ? 


Thanks a lot.

---

### Post by lidex on 2010-08-05
You probably won't see an upgrade on this release. Maverick's default is 1.0.23.
You're using alsamixer-gui? Might want to try pavucontrol.

---

### Post by linuxyogi on 2010-08-05
> **lidex said:**
> You probably won't see an upgrade on this release. Maverick's default is 1.0.23

Alright. 
Thanks again.

---

### Post by linuxyogi on 2010-08-05
> **lidex said:**
> You're using alsamixer-gui? Might want to try pavucontrol.

pavucontrol is installed but when I start it it says "Connection failed: Connection refused".

---

### Post by lidex on 2010-08-05
You're welcome! See my edit above.
If all is good please mark the thread solved using 'Thread Tools' up top.

---

### Post by lidex on 2010-08-05
I guess that work-around is causing it. The screenshot I posted is a stock install, just selected the 5.1 surround from pavucontrol and everything was there. Did you try that initially? That is actually how it's supposed to work now with pulseaudio auto-configuring for you.

---

### Post by linuxyogi on 2010-08-06
> **lidex said:**
> I guess that work-around is causing it. The screenshot I posted is a stock install, just selected the 5.1 surround from pavucontrol and everything was there. Did you try that initially? That is actually how it's supposed to work now with pulseaudio auto-configuring for you.

After implementing the following step --------

gedit ~/.pulse/daemon.conf

; default-sample-channels = 2 

**changed to **

default-sample-channels = 6

I rebooted and tried to find if there's a surround profile in pavucontrol. But it basically was showing the same profiles as before.

Frankly, I have been waiting for a solution for since the release of 9.10. Now that its working (thanks to you) I don't want to modify it anymore. Please understand. alsamixergui is no issue.\\:D/

Thanks.

---

### Post by lidex on 2010-08-06
Great. You really don't want to tempt fate. I'd leave it alone as well ;)

---

### Post by linuxyogi on 2010-08-07
> **lidex said:**
> Great. You really don't want to tempt fate. I'd leave it alone as well ;)

There's a problem, a big one. Actually I did not realize this until now.

Please visit [http://ubuntuforums.org/showthread.php?t=1547693]("http://ubuntuforums.org/showthread.php?t=1547693")

Is the workaround responsible for this ?

I am suspecting the workaround because of this ............

[http://ubuntuforums.org/showthread.php?t=1494594]("http://ubuntuforums.org/showthread.php?t=1494594")

Look at the second post. Looks like this is a sound related issue.

I am uninstalling "indicator-sound". Let's see if that solves the issue.

It will be really difficult for me to give up surround sound.

I am no expert on Pulse Audio but one thing I have realized is it is nothing but trouble.

I wonder why was Pulse Audio used in a stable operating system like Ubuntu.

I really pray that they will remove pulse audio by at least the next LTS release.

I hope you are not a pulse audio fan or I will be dead !!!

Thanks.

---

### Post by lidex on 2010-08-07
I'm not sure how the two are related. Check your dmesg and syslog.

---

### Post by linuxyogi on 2010-08-07
> **lidex said:**
> I'm not sure how the two are related.

These guys here --------

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813]("https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813") 

are trying to solve the issue.

> **lidex said:**
>  Check your dmesg and syslog.

Posting my dmesg or syslog here may rather prove useful but they are both quite huge in length. I wonder if it will be possible to post them as they keep growing as I try to read them.

I tried 

dmesg |tail 

*No mention of polkitd there.*

dmesg |grep polkitd

*Nothing*

I hope someone will respond to that thread.#-o

Thanks for all your support.

---

### Post by linuxyogi on 2010-08-07
Deleting the this file "~/.pulse-cookie" seems to have corrected the problem.

Got the idea by reading this 

[https://bugs.launchpad.net/ubuntu/+s...-1/+bug/572813](https://bugs.launchpad.net/ubuntu/+s...-1/+bug/572813).

---

### Post by linuxyogi on 2010-08-09
Hi, lidex

Sorry to bother you again.
My pc is running fine.
This time its my friend's laptop I am writing about.
I upgraded his alsa installation using your script.

The problem is

When a headphone is plugged into the headphone jack there is no audio . Previously (i.e. before upgrading alsa the headphone jack was outputting audio but the problem was that sound was coming from both the headphones & the internal speaker simultaneously.

These are the details of the laptop --------

uname -a
Linux mylaptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



dpkg -l |grep alsa
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                           1.0.22-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                       1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA


head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20583 (Pebble HSF)

He will visit my place on Friday. In the mean time, if you need anymore details please just ask I will get them from him via mail or phone.

Actually I did start a thread about this laptop's audio problem but that was about the internal mic not working. This is the thread ----

[http://ubuntuforums.org/showthread.php?p=9698155#post9698155]("http://ubuntuforums.org/showthread.php?p=9698155#post9698155")

I am pasting the above mentioned details there as well. 

If you feel that I should start a new thread for this, tell me & I will do that.

This is the laptop 
[http://www1.ap.dell.com/in/en/business/notebooks/laptop-vostro-1014/pd.aspx?refid=laptop-vostro-1014&cs=inbsd1&s=bsd]("http://www1.ap.dell.com/in/en/business/notebooks/laptop-vostro-1014/pd.aspx?refid=laptop-vostro-1014&cs=inbsd1&s=bsd")

Thanks in advance.:D

---

### Post by linuxyogi on 2010-08-21
One thing that I missed about alsa upgrade script & that is it needed  to rerun it with the "-i" option each time you update your kernel.

[http://ubuntuforums.org/showthread.php?p=9749056#post9749056]("http://ubuntuforums.org/showthread.php?p=9749056#post9749056")   [Solved]

---

