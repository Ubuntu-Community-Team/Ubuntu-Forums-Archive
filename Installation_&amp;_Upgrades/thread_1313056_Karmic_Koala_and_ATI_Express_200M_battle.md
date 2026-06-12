---
title: "Karmic Koala and ATI Express 200M battle"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by SkillenUK on 2009-11-03
OK, I've had another thread running on this issue since Thursday but it's getting a bit misleading and now that I understand the problem a bit more I wanted to start a new one. Hopefully someone can help me (apologies if you have seen my older thread)...

If I upgrade from Ubuntu 9.04 to 9.10 then approximately half way through the updating packages stage my screen flickers and resolution changes to something very low then I see a warning message telling me I am in a low graphics mode. The mouse pointer is frozen and I no longer see the update progress but the update still continues as my hard disk is active. Eventually my screen turns blank and the hard disk stops. If I reboot at this stage then from the GRUB screen I can either boot to Kernel 2.6.28-11 or the newer one 2.6.31-14. If I select the newer version then I see a message, something like 'starting...' in black and white text and nothing else happens. If I boot to 2.6.28-11 then it does boot to the desktop but it's unstable and my video really isn't working properly (I can't use any advanced visualisations for example compiz or extra visualisations in the appearance settings). To be honest the installation is a mess, I have tried following a guide to install the open source ATI drivers but this just made the system more unstable. I believe I need to use the open source drivers because my card is no longer supported in the proprietary ones which means I need to use the legacy driver that doesn't work in anything past Ubuntu 8.10.

Really I am looking to perform a clean install and get this working. When I clean install 9.10, the installation seems fine but after selecting Ubuntu from the GRUB screen I immediately get a flashing white curser in the top left hand side of the screen and nothing else happens. I have tried looking for broken packages from the recovery menu but this changes nothing. The Live CD boots without any issues and I can turn on the extra visualisations (my windows wobble etc). So now I&#8217;m thinking whatever is different in the Live CD setup to the install is what I need to replicate and if the Live CD is working then it must be possible to get my installation working. I'm guessing it's a package I need to install or something like that but I don't really know where to start with this. I have tried looking at the xorg packages that are installed on the Live CD. Whatever I need to do really needs to be from the command prompt under recovery mode (to get the clean install working) but I&#8217;m fairly new to Linux and I am struggling now. I'm not sure if I can affect the installation from the Live CD (other than accessing files).

Please can anyone help? Do I need to provide more info? I have searched around on the internet and other people are having trouble with this graphics card in 9.10 but no one else has got stuck just after the GRUB screen like I have (most are solving the problem by using open source ATI drivers which I thought were installed by defualt anyway). I'm keen to solve this because I'm guessing that if I have the problem now then I'll also have the same issue with future releases so this means I have to start looking at other Linux distros (and I don't really want that because Ubuntu has totally converted me!). Thanks,


Chris.

---

### Post by pastalavista on 2009-11-03
I had similar problems when I upgraded from 9.04 to 9.10. I have the same graphics card as you. The upgrade was so bad that I backed up my data and did a clean install. After that, my graphics were working better than they have since 7.10. The new ATI Radeon driver is a kernel module now and I believe Xorg is optimized for it. I don't know why the upgrade didn't work but it also was missing other features that are included with the clean install like Software Center.

So my advice would be back up your drive and do a clean install. My only problem now is an ACPI issue which won't let me resume from suspend or hibernate.

---

### Post by SkillenUK on 2009-11-03
To be honest I've clean installed several times trying different things since Thursday and it doesn't boot at all (clean install was the first thing I tried). I tried re-installing 9.04 and upgrading and that's what I've talked about above, this is the only way I have managed to boot apart from the Live CD.

---

### Post by SkillenUK on 2009-11-03
I've got rid of my upgraded installation and clean installed again because I wanted to try a few things. I can boot to recovery mode (it's slow loading though because it seems to hang a bit) and I do get to a command prompt after a while. I can type startx and boot to desktop. Again this seems to hang a bit and eventually freezes and I have to reboot. But I can get to the settings and the video looks ok (advanced visulisations work etc), maybe the issue is with the GRUB loader or something else. I may close this post and start a new one based on that. Any ideas though?

---

