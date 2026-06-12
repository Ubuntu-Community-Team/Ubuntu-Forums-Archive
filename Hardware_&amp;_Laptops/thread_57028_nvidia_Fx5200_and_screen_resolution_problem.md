---
title: "nvidia Fx5200 and screen resolution problem"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by mpx on 2005-08-15
I'm a linux newb. I searched the forums and haven't found a solution.

During the installation,  a screen about specific resolution modes to chose. By default only 1024x768, 800x600, 640x480 were selected. I did not select more as I wasn't sure what to select. I continued and finished the installation.

Now when I choose "system->preferences->screen resolution" it only displays the above three resolution modes. My graphics card is capable of displaying at much higher resolutions (I'm dual booting with xp where I can choose higher resolutions).

How do I add more choices in the screen resolution menu (and choose them)?

Thanks for the help!

MPX

---

### Post by TristanMike on 2005-08-15
Hi, I have the exact same card, assuming you have the 128MB one. I was having a few video issues too. Have you installed the nVidia driver from here [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) ? It fixed a lot of issues I had, plus I get a cool nVidia splash screen.

---

### Post by duminas on 2005-08-15
You can do this one of two ways.

I'll state the easier.
Go into the terminal and issue this command: **sudo gedit /etc/X11/xorg.conf**. Make sure to make a backup somewhere (I don't recall the exact command to do it, but you can save the file as *xorg.conf_backup* in the same directory once gedit opens).

Now, find a section similar to this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"15 COLOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```
See the "SubSection" notation? You will see several of these, each for various Depths.
Add the desired resolutions to EACH SubSection, then restart x.

Say you wanted 1280x960 available for choosing. You would change all the subsection Mode lines to look like so:
```
		Modes		"1280x960" "1024x768" "800x600" "640x480"
```
Does this make sense?

By the way, when I said "restart x" up there, you may just want to reboot your machine. It'd be the easier way, though if you do not want to reboot, hit CTRL+ALT+Backspace, login when asked, then issue **sudo /etc/init.d/gdm restart** and that should drop you back to the login screen.

-----

For reference, the second way is to drop out to the command-line (CTRL+ALT+Backspace), then issue **sudo dpkg --configure xserver-xorg**, though I'd suggest you not do it this way for now.

---

### Post by Seti on 2005-08-15
You can use those other higher resolutions by editing your /etc/X11/xorg.conf file.

Just look for the lines that say: Section "Screen".
There you can add 1280x1024 or whatever else res your system is capable of.

Just go ```
sudo /etc/X11/xorg.conf
``` 

and add in the res you want to use.

(edit: beat me to it, with better details :-) )

---

### Post by mpx on 2005-08-15
Wow... great responses in short time.. I'm impressed. Ubuntu (and its users) rock!
My problem is solved.  (for some reason ctrl-alt-backspace threw me back to gui login screen and not to the commandline that I was expecting...but that is a minor problem I can live with)

My thanks to duminas, TristanMike & seti. You guys are great. I have another problem at hand with my partitions (I guess I start another thread to reduce confusion - hope you guys can help me). So far my new venture into the linux world is exciting...


Thanks again.
mpx

---

