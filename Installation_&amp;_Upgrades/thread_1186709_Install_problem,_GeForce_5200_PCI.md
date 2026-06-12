---
title: "Install problem, GeForce 5200 PCI"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by diskord on 2009-06-13
So I have an older 915 mobo with a P4 on it that I am converting over to a Mythbuntu box.

I tried doing the Mythbuntu install off CD, select my language, choose install, it then goes to Loading Please Wait, and then when trying to load the Hardware Drivers it gets a bunch of SQUASHFS errors and then it dies.

I decided to try loading Ubuntu instead, and then just apt-get'ing MythTV, but I had the exact same problem.

This was all using a PCI GeForce 5200 as my video card (mobo has built in video, no AGP slot).

I yanked the Video card out, put the monitor on the built in video card, it boots up no problem.

So the issue is obviously something with that 5200, but since this is a MythTV box  I kind of need that card for TV/DVI out. Is there anyway I can do the install with that card, is there some driver or something I can select during install to make this work?

Anyone have any ideas?

Also, this was all being done with Mythbuntu 9.04 and Ubuntu Desktop 9.04.

Thanks for your help

---

### Post by diskord on 2009-06-13
No advice?

If I install on the onboard video card, can I then just put the new GeForce 5200 in after the install and boot up with it in and install drivers?

---

### Post by matthewjames on 2009-06-13
I dont know if this would work in your case but its worth a shot. Do the Following:

Ok. Here is what I would say to do, worked for me. Completely remove the drivers you installed for the card. Go to hardware driver in System/Administration. Check and install Nvidia Accelerated graphics driver (180). After this reboot. Then go into administration and Nvidia X Server Settings. A popup window should appear, follow its directions. To restart the x server do the following:

```
sudo /etc/init.d/gdm restart
```

You might get frozen at a black screen saying reloading. If so just ctrl-alt-delete and let your system reboot. Everything should be done, good luck
Last edited by matthewjames; 13 Minutes Ago at 07:33 PM.. Reason: edit
matthewjames is online now Report Post   	Edit/Delete Message

Do this with the onboard card, then switch to the other one after durring the FIRST reboot. If this does not work you can try the 177 driver. Good luck.

---

### Post by diskord on 2009-06-13
I can't even get Ubuntu to install to deal with drivers! Literally, if the GeForce card is in the machine it crashes on the "Loading Hardware Drivers" screen during boot. This is while trying to install ubuntu, not on an existing install.

Is there some NVidia driver I need to use during install to even be able to install with this card?

---

### Post by diskord on 2009-06-13
For the record, I can't even install in safe mode if the card is in the machine. If I take the card out have no problem at all with the install.

this is driving me up a wall! I know MythTV will run under other OS's, but I really wanted to give Ubuntu a try...

---

### Post by diskord on 2009-06-14
Found a solution to my problem!

This article was actually dealing with a different motherboard, but it was essentially the same issue, and I found about 10 other threads with people having the same issue as me, so hopefully for anyone else they can give this a try: [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/)

Basically you just need to blacklist your onboard AGP card in /etc/modprobe.d/ and you are good to go.

Hope it helps other people.

---

