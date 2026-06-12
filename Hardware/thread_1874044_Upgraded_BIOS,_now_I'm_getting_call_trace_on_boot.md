---
title: "Upgraded BIOS, now I'm getting call trace on boot"
date: 2011-11-02
forum: Hardware
---

### Post by jarthurs on 2011-11-02
I've just upgraded the BIOS in order to gain support for 1066MHz DIMMs, unfortunately on booting the machine (with the original 800MHz DIMMs) I get a call trace. 

I've added a screenshot I took with my phone. I've tried downgrading the BIOS to the original version without any luck, something has changed which is preventing the machine from booting and it's all gobbledigook to me...

I can still boot from CD and see my hard drive fine, just can't boot from it.

Anyone shed any light on this?

Regards,
Jason.

---

### Post by Redblade20XX on 2011-11-02
So you're getting this screen after you load the os or as soon as you turn on your computer? :confused:

- Red

---

### Post by jarthurs on 2011-11-02
> **Redblade20XX said:**
> So you're getting this screen after you load the os or as soon as you turn on your computer? :confused:

- Red

I believe it's as the machine attempts to boot the OS, I can boot up fine from a LiveCD (that's what I'm using now) but any attempt to boot into the OS on the hard drive gets the 'call trace' screen.

It's not a problem with the BIOS screens.

Regards,
Jason.

---

### Post by oldfred on 2011-11-02
Updating BIOS resets everything back to defaults. Did you have any settings that you had changed.

Sometimes you need some changes also.
Some settings other have reported:
> Disable Quickboot in BIOS
BIOS settings need USB mouse & keyboard
It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).


---

### Post by jarthurs on 2011-11-02
> **oldfred said:**
> Updating BIOS resets everything back to defaults. Did you have any settings that you had changed.

Sometimes you need some changes also.
Some settings other have reported:

I spent ages looking at the disk configuration in the BIOS and changing the SATA/IDE settings and was beginning to tear my hair out.

Then I happened to see in the BIOS summary screen some of the settings for the video. It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO). I figured it was worth a try, and it rebooted straight into Ubuntu.

Many Thanks,
Jason.

---

### Post by oldfred on 2011-11-02
Glad you found it. One more to add to my list of BIOS issues.:)

---

