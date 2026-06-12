---
title: "Segmentation Fault  after login &amp; password entered"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Stegga on 2009-02-04
Hi there,

I have just scrubbed and installed 8.10 - what a pleasure!
I then installed VMWare and created an XP vmdk.

I setup my installation user as 'Gizmo', and then created another user 'Andrew'.
While working with Andrew, I was installing the pdf printer, and as I had come across CUPS issues in 7.04, I thought I would switch to user Gizmo (which is how I got around the printer issues in 7.04) and logged in as 'Gizmo' but after typing in the password (which is correct!) the screen went black, and then I could see the white mouse moving around, but the rest of the screen was black. It moved around happily, and changed to a 'I' and a 'hand' as I moved it around the screen, so it was doing what it should do, but I couldn;t see anything on teh desktop.
I eventually then switched off my laptop (holding the power button down for 5 seconds).
I then logged in as Andrew and thought nothing more of the Gizmo login.
This was all yesterday.

I then was working happily on Andrew today, and I got the Ubuntu Kung Fu book, and was running tip 65 and 66 (Installing all Multimedia Codecs) and used Add/Remove applications 'gstreamer'.

The tip then says that I should type 'sudo /usr/share/doc/libdvdread3/install-css.sh'. This was on the top of the next page, and I didn't see it.
Tip 66 says, Use Synaptec and install totem-xine.
It then says you must type 'sudo update-alternatives --config totem'.

Again, I didn;t see the 'Install totem-xine' part of this and I just typed the 'sudo update-alternatives --config totem' line and it gave me some error (I can't remember if it was a Segmentation Fault).
This made me read the tip closer which was where I saw the totem-xine installation part which I did successfully and then re-typed the above sudo command. I got a Segmentation Fault error.

I then re-read Tip 65 and typed in the 'sudo /usr/share/doc/libdvdread3/install-css.sh' and got a Segmentation Fault.

I then googled Segmentation Fault and got some comment about permissions and thought that there may be an instance of 'Synaptec' open that I wasn't aware of or something, so I tried to switch to user Gizmo again, and I typed in my password (correct again!) and it went black screen with the mouse as a 45 degree cross and then jumped back to Login 'window' the one that you get if you lock your screen for user Andrew, and I typed in my password for Andrew as well, and it asked me for it again!

I then turned it off (power button for 5 seconds) and when it came up I tried to login both as Andrew and Gizmo and it would just bounce to the Login screen again - with no error about password incorrect or username not found!

Any ideas?

Andrew

---

### Post by sahabcse on 2009-04-29
Hi

Follow below url this may help

[http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html](http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html)

---

