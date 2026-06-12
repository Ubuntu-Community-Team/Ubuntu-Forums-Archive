---
title: "wireless problem"
date: 2005-12-06
forum: General Help
---

### Post by gabi on 2005-12-06
Well... this is my first post here, so first of all, Hello everyone and good luck with the very good job you're all doing here!
OK, let's get to the point... I installed Kubuntu on my Fujitsu-Siemens laptop, after being a long-term Suse user, and I have encountered two problems: one was the screen resolution, but that was fixed, thanks to the threads I found here, but the other one it's still not solved. I have a PCMCIA wireless network adapter (TrendNet TEW-421PC) which I have installed via ndiswrapper. ndiswrapper -m didn't make it come up, but modprobe ndiswarpper did.
Well, here comes my problem: I am not able to configure the network parameters because everytime I try to go to Settings -> Network it says to go into administrator mode, but there is no option/button to do that. If I go the other way, through the taskbar menu, I find the administrator mode button, but after entering the password, nothing happens, except the red-border rectangle which contains nothing.
Where am I going wrong? How to workaround this? Thank you very much for any suggestions!

---

### Post by WoodyDragon on 2005-12-06
1st problem: try extending the window of the settings, down below is the admin-button.
2nd problem: Did you try the normal password? don't use the root password there

---

### Post by mlomker on 2005-12-06
The graphical tools are fairly broken yet.  You can launch it using sudo instead, just type **kdesu kcontrol** or **kdesu systemsettings** on the Run line or in a terminal.

If you're familiar with Debian you'll probably find it simpler to edit the /etc/network/interfaces file directly.

---

