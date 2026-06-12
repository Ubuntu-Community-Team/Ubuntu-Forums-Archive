---
title: "Google Earth missing characters in intrepid"
date: 2008-10-31
forum: General Help
---

### Post by scebert on 2008-10-31
Google Earth worked fine in Hardy, but didn't render correctly at all in intrepid. I disabled compiz and it works, except that it won't render fonts correctly. Certain characters, which change every time it's started, are not visible in the 3D view (see attachment).

---

### Post by jithin1987 on 2008-10-31
Lucky you are getting even that in my case it was like hell.
[http://ubuntuforums.org/showthread.php?t=954222](http://ubuntuforums.org/showthread.php?t=954222)

---

### Post by jaddle on 2008-11-03
I'm seeing the exact same problem. It's very annoying! I managed to get it to work a little better by changing the '3d font' setting in the preferences, but that didn't help at all for the other fonts displayed like the coordinates at the bottom. Very annoying!

---

### Post by jithin1987 on 2008-11-03
Which graphics chipset is yours. Mine is Intel i915 i think, that's what the kernel module loaded which hardinfo says.

---

### Post by jaddle on 2008-11-03
I have a thinkpad x60s. lspci shows this:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by dcstar on 2008-11-03
> **scebert said:**
> Google Earth worked fine in Hardy, but didn't render correctly at all in intrepid. I disabled compiz and it works, except that it won't render fonts correctly. Certain characters, which change every time it's started, are not visible in the 3D view (see attachment).

Do you have the **msttcorefonts** package installed?

---

### Post by jaddle on 2008-11-03
Yes, I do have msttcorefonts.

---

### Post by jithin1987 on 2008-11-03
Mine is also Intel
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
After installing msttcor. Thefonts fonts are getting displayed but nothing is drawn properly. Then I disabled desktop effects in system settings, I use kubuntu. Then it is working fine.
Is there any way to make google earth work with desktop effects?

---

### Post by jaddle on 2008-11-03
> **jithin1987 said:**
> 
After installing msttcor. Thefonts fonts are getting displayed but nothing is drawn properly. Then I disabled desktop effects in system settings, I use kubuntu. Then it is working fine.
Is there any way to make google earth work with desktop effects?

I don't use desktop effects at all, but I still have messed up fonts in google earth...

---

### Post by scebert on 2008-11-03
> Mine is also Intel
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
I have the same graphics controller and msttcorefonts installed, and desktop effects disabled, but the fonts still don't work correctly.

---

### Post by jithin1987 on 2008-11-03
hmm thats strange because I have not done anything else other than having msttcorefonts installed and with desktop effects disabled. My display is still not perfect there are rectangular tracts on zoomed out view. Which ubuntu do u use?

---

### Post by scebert on 2008-11-03
8.10 32 bit.

---

### Post by degenerate141 on 2008-11-03
i had the same problem with missing characters,  i fixed it by going into 3d fonts and changing the script to unicode...

---

### Post by scebert on 2008-11-04
I don't have an option in 3D fonts to change to unicode, just font, size etc.

---

### Post by csy33delight on 2008-11-04
For what it is worth, I installed Google Earth as a supervisor and got this problem. I installed it again, this time as a user, and it worked fine. Go figure.

---

### Post by AlphaMack on 2008-11-04
Count me as another one...ThinkPad R61i with the Intel GM965 integrated graphics.

> **degenerate141 said:**
> i had the same problem with missing characters,  i fixed it by going into 3d fonts and changing the script to unicode...

There is no unicode script.

---

### Post by degenerate141 on 2008-11-05
> **AlphaMack said:**
> Count me as another one...ThinkPad R61i with the Intel GM965 integrated graphics.



There is no unicode script.






lies.

---

### Post by degenerate141 on 2008-11-05
which version of google earth do you have?

---

### Post by AlphaMack on 2008-11-06
4.3.7284.3916, straight from the Medibuntu repos.

---

### Post by geopgeop on 2008-11-06
I'm having the same problem as well. I'm running Google Earth 4.2 on Ubuntu 8.10 Intrepid with an Intel 945GM chipset (xserver-xorg-video-intel 2:2.4.1-1ubuntu10) on my Toshiba Satellite P105 laptop. (4.3 doesn't work due to a myriad of other reasons, but that's not the issue here.)

Wiggling with the 3D font settings helps somewhat, so that only certain numbers are missing, such as the 0's in 2008 on the copyright notice, etc., but it doesn't stick.

---

### Post by meijer.o on 2008-11-09
I have the same when using Google Earth with 8.10 (xorg-xserver-video-intel)

I have reported a bug:

See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/295934/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/295934/)

---

### Post by rogerdean on 2008-11-23
Same story here I'm afraid. Thinkpad X60s, Intrepid, msttcorefonts, Compiz off. With GE 4.2 I get no text at all on placemarks etc, and with 4.3 I have random missing letters

I do hope someone can help sort this, or even just let me know that a fix is in the works?

Cheers
Roger

---

### Post by rogerdean on 2008-11-28
Hello all

Here's how I work around my GE probs (missing letters etc) on a Thinkpad X60s (Intel 945 graphics, 2gb RAM). It's probably very messy and with unnecessary steps, but this was what worked for me [insert general disclaimer here]

Install the old Intel i810 driver

```
sudo apt-get install xserver-xorg-video-i810
```

The I changed my xorg.conf file so the bottom bit reads like this -

```
Section "Device"
        Identifier 	"Intel Graphics Adapter"
        Driver     	"i810"
	VideoRAM 128000
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
        Device 		"Intel Graphics Adapter"
EndSection
```

Replace Google Earth 4.3 with 4.2 - not sure if this is necessary but I read somewhere that 4.2 has fewer graphics issues

Log out and in again or restart

Of course compiz is off, and after this change won't go on again, but GE works slowly (with atmosphere off) but correctly

Now, if anyone out there can refine the above I'd be very grateful!

Cheers
Roger

---

