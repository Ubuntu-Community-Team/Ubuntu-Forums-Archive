---
title: "Why can't I eject my CD or DVD?"
date: 2009-10-02
forum: Hardware
---

### Post by jia103 on 2009-10-02
Physically logged into the GNOME environment on my Ubuntu 8.04 box, I put in a DVD-RW into my drive, umounted the device, used dd to make an ISO image of it, then pressed the Eject button as I usually do to eject the disc. No problem.

(I know many people have already written to umount before ejecting, but (1) I already did before dd, and (2) it seems lately it's safe to do this as eject often appears to umount for me, at least from inside GNOME.)

Problem: After ejecting, removing the DVD, and closing the tray, I wanted to place a blank DVD+R into the drive in order to burn the ISO image onto it. Unfortunately, pressing the eject button on the drive no longer had any effect. In addition, the "eject" command didn't work from the prompt (nor "sudo eject"). It also appeared nothing was mounted.

Being stumped, I searched around and found the usual answers from several years ago regarding umounting before ejecting and how this is desirable... All good things but nothing to help me here.

Then I realized what the problem might be. I'm posting it here in hopes it'll help others if they run into a similar situation; however, note that this isn't for newbies as you'll soon read why.

Being a multi-user environment, Linux allows several users to log-in either locally (switching desktops, virtual consoles, etc.) or remotely (telnet/ssh/etc.). At the time I was trying to do this sitting in front of the box, I was also logged into another GNOME session via VNC, and another user was logged into yet another GNOME session via VNC.

Thus, there were three desktops at this time. After visiting the other two sessions, I realized what happened. When I inserted the first DVD, I nothing nothing more than a new DVD icon on my local GNOME desktop. At the same time, the other two users had VLC or Totem pop up on their remote desktops to watch the DVD, which had since been ejected. (Neither was there at the time, so the windows stayed up until I logged into each session and saw the desktop.)

After closing the media player windows, nothing was using the phantom DVD anymore. When I pressed the eject button on the CD/DVD drive, the tray now popped out.

Problem solved!

(I'm sure there's a better way to set this up for myself and for anyone else who logs in remotely so only one user would mount or use the CD/DVD at a time. If anyone has suggestions or inputs, you're welcome to respond and provide your thoughts.)

---

### Post by stinger30au on 2009-10-03
from shell you can type in

eject cdrom

and it should eject the cdrom no worries

---

### Post by jia103 on 2009-10-04
Sorry, I guess I should've clarified more.

I tried the following (not necessarily in this order):

[LIST=1]
[*]Pressed the Eject button on the drive.
[*]Looked for a CD/DVD icon on the GNOME desktop to right-click/eject; no icon available.
[*]Typed eject
[*]Typed eject cdrom
[*]Typed eject /dev/cdrom
[*]Typed mount to see if anything was mounted.
[/LIST]

I think that's about it. None of these helped. Hence the OP.

Thanks anyway.

---

### Post by eminembdg on 2010-02-21
I know this thread is old, but you made need to put

sudo eject cdrom

---

