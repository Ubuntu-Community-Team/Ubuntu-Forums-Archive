---
title: "Acer Aspire 7720-6374"
date: 2008-04-24
forum: Hardware
---

### Post by deevabone on 2008-04-24
hello all, 

I am going to put 8.04 onto an acer aspire laptop 7720-6374 - I tried to put on ubuntu 7.10 and it installed ok but I had a nightmare getting the keys mapped properly - I believe my keyboard layout is for both an English and French Canadian layout. However installing 7.10 always gave me the default (green alternate character on the keyboard) display which I do not want - effectively I ended up not being able to use | or ~.

Does anyone have any suggestions for an 8.04 install and on an other topic should I be concerned that the CPU fan will have problems on this acer as I believe it is controlled by software that is part of vista but not availble for linux. Same goes with sound I assume that I will still have the problem with getting sound fixed unless I update alsa and adjust the config for Acer.

Any feedback is much appreciated and I will comment on the install when done.

D.

---

### Post by steve8track on 2008-04-27
I have an Acer Aspire 7720-6152.  I was running 7.10 and now I'm running 8.04 with the rt kernel upgraded from March's beta version.  Keep in mind that my 7.10 was normal Ubuntu with the generic kernel, and my 8.04 was Ubuntu Studio with the rt kernel.  Here is the experience I've had so far:

[LIST]
[*]On Ubuntu 7.10 my Realtek audio wasn't working right off.  I had to manually install the latest alsa drivers.  8.04 works with the sound right off, although once in a while amarok gives an error that the sound has to be restarted and sometimes sound stops working, but not very often.
[*]On both Ubuntu 7.10 and 8.04, my built in webcam worked without any problems after installing cheeze.
[*]If I remember correctly, 7.10's wireless internet didn't work right off, but 8.04 did.
[*]The keyboard extra keys worked for me with 7.10 and the generic kernel with the exception of the Euro key and the Dollar Sign key above the left and right arrow keys.  8.04 and the rt kernel, extra keys that didn't work were: the e, the mail button, internet and bluetooth key, and the internet key, some stick figure of a guy key, the Euro key and dollar sign key.  Function and Media keys such as volume, mute, and changing brightness seem to work, but I don't use the next/previous play/pause and stop keys, but they seem to work.  I'm not sure if this is an rt-kernel problem since it used to work.
[*]The Nvidia drivers didn't seem to like compiz-fusion at first (or vica-versa), and animations are choppy, especially after running for a while (memory leak? I don't see any though...).  Loading a page in epiphany while rotating the cube slows the rotation down more than on my older, much weaker laptop.  I don't think the 8600M GT is very well supported yet for compiz, but games seem to run well and an update to compiz recently seems to have at least helped.  I've tried the 169 Nvidia driver (default), the 171, and the 173, and so far I think I prefer the 171 because it is newer than 169 but 173 doesn't let you change the resolution for games to anything but my highest resolution.  You have to install without the repository for the later two.  The installer nvidia makes works well if you uninstall the restricted modules and install the kernel headers.
[*]I never did get the subwoofer working.
[*]The fan seems to be working fine, but I don't know if our laptops are identical.  The fan seems to blow when it should.
[*]Epiphany, my prefered web browser, seems to crawl compared to firefox.  Expecially hovering over links with javascript and changing tabs.
[*]Nautilus frequently freaks out when I drag files over the pane on the left side.  It thinks I want to drop files before I let go of the key.  This might just be a 8.04 beta issue though.
[*]Flash nonfree plugin doesn't work very well.  It will play a youtube video for about 1 minute, and then the cpu will drop to near 0% and the browser will freeze.  This seems to happen in both Firefox and Epiphany, and even Konqueror doesn't seem to like flash much.
[/LIST]

So in summary, sound and wireless should work for you, but unfortunately the keys or special buttons at top of the keyboard don't.  Also the compiz-fusion, flash and epiphany bugs are bothersome, though compiz does seem to be working better now.  With those two exceptions, things seem to be working well.

One last thought, if you don't like variable cpu speeds (like if you are plugged in all of the time) you could try setting the speed to performance on startup

Check your speed this way:
```

cat /proc/cpuinfo
```

This is how I changed it to the fastest setting, where -c # is the number
of the processor.
```

sudo cpufreq-selector -c 0 -g performance
sudo cpufreq-selector -c 1 -g performance
```

Let me know if anyone figures out the fixes to any of these problems I've had.  I hope this helps and I hope someone can help me too.  I can't wait until most of the bugs are worked out for this hardware, because it will be a very nice machine, although it is already pretty good.

Steve

---

### Post by deevabone on 2008-05-02
Thanks Steve, 

I have to say that with 8.04 everything seems to work right out of the box. I have had absolutely no keyboard issues, sound was working right from install (although at maximum the volume is still not loud enough for me so I will see if I can change this) - I cannot get the subwoofer to work as well.

At this point I have found no problems with the CPU getting too hot and shutting down - although I have disabled hibernate and any sleep status which I believe was causing the problem from previous versions - I really have no need for these in my environment anyway.

the webcam does indeed work with cheese and the alps touchpad that I had problems with previously does work fine except that the rocker button (middle button) when clicked up it will scroll the screen doen when clicked down it will not scroll at all.

I was away on business the past week so I have not had the chance to go through all the options but I was so glad that the wireless card was working right away, sound working right away, no display issues, ethernet card recognized, all of my keys except for the euro key seem to be fine.

The only complain really is that when I boot into Ubuntu it displays my screen brightness at the lowest automatically which I then have to adjust everytime - I have noticed that it will occasionally reset to the lowest brightness setting while I am working as well - not a big deal for me to increase the brightness when this happens although I would like to know why it is doing this.

All in all I am very happy with the install and my migration from Vista on this device should be complete very shortly - just need a suitable dreamweaver alternative and C#.net development ability (I am looking into options).

Thanks again.

---

### Post by steve8track on 2008-05-08
I'm glad to hear everything seems to be working for you, even the extra keys other than euro?  I'm thinking of doing a fresh install of Ubuntu, I'm not sure if some of my problems are from Ubuntu Studio and the rt kernel.

I noticed the screen dims as well, and the pattern seems to be (other than dimming on startup) as your battery runs low, the screen seems to be compensating for it.  My screen never dims on AC power except when it first boots.  I'm guessing there should be a fix for it, but I haven't been bothered enought to look for it.  Maybe it's something changable in the gconf-editor.  Which reminds me...

If you notice your volume wheel being too quick to change volumes (the "step" is too big) go to /apps/gnome_settings_daemon in the gconf-editor (Configuration Editor) and change the volume_step, which I set to 2.  Also, the volume was backwards where wheeling up turns the volume down (also true in Windows) so I reversed it in System->Preferences->Keyboard Shortcuts.

I just had an update that has messed my wireless up, so I hope I can get it fixed soon.  The network-manager is still there, but no networks show up, and I can only get it to connect (sometimes) with a manual configuration.

Let me know if you or anyone else have some good advice about this model of laptop.

Steve

---

### Post by xanthe on 2008-06-22
@Steve - Thanks for the tip on volume steps and reversing the wheel- I've been living with the small annoyance until now. Any luck with the subwoofer? It's the last problem I have on my Acer 7720G, albeit not a huge problem, when I'm without headphones the sound is so tinny.

@deevabone - You've probably found a Dreamweaver replacement already, but it's worth recommending Aptana Studio- I'm a professional web developer who solely used the code view in Dreamweaver for XHTML/CSS- never touched the WYSIWYG. Aptana is actually better for this!

---

### Post by deevabone on 2008-06-30
Hello, 

@xanthe - thanks for the Aptana suggestion I prefer to do any web development at the code level so this looks very good - just need to get used to a few things. Mostly doing stuff with Turbogears now and seeing how I can utilize Aptana for my template development.

However not sure if you have noticed as well but reviewing my log files the debug log was being consumed with constant APIC error on CPU0 :40(40) errors. I tried forever to figure out what the problem was but was never able to determine. However I decided to update the BIOS to v1.40 which I picked up from here [ftp://ftp.work.acer-euro.com/notebook/aspire_7720/vista/Bios/](ftp://ftp.work.acer-euro.com/notebook/aspire_7720/vista/Bios/) and then flashed with a boot disk (Ultimate Boot Disk using Free Dos) and this solved the problem. Now I am not sure if you are encountering the same problems or if this is right for your machine version but thought that I would mention - BIOS updates can be scary.

I still need to do C# development and was not too happy with Mono so I decided to install a copy of Windows XP using VMware Server within Ubuntu. This seems to work well with no problems. I set up samba and created a folder to share files between the virtual OS and Ubuntu which is great.

Still can't get the subwoofer to work or the MIC to record anything. I have also noticed that I am unable to use pulse audio for anything and have made ALSA my defualt - not too bad but would be nice to control volume at the application level.

All in all things seem to be going quite well.

D.

---

### Post by steve8track on 2008-07-12
Currently, my keyboard is still missing the extra keys at the top, and the euro and $ keys by the arrows.  My sub still doesn't work, and I still have audio problems once in a while, when amorok sends an error message saying it can't initialize the audio.  Usually playing some audio/video with a different media player fixes it, otherwise I have to restart.

Otherwise, everything seems to be working fine.  My wireless is working good now, although I'm afraid if another update will break it, because updates have already broken my wireless on two separate occasions.

Also my middle button on the touch pad has the same symptoms mentioned above that only clicking up works, but for me it doesn't scroll up, it rotates my desktop, probably because I have two extra buttons on my mouse set to rotate the desktop, and for some reason my middle button is mapped to those buttons instead of the scroll bar.  Also, the touch pad seems a little slow at crossing the screen, but if I change it, my mouse will likely be effected.

Let me know if anyone knows the fixes to any of those problems.

Thanks,

Steve

---

### Post by steve8track on 2008-07-12
Oh, I forgot.  You can reverse the volume control so that the wheel on the side of some Acer laptops is more logical, and lets rolling up raise the volume instead of the default of lowering it, and vice-versa.  The same problem happens in Windows.  Just change the keyboard shortcuts in preferences.

---

### Post by steve8track on 2008-12-27
Well, I thought I would give an update to my problems on my Acer Aspire 7720-6152.
Here is what I have working and what I don't have working.
If anyone has any ideas how to fix any of these problems, please let me know.

Summary Of Changes:
	[LIST]Even though I didn't get much else working, I've been very pleased with the added graphics performance, Epiphany Tabs are working right, and
	wireless hasn't broken on any upgrades lately.  I'm also glad my OpenGL drivers aren't corrupted anymore.[/LIST]
	[LIST]What I would like fixed the most is:
		[LIST]Audio Mixing - I'd prefer hardware mixing[/LIST]
		[LIST]Flash Video on youtube freezes - possibly related to audio mixing[/LIST]
		[LIST]Video Resolution - can't reduce the resolution for games[/LIST]
		[LIST]Extra Keys[/LIST][/LIST]
BELOW IS A MORE COMPREHENSIVE REVIEW:

Information/Specs:
	[LIST]Ubuntu Studio[/LIST]
	[LIST]Kernel: 2.6.24-23-rt[/LIST]
	[LIST]Wireless: PRO/Wireless 4965 AG or AGN Network Connection (rev 61) - Working[/LIST]
	[LIST]Audio: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
		[LIST]Dolby Digital Live[/LIST]
		[LIST]Subwoofer - not working[/LIST]
		[LIST]optical output - untested[/LIST]
		[LIST]Mixing - HUGE problem.  I'd prefer hardware mixing
			Doesn't mix channels at all.  It freezes or breaks software when
			trying to do two sounds at once.
			Symptoms:
				[LIST]Amorok says it can't initialize audio drivers[/LIST]
				[LIST]Epiphany freezes on youtube videos[/LIST]
				[LIST]Pidgin has to have all of it's audio turned off to use any other programs that use audio[/LIST][/LIST][/LIST]
	[LIST]Graphics: Nvidia GeForce 8600M GT 512 MB
		[LIST]Nvidia Drivers:
			[LIST]NVIDIA-Linux-x86_64-180.17-pkg2 - Gnome Menu is delayed and highlights multiple entries, so I reverted to 177.82[/LIST]
			[LIST]177.82 - BEST (The one I'm currently using)
				Advantages:
					[LIST]Great performance[/LIST]
					[LIST]Tabs on Epiphany are finally working faster[/LIST]
				Problems:
					[LIST]Breaks openGL libraries (solved)

						If you are writing OpenGL programs, reinstall using this command to fix your broken libraries (gl.h):
							```
sudo apt-get install --reinstall libgl1-mesa-dev freeglut3-dev xlibmesa-gl-dev mesa-common-dev
```[/LIST]
					[LIST]I can't reduce/lower my screen resolution for games.  Most forums only show how to get the maximum
						resolution, but I want to use gvidm to switch my resolution down when I need it.
						With this driver, reducing the resolution either blackens the screen or turns the screen
						into what looks like an etch-n-sketch, where it starts black and lines start forming in light colors like it
						isn't refreshing.[/LIST]
					[LIST]Virtual Box with Windows XP crashes or ceases to refresh the whole screen sometimes when I:
						[LIST]resize with the Alt key in Compiz[/LIST]
						[LIST]switch to fullscreen with R_Ctrl-F[/LIST][/LIST][/LIST]
			[LIST]Older Versions:
				[LIST]Advantage: I can reduce my resolution for games using gvidm[/LIST]
				[LIST]Problems:
					[LIST]lesser performance[/LIST]
					[LIST]slow Epiphany Web Browser tabs (Firefox)[/LIST]
					[LIST]minimizing/maximizing effects that were slow (This was a common 8000 and 9000 series problems)[/LIST]
					[LIST]OpenGL 3D programs would flicker (maybe that was my other laptop with an Intel 915 Graphics Chipset...)[/LIST][/LIST][/LIST][/LIST][/LIST]

	[LIST]Keyboard:
		[LIST]Working extra keys:
			[LIST]Wireless Button[/LIST]
			[LIST]Reduce brightness[/LIST]
			[LIST]Increase brightness[/LIST]
			[LIST]stop[/LIST]
			[LIST]play/pause[/LIST]
			[LIST]next track[/LIST]
			[LIST]previous track[/LIST]
			[LIST]mute[/LIST]
			[LIST]audio wheel (see above posts for some fixes)[/LIST]
			[LIST]all other blue function keys seem to be working too[/LIST][/LIST]
		[LIST]Non-working keys that don't produce results in xev:
			[LIST]Web Browser Button[/LIST]
			[LIST]Mail Button[/LIST]
			[LIST]Bluetooth Button (I don't have bluetooth)[/LIST]
			[LIST]Stick Figure Dude Button[/LIST]
			[LIST]E Green Button Thingy[/LIST]
			[LIST]Dollar and Pound sign buttons above left/right arrows[/LIST][/LIST][/LIST]
	[LIST]Camera works dandy[/LIST]
	[LIST]Touchpad - works, but the special middle button that is supposed to scroll instead middle clicks for down and up is set to button 8[/LIST]
	[LIST]Nautilus
		[LIST]Dragging files into the window over the bookmark bar causes the CPU to skyrocket and freezes Nautilus for about 10 seconds[/LIST]
		[LIST]FTP doesn't connect if the server doesn't allow the root directory for the connection[/LIST]
	[/LIST]
	
	Let me know if you need any more details on any of these problems or on any solutions I've found so far.

---

### Post by steve8track on 2008-12-27
Duh, the audio wasn't hard to fix after all!  I just copied what this tutorial said into .asoundrc:

[http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing](http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing)

I wasn't sure if I had software or hardware mixing, until I found a forum that said you can check with:

```
cat /proc/asound/pcm
```

in the command line.

If playback is >1, then it supports hardware mixing.  I would have thought a soundcard with 5.1 surround sound should support hardware mixing, but apparently not according to this file.

I hope this helps someone.

Steve

---

### Post by BB88 on 2008-12-29
After reading around a lot, and just ending up in circles, I have shed some light at the end of the tunnel on the subwoofer issue.

Firstly, you will need to determine which sound card codec you are using; I am assuming ALC268, as we are dealing with the Acer 7720 series,

```
cat /proc/asound/card0/codec#* | grep Codec
```

which returned this for me.

```
Codec: Realtek ALC268
Codec: Conexant ID 2c06
```

You will then need to check out this link [here](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) which will tell you of the sound options to use in the alsa-base configuration file. Find your codec number, e.g. ALC268.

Open up a terminal and type in 

```
sudo gedit /etc/modprobe.d/alsa-base
```

Scroll to the bottom and add the following lines,

```
options snd-hda-intel model=MODEL
```

Repalcing MODEL with the model from the list on the link provided above. It appears that using model=auto gives the best results, as new options appear in the Volume Control and Volume Preferences.

```
824		ALC268
825		  3stack	3-stack model
826		  toshiba	Toshiba A205
827		  acer		Acer laptops
828		  dell		Dell OEM laptops (Vostro 1200)
829		  test		for testing/debugging purpose, almost all controls can
830				adjusted.  Appearing only when compiled with
831				$CONFIG_SND_DEBUG=y
832		  auto		auto-config reading BIOS (default)
```

I hope this brings us closer to solving the subwoofer issue!

---

### Post by BB88 on 2008-12-29
> **steve8track said:**
> Duh, the audio wasn't hard to fix after all!  I just copied what this tutorial said into .asoundrc:

[http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing](http://alsa.opensrc.org/index.php/Hardware_mixing,_software_mixing)

I wasn't sure if I had software or hardware mixing, until I found a forum that said you can check with:

```
cat /proc/asound/pcm
```

in the command line.

If playback is >1, then it supports hardware mixing.  I would have thought a soundcard with 5.1 surround sound should support hardware mixing, but apparently not according to this file.

I hope this helps someone.

Steve

Thank you for this tip, this greatly helped, now just the problematic subwoofer!

---

### Post by Bendihossan on 2009-01-20
Hey all. Would just like to thank all for the help in this thread! Thanks to this I've now got sound and mic working (although mic is quite noisy).

I'm also having issues with subwoofer. No output at all! 8.10 doesn't even seem to recognise it exists! :( I'm still playing with setups and gathering info from other places. If I make any progress you'll be the first to know :)

---

### Post by Bendihossan on 2009-04-01
Still working on the woofer and still no progress :(
Anyone?

---

### Post by deevabone on 2009-04-03
I have had absolutely no luck with this. I tried to see if building from arch using the 2.6.28 kernel would solve the problem or at least provide some further info but no luck.

Someone has actually recently posted to the kernel buglist about this though so maybe something will come of this.

[http://bugzilla.kernel.org/show_bug.cgi?id=12916](http://bugzilla.kernel.org/show_bug.cgi?id=12916)

I am still having great difficulty recording any sound from the internal mic - has anyone got this working perfectly?

---

### Post by Bendihossan on 2009-04-03
> **deevabone said:**
> I have had absolutely no luck with this. I tried to see if building from arch using the 2.6.28 kernel would solve the problem or at least provide some further info but no luck.

Someone has actually recently posted to the kernel buglist about this though so maybe something will come of this.

[http://bugzilla.kernel.org/show_bug.cgi?id=12916](http://bugzilla.kernel.org/show_bug.cgi?id=12916)

I am still having great difficulty recording any sound from the internal mic - has anyone got this working perfectly?

Thanks for the link to the bug article deevabone. I've not got the internal mic working perfectly...but I have got it working. Just update to the latest ALSA and fiddle for a while...or rather a long time! It's just a matter of balancing the "mic" and "mic boost" sliders to filter the noise and volume levels.

---

