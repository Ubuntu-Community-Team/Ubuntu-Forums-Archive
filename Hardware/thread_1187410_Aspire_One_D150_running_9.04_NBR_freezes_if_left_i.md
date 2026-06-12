---
title: "Aspire One D150 running 9.04 NBR freezes if left idle"
date: 2009-06-14
forum: Hardware
---

### Post by Kimos on 2009-06-14
I have a brand new Acer Aspore One D150 that I've loaded with Jaunty 9.04 Netbook Remix. It's pretty much perfect. Out of the box the sound, wifi, webcam, touchpad, and pretty much everything else just works. Even suspend and hibernate work if I trigger them manually through the "Quit..." menu.

Only problem. If I close the lid and walk away, when I come back after an hour or so the system is locked up hard. No Alt+Ctrl+Bksp or anything. I have to do a hard reboot which seems to wipe out any logs or errors which might help me figure out what the problem is.

I have it set to not suspend with the cable plugged in and I have deactivated the screensaver. I had read that both of those things could cause lockups. Manually suspending or hibernating works perfectly. Setting the screensaver to start in one minute and watching it start works perfectly too. 

Any suggestions as to what the problem might be? Even help troubleshooting would be amazing. Ubuntu is so perfect on this machine, but having it lock up constantly makes it pretty useless.  :'(

---

### Post by Kimos on 2009-06-14
Ok, I've found something interesting in the kern.log

```
Jun 14 17:11:47 pat-laptop kernel: [ 5367.336095] Xorg invoked oom-killer: gfp_mask=0xd0, order=0, oomkilladj=0
Jun 14 17:11:47 pat-laptop kernel: [ 5367.336112] Pid: 2726, comm: Xorg Tainted: P           2.6.28-11-generic #42-Ubuntu

```

Over and over with various processes until I assume the OS dies. Ideas?

---

### Post by Kimos on 2009-06-16
Alright, so I don't think that it's idle that's my problem. It's closing the lid.

This seems to match my problem description on my exact hardware:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364592](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364592)

I get these errors when I close the lid, then the oom-killer events until the system locks up:
```
[84629.621056] ACPI: EC: missing confirmations, switch off interrupt mode.
```
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284263)

This thread, still ongoing, describes the lid problem as well:
[http://ubuntuforums.org/showthread.php?t=1095616&page=3](http://ubuntuforums.org/showthread.php?t=1095616&page=3)

Any ideas? I'm alright with a workaround for now. It runs perfectly except for this problem!

---

### Post by Kimos on 2009-06-16
So I've determined that kacipid and kacpid_notify consume memory and CPU until the system dies. It is responding to a continual call of the lid close even from ACPI.

If I disable ACPI support, I get no fan/power management, no suspend/hibernate, and likely no wifi support from the built in card.

Can anyone offer any help? All threads and bug fixes I've found regarding problems similar to this have all gone unsolved or unanswered. I can post any further details needed.

---

### Post by rico1981 on 2009-06-25
hi, I used to experience the same problem (my D150 didn't suspend on closing the lid) with Ubuntu 9.04 NBR. 

I don't know if that helped me but after updating BIOS to latest version (1.09 for KAV10) suspend/resume on closing lid seems to work fine.

Note that updating the BIOS is a dangerous process and it could "brick" your laptop...so I can't guarantee anything, maybe I was just lucky.

---

### Post by Kimos on 2009-06-25
That's a great idea. Thanks for the heads up. I'll look into the BIOS update for sure.

I've had no movement on my bug report but I've found it's pretty easy to work around. Just as long as I always hit suspend before I close the lid it works perfect. If I forget the OS locks hard, but I can manage. 9.04 NBR is a great release.

---

### Post by Shata on 2009-07-05
Yeah i also have D150 and ive tried everything u have so i guess when i torrent i wont be closing the lid huh lol.  If anyone can come up with fix id love it.

---

### Post by zachwood on 2009-07-26
Did you notice anything else working with the 1.09 update? Can you link me to the procedure you used to do it? I've heard some horror stories and don't want to goof it up.

---

### Post by Kimos on 2009-07-26
> **zachwood said:**
> Did you notice anything else working with the 1.09 update? Can you link me to the procedure you used to do it? I've heard some horror stories and don't want to goof it up.

Do you mean the BIOS update? I've decided it's too scary and haven't done it. Now that I've isolated the problem to closing the lid, I just make sure I sleep/hibernate it manually before closing the lid and I have no other problems. I didn't want to risk breaking something else.

---

### Post by irober02 on 2009-07-31
I'm having the same trouble on my new AAO D250 but didn't notice it on my old broken AAO (don't ask :-( )

Have you tried selecting a different close-lid option under Preferences > Power Management?

bye

ian

---

### Post by Kimos on 2009-07-31
> **irober02 said:**
> Have you tried selecting a different close-lid option under Preferences > Power Management?


Yes I have and to no effect. All those actions are reacting to the same flood of ACPI events.

---

