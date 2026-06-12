---
title: "Graphical Window Border Glitch?"
date: 2008-11-04
forum: General Help
---

### Post by FiremothPilot on 2008-11-04
Just upgraded to the Ibex last night! I've been using Linux for close to two years now and have never seen this issue before.

Running the GNOME desktop with full graphical effects and dual monitors. For some reason, the border on the active window will intermittently become just a gray bar. If I move the cursor around inside the window, the border sort of flashes. (See attached screen)

This is obviously some sort of graphics error, maybe with the driver? I have an nVidia GeForce Go 7600 running on an HP dv8000.

Thanks in advance,

---

### Post by pedro_orange on 2008-11-04
Is the application active? And can you interact with it?

I usually see that sort of effect when an application is not responding. Within Browsers it's usually associated to Flash not being setup correctly.

---

### Post by FiremothPilot on 2008-11-04
> **pedro_orange said:**
> Is the application active? And can you interact with it?

I usually see that sort of effect when an application is not responding. Within Browsers it's usually associated to Flash not being setup correctly.

I can interact with all applications, even when the border glitch is occurring. I don't think its a Flash problem because it happens in ALL application windows, not just Firefox.

---

### Post by DrDagostino1 on 2008-11-05
I have also recently upgraded to Ibex and have been having problems ever since!

The window glitch is just one of the many bugs/glitches. By the way, I dont have dual monitors so it must be the driver.

---

### Post by FiremothPilot on 2008-11-05
> **DrDagostino1 said:**
> I have also recently upgraded to Ibex and have been having problems ever since! 

I'm seeing a disturbing amount of complaints regarding small bugs and minor annoyances. What happened with this release? Its the only distro in a long time that I've had so many minor issues with.

Other than that, this was the first Ubuntu release that I got dual monitors to work under...=D>

---

### Post by HyperHacker on 2008-11-05
I've seen the window borders in Compiz (using Gtk-window-decorator) get corrupted when OpenOffice is running. Could that be it?

---

### Post by FiremothPilot on 2008-11-06
> **HyperHacker said:**
> I've seen the window borders in Compiz (using Gtk-window-decorator) get corrupted when OpenOffice is running. Could that be it?

Do you mean the problem would occur only when OpenOffice is running? If so, that's probably not it. I receive this graphical glitch no matter how many or how few windows are open or applications are running.

If you meant something else, please correct me.

---

### Post by FiremothPilot on 2008-11-06
> **Chauncellor said:**
> There was another thread about this.

[http://sudan.ubuntuforums.com/showthread.php?t=950217](http://sudan.ubuntuforums.com/showthread.php?t=950217)

Bug Report:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508)

The unanimous assumption is that it is indeed a problem with an NVidia driver. NVidia is aware of the problem now, though, so I guess we just have to wait it out.

[http://www.nvnews.net/vbulletin/showthread.php?t=122043](http://www.nvnews.net/vbulletin/showthread.php?t=122043)

Both the recent driver updates and the old driver produced the same results for me. You could go to System>Preferences>Appearance and change the Window Border to Clear Looks for a more tolerable graphical bar. The problem is still there, but not nearly as much as with the Human bar.

Wow. Good research and thanks for letting us know. I'm really interested to know what changed (graphically) between Hardy and Intrpid that would cause this error...

---

### Post by FiremothPilot on 2008-11-06
> **Chauncellor said:**
> 
If only NVidia open-sourced information....:)

Amen!

These types of issues make bring me this close (*places fingers <1mm from each other*) to making my next card an ATI. Or maybe I'll just use Intel Graphics on all the rest of my machines. Every Compiz effect I've seen on my friend's Intel-based Compaq laptop run three times more smoothly than on my NVIDIA card with 256MB of discrete graphics memory. ](*,)

Maybe we could set up a protest outside the NVIDIA HQ...):P

---

### Post by HyperHacker on 2008-11-06
On the contrary, my attempts to get Xubuntu at all usable on an ATI card ended with me buying an NVidia instead, because the drivers just did not work at all, and this was apparently a widespread issue. NVidia seems to be good about driver support; they provide drivers (already better than many companies) that work very well, and keep them up to date, as well as the convenient nvidia-settings program.

And yes, the issue I mentioned only happened when OpenOffice was running.

---

### Post by PRGUY85 on 2008-11-12
Same issue here.  This occurs only in Ibex.  I'm using Nvidia 177 too.

---

