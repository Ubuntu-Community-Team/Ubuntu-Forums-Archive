---
title: "Help!  How to force apt-get to use the cd (commandline only)"
date: 2008-11-05
forum: General Help
---

### Post by Winterhart on 2008-11-05
Is there a way to force apt-get to use only the cd-rom as a source?  X won't start, so all I have is the root terminal from the Recovery menu, and that doesn't initialize the internet connection.  The only package source I have is the CD.

I've gone so far as to remove everything *but* the cdrom line from /etc/apt/sources.list, and apt-get update runs fine.  When I try to reinstall xfonts-base, though, it tells me that the package cannot be reinstalled because it cannot be downloaded.

What the heck?!

For the record, the error I'm getting is "Fatal server error: could not open default font 'fixed'"  (fc-cache -f -v doesn't work, neither does dpkg-reconfigure xserver-xorg.  The only thing I can think of is to reinstall the xfonts package... and if that doesn't work I'm just screwed.)

---

### Post by cmnorton on 2008-11-05
You have to go into your repository sources and check off the CD. On Ubuntu, I've forgotten where it is exactly -- I use Kubuntu -- but it's under Admin.

---

