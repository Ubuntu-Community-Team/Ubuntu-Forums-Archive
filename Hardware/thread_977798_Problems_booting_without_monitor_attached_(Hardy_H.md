---
title: "Problems booting without monitor attached (Hardy Heron)"
date: 2008-11-10
forum: Hardware
---

### Post by Rinusch on 2008-11-10
Hello,

I'm using Hardy Heron on a machine that I only connect to using VNC.

It has been asked before, but I haven't seen it answered: when I boot without the monitor attached, the system stops booting and displays the 'ubuntu is running in low-graphics mode' screen.

What can I do to prevent this? Connecting a monitor is no option..

Also, where can I find the configuration screen for display settings?

Any help would be greatly appreciated.

Kind regards,
Rinusch.

---

### Post by Coreigh on 2008-11-10
Where does it display this message if there is not monitor attached? Through VNC? Are you using VNC server package or RemoteDesktop? You will probably have better results with RemoteDesktop. (Go to System > Preferences > Remote Desktop and enable it, if that is not what you are already doing.) 

The configuration screens are System >> Preferences >> Screen Resolution, and System >> Administration >> Screens and Graphics.

---

### Post by Rinusch on 2008-11-11
Hi, 

Thanks!

The screen 'appears' when no monitor is connected (or turned on??) during boot. When I then plug in a monitor to see what's going on, I see that screen. It is halting the boot process..

Any clue?

By the way: I don't have the 'System->preferences' menu option ('preferences' is not under the 'system' menu). I'm using Xubuntu, Hardy Heron. Don't know if this makes any difference to 'normal' Ubuntu menu options?

Regards,
Rinusch.

---

### Post by Coreigh on 2008-11-11
OK Now I understand. Just to make sure If you boot the computer with a monitor connected it boots normally and you can connect via remote desktop (VNC). But if you unplug the monitor and reboot the machine never fully boots but complains about the resolution setting.

What you want it to run "headless." I have done this with Ubuntu without any special configuration. Setup the computer once with a monitor attached, enable remote desktop and other settings, remove the monitor and close the closet door. I do not know why Xubuntu is complaining. Are you choosing Xubuntu for its lightweight GUI or just because you like that one?

At any rate all I can offer you is to research headless operation. I got several results from Google but nothing specific about setting or configuration regarding your problem.

I wish you luck.

---

### Post by Zimmer on 2008-11-11
It is probably X trying to autodetect the hardware(Monitor) you may need to construct a bespoke xorg.conf with a valid modeline for a monitor and use the option 
  Option         "UseEdid" "False"

in the screen section.

see Appendix B

 [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html)

---

### Post by Rinusch on 2008-11-13
Thanks guys, for the time you're putting into my problem.

@Coreigh: 
> OK Now I understand. Just to make sure If you boot the computer with a monitor connected it boots normally and you can connect via remote desktop (VNC). But if you unplug the monitor and reboot the machine never fully boots but complains about the resolution setting.

Completely right!
I already read something about a "headless" setup. I'm indeed using Xubuntu for its lightweight GUI. My machine is an Atom T7 barebone from Tranquil pc (great machine by the way!). Runs very smoothly!
Thanks, I will look into this further myself first. If it raises more questions, I will ask them here.

@Zimmer:
Thanks, I'll dive into this!

Thanks again guys!

Regards!

---

