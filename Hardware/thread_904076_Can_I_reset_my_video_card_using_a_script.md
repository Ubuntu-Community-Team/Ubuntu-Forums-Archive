---
title: "Can I reset my video card using a script?"
date: 2008-08-28
forum: Hardware
---

### Post by fizzybrain on 2008-08-28
What-ho,
My laptop is rather ill, the graphics card doesn't seem to initialise properly when switching modes.

I'm using an ACER 1804 with ATI mobility radeon x600 / kubuntu 8.04 / kde 3.5 / xorg / kwin / xrandr

It's fine for the text modes at BIOS-time, and for the first graphical startup screen, but when it actually starts the desktop proper I get garbage on the laptop screen (the external screen is fine). I'm pretty sure it's a hardware fault with this machine of mine, but it's fine if I do a trick to reset it:

- What I normally do is ctrl-alt-F1 as though I were invoking a terminal session (screen is still garbage at this point), and then ctrl-alt-F7 to get back to the desktop, by which time it's miraculously cured itself (it's a bit of a faff though, as I'm controlling it from a separate machine using synergy and ctrl-alt-f1 is not transmitted).

- I've also just written a script which uses xrandr to "disconnect" that display and then re-enable it, but that shoves my windows round a bit, so not ideal.

Doing the ctrl-alt-F1/F7 trick seems to reset the video card and that gets it running fine - any idea how I can do this with a command?

Share and Enjoy
F.

---

### Post by phidia on 2008-08-28
I think this > sudo /etc/init.d/gdm restart should do.

---

### Post by fizzybrain on 2008-08-29
> **phidia said:**
> I think this  should do.

Thanks, but no - that just restarts the display manager, so it's as though I'd just switched on and I just get the garbage again.
I need to do some kind of reset of the display hardware.

---

### Post by phidia on 2008-08-29
> **fizzybrain said:**
> Thanks, but no - that just restarts the display manager, so it's as though I'd just switched on and I just get the garbage again.
I need to do some kind of reset of the display hardware.

Well actually doing Alt+Ctrl+F1 to F7 doesn't kill or restart the xserver either-so I don't know what's going on. 
The keystroke method of restarting x is Alt+Ctrl+backspace.
All that you're doing with the keystrokes you're using is switching tty's.

You could look at man xinit and xserver.

---

### Post by fizzybrain on 2008-08-29
> **phidia said:**
> Well actually doing Alt+Ctrl+F1 to F7 doesn't kill or restart the xserver either-so I don't know what's going on.
Exactly - I'm not trying to restart the x server (that doesn't help). I'm trying to re-initialise the display hardware somehow.
> **phidia said:**
> 
All that you're doing with the keystrokes you're using is switching tty's.
- and that works. It seems that it is changing display mode from graphic to text (or at least a graphic mode with different resolution) and back to graphic that resets the hardware. Alternatively, I can switch that display on and off again using xrandr, but that is not ideal.
I remember seeing some option on some operating system where one could force the video hardware to re-initialise after, say, coming out of standby - I think I need something like this.

---

### Post by nicedude on 2008-08-29
Why not try using envyng to install a better ATI graphics driver and see if it corrects the behavior. This may be a driver issue and not a actual hardware problem, I would bet it is and the default Nvidia and ATI drivers never are the best ones in Ubuntu.

Command to install envyng

sudo apt-get install envyng-gtk

Command to run it

sudo envyng-gtk

Once started select install an ATI driver and let it do everything when it asks.

I would not be surprised a bit if that fixes it, and I hope it does :-)

PS I don't think you can ctrl+alt+f1 etc from a script anyway.

---

### Post by fizzybrain on 2008-08-29
> **nicedude said:**
> Why not try using envyng to install a better ATI graphics driver and see if it corrects the behavior. 

Would that not screw up my dual-monitor configuration? The last time I tried to use the "proper" ATi drivers I found I could no longer use xrandr, so I'm currently using fglrx.

I'm running kde, so I assume I need to use envyng-qt (not -gtk)?
SO when I mark that in synaptic it says it's going to install (amongst others) kde4libs - does that mean it's going to make me use KDE-4? I don't think I want to do that - I'm not sure how well cinelerra will co-exist with KDE-4 (and I'm pretty sure kdenlive 0.6 will *not*).

I'll maybe give it a go when I'm feeling brave....

---

### Post by nicedude on 2008-08-29
I have no idea how your dual monitor setup will be affected since I dont use any ATI cards I am a Nvidia guy.


Just because it wants to install kde4libs I don't think that means you would be switching to KDE4 as it probably just needs that library to work.


All I know is that you can't do what you were asking I looked and found tons of people asking the same thing ( for many other reasons ) in many different flavors of linux and no one said it was possible.

---

### Post by phidia on 2008-08-29
Actually he might be able to. If you wade in to the xserver manual "man xserver"
There are some commands in the SIGNALS section that might work?

> SIGNALS
       The X server attaches special meaning to the following signals:

       SIGHUP  This  signal  causes  the  server to close all existing connec&#8208;
               tions, free all resources, and restore  all  defaults.   It  is
               sent  by  the  display  manager  whenever  the main user&#8217;s main
               application (usually an xterm or window manager) exits to force
               the server to clean up and prepare for the next user.

       SIGTERM This signal causes the server to exit cleanly.

       SIGUSR1 This signal is used quite differently from either of the above.
               When the server starts, it checks to see if  it  has  inherited
               SIGUSR1 as SIG_IGN instead of the usual SIG_DFL.  In this case,
               the server sends a SIGUSR1 to its parent process after  it  has
               set  up  the various connection schemes.  Xdm uses this feature
               to recognize when connecting to the server is possible.


---

### Post by nicedude on 2008-08-30
He is not trying to restart the xserver

---

