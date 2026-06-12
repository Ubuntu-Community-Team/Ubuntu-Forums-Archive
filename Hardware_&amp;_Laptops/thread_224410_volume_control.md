---
title: "volume control"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by runoverbobby on 2006-07-27
I'm running KDE on a Sony VAIO VGN-FS640. I HAVE SOUND, but no control over the volume. The volume controls and mixer in the KDE system settings doesn't have any effect. Neither does the desktop icon for master volume.

This might be normal, and sorry if its already been mentioned, but the only threads i've seen are dealing with problems involving a complete and total lack of sound. 

anyone have a fix?

---

### Post by spier on 2006-07-28
I got my vaio fs function keys working following [this gentoo howto]("http://forums.gentoo.org/viewtopic-p-2722251.html#2722251"). May have nothing to do with your problem, maybe does.

---

### Post by Shay Stephens on 2006-07-28
I changed the keyboard shortcuts to control up arrow for volume up, control down arrow for volume down, and control end for mute.  It works great and is right at my finger tips too.

If you go to system, preferences, keyboard shortcuts, and scroll down to sound you will find the options there.

---

### Post by runoverbobby on 2006-07-28
Thanks for the shortcuts, those will be useful. Unfortunately I didn't have any luck with either of those suggestions. I can adjust the volume "bar" (aka move the sliders), but it doesn't affect the actual sound. Any other ideas?

---

### Post by spier on 2006-07-28
I'm not on my linux computer right now, but if i remember correctly, this behavior may be due to a wrong sound setting, like default output directing to headphones, or front jacket, or ..., something like that? :-k

---

### Post by ltmon on 2006-07-29
> **spier said:**
> I'm not on my linux computer right now, but if i remember correctly, this behavior may be due to a wrong sound setting, like default output directing to headphones, or front jacket, or ..., something like that? :-k

Yes you're right, it can be a problem especially with newer chipsets.  I have this problem on my Asus Z96J, which has an Intel HDA sound card.  The volume slider/shortcut keys adjust the "headphone" channel, but this is the wrong channel, and it really doesn't change any volumes at all.

The best workaround I have so far is to assign shortcut codes XF86AudioRaiseVolume, XF86AudioLowerVolume and XF86AudioMute to the correct keys using xmodmap (search for xmodmap in this forum or the wiki... there are many howtos).  This got the on-screen-display for volume keys working, but it was still adjusting the headphone channel.

I then assigned the volume up and down shortcuts to volume up and down in Kmix.  Kmix is the little speaker icon that is in your system tray.  It can be launched from the kmenu if it isn't there.  Click on the icon to show the volume and then click "Mixer".  This will allow you to get to the menus and assign global shortcuts.

Next right click on the kmix icon and choose "Select Master Channel...".  Now you should select a different channel to your non-working channel.  "Front" or "PCM" are common channels that may work.

Next you have to restart KDE, because kmix is still not getting those shortcuts keys.  They are being intercepted by another program which does the pretty on screen display, but adjusts the wrong channel.  When you restart KDE, kmix will start getting the shortcuts.

And now you should have working volume changing, but without the pretty on-screen display.

To fix this properly ALSA needs to start reporting the correct master channel for the soundcard.  Things you could try if you are adventurous is compiling a new version of ALSA, or setting some options on your sound module to try and fix it.  You can do a "modinfo" command to get the options available, for example on the Intel HDA card:
```

ltmon@clifford:~$ modinfo snd_hda_intel
filename:       /lib/modules/2.6.15-26-686/kernel/sound/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.15-26-686 SMP preempt 686 gcc-4.0
depends:        snd-pcm,snd-page-alloc,snd-hda-codec,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
srcversion:     A2D78B5840326DB499FE8D0
parm:           enable:bool
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)

```

I've tried mucking around with both of these, but no luck so far.

L.

---

### Post by mrfuzzemz on 2007-01-04
I found disabling the Ubuntu shortcuts and customizing them with keytouch and keytouch-editor worked wonders.  I even set up an eject cd key and gmail key. You can right click on the audio icon  in the panel to change it to watch "Front", "PCM" or whatever you've configured.

---

### Post by olavjunior on 2007-08-19
> **ltmon said:**
> 

I then assigned the volume up and down shortcuts to volume up and down in Kmix.  Kmix is the little speaker icon that is in your system tray.  It can be launched from the kmenu if it isn't there.  Click on the icon to show the volume and then click "Mixer".  This will allow you to get to the menus and assign global shortcuts.


L.

Any idea of how to do this in gnome?

---

