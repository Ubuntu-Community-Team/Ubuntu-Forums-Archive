---
title: "OEM install mode difference."
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by 123456789123456789123456 on 2009-04-27
This is an interesting one.  I have a computer I am building for a customer.  For some strange reason, that is currently unknown to me, the 9.04 live cd would never boot.  However 8.10 did, I installed 8.10, and upgraded to 9.04 directly after the installation of 8.10 was completed.  I am used to under OEM mode, that it does not ask for a username/password, just goes to the desktop.  Well after I upgraded to 9.04, it went to the asking for username and password.  I can enter in the oem, and oem password, and get into the system.  This is just a little strange to me.  And I was wondering if anyone has an openion, or knowledge, My current theory is when I tell the machine, to prepare for shipping, that the next startup, it will not ask for a username and password, since it no longer has one on the system.  Do you agree?

Also, something else interesting.
I happened to stop by the update manager, before it even checked for updates, it had in it's list, the cd burning software listed as needing an update.  But the update was greyed out, It would never highlight, or let me select it to download the update.  I have no other instance of 9.04 saying there are any updates as yet, since it is still very early in the release.

synaptic package manager, apt, and add/remove, programs work properly.

I would like to see if this can be resolved, if it is a problem, before I ship the computer.

---

### Post by 123456789123456789123456 on 2009-04-27
partially solved I think, It turns out that for some reason after restart of the upgrade, the auto login function was disabled, I just had to enable it again.

The update manager problem seems to still be there
It is still listing the cd/dvd burning software, but is greyed out, however it does get all other updates as needed, and they can be accessed and downloaded.

the other thing is a bit weired.
could completely removing the software in question, and reinstalling it, possibly fix the problem?

---

### Post by 123456789123456789123456 on 2009-04-27
concerning the update manger.  I wonder if the problem could be related to the fact that directly after I installed 8.10 sucessfully on the machine, I upgraded directly to 9.04, without downloading any security updates for 8.10.  I am wondering if the update that is appearing for the burner software, was not an update ment for 8.10 and has somehow been left over, and since it is not needed for 9.04, that is why it is not allowing me to access the update.

I wonder, does anyone have any information of possible, removing the program, that should emliminate the upgrade, since it is no longer on the system.  Plus after that, installing the program again, that reinstallation should include any updates made to the program.  At least that is my theory, does anyone agree?  Disagree?

---

