---
title: "Help with sound driver."
date: 2010-06-14
forum: Hardware
---

### Post by Jadiction on 2010-06-14
Now, i probably sound like a noob here, xD. But i am new to Ubuntu and i have no sound. It's my friends TOSHIBA laptop. I couldn't find any audio drivers for it on the site, so please help. Thanks.

---

### Post by Sylos on 2010-06-14
This could be a lot of different problems with many causes (most of which I dont understand).

Have you made sure the volume control is up (a common issue with it being muted by default).

Have you tested it through the preferences-sound menu?

---

### Post by Jadiction on 2010-06-14
Yes, i have. And i even plugged it into headphones and speakers that work to see if was the built in speakers. Usually, i would think Ubuntu updates would take care of the audio driver.

---

### Post by Sylos on 2010-06-14
Normally it would I think.
 Try 
[HTML]sudo alsa force-reload[/HTML]


tell me what you get.

---

### Post by Jadiction on 2010-06-14
Didn't work. =/ It said "Output information may be incomplete and unloading ALSA sound driver modules: (none loaded)."

---

### Post by Sylos on 2010-06-14
Sounds like you need some form of sound drivers loaded. 

Which Ubuntu version are you on?

I know there are a lot of options for sound. I use alsa so you could just try and install alsa.

---

### Post by Jadiction on 2010-06-14
Just plain Ubuntu. And can you give me a download link? I'll try it out. Anything to fix this sound.

---

### Post by Sylos on 2010-06-14
By version I meant release eg. 10.04 Lucid Lynx (the latest one). I ask because it may mean it uses a different sound set up.

That being said if you are willing to run with alsa regardless of what your system does by default (cant see any reason why it should matter but then Im no expert) then just type the following at the terminal:

```
sudo apt-get install alsa
```

That should install it once you have entered your password and hopefully all will be well.

Let me know how it goes.

---

### Post by Jadiction on 2010-06-14
It said alsa-base is already the newest version, 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Sounds like it already have it. But when i got to sound preferences, it doesn't give an option to choose that device to configure. Which sounds like there is not going to be anything for the audio device to confirm.

---

### Post by Sylos on 2010-06-14
Sorry to say im running out of ideas.

I think the recent versions of Ubuntu use Pulseaudio as manager for muliple sounds. 
Try using the following commands:

```
killall pulseaudio
```

```
pulseaudio
```

Keep me posted.

---

### Post by Jadiction on 2010-06-14
It said: 
"E: pid.c Daemon already running.
E: main.c pa_pid_file_create() failed."
No idea. It's okay that you're running out of ideas. At least, you're helping. ;D

---

### Post by Jadiction on 2010-06-14
=/

---

### Post by Sylos on 2010-06-14
My final suggestion for tonight is try 

```
aslamixer
```

and try turning all the volume levels up from there.

Other than that I can only suggest lots of googling and searching the forums. I shall have another look at this tomorrow and see if I can come up with any more ideas for you.

Good luck!

---

### Post by Sylos on 2010-06-15
Please test the sound on a number of different programs eg. rythm box, totem, etc and test the system alert sounds and see if any of them give a sound.

Also we should see if your audio card is being detected. 
Try:

```
cat /proc/asound/cards
```

then...

```
cat /proc/asound/modules
```

then..

```
aplay -l
```

Post the results and I will do my best to read them.

---

### Post by lidex on 2010-06-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by B-Mart on 2010-08-29
I have been having about the same problem, that I can not get any sound from my speakers, headphone jack, or even my mic input (as well as the one built into the computer) I dunno about the webcam built in, I haven't tested it yet...but as far as it goes I am really digging ubuntu...haha, as it goes, I have been following along this thread and have ran into the same problems...so I am going to post my terminal as per Lidex's request, though I don't really get what you mean by posting per code tags..do you mean I leave out my computer nonsense?

```

 uname -a
Linux Achewood 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
ii  alsa-base                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                               1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                               4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                       0.10.28-1                                       GStreamer plugin for ALSA

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 270

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVCTG

```I am using a HP G72 though as far as specifics im not terribly sure, It's pretty new, seeing as I just bought it the other day (august 26th)

---

### Post by lidex on 2010-08-29
> **B-Mart said:**
> I have been having about the same problem, that I can not get any sound from my speakers, headphone jack, or even my mic input (as well as the one built into the computer) I dunno about the webcam built in, I haven't tested it yet...but as far as it goes I am really digging ubuntu...haha, as it goes, I have been following along this thread and have ran into the same problems...so I am going to post my terminal as per Lidex's request, though I don't really get what you mean by posting per code tags..do you mean I leave out my computer nonsense?

```

 uname -a
Linux Achewood 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
ii  alsa-base                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                               1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                               4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                       0.10.28-1                                       GStreamer plugin for ALSA

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 270

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVCTG

```I am using a HP G72 though as far as specifics im not terribly sure, It's pretty new, seeing as I just bought it the other day (august 26th)

Alsa is using the generic parser for your codec chip, so it's definitely new. At this point an alsa upgrade is called for. Use the link in my sig.

---

### Post by B-Mart on 2010-08-29
Right on! I checked out that link and it totally works now, along with my Mic. Issues, I still have to see if my webcam will work, but thats very back burner compared to my new problem

...Can't Play a DVD...And here I was hoping to finish the last hours of my shift watching Black Lagoon...But I am sure it's just a driver issue of some sort, So I will go look somewhere else.  Anyway, Thanks for the help Lidex, YOU SIR...are "The Man"

---

### Post by lidex on 2010-08-29
> **B-Mart said:**
> Right on! I checked out that link and it totally works now, along with my Mic. Issues, I still have to see if my webcam will work, but thats very back burner compared to my new problem

...Can't Play a DVD...And here I was hoping to finish the last hours of my shift watching Black Lagoon...But I am sure it's just a driver issue of some sort, So I will go look somewhere else.  Anyway, Thanks for the help Lidex, YOU SIR...are "The Man"

For DVD check into these:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

