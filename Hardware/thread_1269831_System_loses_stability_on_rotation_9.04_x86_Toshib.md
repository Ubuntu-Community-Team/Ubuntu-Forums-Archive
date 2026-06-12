---
title: "System loses stability on rotation 9.04 x86 Toshiba M200 Nvidia Go5200"
date: 2009-09-18
forum: Hardware
---

### Post by Kaworu's Fallen Angel on 2009-09-18
Sorry if there's a thread on this already, but I made a good-faith 3-day search for one, and nothing fits my situation exactly. I have a Toshiba M200 tablet, and the stylus actually runs fine by default (though the side and eraser pen buttons are not working). Rotation is obviously a huge issue for Linux users, but I'm having a very specific problem. I have rotation enabled, and it seems to work, but the system's stability is compromised after rotating. Everything seems to grind to a halt, and the video display takes several seconds to update. Often visible distortions are present, such as blurs and static fuzz appearing in place of buttons and other objects. Rotating back to the default orientation does not fix the issue, and needs a reboot (usually cold).

This happens when I rotate using the rotation settings on the Nvidia X-Server control panel, as well as using this guy's shell script: [http://www.intilinux.com/howto/531/toshiba-portege-m200m205-tablets-on-ubuntu/](http://www.intilinux.com/howto/531/toshiba-portege-m200m205-tablets-on-ubuntu/) (which, by the way, does not seem to fix the stylus' orientation).

This is a Toshiba Portege M200 tablet running 32-bit/x86 Jaunty/9.04 with Nvidia propietary driver, v. 173. Default GNOME setup.

I'm fairly experienced with computers (I work at Geek Squad lol) but I'm still fairly green with Linux. I'm still learning all the terminal commands, and the syntax is coming slowly (the DOS in my brain doesn't seem to like UNIX syntax). I really want to make this switch permanent, since Linux is obviously a much more powerful operating system, and it allows for so much more innovation and customization than Windows. I'm still in college, however, and I MUST have my tablet fully functional for taking notes, or else Linux will never be more than a sandbox install dual-booting Windows 7.

Does anyone know anything about this? I really appreciate people taking the time out to help!

---

### Post by Favux on 2009-09-18
Hi Kaworu's Fallen Angel,

Welcome to Ubuntu Forums!

Did you add the line:
```
	Option		"RandRRotation"  "on"
```
to your xorg.conf?  It would be to this section and look something like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"RandRRotation"  "on"
EndSection
```
If you don't know how to back up xorg.conf and how to edit it just ask.

For rotation see methods 1 or 3 at this HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  In the Method 1 scripts you'd want to comment out or remove the xsetwacom command lines with touch.

Then the other thing to deal with is since you are in Jaunty is that the wacom.fdi is not parsing the linuxwacom names correctly.  So xsetwacom commands won't work (rotation of the stylus and eraser).  To see this enter in a terminal:
```
xsetwacom list
```
It should return stylus and eraser, not be blank.  To see what HAL is calling your Wacom devices enter in a terminal:
```
xinput --list
```
Since the M200 is a serial (the internal connection to the tablet) Wacom tablet pc rather than a usb you'll want to look at 3) and 3a) in "Jaunty Users" near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

Hope this helps.

---

### Post by Kaworu's Fallen Angel on 2009-09-18
Hey, thanks so much. The Wacom pen orientation was a real issue, since all the articles dealing with it use the xwacom nomenclature, and my rotation scripts always error out on the pen setup. I'll definitely try that. 

I already have the Nvidia RandRRotation enabled, and it works fine, but after some further toying around I believe the issue is caused by Compiz. If I terminate Compiz (and Compiz.real) with a killall, I can rotate quick and painless, and I can even restart Compiz rotated, and it works fine. Of course, this really isn't a solution, because killing Compiz leaves me with a random mess of all my open applications that don't move, resize or minimize, and there is no desktop bar across the top. 

I could theoretically write it into the rotate script to kill Compiz before every rotation, and restart it after, but this seems like a major pain, and there has got to be a better solution.

---

### Post by Favux on 2009-09-18
Hi Kaworu's Fallen Angel,

There might be a specific issue with Compiz and your nvidia card.  To identify the card:
```
lspci | grep VGA
```
Then you have the right key words to search for Compiz problems/optimizations.

I don't think you should be having a problem, so something may be hinky, but anyway doing Compiz off in a rotation script isn't a big deal.  There's a script attached to the bottom of the HOW TO for ATI cards which don't work with Compiz when rotated using the proprietary "fglrx" driver.  That would show you how to do it.

---

