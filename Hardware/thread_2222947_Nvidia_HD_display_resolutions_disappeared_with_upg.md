---
title: "Nvidia HD display resolutions disappeared with upgrade to Trusty"
date: 2014-05-08
forum: Hardware
---

### Post by halfbeing on 2014-05-08
I have just upgraded one of my machines to Trusty and I am finding that all the higher display resolutions have disappeared. The machine has an Nvidia card (Asus EN210) connected by HDMI to a full-HD TV. Before the upgrade I had a full HD resolution picture. Now the highest resolution offered to me is 1024x768. I was using the proprietary driver and I have left it enabled after the upgrade. I am using UbuntuStudio and therefore the XFCE tool for selecting the video resolution. How can I get my full HD back again?

Thanks in advance.

---

### Post by AllenGG on 2014-05-08
That appears to be an ASUS 
EN210 SILENT/DI/1GD2(LP)

Suggest that you download drivers from ASUS, they are somewhat Linux/Ubuntu friendly.
As well try rebooting and go into recovery before log in.

I had the same problem on a GT440 card.[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by halfbeing on 2014-05-09
Thanks for replying :)

There aren't any Linux drivers at the Asus site. Basically it is an Nvidia card and should work with normal Nvidia drivers.

I'm not sure what I would be supposed to do in recovery mode. There is no recovery mode option in the Grub menu so presumably I would need to edit a grub entry by hand to get into it.

One thing I've noticed is that the display is listed in the display settings as "default". As far as I remember, it used to be identified as a a Toshiba something or other.

What I think has happened is that the Nvidia module has not been built for the new kernel. At least I can't find any trace of it in /lib/modules. But I don't know how to force it to rebuild the module.

---

