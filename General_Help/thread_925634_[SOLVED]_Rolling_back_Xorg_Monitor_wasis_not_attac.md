---
title: "[SOLVED] Rolling back Xorg? Monitor was/is not attached when I told screen res. to au"
date: 2008-09-20
forum: General Help
---

### Post by Predator106 on 2008-09-20
Hey, 

I have a server downstairs (running Hardy desktop).

This server has no monitor, as I had it upstairs plugged into one when I installed it, but now it is just downstairs being plugged into just Ethernet and power.

I can only VNC this workstation, I don't want to haul it back up here and plug a monitor and keyboard and all that stuff in, having to do more work.

I want to rollback Xorg, as apparently it is my problem.

My brother had hit, in the screen resolution, auto-detect, because he wanted to change the monitor res. but since there is no monitor, I can now only view this 2x2 INCH SCREEN!! LOL, it is literally 2 physical inches by 2. I can't hardly do anything. The most I can do is goto a terminal and type stuff in, I tried going to 'nano' but it won't run because it realizes the screen is way too damn small. It's pretty funny, when you think about it, but it sucks.

Basically, I want to roll back my xorg.conf to a previous one, but the thing is, I don't know which one is previous. Like I said, I get this tiny *** window and can barely use the terminal, only being able to read half of what it says.

Any ways of helping me? It would certainly be appreciated.

---

### Post by pytheas22 on 2008-09-20
If you type:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

it should auto-reconfigure the X server to whatever it was by default.  Does that solve it?  If not, check to see if there are any files with names like /etc/X11/xorg.conf~ (where the ~ is important) on your system--these would be older versions of your xorg.conf file.

---

### Post by Predator106 on 2008-09-20
Well I already tried that command earlier I thought, are you sure it doesn't just autodetect and rewrite the file?

And just to let anyone know, since I can hardly use the terminal, nautilus is completely useless. So I had to use ls /etc/X11/ to list all the goodies in there.

Well this is the output of the command I tried just now....

```
server@server-P4:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for server: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080920223026
server@server-P4:~$ 
```

---

### Post by Predator106 on 2008-09-20
Still didn't set it to normal either.... 

I also tried reverting back to other ones, but since it's a new install, there are no backup configs...

Also, I edited my xorg.conf file, gedit actually works, although it is all wordwrapped to about 10 characters per line :( .

But my video card and stuff are also blank. Even on my main computer they are as such, but my main computer (this one) uses an nvidia card, with an actual monitor. Am I pointing to the right place? The man page says it has multiple places also, but how do I know which one mine is using, etc.

---

### Post by pytheas22 on 2008-09-20
In the modern version of X, the video card and stuff are not specified by default, so that's not the problem.

The command should have rewritten xorg.conf to whatever it was by default when you first installed Ubuntu.

Did you make sure to log out of X and log back in after running that command?  The new xorg.conf won't take effect till the next logout.

---

### Post by Predator106 on 2008-09-20
Yep, I've been rebooting every time I change something.

---

### Post by pytheas22 on 2008-09-21
I'm wondering if the problem is with VNC rather than your X11 configuration, as I can't think of anything else to look at in xorg.conf that would affect this.

How are you connecting to the VNC server--are you using the VNC GUI client that ships default with Ubuntu, are you using the command line...?  Did you check the settings of the VNC server on the monitor-less machine to ensure that it's configured to export a display larger than 2x2 inches?

Also, you may want to try installing an ssh server on the remote machine ('sudo apt-get install ssh'), then connect to it with X forwarding enabled:
```

ssh -X username@IP-address-of-remote-machine
```

Once connected, type:
```

gnome-session
```

and it should forward the entire desktop to you via ssh (it may be laggy depending on the speed of your connection--ssh is not as efficient as VNC--although on a local network it may be fine).  Is this desktop also really small?

---

### Post by Predator106 on 2008-09-21
Sorry for the late post, but after working on it until about 12-1 am I decided to just plug it into a monitor. Apparently I am also having graphics card problems. I.E. It is not being recognized correctly, I have an ATI 9600 SE, so I tried various other legacy ones none of which supported higher resolutions. It appears that the X1600PRO ATI card that I have is the best/only card that works properly. Am I the only one that thinks ATI 's drivers suck?

The proprietary drivers weren't even recognized, it didn't show up as anything with the 9600. But it does/is running not bad with the X1600. The only problem is now, compiz.

Also, how I knew it wasn't a problem with VNC, is that my brother was using tightVNC also from a different IP/computer. So that couldn't have been it.

Nvidia drivers were so much easier, unless it was just because I was using an 8600GT, I don't know.

But now another question, how can I get compiz to work correctly with it. It doesn't look like compiz likes ati drivers, when I start it up, hosted under a terminal(with gnome running, of course), the screen greys out completely. Like the gray color of a windoze object/control or something. But the entire screen is like that, so I then hit CTRL+C to break it off.

The result is somewhere along the lines of it not being able to find an Nvidia card, or two other card types that I didn't recognize. I have read problems with ATI and compiz occurring. How can I fix this?

EDIT: Oh, I just realized that the fglrx drivers don't support 9200, only 9500 and higher.

---

### Post by pytheas22 on 2008-09-21
I don't have an ATI card (stick with Intel unless you need a card for gaming--compiz is nice and zippy on Intel, the chips are cheap, and 3D acceleration works out-of-the-box in Linux, since Intel provides open-source drivers), so I'm afraid I can't offer much good advice there.  The best thing I can say is to try using [envy]("http://albertomilone.com/nvidia_scripts1.html"); it may be able to pick the right driver for your card automatically.  Otherwise, search around to see if others have gotten compiz to run on this card.

---

### Post by Predator106 on 2008-09-21
Yeah, already tried that. As for Intel, you mean integrated right? How do I know if my motherboard uses integrated intel graphics, do basically all of them?

But now it's not so much that I'm worried about, it's Xorg keeps on autodetecting a monitor, but since there is no monitor attached, it gives me this small *** screen.

How can I stop X server from auto-detecting the display? I have already put an entry for a monitor in the xorg.conf file, and nothing changed.

---

### Post by pytheas22 on 2008-09-21
You marked this as solved.  Did you figure it out?

Maybe the easiest thing to do here is just to reinstall.  I'm not sure where else to look--I don't know how to force X to create a larger display--but if you've already gone to the trouble of hooking this machine up to a monitor, it would only take you half an hour to reinstall Ubuntu.

> 
As for Intel, you mean integrated right? How do I know if my motherboard uses integrated intel graphics, do basically all of them

If you run the command 'lspci' it will list all the hardware devices on your machine, including graphics cards.  If you see a line that looks like:

```
VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller
```

then you have Intel graphics.  Not all motherboards have them, but many do.

---

