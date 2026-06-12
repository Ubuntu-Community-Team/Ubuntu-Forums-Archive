---
title: "Ubuntu 13.04/Nvidia card not detecting my HDMI-attached TV"
date: 2013-04-30
forum: Hardware
---

### Post by baslow on 2013-04-30
A few months ago, when I was running Ubuntu 12.10,  I hooked my television ( a SONY Bravia 32", if it matters) to my PC via an HDMI cable. No problem.

The upgrade to 13.04 via the update manager went badly, messing up the window manager, display resolution and who knows what else.  I managed to create an installation disk and re-installed Ringtail, retaining existing files and accounts.  My login account was still messed up however and virtually unusable so I created a new account and made it the admin.  Mostly, this seems to be working except that neither the "Display" control in "System Settings" nor the nvidia-settings app can now detect my TV.

Here is what "sudo lspci -v" says about the video card:

[I]01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 1312
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d800 [size=128]
	[virtual] Expansion ROM at fea80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
[/I]

I am semi-literate in Linux but know virtually nothing about graphics.  Can anyone suggest measures I can take to get Ubuntu to detect my television?

Thank you.

---

### Post by baslow on 2013-05-06
I've found [this post]("http://ux51vz.blogspot.com/2013/04/how-to-install-nvidia-31912-drivers.html") about what seems to be the same problem. While it suggests that installation of something called [Bumblebee ]("http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html") might solve the problem the poster favors the installation of a recent beta nVidia driver (nvidia 319.12) as a better solution.  He points to this ( "dirty" ) method of getting that driver installed: [http://paste.ubuntu.com/5601226/](http://paste.ubuntu.com/5601226/) 

I don't really understand a lot of this.  I gather that Nvidia provides a technology called [Optimus ]("http://en.wikipedia.org/wiki/Nvidia_Optimus"), originally intended for laptops but now marketed for desktops under the name "Synergy".  To minimize power usage, Optimus switches the kind of graphics processing used depending on the nature of the task -- so that it only uses its more energy-intensive heavy guns when they are necessary.  The technology has been released in easy-to-install packages for Windows and Mac but is [not yet fully supported under Linux]("http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html") (which is why it's necessary to install the beta).  But I don't understand what any of this has to do with the card being able to detect an HDMI display.

I am now working up the nerve to try implementing the "dirty" solution mentioned above. Any helpful observations or comments (or words of warning, for that matter) would be welcome.

---

### Post by SimplyHuffy on 2013-09-25
> **baslow said:**
> I've found [this post]("http://ux51vz.blogspot.com/2013/04/how-to-install-nvidia-31912-drivers.html") about what seems to be the same problem. While it suggests that installation of something called [Bumblebee ]("http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html") might solve the problem the poster favors the installation of a recent beta nVidia driver (nvidia 319.12) as a better solution.  He points to this ( "dirty" ) method of getting that driver installed: [http://paste.ubuntu.com/5601226/](http://paste.ubuntu.com/5601226/) 

I don't really understand a lot of this.  I gather that Nvidia provides a technology called [Optimus ]("http://en.wikipedia.org/wiki/Nvidia_Optimus"), originally intended for laptops but now marketed for desktops under the name "Synergy".  To minimize power usage, Optimus switches the kind of graphics processing used depending on the nature of the task -- so that it only uses its more energy-intensive heavy guns when they are necessary.  The technology has been released in easy-to-install packages for Windows and Mac but is [not yet fully supported under Linux]("http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html") (which is why it's necessary to install the beta).  But I don't understand what any of this has to do with the card being able to detect an HDMI display.

I am now working up the nerve to try implementing the "dirty" solution mentioned above. Any helpful observations or comments (or words of warning, for that matter) would be welcome.

[http://askubuntu.com/questions/331625/kubuntu-no-display-configuration-tool-after-upgrade-from-12-10](http://askubuntu.com/questions/331625/kubuntu-no-display-configuration-tool-after-upgrade-from-12-10) hey man check out this answer

---

