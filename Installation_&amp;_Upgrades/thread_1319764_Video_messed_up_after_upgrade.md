---
title: "Video messed up after upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Thoralex on 2009-11-08
Hi, sorry if this has been up before, i searched a didn't find anything

After upgrading to 9.10 yesterday the colors are suddenly messed up when i watch video. Kind like watching negatives. I tried both VLC and the media player, and I've tried mpg, wmv and avi and get the same thing everywhere. 

Anyone know what this could be?

---

### Post by Krallus on 2009-11-08
I just upgraded myself.  Open Totem (Movie Player) and go to Edit=>Preferences=>Display and click "Reset to Defaults".  I'm noticing that the image flickers when there's fast panning, though .. which is another problem entirely.  I'd be interested to know if you or others are experiencing that as well.

---

### Post by lidex on 2009-11-08
> **Krallus said:**
> I just upgraded myself.  Open Totem (Movie Player) and go to Edit=>Preferences=>Display and click "Reset to Defaults".  I'm noticing that the image flickers when there's fast panning, though .. which is another problem entirely.  I'd be interested to know if you or others are experiencing that as well.
Are you using compiz? If so you may want to edit some config options. Go to 
"System>Preferences>CompizConfig Settings Manager" Under "General Options" the "Display Settings" tab. Uncheck "detect refresh rate". Set the refresh rate to your monitor's default. Check the option for "Sync to VBlank".

Here"s mine:

---

### Post by Krallus on 2009-12-30
Thanks, lidex!  I finally got around to trying this.  I first tried the manual refresh rate, but that made no difference.  Checking "Sync to VBlank", however, was the cure.  I changed the refresh back to auto-detect and video remained good.  I noticed that "Sync to VBlank" is an option that appears in a couple of places in the NVidia XServer configuration screens as well.  For NVidia, at least one is enabled and one is not.  I haven't touched those, but I'm wondering if I should.  For everyone else reading this, my searching into this also revealed that the "flickering" I was reporting is technically called "screen tearing": [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

---

