---
title: "Microphone Input Solution"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by jjalocha on 2007-04-22
This is my experience with microphone input problems, and how I solved them. Many people are having different problems with microphone input in Ubuntu, so I hope this post is helpful for  some of them.

Both, with Edgy and Feisty, [my hardware]("http://ubuntuforums.org/showthread.php?t=367898") gets detected correctly out of the box, but I was unable to record anything, using a microphone plugged into the jack.

This is my soundcard:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

[FONT="Fixedsys"]lspci[/FONT] gives different output in Edgy and Feisty:

Edgy:

```

$ lspci
[...]
00:14.2 Audio device: ATI Technologies Inc Unknown device 4383
[...]

```

Feisty:

```

$ lspci
[...]
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
[...]

```

The solution needs the [FONT="Fixedsys"]alsamixer[/FONT] and [FONT="Fixedsys"]amixer[/FONT] command line tools. If they aren't installed already, you need to install the 'alsa-utils' package (using for example Synaptic).

From the command line, you can use [FONT="Fixedsys"]alsamixer[/FONT]. Use TAB for selecting the 'Playback', 'Capture' or 'All' window, and use LEFT/RIGHT to select the desired control. You have to make sure you get the following settings right (*all of them*):
[LIST]
[*]All channels must be non-zero (use UP/DOWN).
[*]'Capture' must be enabled (use SPACE).
[*]Select the correct 'Input Source' if you have more than one. (I only have 'Mic'.)
[/LIST]

In my case, i had to enable 'Capture'. This is how it looked before the change (not-working). Note dashed line above 'Capture':

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=30447&stc=1&d=1177251877[/IMG]

And this is how it looked after getting it right. Note red 'CAPTUR' tag above 'Capture':

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=30446&stc=1&d=1177251877[/IMG]

Activating capture can be done easier  with the [FONT="Fixedsys"]amixer[/FONT] tool:

```

$ amixer set 'Capture' cap

```

If the configuration gets lost after each reboot, then you can make the cnahge permanent adding this line to '/etc/rc.local' file, before 'exit 0'.

Simply typing [FONT="Fixedsys"]amixer[/FONT] in the terminal puts out your current settings. In my case, when 'Capture' was disabled, both channels were '[off]':

```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 9 [60%] [13.50dB] [off]
  Front Right: Capture 9 [60%] [13.50dB] [off]

```

After enabling it:

```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 9 [60%] [13.50dB] [on]
  Front Right: Capture 9 [60%] [13.50dB] [on]

```

[2007-04-22 EDIT: Added /etc/rc.local fix.]
[2007-04-23 EDIT: Better explained.]

---

### Post by El Viejo Lobo on 2007-04-22
Maybe I get get some help if somebody will look at:
[http://ubuntuforums.org/showthread.php?p=2511758#post2511758](http://ubuntuforums.org/showthread.php?p=2511758#post2511758)
:lolflag:

---

### Post by jjalocha on 2007-04-23
Since it seems that the wording in my first post was not clear enough, I have edited it, and tried to be more precise.

---

### Post by jjalocha on 2007-04-23
Here's another happy (Edgy) user that got his mic working with another method:
[http://ubuntuforums.org/showpost.php?p=2515413&postcount=3](http://ubuntuforums.org/showpost.php?p=2515413&postcount=3)

---

### Post by _mOrgoth_ on 2007-05-16
THX MAN... IT HELP!!!!  Respect!! :lolflag:

---

### Post by pillu on 2007-05-19
Thanks for the help...I can't believe the solution was so simple....I was dreading that I had to install a alsa from source or something...turns out, i just have to turn the capture on

thanks
pillu

---

### Post by jjalocha on 2007-05-19
I'm glad this was useful!

There's been reported [another solution]("http://ubuntuforums.org/showpost.php?p=2619195&postcount=3"), which seems to help when the files '/etc/asound.names' or '/var/lib/alsa/asound.state' are missing:

```

$ sudo alsactl names
$ sudo alsactl store
$ sudo reboot

``` 

Be careful, though, since this might screw up your whole configuration!

There's [another solution]("http://ubuntuforums.org/showpost.php?p=1357412&postcount=23") with kernel modules for STAC hardware.

Don't forget there seems to be also a solution with kmix (works also under Gnome).

---

### Post by euchrid on 2007-06-07
I didn't have '/etc/asound.names' or '/var/lib/alsa/asound.state' on my system - apparently, you don't *necessarily* need them - but systems seem to vary quite widely.

I found I had to update the Alsa drivers. I explained how I did it in this post: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Hope this is useful to someone. It was killing me for hours!

---

### Post by omarabdelhaleem on 2008-03-21
Thanks! Now I am really up and running. :)

---

