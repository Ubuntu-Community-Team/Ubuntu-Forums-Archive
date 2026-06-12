---
title: "External monitor problems with laptop"
date: 2012-01-02
forum: Hardware
---

### Post by g_bean on 2012-01-02
I have a Dell Precision M6500 laptop with 2 x 24" dell monitors connected via a docking station. Graphics card is NVIDIA Quadro FX2800M.

Everything has been ok (except for manually setting the displays in NVIDIA X-server Settings) when running ubuntu 10.10, but when I upgraded to 11.10 I can't get the external monitors to work.

The NVIDIA X settings hangs when i try to enable the 2nd external display, and the only way to reset is to do a restart of the computer. It somehow works for only one display, but it changed the desktop settings.

I have found some posts about the same problem on other forums, but so far I have been unsuccessful in finding any real solutions. There seems to be some work-arounds for desktop computers, but I don't like the idea of having to edit the xorg.conf and reboot every time I un-dock the laptop.

Does anyone know any solutions? Suggestions will be most welcome!

---

### Post by sjfeatherstone on 2012-01-06
I have had the same issues with my M6500 with 2 monitors connected to the dock. In the Nvidia X server Settings, I have to do this process every time I put mine on the dock before I start any other programs.
1) Set one of the dock monitors to twinview
2) Disable the integrated LCD
3) Enable the last monitor making sure the position is right of or left of the primary
4) Set the check box for one of the dock monitors to be primary
5) Click enable - sometimes it doesn't take so I have to try it again.

The one thing I never do is save the x-configuration. If I do that when I am not docked I have to copy my backup xorg.conf file back over the running one and reboot.

I have tried many things to get OS to see the dock monitors as the primary monitors, however, it never works. BIOS and Grub sees them and uses my monitor in port 1 as the primary, then when the login for Ubuntu shows up my monitor goes black and the second one says there is no signal. I then have to open the laptop, if I forgot to open it, and go through the settings I outlined above.

If anyone can give us a workaround that might work, I would be happy to try it. I have tried 2 xorg.conf files and using rc.d to check for components on the Dock and copy that corresponding file over if it sees or doesn't see the components, doesn't work.

---

