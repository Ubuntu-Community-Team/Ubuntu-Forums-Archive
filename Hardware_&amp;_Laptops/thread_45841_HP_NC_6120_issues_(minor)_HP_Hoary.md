---
title: "HP NC 6120 issues (minor) HP Hoary"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by JLB on 2005-07-01
Some minor things noticed while running the HP-ized Hoary release on my HP NC 6120:

Wireless nic not always available after suspend or hibernate. Must use the ethernet control panel to deactivate and reactive NIC.

Fan control is sometimes lost after a suspend or hibernate. This one has resulted in occacsional immediate shutdowns due to cpu overtemp (89 degrees). adding a cputemp panel application would be a bonus and possibly alert the user prior to any cpu overtemps. I must shutdown and restart the laptop to regain proper power control. I am currently using the gnome panel applicat emifreqd to monitor cpu temp.

Trackpad acts a little whacky. Tapping actually acts like pressing a middle mouse button at times. Ballistic sensetivity is awefully high. It seems excessive force is required to tap.

The above things are minor in my opinion but do take away from the overall experience enough to consider them an annoyance. I hope to see these addressed in breeezy. Overall impression of HP Hoary on this HP laptop is very good. I highly recommend this laptop for use with Ubuntu.

Regards!

JL

---

### Post by senectus on 2005-07-19
I have a HP NX6120 and am having some really painfull problems with the LCD screen.
I've found that most fonts look really crappy (blurry and "messy" looking).

I also have the ultra sensative track pad.. though it's useable.
I've not noticed anything to do with the fan but I've not looked into it either.. and I haven't had it long enough to test the power management stuff.

---

### Post by mips on 2005-07-21
If you want the fonts to look 'good' on Ubuntu follow this little procedure   [http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)

It makes the worlds difference.

cheers
mips
HP nx6110

---

### Post by JLB on 2005-08-21
TRACKPAD MOUSE ISSUE SOLVED.The ultra sensitive mouse issue and the crazy tapping, tap=middle click, random tap clicks without touching the pad etc. have been solved.

Turns out the synaptics driver is not in the xorg config file and adding 3 more lines solves the random tapping stuff. I now have a fully useable touchpad on my HP NC6120. This has been tested on a stock Hoary and a Breezy installation updated to colony 3.

edit your xorg.conf file and add this to the following sections:
```

Section "Module"
	
	Load	"synaptics"    <---- Add this line 
```

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
	Option     "TapButton1"     "1"    <---- 
	Option     "TapButton2"     "1"    <---- Add these lines
	Option     "TapButton3"     "1"    <---- 
```


Save it and restart X (CTRL-ALT-Backspace). 

Regards!
JL

---

### Post by alleycat on 2005-10-22
Hi everyone,

I am a complete Linux NOOB. First here is a little about how I got here:

My NX6120 came with XP Home preinstalled. Two days ago it crashed. I tried repairing it with the repair cd supplied, to no avail.

That's when I decided: That's it!!!! No more Windows. Fortunately I have access to another notebook and was able to download and burn Breezy.

This I did after an extremely unsuccessful go at installing Solaris (5CD!!!!!). Thankfully I didn't give up and looked for a new distribution (I'm getting with the Linux lingo but I still need clarification or a glossary for some terms I see used quite often) and now I'm writing this using a wireless connection that was configured when I booted up for the first time.

Right now most of my laptop's hardware is configured: The MMC and PCMCIA slots are about the only things I can't seem to get working. 

So if anyone has any hints on how to get these working please let me know.

Thanks,

A

---

