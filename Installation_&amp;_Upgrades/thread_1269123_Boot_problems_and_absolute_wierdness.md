---
title: "Boot problems and absolute wierdness"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2009-09-17
I have a small form factor Shuttle XPC.  It has been giving me problems on boot.  Basically, it hangs either after the memory test (where it reports the clock speed), or during the detection of ide drives.

If I wait long enough (time to run upstairs and take a whiz or even "longer"), I'll come back to a boot screen that has stopped with a warning that boot parameters have been changed, enter setup to correct or press F1 to continue.

Most times, pressing F1 brings me to the OS selection menu where I can choose to boot into Ubuntu Studio or Windows XP or one of those recovery mode choices.

It seems lately that boot time has become increasingly long.

So, I posted the problem on the Sudhian forum, and was advised to check my drive DIP setup to make certain I had it set for Master/Slave vs Cable Select (I had it set to cable select).

So, tonight, I change the drive setup to Master w Slave present/Slave.

Sure enough, my machine's bios picked up the slave drive (it had been reporting it not present, even though everything worked normally when you finally managed to boot into an operating system).

However, booting into Ubuntu brought up the scaly 'studio' desktop, but the sign in box was garbled along with the mouse cursor.  The cursor would move with the mouse, but you could not make it focus on the garbled input box - log in not possible.

Numerous reboots resulted in the same garble.

What's even more unusual is that booting into XP would bring the normal sign-in music, but a brief appearance of the Ubuntu Studio desktop followed by darkness - no log in possible.

I finally switched the dip switches back to cable select, and now, my bios detects both drives as master/slave respectively, and things are working normally - boot time slow, but much faster than previous to my fiddling around.

Could anyone offer a clue as to what might be going on with my machine?

I will offer that the drives are new and work perfectly when I finally get logged on.

Grub still reports with each boot that drive parameters have been changed - I don't understand that, but can live with it as long as I don't have to waste a half hour or more booting and rebooting or simply walking away from the machine until it decides to complete the boot process.

I'm thinking this boot problem has something to do with the bios, but the cross-corruption definitely had to do with my switching the position of the dip pins (is that what you call those little slip on things that short the dip pins?).

Any clues would be appreciated.

Caruso - PS: After returning to my original drive cable configuration, my scaly Ubuntu Studio desktop is gone, and I'm back to the original orange 9.04 desktop - the studio aps are still installed, and the desktop 'gestures' (the way my browser address window works, for instance) is still consistent with Studio.  Curious/strange.

---

### Post by carusoswi on 2009-09-17
Sorry, DIP is not the right name for those pins in the back.  I meant to say jumper pins (I think?).  Anyhow, you move these little white or black plastic thingies that contain some conductive wire, and they short the two pins over which they reside, and you use them according to the instructions included with the drive (thankfully printed on a sticker somewhere on the top of the drive)to set it up as the only drive, the master drive, or the slave drive.

Most anyone offering advice already knows that, so, sorry if I'm repeating the obvious.  Machine booting much better now, btw.

Caruso

---

### Post by carusoswi on 2009-09-19
My problem turns out to be some issue that has developed in my machine that makes it choke when I have two drives in the system.  Pull out one drive, and I can boot into Ubuntu 9.04 in about 50 seconds from the time I touch the start button to the completed desktop (windows XP takes seven minutes after Grub appears and I select that OS from the list).

Put in two drives, and I can go pop a bag of corn in the microwave, come back, and the F1 screen is sitting there telling me that the boot parameters have changed (F1 to continue).

I really can't figure out what might be causing that.  If I press F1, most of the time, Grub starts and I can go ahead and boot into Ubuntu, after which, I can run without problems (and full use of both drives) seemingly forever.

Any suggestions would be appreciated.  For now, I'm just running with one drive.  The second one I have inserted into a firewire enclosure so that I can access its data.

Caruso

---

### Post by carusoswi on 2009-09-24
SOLVED: Drive 2 was bad.  Won't respond in either a firewire or usb external enclosure, either.  Cannot format it.  It's a relatively new 320 gb drive.  Popped in another drive, and machine boots fine.

Caruso

---

