---
title: "MPlayer, DVD, and Removable Drives and Storage"
date: 2005-11-28
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-11-28
I saw a cool tutorial once for getting Xine to play DVD's automatically when one was inserted into the drive.
I am trying to get MPlayer to do this, but so far am having no luck...
What I want to happen is when I put in the DVD, MPlayer opens up like normal and plays the DVD with the controls showing.

After I close MPlayer and right click the DVD on my gnome desktop, and select Eject I am getting an Error.
**unable to eject, last error: Invalid argument**
When the DVD is playing there is also no MPlayer controls showing on the screen.

Here is the line I put into the Removable Drives and Storage (Video DVD Disk) section:
*mplayer dvd://1 -dvd-device /dev/hdc*

Anybody got a fix for this?

---

### Post by Mr. Electric Wizard on 2005-11-28
Wierd.
I ended up fixing this by doing:
*mplayer -fs dvd://* at the Removable Drives and Media.
This plays the DVD in full screen mode and does not give the eject error.

BTW, MPlayer plays dvds much better than Xine or Totem, or VLC...
No support for menus though...:smile:

---

