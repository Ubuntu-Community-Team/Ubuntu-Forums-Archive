---
title: "Lost some settings in reinstallation"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by greymoose58 on 2005-12-07
I have just upgraded my hard drive and copied my home folder from the old hard drive. Some things like Evolution fired up as if there had been no change but both the shortcuts on the panels (of which there are lots) and the settings in Firefox (including a stack of bookmarks that took me ages to find) have disappeared.

I made sure the .mozilla/firefox folder in my home directory had the same profile in it as the one on the backup copy. It made no difference.

I have no idea where to find the panel settings.....

While we're at it - where would I find the file containing the Evolution contacts for an extra contact list I created? I can find the default list easily enough but not my new one.  

If anyone has any idea how I might solve any of these wee challenges I'd appreciate your advice.

Cheers.

---

### Post by greymoose58 on 2005-12-07
OK. I've got them back. For anyone else who does the same thing It probably pays to know the following:

When you copy your home partition using sudo all of the files are given ownership of root so you need to change ownership to your own user name. I thought I had. Unfortunately there were a bundle of sub-directories that hadn't changed. The panel shortcuts were in home/user/.gnome2/panel2.d/default/launchers/greasy-00917d2fl.desktop. I guess the final file name may vary. Once I changed the ownership of that to my user name I got all of the shortcuts back.

I must have shut down my computer without closing Firefox last time. There was a shortcut called lock in the profile folder which told Firefox that the profile was already in use.

I still haven't figured out about the file for the extra contact list......

Cheers.

---

