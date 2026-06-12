---
title: "Enable suspend mode on Thinkpad A31 - enable ACPI_SLEEP=true does not work"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by mmedson on 2006-07-25
I've uncommented the appropriate line in /etc/default/acpi-support, and pressing Fn-F4 still does not kick my Thinkpad into suspend (standby) mode.  And there's no option listed on the logout screen to do this either.  Hibernation (suspend to disk) works fine, although to me it's sort of a pointless thing to do.  I've Googled and Googled, but the only stuff I've found says that all I need to do with the current, fully-updated Ubuntu is to uncomment the line ACPI_SLEEP=true.  

Any other ideas?

---

### Post by hizaguchi on 2006-07-25
In Gnome, System --> Preferences --> Power Management and use the gui interface to set up what the suspend button does.

Not sure how to do this in KDE.  Probably a setting in kcontrol, or you might just be able to run "klaptop" and get to the settings.

---

### Post by bulwinkl on 2006-11-19
Probably have to update the bios. Try [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-45898](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-45898)
hope this helps.
John

---

### Post by 56phil on 2006-11-19
I had a similar problem on my Gateway M680. I had to put the swap partition's UUID in the /etc/initramfs-tools/conf.d/resume file. Once you do that, make this entry:
```
sudo update-initramfs -u
```

I hope this helps.

Happy Ubuntu!

---

