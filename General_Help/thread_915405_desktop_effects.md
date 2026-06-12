---
title: "desktop effects"
date: 2008-09-09
forum: General Help
---

### Post by agapecsc on 2008-09-09
Hello:
I'm new to ubuntu, so I have many questions however, I'll start with this: I have GeForce 8600 GTS PCT-Express video card. Whenever I try to use desktop effects and enable the graphics drivers and reboot the screen is black. I hope I explain this well enough.

---

### Post by gldearman on 2008-09-09
I had this exact problem with my GeForce card.

Here are a few suggestions.  (I apologize if I am *too* basic -- you say you are new)

Can you boot Ubuntu at all?  If not, boot to recovery mode and choose the "Recover X Server" option.  That should enable you to log in.

Try checking this page

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

there is a whole section titled "Screen Blanks/Monitor Turns Off."  It suggests adding a line to your xorg.conf file (and will walk you through doing it, if you don't know how).  Always create a backup of the xorg.conf file before you alter it!  That way, you have something to restore if your change makes things worse.

If that doesn't work for you, try running the following command in Terminal *after* installing the driver, but *before* rebooting.

```
sudo nvidia-xconfig
```

That worked for me, getting rid of the problem.

My last suggestion is not to install the driver via System > Administration > Hardware Drivers.  Use a program called EnvyNG to install it instead.  The system misdetected my hardware, and installed the wrong driver!  With Envy, you can manually select the driver to be installed.  EnvyNG is in the repository (you'll want the package envyng-gtk if you are running Hardy with the GNOME desktop).  You can find the driver you will need from this list:

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)

Hope this helps

---

