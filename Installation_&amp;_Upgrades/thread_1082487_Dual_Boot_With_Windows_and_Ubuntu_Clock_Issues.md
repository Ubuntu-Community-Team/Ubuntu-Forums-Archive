---
title: "Dual Boot With Windows and Ubuntu Clock Issues"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by crapple on 2009-02-27
I am currently dual booting ubuntu 8.10 with windows xp. I thought I had successfully dual booted until I noticed the clock time was wrong in Windows. I used the code w32tm /resync in command prompt in windows which fixes the issue as long as I only boot windows. As soon as I boot ubuntu and then reboot to windows the time is messed up again. It usually says it is sometime in the morning when it is late at night or vies versa. I didn't have the problem before dual booting so I think it might have something to do with grub. I am using grub to dual boot. I have it set up so that it boots windows but grub is not installed on the windows harddrive.(i am dual booting with 2 hard drives. primary window secondary ubuntu). Would making the ubuntu drive the master make any difference? The bios is set to boot automatically from the slave so that isn't a problem. Any ideas on how to fix this problem. The time in ubuntu works no problem. (just another reason why i like ubuntu better then windows) Thanks

---

### Post by caljohnsmith on 2009-02-27
How about posting the output of:
```
cat /etc/default/rcS
```
If that shows "UTC=yes", try changing it to "UTC=no", and I think that might solve your problem. Let me know how that goes.

---

### Post by crapple on 2009-02-28
Thank you i changed it and everything appears to work fine

---

