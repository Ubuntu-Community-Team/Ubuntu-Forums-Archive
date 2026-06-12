---
title: "Information for nvidia"
date: 2014-09-10
forum: Hardware
---

### Post by jman514 on 2014-09-10
This is not a question but rather my experience that I have had with my HP desktop.  This may be useful to others who have similar problems.  I have an HP Pavilion a6720f desktop with on board nvidia 8200.  It came with Windows Vista.  Then I put a duel boot with Ubuntu 12.04.  The 12.04 worked perfectly.  The Windows developed problems so I decided to do a clean install, wiping the hard drive.  I installed Ubuntu 14.04.  I did all the updates and the nvidia driver.  I encountered a persistent problem.  I am using a Logitech wireless mouse and keyboard with a unifying receiver.  The unifying receiver kept crashing.  I would crash at different times: at boot, five minutes in, an hour, ect. Changing USB ports did not work.  I had to unplug and reboot.  So I decided to go back to 12.04.  When I tried to activate the nvidia driver my screen would scramble becoming unusable.  From the recovery mode I took a look at the xorg log and then purged nvidia.  The xorg log had stated that it had stopped the unified receiver (it had crashed like in 14.04).  
So what I understand is this.
The new nvidia update will not work on some of the cards.
Xorg causes the Logitech Unifying Receiver to crash while using the update.

Currently I am trying to install the nvidia-304 instead of the 331.  However I am running into dependency problems.  Sorry I can't give more detailed information.  I hope this is helpful to someone.

---

