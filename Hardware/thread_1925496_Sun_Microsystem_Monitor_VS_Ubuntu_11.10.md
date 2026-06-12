---
title: "Sun Microsystem Monitor VS Ubuntu 11.10"
date: 2012-02-14
forum: Hardware
---

### Post by jedimind625 on 2012-02-14
Hi everybody I'm new to the Linux scene and just got Ubuntu 11.10 up and running on my desktop. The only problem I am having is my regular monitor comes up with a message stating "Outside Scan Range, Please change settings" when the Ubuntu GUI comes up. I am currently using a dusty old backup I'm glad I kept.

So once again the PC is a Acer tower running Ubuntu 11.10
the monitor is a Sun Microsystems N218. not sure if that's the model number but it's the only one that appeared to be, there's also a serial number on the back if anybody knows how to analyze that.

---

### Post by ajgreeny on 2012-02-14
What does the system > preferences >display (or possibly "monitors") show as the resolution and refresh rate?  Not sure how you get to that in 11.10, I'm afraid, but search with the dash to see if you can find either.

Let's see the output from the command ```
cat /etc/X11/xorg.conf
``` which will show us if there is a setting in that which can be removed.

---

### Post by jedimind625 on 2012-02-15
ok well i must the super noob, i tried to use that a few different ways and i'm not sure how to use the command line...like i said i just installed linux for the first time, so is there anyway you can help me with a step by step or point me towards a crash course in the terminal?

the linux community has a rep for busting on noobs like me for asking questions like "how to use command line?" so please, take it easy, i know about RTFM and i'm not trying to get around that, just want to get my good monitor working so i can finally retire this tired <snip> i'm using and then finally RTFM.

---

### Post by jedimind625 on 2012-02-15
i attatched a screen shot of my terminal when i tired to use that command...thank god that part is the same as in windows lol.
thanks i appreciate the help man.

---

### Post by nothingspecial on 2012-02-15
Hi, rather than attaching a screenshot of your terminal, copy the output, click the # in the formatting options at the top of the posting box and paste the output inside.

---

### Post by Grenage on 2012-02-15
> **jedimind625 said:**
> i attatched a screen shot of my terminal when i tired to use that command...thank god that part is the same as in windows lol.
thanks i appreciate the help man.

You don't have an xorg.conf, which is why the file won't open; there's nothing unusual in that, not these days.

Could you reply with your desired resolution, the model/make of the monitor, and the output of:

```
lspci | grep VGA
```

---

### Post by jedimind625 on 2012-02-15
ok so here is the info on the monitor, obtained from this link:
[http://www.computerdisplays.co.uk/21%20inch%20monitors/sun%20gdm.htm](http://www.computerdisplays.co.uk/21%20inch%20monitors/sun%20gdm.htm)
Sun Microsystems 21" flat screen CRT, model GDM5410
1880 x 1400 @ 85Hz. Resolution

the code you asked me to input gave me the following
 ```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

tod@jeditower:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
tod@jeditower:~$ 
```

thanks again

---

### Post by Grenage on 2012-02-16
Ok, this is a very basic xorg.conf which will probably work.  First things first, make sure you've got a liveCD handy; you'll need that on the off-chance that the config stops the PC booting properly.  If that happens, you can simply boot from the CD, and delete the config file.

First, open gedit as root:

```
gksu gedit /etc/X11/xorg.conf
```

Paste in the following config:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Sun"
	ModelName "GDM-5410"
	HorizSync 30 - 121
	VertRefresh 48 - 160
EndSection

Section "Device"
	Identifier "Device0"
	Driver "radeon"
	VendorName "ATI"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1880x1400"
	EndSubSection
EndSection
```

That's using the open Radeon driver.  Save the file and reboot the PC!

---

### Post by jedimind625 on 2012-02-18
Success!
So if I follow what we just did, I didn't have the file ajgreeny asked me about, but then I created it with the command line prompt Grenage told me, then saved the file with the rest of the info he posted for me, which is based on the information obtained on the monitor from computerdisplays.co.uk?
Whatever it was the monitor looks great, thanks again everybody.

---

### Post by Grenage on 2012-02-20
That's right;  we basically just gave it the information it needed, and told it what resolution etc to run. :)

---

