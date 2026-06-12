---
title: "Gutsy Problems on DV6500 Laptop?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by godzirra on 2007-10-24
Anyone have any issues with Gutsy like this since release? 

 After a few hours of working, my wireless network stops working and can't reconnect, I can't run anything with sudo, and opening a terminal window in X won't work.  I had no issues with Feisty, and jnc was positive that its my network, but i can't find anything wrong with it.  I've added a root user so I could see if I could log in to see whether it was a pam issue, and had no trouble logging in.  Anything else?

I'm open to any suggestions, as I'm out of ideas. 

Thanks,
godzirra

---

### Post by godzirra on 2007-10-24
Anyone?

---

### Post by djuniah on 2007-10-24
If your SURE its the wireless then maybe switching from fwcutter to ndiswrapper might help.  I had some similar issues and that seemed to fix them for me.  Search around the forums, there are tutorials for it.

---

### Post by godzirra on 2007-10-25
> **djuniah said:**
> If your SURE its the wireless then maybe switching from fwcutter to ndiswrapper might help.  I had some similar issues and that seemed to fix them for me.  Search around the forums, there are tutorials for it.

Is fwcutter what it uses by default in Gutsy?  If so, then I am using it.  I have no idea if the wireless stopping working and it causes this problem, or if the wireless not working is just a symptom of another problem.  I'll search around the forums and try ndiswrapper and see if i still have it.  Thanks for the info!

---

### Post by scuttles on 2007-10-30
I have a dv6529em. Everything seems to work fine on Gutsy with the exception of two things:

1) Wireless. I have tried everything I can think of and still I'm left tearing my hair out. Started with restricted drivers manager which used fwcutter. I then tried installing fwcutter manually. Then ndiswrapper. The problem is exactly the same with all the available options, the card is recognised and seems to work, but then no networks are detected even when I'm 3 feet away from the router. It's as if the radio is turned off or something.

2) Very strange issue this one. Laptop is plugged in and switched on - works fine. Unplug power to continue using on battery - backlight dies. I don't just mean it dims, it actually turns off completely (you can *just* make out the outlines of windows) and takes a boot into Vista to start working again.

If anyone has the same issues or knows of any solutions it would at least give me something to work on! For the record, Feisty was all good with the exeption of nvidia graphics (it's a new card - 7150 - so I don't think it's supported yet).

---

### Post by Cyber-J on 2007-10-30
I've been using a firmware for the bcm43xx-fwcutter driver which is available at  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o") a few weeks now and it appears to be quite stable. It works for my dv6300 which uses a BCM4311 wireless chipset.

---

### Post by scuttles on 2007-11-11
Thanks for the advice Cyber-J. I'd actually tried that already but I gave it another go just to be sure. No joy I'm afraid. However, I managed to find this howto

[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

which worked perfectly! So now I have working wireless. Just the weird backlight thing to sort out now....:confused:

---

### Post by Ayuthia on 2007-11-11
> **scuttles said:**
> Thanks for the advice Cyber-J. I'd actually tried that already but I gave it another go just to be sure. No joy I'm afraid. However, I managed to find this howto

[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

which worked perfectly! So now I have working wireless. Just the weird backlight thing to sort out now....:confused:
You might want to check this this one out:
[http://ubuntuforums.org/showthread.php?t=512059&page=24](http://ubuntuforums.org/showthread.php?t=512059&page=24)
The person who entered post 233 had the same problem and seems to have resolved it by adjusting his power settings.

---

### Post by scuttles on 2007-11-15
Thanks Ayuthia. That was actually the first thing I tried, using the power settings in GNOME, which all seemed to be completely normal. Then I installed the full kubuntu desktop and tried the power settings from there. Strangely, the brightness was set all the way down to zero for battery power. I have no idea why the settings were different for the different desktops, but at least it's working now.

I'll check the bug reports and file one if necessary.

---

