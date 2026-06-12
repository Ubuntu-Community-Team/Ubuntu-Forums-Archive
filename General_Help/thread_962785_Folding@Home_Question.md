---
title: "Folding@Home Question"
date: 2008-10-29
forum: General Help
---

### Post by GmAz on 2008-10-29
Ok, I want to run F@H, and I do actually.  but it runs in an annoying terminal window.  I don't want to see it running, just know that it is.  I have seen on many screenshots around the web of people's desktops and seen a F@H icon up by the clock and no terminal window.  How can I accomplish this?  My desktop usually runs during the day and night doing nothing but sucking electricity.  I figure it may as well do something useful.  I did find how to make it into a service, but I would like the option to shut it down if I need to from the icon on the panel near the clock.

---

### Post by m_duck on 2008-10-30
Have you installed it as root or as a user? If you install it as root it will run from when you turn your pc on, until you turn it off. However you can stop it running
```
sudo /etc/init.d/foldingathome stop
   or
~/opt/foldingathome stop
```if you installed as root or user respectively. I am not sure if this is only relevant if you have used the fah_install script, but I would have thought it would still apply.

The wiki has some pretty useful info on this:

[Ubuntu wiki - folding at home]("https://help.ubuntu.com/community/FoldingAtHome")
[Ubuntu wiki - fah_install]("https://help.ubuntu.com/community/FoldingAtHome/fah_install")

To check that it is running, you can run **top** within a terminal window and see if "FahCore" or something like that is running. Another method is to get conky (a light system monitor) to read the progress file to show the status on your desktop. A final method that I know of is one I saw earlier called [Protein Think]("http://sourceforge.net/projects/prothink/") though I do not know anything about it.

---

