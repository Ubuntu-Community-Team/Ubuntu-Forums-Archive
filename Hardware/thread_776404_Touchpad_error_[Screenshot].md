---
title: "Touchpad error [Screenshot]"
date: 2008-04-30
forum: Hardware
---

### Post by Aesir09 on 2008-04-30
i installed **Touchpad** from the repository 

and when i try to launch i get this:

 [img]http://www.zilefile.com/pfiles/170/Screenshot-gsynaptics.png[/img]

---

### Post by itix on 2008-04-30
terminal:
```
gksu gedit etc/X11/xorg.conf
```

That'll bring you a file that looks like this:
```
# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
.
.
.

```

Go to the synaptic section which looks like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
```
and add the line:
*Option "SMHConfig" "1"*
and save and restart your computer.

---

### Post by Aesir09 on 2008-04-30
thanks will try!

do you by chance know how to use the razer deathadder cfg?

---

### Post by itix on 2008-04-30
Uh... no. Never heard of it actually =p
I DO however after half a year of linux experience know how fiddle around with the touchpad. If you want to turn it of, add line *Option "TouchpadOff" "1"*. If you want to disable tapping, add the line *Option "MaxTapTime" "0"* etc =)

---

### Post by Aesir09 on 2008-04-30
will do thx! :)

but know umm here, please explain this to me:

exact step by step and i will <3 you lawlz.

[http://www.bu3sch.de/razercfg.php]("http://www.bu3sch.de/razercfg.php")


why do things that aren't .deb files and that aren't in the repository have to be so damn hard to install!?!?
:(

---

### Post by itix on 2008-04-30
Ah!... That seams like just what you want (and I'd want if I had a mouse with more than 3 buttons =)
GUI ftw. Can't understand all these terminal ppl.

People should get hanged for throwing out tars without proper installation instructions...

I have never ever heard of GIT before. Took some time reading about it and it seamed to be a lesser nightmare. May I go to sleep now and deal with this when I wake up??

---

### Post by itix on 2008-05-01
This is the best I can come up with.
[http://git.or.cz/](http://git.or.cz/)
If you read there, it tells you that if you have git installed, you can "**get the latest development version via Git itself** and then is adds a code line after which reads:
git clone git://git.kernel.org/pub/scm/git/git.git

What I think you have to do is to install git from the synaptic package manager, and then type *git clone [http://bu3sch.de/git/razer.git](http://bu3sch.de/git/razer.git)* in the terminal and maybe add something else. Use that page I gave you and see how that install is done.

---

### Post by Aesir09 on 2008-05-01
thanks man, will try ^_^

---

