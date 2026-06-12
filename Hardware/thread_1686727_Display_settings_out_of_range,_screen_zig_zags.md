---
title: "Display settings out of range, screen zig zags"
date: 2011-02-12
forum: Hardware
---

### Post by geercom on 2011-02-12
I have 10.04 on an IBM Thinkpad R40. I set the Display settings to 1300 and something by some other number and the laptop must not support it because the screen came back all black and grey zig zags like a TV set gone array. No settings or anything can be reached from the screen now. What do I have to do to set it back?

---

### Post by Bucky Ball on 2011-02-12
> **geercom said:**
> ... like a TV set gone array.

I think you mean 'awry'. ;)

Boot into the recovery kernel (second on the boot list) and when you get to recovery options choose 'Failsafe X'. This will get you in using low resolution. You should then be able to alter your settings. Are you using the appropriate driver for your graphics card, if required?

---

### Post by geercom on 2011-02-12
> **Bucky Ball said:**
> I think you mean 'awry'. ;)

Boot into the recovery kernel (second on the boot list) and when you get to recovery options choose 'Failsafe X'. This will get you in using low resolution. You should then be able to alter your settings. Are you using the appropriate driver for your graphics card, if required?

How do I make these boot options appear on boot up? I don't see them.

---

### Post by Bucky Ball on 2011-02-12
At boot press escape repeatedly to get to the grub menu. In 10.04/10.10 I think it may have changed to shift.

I'm presuming you mean you switch on your machine and it boots straight to the login screen, no grub list?

---

### Post by geercom on 2011-02-12
> **Bucky Ball said:**
> At boot press escape repeatedly to get to the grub menu. In 10.04/10.10 I think it may have changed to shift.

I'm presuming you mean you switch on your machine and it boots straight to the login screen, no grub list?

That got me into a low resolution mode where I could look at the settings. But the settings showed up as 1024 x 768, 0 Hz and it didn't  permit me to see other options or change these settings. On reboot, I still had the same issue.

What now?

---

### Post by Bucky Ball on 2011-02-13
System>Administration>Additional Drivers (this is presuming you are online and have done updates). Anything there? A graphics driver disabled by any chance?

---

### Post by geercom on 2011-02-13
> **Bucky Ball said:**
> System>Administration>Additional Drivers (this is presuming you are online and have done updates). Anything there? A graphics driver disabled by any chance?

I could get grub to load last night but now it won't. Sometimes I push Shift until it says grub loading, but then that goes away and it boots all the way in anyway.

What could I be doing wrong with push shift on boot up?

---

### Post by geercom on 2011-02-13
> **Bucky Ball said:**
> System>Administration>Additional Drivers (this is presuming you are online and have done updates). Anything there? A graphics driver disabled by any chance?

I am back in. There are no proprietary drivers. I cannot download updates and I get the following error:

W: A error occurred during the signature verification. The repository is
not updated and the previous index files will be used.GPG error:
[http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't
be verified because the public key is not available: NO_PUBKEY
A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old
ones used instead.

It looks like I need to fix this, then get updates, then check again for drivers, then make sure all are working properly?

Or is there another way to check that current drivers are installed and working properly?

I need to fix both problems.

---

### Post by geercom on 2011-02-13
And there was no selection under Administration for additional drivers, just hardware drivers, and there was nothing there.

---

