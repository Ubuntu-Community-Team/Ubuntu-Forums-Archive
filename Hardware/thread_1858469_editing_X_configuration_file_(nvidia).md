---
title: "editing X configuration file (nvidia)"
date: 2011-10-12
forum: Hardware
---

### Post by gavinred on 2011-10-12
Be gentle with me as I don't really know what I'm doing, but I'm trying very hard. I'm sorry if I give too much or the wrong information, I'm not sure what's relevant.

Ubuntu has been working great for me, but I'm trying to run [VMD]("http://www.ks.uiuc.edu/Research/vmd/") to render some molecular simulations. When I try to run it, I get the error message 

> ERROR) The X server does not support the OpenGL GLX extension.   Exiting ...Googling around a bit has lead me to believe that this has something to do with the compatibility of the graphics card. I have gone to > system -> administration -> additional drivers, and installed the recommended 'NVIDIA accelerated graphics driver'. It now tells me that the driver is 'active but not in use', which I'm not sure is right or not. 

I also checked 'System -> Administration -> NVIDIA X Server settings' because it seemed relevant. clicking this gives the message > You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.typing 'sudo nvidia-xconfig' gives the message > WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'restarting the xserver (after activating the ctrl+alt+backspace shortcut) nothing seemed to change and I still got the same message telling me to edit the configuration file. However, it did cause the laptop to crash every time I restarted it, until I reset the configuration to default from failsafe graphics mode.

Any help would be appreciated.

more information that may or may not be relevant: 

Release 11.04 (natty)
Kernel Linux 2.6.38-11-generic-pae
GNNOME 2.32.1

---

### Post by hollowhead on 2011-10-12
This might help  [http://ubuntuforums.org/showthread.php?t=1730188](http://ubuntuforums.org/showthread.php?t=1730188) in that the xconf file seems to have been divided up into parts.  It looks like you need to hack the monitor one.   There will be instructions on how to do this for nvidia graphics on the web.  Remember to make a backup first (cp to a new name).  I was going to download the software to try it I'm a biologist, but you have to register.

---

### Post by gavinred on 2011-10-13
Thanks for the tip, much appreciated! I can't try it right now, but I'll let you know if it works.

---

### Post by gavinred on 2011-10-13
I tried to do what you suggested. I noticed VMD works on windows though, so I think I'll try it on there instead. It would be nice to not have to switch between the systems, but oh well. 

btw, is it on principle that you won't download anything that requires registration? It doen't ask anything particularly intrusive, and you could get away with making up a name if you like.

---

