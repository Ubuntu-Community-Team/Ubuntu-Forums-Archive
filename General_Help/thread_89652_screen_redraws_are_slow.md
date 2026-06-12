---
title: "screen redraws are slow"
date: 2005-11-13
forum: General Help
---

### Post by beijingjj on 2005-11-13
I'm running 5.1 on my IBM Thinkpad T42.  Following the guidance at [http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/](http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/) I have installed the binary fglrx video driver, and that did improve things, however I've noticed that screen draws are slow on this installation compared to other installations I've installed on the same laptop.

For example, if I alt-tab to change windows, if it's a window I haven't viewed recently there is perhaps a 1/2 second delay before it comes up.  Similarly sometimes when I click on one of the drop-down menus on mozilla there is a delay before it is drawn.  This did not happen when I was running Mepis on this same laptop, so it must be a configuration issue somewhere.  I've tried both gnome and kde.

Any ideas?

---

### Post by elempoimen on 2005-11-13
Same kind of issues here with a Thinkpad T23.  

One thing I did was switch from Firefox to Epiphany...Firefox is a dog on Linux.  But I really think the problem lies in Ubuntu's x.org configuration.  I don't know enough about x.org to mess with it.

---

### Post by beijingjj on 2005-11-13
I've been using Mozilla for a long time now without this problem, it's only since moving to Ubuntu.

-BeijingJJ

---

### Post by beijingjj on 2005-11-15
I believe I've found a solution to this.  Go to the mozilla releases page but don't download the default mozilla, download the one that says gtk2+xft.  It is faster with the screen redraws.   I'm still puzzled why I didn't have this problem with Mepis though.

---

### Post by reedlaw on 2005-11-17
I'm getting a really slow redraw for Evolution.  When I switch from Firefox to Evolution I notice about a one second delay as the frames are all redrawn.  I have a Geforce FX 5200 128MB so I wonder why it should be so slow.  Why can't Gnome use some of that hardware acceleration?

---

### Post by elempoimen on 2005-11-17
You know, one thing I noticed after trying to reconfigure x.org is that dropping my screen depth to 16-bit really helped the speed.  Just load up /etc/X11/xorg.conf in your favorite editor (kate, gedit, nano...) and find the "screen" section.  Make sure "16" as listed as a display mode, then change "DefaultDepth" to 16.  Restart X (Reboot or Ctrl Alt Bksp) and see if that doesn't help.

---

