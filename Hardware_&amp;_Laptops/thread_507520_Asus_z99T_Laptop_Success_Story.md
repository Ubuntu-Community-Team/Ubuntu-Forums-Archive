---
title: "Asus z99T Laptop Success Story"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by Jhongy on 2007-07-23
Success story here with Feisty on an Asus Laptop. The model number is z99T, but I believe this is country-specific -- it's a Turion x2 TL52, nVidia Go 7300, Atheros wireless & MCP51/Azalia audio.

(That specific model is supposed to be sold here with Red Flag Linux -- the reason I selected it. As far as I can tell though, it was just a ruse for pre-installing 'fake' windows -- when I picked up the laptop, I got led 'out the back', where they asked me if I wanted my OS in Chinese or English... and promptly whipped out an XP CD. By the time I realised this and told them that I actually wanted Linux, they had already formatted HDD.... oh well)

The wireless worked flawlessly immediately after install, no configuration required. A restricted driver was pre-selected for the Atheros chipset at very first boot.

The screen resolution of course was not set as it should be -- but this is Ubuntu, that what we've come to expect, eh! Installing the nVidia restricted driver, and then adding 1280x800 to each of the mode lines in my /etc/X11/xorg.conf solved the problem easily.

Sound was not detected correctly, as is the case with many users of this sound chipset. But with the help of [this post](http://ubuntuforums.org/showpost.php?p=2013895&postcount=17) about snd_hda_intel, I got it working. NOTE: The mode was not 'asus', but '3stack'. (I still have to try 'laptop', which may be a better match.)

The Synaptics touchpad worked straight away, but scrolling and drag-n-drop didn't work. I checked in my xorg.conf again, and there was no mention of a synaptics touchpad. A quick search of this forum turned up the correct block and line to add to my xorg.conf. Most references state that in anything other than dapper or earlier, this should already be there -- it wan't, but no big deal. After restarting X, I then installed gsynaptics, and set up the touchpad using the GUI -- got it working perfectly.

Suspend to RAM works OK, although things appears to be a bit flaky afterwards (e.g. it crashes on shutdown if it has been suspended since last reboot) -- I still have to play with the options. IME flaky ACPI is par for the course for Asus on Windows too -- but I'm sure I can fix it.

Other power management features seem to be fine.

Fn buttons for screen switch, brightness-down and volume all work as expected. Brightness-up doesn't work, however, and while the wireless on/off key turns the LED on and off on the laptop, it doesn't seem to affect wireless operation. I expect these will be fixable, but haven't searched yet. (tip: If you've turned the brightness down and want to turn it back up, you can do so via the power management panel).

Beryl installed without a hitch and runs smoothly. Flipping the cube with the touchpad scroller is smooth & easy.

DVD writer seems to be working flawlessly.

I suppose the fact that many of Asus' laptops are advertised as being pre-loaded with Linux is a good sign -- and the reason I was drawn to them in the first place. (even if the people selling them, in my case, couldn't care less about Linux). An AMD model with the atheros wireless chipset seems to be an excellent choice for people wanting to avoid the frustration often associated with wireless.

The only real negative to weigh up is that I have, in the past, have had a very, very poor experience with Asus customer support -- not responding to e-mails or doing anything about a flaky motherboard that was under warranty. This was several years ago, however, so I have given them the benefit of the doubt this time around.

All in all, this is a very good choice for an Ubuntu laptop, with the issues above proving only to be of minor frustration.... and no Windows Tax!!!!

It cost around $900 -- at the low end of the laptop price range..... so definitely two thumbs up!

---

### Post by petri on 2007-07-28
Nice to read success stories  :popcorn:

I have an similar Asus (F3T) with GeForce 7600, Turion64 x2 and Atheros and with exactly same results. I have to add 1280x800 to xorg.conf and the brightness doesn't go upp again with functions keys but otherwise everything works great even the horizontal scrolling :)

The story I followed is here [http://www.linux-on-laptops.com/asus.html](http://www.linux-on-laptops.com/asus.html)

---

