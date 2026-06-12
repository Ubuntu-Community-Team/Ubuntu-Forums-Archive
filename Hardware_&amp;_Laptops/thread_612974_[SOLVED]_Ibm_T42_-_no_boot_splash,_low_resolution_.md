---
title: "[SOLVED] Ibm T42 - no boot splash, low resolution and ALT+F1 text MASSIVE!"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by tedrogers on 2007-11-14
Hi ubuntu people,

I have just got rid if my T22 in favour of a T42, which I got for free (it was broken) and so I replaced the motherboard for 85GBP and have a fully working 1.7Ghz machine! The only compromise is that my old (burned out) board had the Mobility 9800 on it, and my new one has Mobility 7500 on it.

On installing Gutsy, the live CD works fine (something that never worked with my T22) and it installs fine. However, on first reboot I noticed there was no boot splash at all (just a black screen) and eventually it boots into X and prompts me to login. 

My first question then....why no boot splash? The boot splash worked fine in the live CD, but not when installed?? Weird.

When logged in, all desktop effects work out of the box, as does my wireless (yay!!), but I can't get my resolution higher than 1024x768. I tried reconfiguring the X server, but this just left me with a broken system and X wouldn't start. I had to go back to the back up file created to get it working.

My second question? What can I do to get the Mobility 7500 on a 15" screen to get higher than 1024x768. I know the external monitor connection is capable of very high resolutions...but please don't tell me that the LCD/7500 is limited to 1024x768?

Finally, as part of my tinkering I noticed that doing an ALT+F1 takes me to a terminal outside of X, but the font on screen in absolutely HUGE! I talking like 8 words per line accross the screen...it must be font size 80 points or higher. It also looks bad as you can imagine and is pretty unusable.

My final question then, why would ALT+F1 (and all the others) have such a massive font and is this related to my problems with not getting a boot splash?

Apart from all of that it's great to have a system with some guts behind it for once, rather than my clunky old 800mhz T22!

Any help truly appreciated. Thanks in advance.

---

### Post by l2thet on 2007-11-14
> **tedrogers said:**
> Hi ubuntu people,
My second question? What can I do to get the Mobility 7500 on a 15" screen to get higher than 1024x768. It is capable of a lot more from what I have read.


I can't help with most of the other questions, however this one I can.
First make sure to make a backup of xorg.conf, incase anything goes wrong.  From the problems I have had with my resolution, it was due to the refresh rates in xorg.conf.  This section,

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Your section might not look exactly the same as mine.  The lines that you need to look at are the HorizSync and VertRefresh.  Find out what the ranges are for you monitor (I found mine with a quick google), then update those numbers to what they should be.

After that...
Look for this section

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Again the "Screen" section wont match exactly what I have here, you will more than likely have more than one Depth, this is just a example.
In the "Display" Subsection,
Modes is what defines, the resolutions for X.  Usually I remove the "800x600" and "640x480", and also add my own custom ones, my gaming box xorg.conf for this section looks like this.(Just for the modes)

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" 
	EndSubSection
EndSection


Hope that helps.

---

### Post by tedrogers on 2007-11-14
Thanks for your speedy reply...I will definitely try your suggestion for fixing question number 2.

In the meantime, I thought it might be good for anyone to know that I solved question 1 and 3 by just installing Feisty from scratch. This release doesn't exhibit  the same problems as gutsy in this department for some bizarre reason that completely escapes me! 

Using Feisty I have a nice boot splash (albeit at 1024 x 768 still) and CTRL+ALT+F1 etc works great too!! Nuts!!

I'm now upgrading to Gutsy to see what happens. If all that works I will try your suggestion for the xorg.conf file and let you know.

If anyone else can shed some light on this weird problem then please do chip in. :)

---

### Post by phen on 2007-11-15
same boot problem here with thinkpad x31

will later try to tinker with the vga= settings in grub. how do i turn off usplash for simple text boot? because a black screen is strange

---

### Post by phen on 2007-11-15
[http://ubuntuforums.org/showthread.php?t=610396&highlight=usplash](http://ubuntuforums.org/showthread.php?t=610396&highlight=usplash)


TRY THIS now it works fine for me.

change to your res: /etc/usplash.conf

and type dpkg-reconfigure -phigh usplash



good luck

---

### Post by tedrogers on 2007-11-16
Well it upgraded to Gutsy no probs and I still have a 1024x768 bootsplash...but none of the options suggested above could get me to a resolution higher than 1024x768.

As a further test I kind of went all out and made an image of my system, formated and installed XP, got the XP driver and I couldn't get his higher than 1024x768 either. So I put my Gutsy image back on and I guess that 1024x768 is as high as it can go.

Anyone had a Mobility 7500 higher than 1024x768 using the inbuilt LCD and not the external VGA port?

---

### Post by tedrogers on 2007-11-19
BUMP!

Still no boot splash in Gutsy fresh install on T42...and MASSIVE text in CTRL+ALT+F1 thru CTRL+ALT+F6.

Any ideas.

Really want a fresh install.

---

### Post by LinuxGuy1234 on 2007-11-19
> **tedrogers said:**
> BUMP!

Still no boot splash in Gutsy fresh install on T42...and MASSIVE text in CTRL+ALT+F1 thru CTRL+ALT+F6.

Any ideas.

Really want a fresh install.

Massive text... don't know. For the splash try:
```
sudo dpkg-reconfigure linux-arch
```

Where arch is:
386
486
586
686
k6
k7
amd64
powerpc
generic
(Gusty only and for PS3/PowerPC)
cell

Try 386 or generic if you don't know.

---

### Post by tedrogers on 2007-11-20
Bizarely, either your suggestion or uninstalling and reinstalling ubuntu-dekstop (i.e.sudo apt-get remove ubuntu-desktop --purge, then sudo apt-get install ubuntu-desktop) has solved the massive text issue...or at least made it smaller and more readable. It actually still looks slightly oversized to me but it could be just me.

The other problem of no boot splash and long boot time remains.

On pressing CTRL+ALT+F1 during boot speeds up the process and gives this output:

```

kinit: no resume image, doing normal boot
intel-rng: FWH not detected

```

Any ideas?

---

### Post by tedrogers on 2007-11-20
The long boot time provided the final clue...

The usplash.conf settings were incorrect as per this thread,

[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

Weird but all problems solved now.

---

### Post by helpme!!!!! on 2008-04-11
hey guys i have a problem with my new lenovo t61.
my laptop has NVIDIA geforce video card 2gb ram 120gb sata harddrive(working fine when i bought it) but now every time i turn on my laptop my logon screen is in the lowest resolution and color(the icons are all classic style).i don't no what happened:confused:
then when i fix it the problem comes back when i restart.
can you guys please help me!
thank you so much!!!

---

### Post by tedrogers on 2008-04-11
Have you tried this. Run the following in a terminal. Put in your password when requested.

```
sudo gedit /etc/usplash.conf
```

Change the xres and yres values to these and save the file:

```
xres=1024
yres=768
```

Update the theme with:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

