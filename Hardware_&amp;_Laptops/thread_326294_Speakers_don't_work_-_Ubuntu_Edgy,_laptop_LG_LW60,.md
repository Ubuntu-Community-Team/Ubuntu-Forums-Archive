---
title: "Speakers don't work - Ubuntu Edgy, laptop LG LW60, C-Media 9880"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Funto66 on 2006-12-27
Hello,

I've installed Ubuntu Edgy on my laptop LG LW60 Express, which has a C-Media 9880 soundcard, and I can't get any sound on my speakers :(

The card is recognized by Ubuntu, in so far as when I plug external speakers on my soundcard, I can get audio output, but I never managed to get sound on the laptop speakers :(

Also, I don't have any audio input...

Does someone have any idea? Should I give some more information? What should I do?

Thanks in advance.

---

### Post by ORBiTrus on 2007-02-19
[Appologies to forum for answering an old thread - it's a google hit, so...]

This is what I *just* did:

a) Load the module with a model specified (any one seems to work)
b) Unmute center/subwoofer


--------------- Details for anyone NOT used to Linux ----------------

OK, first we need to set a model for the hda-intel driver.  For some reason the auto-discover won't enable the speakers.

Your model options are:
minimal : 3-jack in back
min_fp : 3-jack in back, 2-jack in front
full : 6-jack in back, 2-jack in front
full_dig : 6-jack in back, 2-jack in front, SPDIF I/O
allout : 5-jack in back, 2-jack in front, SPDIF out
auto : auto-config reading BIOS (default)

You can test them out by
 - Removing ALL audio devices - this includes the volume control applet in the panel.
 - Opening a terminal, and becoming root by typing "sudo su" (alternatively, prefix all commands with "sudo")
 - As root, remove the hda-intel driver: "rmmod snd-hda-intel"
 - As root, load the hda-intel driver: "modprobe snd-hda-intel model=minimal" [this is the model my LW60 uses]
 - Now, this is important, since when nothing is connected to line-out, the Center/Subwoofer channels control Front-Left and Front-Right output!  Run "alsamixer" and unmute (hit "m" over the channel) the PCM, Center and LFE channels.
 - Test it out: "speaker-test -c2"

If you hear sound, congratulations!  It works!  If not, "fiddle."

With that working, make it so that this model is always the one loaded.  Use your preferred editor to alter the "/etc/modprobe.d/snd-hda-intel.modprobe" file.  Or, just type this, which will empty the file, replacing it with the line echo'd.
"echo options snd-hda-intel model=minimal > /etc/modprobe.d/snd-hda-intel.modprobe"

Other distributions should modify "/etc/modprobe.conf"

In case you're curious, the entimology of the command is that "echo" will simply output whatever comes after it to the screen.  The ">" means that any output from the preceeding is send to the file which comes after it.  Alternatively, there is ">>" which does not empty the file before writing, and "|" which redirects output to a program.

FINALLY, don't worry about the PCM not having a volume control - for some reason, it gains one the first sound you play.

---

### Post by Xtyn on 2007-03-02
Waw, this worked for my LG lw60 express laptop, thanks a lot.

---

### Post by sparttacus on 2007-08-12
with ORBiTrus tutorial,
I had to change the file alsa-base

sudo gedit /etc/modprobe.d/alsa-base

and add:
options snd-hda-intel model=minimal

And it works fine.

Thanks ORBiTrus.

---

### Post by drndrw on 2007-10-23
By reset system, do you mean restart the computer?

---

### Post by Funto66 on 2008-01-07
Wow, I hadn't seen there were answers !

ORBiTrus >> thanks a lot for your explanation, now I got sound ! It seems however that only the right channel works, as when running speaker-test -c2, I don't get any output on the left one.

sparttacus >> thanks too, althought your solution didn't work for me ^^

---

