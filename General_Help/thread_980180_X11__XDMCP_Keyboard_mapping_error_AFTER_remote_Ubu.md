---
title: "X11 / XDMCP Keyboard mapping error AFTER remote Ubuntu login (!)"
date: 2008-11-12
forum: General Help
---

### Post by theheadguy on 2008-11-12
I am not familiar with every single 'term' so please bear with me.  Also posted to [MacRumors]("http://forums.macrumors.com/showthread.php?t=599056").

Setup:
MBP running 10.5.5 w/ newest version of X11
Linux box running Ubuntu 8.04 (Hardy Heron)

Issue:
Keys not mapped correctly *after* successful remote XDMCP login from OS X to Ubuntu.

Background:
When I open Terminal and remotely access Ubuntu, the Ubuntu login screen shows up as expected.  I can _successfully_ type my username and password from my Mac.  However, once the login actually occurs, the keyboard no longer types the same letters that are pressed.  Meaning, if I press "d" on the keyboard, a "y" will show up on Ubuntu, pressing "f" results in an apostrophe ('), etc.  There are various forums on the Internet that reveal few people having the same issue, but I can't understand the solution (and I thought I was a techie).  To make things even more bizarre, when I VNC in using a standard OS X VNC client and Ubuntu's native remote desktop feature, the keyboard mapping is perfect.  There are NO issues with VNC.

Q&A:
Q: Why don't you just VNC instead of XDMCP?
A: I would love to, BUT, I want to be able to put my small Linux server box hidden in a ventilated cabinet with no monitor, keyboard or mouse.  Out of the box, Ubuntu does not start the VNC service without someone already being logged in.

Q: Why don't you find a way to start the VNC service before login?
A: I'm trying to, but it is proving equally difficult.

Q: Why don't you log in with XDMCP, start a VNC session, then close XDMCP and continue with your VNC session?
A: Great idea.  However, when I close out of XDMCP, Ubuntu immediately logs out for security purposes and, thus, closes my VNC session.

Q: Why don't you log in with XDMCP, minimize it, and start a VNC session and keep both open?
A: Great idea.  However, with both sessions open, the VNC session is not viewable.  So to use the Linux box, I have to seen windows within XDMCP and to type I have to use the black VNC screen while watching the XDMCP window.  Thank goodness nobody is watching me type in a black window, I'm sure I look crazy.

Q: Why are you doing this?
A: I have Boxee on my AppleTV and have found the interface to be much better.  But moreover, the ability to pull content off of several network resources (mainly my Linux box) is amazingly easy.  My Linux box is dedicated solely to downloading movies (uh, free ones of course) and as soon as the download is complete, it instantly appears on Boxee, without any intervention from me.  It's a great setup as long as I can ditch the need for a monitor, keyboard and mouse from Ubuntu.

Thanks for your help.  Hopefully, if this gets resolved, it can help someone else.

---

