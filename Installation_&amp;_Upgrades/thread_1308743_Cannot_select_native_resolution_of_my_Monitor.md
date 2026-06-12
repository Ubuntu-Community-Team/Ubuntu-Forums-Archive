---
title: "Cannot select native resolution of my Monitor"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Meroveus on 2009-10-31
video card:  nvidia GEForce 7600 GT
driver:  1.90 (from nvidia) I also tried 1.85 from distro w/ same result.

running 
sudo nvidia-settings
allows me to select from a range of resolutions, however the native resolution of my Samsung SyncMaster 915N is 1280x1024, and it is not on the list.

I tried following the man page for xrandr, but although afterwards xrandr reported that the mode was available, it was not in the list of resolutions of nvidia-settings.

In the xorg.conf from my ubuntu 6.10 installation I had several modes, including the 1280x1024, however copying the display section from that xorg.conf into the xorg.conf or my 9.10 installation did not work -- the mode is not in the list of selectable modes.

Incidentally, my 6.10 runs on the same machine, and happily gives me 1280x1024 using that card and monitor.

I'm suspecting that nvidia-settings is trying to read the monitor resolutions available from the monitor itself and failing.  I use a KVM switch, but my windows XP and EdgyEft both work through the switch, and both work.

Help appreciated.
--Meroveus

---

### Post by Turtle.net on 2009-10-31
I don't know, it's maybe a shoot in the dark, but have you tried to launch nvidia-settings and then select "X Server Display Configuration"
Can you select a Resolution you want ?
If not go to X Screen and try to create a create the MetaMode you may require.

Hope this can help ...

---

### Post by ROY.G.BIV on 2009-10-31
Try specifying the horizontal and vertical refrsh rates.. they'll look something like:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1708FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

```You'll need to look up the make and model of your monitor though to get these numbers right.

It is also possible that support for that monitor has been dropped. I say this because you said it worked in 6.10, but not in 9.10

---

### Post by cariboo on 2009-10-31
Try running **nvidia-xconfig** in a terminal, that's what I had to do to get my KDS VS-190 CRT to display the proper resolution. Once you run the command, you'll have to reboot.

---

### Post by Meroveus on 2009-10-31
[quote=Roy G. Biv]I don't know, it's maybe a shoot in the dark, but have you tried to launch nvidia-settings and then select "X Server Display Configuration"
Can you select a Resolution you want ?[/quote]I can do that, however the resolution I want is not on the list -- I'd like to know how to get it there.

[quote=Caribou]Try running **nvidia-xconfig** in a terminal[/quote]Yes, I did that immediately after installing the nvidia driver.  I deleted xorg.conf before doing so to ensure that it was a "clean" file.  The xorg.conf does not seem to recognize settings in the monitor section.

[quote=turtle]You'll need to look up the make and model of your monitor though to get these numbers right.

It is also possible that support for that monitor has been dropped. I say this because you said it worked in 6.10, but not in 9.10[/quote]You might be on to something there, but a monitor is a monitor -- right?  If I get the mode right, it should just work, should it not?

---

### Post by ROY.G.BIV on 2009-10-31
I'm turtle? Lol. :D Think you got the quotes mixed up.

As per your question: you'd think so, but I'm not totally sure... I've heard of monitors not working before, but i think a driver fixes that.

---

### Post by Meroveus on 2009-11-01
*solved*
In the xorg.conf in the "Monitor" section are the following two lines:
```
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
```I found the manual for this monitor on line, and in the specifications section it actually had the following values listed:
```
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
```When I entered those values and restarted XServer, what should appear but all the modes my monitor is capable of -- and a few more besides.

Roy gets the nod for nailing the problem.  The original file had numbers for those  values so I had thought that the driver read them from the monitor.  Guess not.

Thanks to all who took the time to suggest anwsers.
--Meroveus

---

