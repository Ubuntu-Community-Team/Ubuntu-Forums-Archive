---
title: "Unable to print to a Samba printer"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by underpope on 2006-01-05
I'm having a devil of a time getting my Breezy install to print to a Samba shared printer.  The setup is my HP 712C DeskJet hooked up to another Linux computer and shared out by Samba so I can reach it with both Windows and Linux.  I am able to print to this printer with my Fedora laptop, but not with my Kubuntu desktop.

CUPS seems to be working fine on my desktop.  When I watch the CUPS queue, print jobs seem to go through it fine.  When I execute watch lpq, I can see it pass through my local queue.

However, print jobs never seem to make it to the Samba queue.  There seems to be a communication issue between CUPS on my machine and Samba on the remote machine.  I have the printer set up as a Samba printer on my desktop, and I can see it just fine when doing a network browse.

Anyone got any ideas?  This is driving me crazy.

---

