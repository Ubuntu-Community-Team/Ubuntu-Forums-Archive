---
title: "Compaq Presario F700 suspend issue, any ideas?"
date: 2009-01-16
forum: Hardware
---

### Post by Blescreen_of_Death on 2009-01-16
Okay, I'm a member of [www.overclock.net](www.overclock.net), and I cant seem to get the Ubuntu help I need over there, so now I'm here to pester you guys xD

Whenever I boot my lappy, while booting, it wants to suspend, thus stopping the booting process. It wont actually suspend though. It just halts booting and sits there until interrupted [I press and hold spacebar to get it to boot]

if I go into GRUB and add the boot parameter to the kernel "acpi=off" my wireless gets spotty at best and my lappy thinks its running on a power cord when its not. also, my package manager botches its self.

I've already looked at the "suspend quirk" page out there, and when I run the quirk-checker.sh file, I get a critical error:

CRITICAL ERROR: Using nvidia binary driver. This is not supported!

suggestions? I'd love a lappy that I dont need to hold spacebar down on to boot, but I need battery notification. Is there anyway I can keep acpi off until after booting is done?

---

### Post by Blescreen_of_Death on 2009-01-16
bump.

and I just noticed that I mispelled my username =X

Should be Bluescreen of Death, not blescreen xDDD

---

### Post by Blescreen_of_Death on 2009-02-17
bump xD.

remembered that I made this thread a LONG time ago. still need a fix, if there IS one.

---

### Post by magli on 2009-03-08
I don't have a solution.

This problem has been driving me nuts, and it sometimes occurs while shutting down, as well as while booting.

I didn't realize it was related to ACPI/suspend. I never bothered searching for a fix, but the problem was gone when I booted my laptop today. This intrigued me, hence why I am here. 

I wasn't on-line last time I booted, so I haven't updated anything since. I remember having to continuously interrupt last time I booted.

Maybe it was a fluke. I'll reboot now to verify.

Have you been able to get either suspend or hibernate to work?

---

### Post by Chibone on 2009-03-08
Is it related to this bug?

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247)

From reading your post, "It just halts booting and sits there until interrupted [I press and hold spacebar to get it to boot]" sounds like "freezing on boot, unless I hold down a key" to me.

I had a similar problem and I own a F700 too (specifically the F767NR) and I had to add "hpet=disable" to my kernel line in grub to fix it.

Fortunately, this problem seems fixed in Jaunty for me, along with some other bugs (just tested a livecd earlier today).

And suspend/hibernate does not work for me.  Never has.

---

### Post by mharrolle on 2009-10-08
> **Chibone said:**
> Is it related to this bug?

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247)

From reading your post, "It just halts booting and sits there until interrupted [I press and hold spacebar to get it to boot]" sounds like "freezing on boot, unless I hold down a key" to me.

I had a similar problem and I own a F700 too (specifically the F767NR) and I had to add "hpet=disable" to my kernel line in grub to fix it.

Fortunately, this problem seems fixed in Jaunty for me, along with some other bugs (just tested a livecd earlier today).

And suspend/hibernate does not work for me.  Never has.
Chibone, 
  I have an F700 also and I'm running Jaunty.  I have the suspend/hibernate problems and in addition to that when I'm on battery power the system won't start up with out pushing or holding keys down and even then it does weird things like ask me to sign in when it does finally start. (wow! run on sentence from hell)  Also it does something similar when shutting down under battery power.  Here's my issue. I am a total newb to Ubuntu/Linnux and the work around at the link you gave looks roughly like stereo instructions that have been translated from english to japanese and back again. Is there any possibility that someone will "Newbie Proof" this fix anytime in the near future? Or has that already been done and I just haven't found it yet?

---

