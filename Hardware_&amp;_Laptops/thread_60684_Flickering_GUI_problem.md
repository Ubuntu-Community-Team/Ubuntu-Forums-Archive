---
title: "Flickering GUI problem"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by elemental_silver on 2005-08-28
I'm having a small, but fatal, problem. I've tried installing and everything seems to work out fine until it loads up the GUI. At that point, it just starts flickering and displaying scrolling chunks of line... its hard to explain, but I'm not sure if it's a bad ISO install or my Video Card going dumb on me. I have a Cirrus Logic card, in case you're wondering. And it seems like even though the image is chopped and unreadable and flickering that the computer does respond to typing and begins to think for a moment when I try. Any suggestions?

By the by, ubuntu-5.04-install-i386 is the iso I'm using. Does anyone know the checksum for it so I can do a quick check to see if it is the ISO?

---

### Post by xmastree on 2005-08-28
[This](http://us.releases.ubuntu.com/releases/5.04/MD5SUMS) should tell you the md5sum.

Although you may be better off checking the burned disc rather than the ISO, as a good ISO can still lead to a bad burn.

The md5sum.txt file in the root of the CD has them all, so running```
md5sum -c md5sum.txt
``` from a terminal should help. I presume you can still get into a terminal using Ctrl-Alt F1 to F6

---

### Post by elemental_silver on 2005-08-28
Thanks. Didn't realise it was on the CD, and thanks for being considerate enough to tell me how to check off of the CD. Most forums I go to just yell and scream at me and call me a noob, which isn't far from the truth but I'm not some lame "lolerskates" idiot noob or something. -.-

Anyway, any suggestions on what my problem might be while I go check to see if that's the problem?

---

### Post by xmastree on 2005-08-28
> Thanks. Didn't realise it was on the CD, and thanks for being considerate enough to tell me how to check off of the CD. No problem.> Most forums I go to just yell and scream at me and call me a noob,[SIZE=2][COLOR=Red]**Goddamn noob. Jeez, what a stupid question! Doesn't even know how to check his md5!**[/COLOR][/SIZE] :razz: 
There, feel better now?  :)  :)  :)  :) 

> Anyway, any suggestions on what my problem might be while I go check to see if that's the problem?I would be inclined to have a look at your xorg.conf file, 
```
gedit /etc/X11/xorg.conf
```In particular, this bit:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection 
```then search the web for:
"cirrus logic" xorg.conf to get something like [this](http://www.die.net/doc/linux/man/man4/cirrus.4.html) 
If that doesn't work, check out the some of the search hits, you may find someone has posted their working config out there, and you can compare that with yours.

Just out of interest, what happens if you Ctrl-Alt-Num+ or Num- to switch resolutions?

---

### Post by elemental_silver on 2005-08-29
Wow, its spewing up lots of garbage now. Like Xserver isn't configured correctly. Can't adjust the resolution at all. Trying to adjust the resolution is what cleared up the flickering, all I had to press was control and poof, it cleared up. Won't let me edit the config file, either. Gives me a display error. Think the disk is bad?

Edit: By the by, sorry this turned into a software question. Thought it was my video card wonking out.

---

### Post by xmastree on 2005-08-29
> Won't let me edit the config file, either. Gives me a display error. How are you trying to edit it? you need to be root to edit, otherwise it'll be read-only.
Since you appear to have a desktop now, open a terminal and type:```
sudo gedit /etc/X11/xorg.conf
```That should open it.

Failing that, you might have to switch to a different terminal Ctrl-Alt-F1 and use a more geeky editor, like vi to do it.
```
vi /etc/X11/xorg.conf
```will let you view it, running it as root will also let you edit and save it. Back it up first, just in case you completely mess it up. :-\"

---

### Post by elemental_silver on 2005-08-29
*whistles* Back what up? According to the VI editor, doing that makes a new file. And it still gives me a display error when I use gedit. I think I'm just gonna junk the CD and try again. I have an iso of kubuntu downloading so I figure I'll try that next, just so I have something different to work with so I don't get frustrated. I've been trying for months to get a stable linux distro installed on it, but I'm new at it and I've been having problem after problem with all kinds of different distros. Most of which problems on my side, like bad Isos with checksums that don't match and bootstrap errors... In fact, this is my second Ubuntu CD, I had a bootstrap error last time I burnt because I burnt at too fast of a speed.

I've tried Debian(Two versions, an older version which acually worked somewhat and a newer version), Gentoo(That one made me cry once or twice  ](*,) ) , SUSE, Slackware, and now Ubuntu.

---

### Post by elemental_silver on 2005-08-29
*SCREAM*

There, I feel better...

Anyway, Kubuntu gave me the same errors in every way, only instead of displaying an xserver error, it just brought me to the user name prompt. Meh, it has to be a hardware problem, guys... Any suggestions?

Edit: Let me give the hardware specs. Compaq Presario 4550 Desktop, mostly stock from the shop with the exception of the zip drive, which I removed to simplify installations, and I switched out the CD drive to something faster and much more relyable. I also inserted a Video card, the Cirrus Logic of problem, in it to replace the built in video card on the motherboard. And don't say to try to use the video card on the board, cause that was my first choice and I had the problem with it too. 

[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=92804&cc=us&docname=c00008588](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=92804&cc=us&docname=c00008588)

---

### Post by xmastree on 2005-08-29
[QUOTE=elemental_silver]According to the VI editor, doing that makes a new file.[/QUOTE]It shouldn't do, if the file exists. If you type the wrong path it will make a new file, but if the file is there it should have opened it.

Be sure to type X11 and not x11

If you want to actually edit and save the file, you'll need to be root, so sudo the command.

> Kubuntu gave me the same errors in every way, only instead of displaying an xserver error, it just brought me to the user name prompt. Meh, it has to be a hardware problem, guys... Any suggestions?Log in from the terminal, and type:```
startx
```That would normally start the x server, but in your case it probably won't. Look at the errors it throws up, might give you a clue. If not, do it again, but send the output to a file:```
startx >filename.txt
```and post the result here. Assuming there's a way to get it from that pc onto the one you're using for this forum...

---

### Post by elemental_silver on 2005-08-29
I had some great help from the Kubuntu chatroom on IRC. They helped me fix my problem. It was trying to load the wrong driver for some odd reason. I switched to another video card and ran the configuration for it, which fixed it all up. I'm now running perfectly... well, near perfect. The sound card won't work. Oh well, good thing I didn't intend to have speakers on it. *disables sound* Hehe. Also, its slow. Damn slow. Like I open open office and it lags to a complete stop every time I type a word. It takes 10 minutes just for Open office to start up =P

Ah well. It works, I'm happy.

---

