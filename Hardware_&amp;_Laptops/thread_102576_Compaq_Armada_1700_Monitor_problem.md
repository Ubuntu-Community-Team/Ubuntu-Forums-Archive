---
title: "Compaq Armada 1700 Monitor problem"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by pilotcp on 2005-12-12
Hello all!
so i have had version 5.10 on my compaq armada 1700 and i notice that i don't get the full screen on my monitor...it looks like ther is a 2 inch border of unused monitor space on my computer. kinda like this

|-------------------------------|
|...Black, Empty, Unused Space..|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|.....XXXXXUBUNTUXXXXXX........|
|...Black, Empty unused space....|
--------------------------------|

granted, the example above isn't spaced correctly, as everything shows up in a rectangle right in the center of the screen, with equal distance on all sides, and i also know that this picture will show up funny on some computer, so i hope i didn't confuse anyone with the pic!

so as you can see, not all my monitor space is being used!
I remember i used to have screen resolution problems before with version 4 ubuntu and i was told to check out a file in /etc/X11/Xf86config-4 to change the screen resolution, so i thought maybe a similar setting was the cause of the problem, but i don't have that file to look in. 
does anybody know how i can strech the screen to use all of the viewable space on the monitor?
or is this maybe a hardware problem? i know that on a normal desktop monitor, there are setting for this kinda thing, but my laptop doesn't seem to have that feature, as it only have brightness and contrast, and a monitor selection button, if you wanted to switch a desktop monitor and the laptop monitor...
oh, and btw, i did try plugging in a desktop monitor, and it worked just fine...

any ideas? opinions? rude remarks  ?

also i apoligize to any ascii artists here, you are very good, i am not!

Thanks, Charlie

---

### Post by pilotcp on 2005-12-13
anybody?

---

### Post by byourg on 2005-12-17
You need to add the horizontal & vertical refresh rates to get the screen full size. In the /etc/x11/xorg.conf file add the code for them in the Monitor section.
Reboot the laptop to take effect.
```
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
```

I have a Armada 7400 and this worked for me.

---

### Post by NotJustANewbie on 2005-12-17
I had this problem with my Compaq, Try [BeatriX]("http://watsky.net") (worked beautifully for me, and fast!)

---

