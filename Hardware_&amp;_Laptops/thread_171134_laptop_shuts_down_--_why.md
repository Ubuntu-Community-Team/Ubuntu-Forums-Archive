---
title: "laptop shuts down -- why?"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by pokeyflan on 2006-05-06
Hi Folks:

I have a Dell Latitude C610.  Had Ubuntu 5.10 sucessfully on it before, but then the computer developed RAM problems.  Once out of the shop,  i re-installed and now the laptop will shut down if left alone for ~15 minutes.

I really don't know why and don't know where to look to amend this.  In System > Preferences > Screensaver Preferences > Advanced, the Display Power Mgmnt is set for Off after 120 minutes.  (Altho i've tried disabling it, to no effect.)

I appreciate all suggestions as i'm truly baffled (enough of a noob to know it)

Thanks!

--chris

---

### Post by wbmj on 2006-05-06
Check your laptop BIOS....it maybe that you have ACPI settings that need to be changed prior to setting preference in Ubuntu

---

### Post by kennethb on 2006-05-06
Try the following:

Choose "System > Preferences > Power Preferences" from the menu bar.

and adjust your power preferences. Maybe that will work???

---

### Post by pokeyflan on 2006-05-06
wbmj & kennethb:

Thanks for the suggestions!  
I suspect my problem *might* be the BIOS load, but once again am not sure what exact ACPI setting should be changed.  This is what i have:

POWER MANAGEMENT: 
(enabled on both battery & AC)
DISPLAY TIME OUT:
(3 minutes and Disabled, respectively)
SUSPEND TIME OUT:
(5 minutes and Disabled)
SMART CPU  MODE:
(Enabled for both settings)

Which of these should be changed?

And, when I go to Preferences> Power preferences, I get the message "You have notyet enabled DPMS support in gnome-screensaver" ... but that's not true in the Preferences > Screensaver > Advanced menu.  Or am i still missing something?

Thanks already & in advance for all your help!

--chris

---

### Post by tsb on 2006-05-06
similar problem here with DPMS
I have no options in power preferences-options either
I just want to make my laptop automatically shutdown if the power is below 3%
it was so easy to do in Kubuntu, butI can't figure it out in Ubuntu
I tried to install gnome-screensaver, but it had virtually nothing.....the default screensaver has the advanced menu with the DPMS so I uninstalled gnome-screensaver and left the default
do I need to uninstall the default before installing gnome-screensaver?
why do I have no options in power preferences-options?
also, how do I make the screensaver stop when the diplay goes on standby like it did in Kubuntu?
thanks.

---

