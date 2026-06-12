---
title: "Laptop crashed - can't reboot"
date: 2010-11-24
forum: Hardware
---

### Post by Buster95 on 2010-11-24
My laptop crashed (froze actually) while reading emails. When I rebooted, it went into a drive check process which reported a mounting problem with / . Actually, I can't read it all because the display massively overlaps the screen.

I tried to boot in recovery mode but as far as I could tell with the screen overlap, it reported a corrupted orphan linked list. I have not been able to progress beyond this point with recovery mode.

I also tried to boot directly off the original download disk but after spinning up the drive, it seemed not to be able to read it and defaulted back to the grub screen.

I then downloaded and burnt a new 10.10 iso and tried it. As before, it continued to ignore the disk drive and jump to the normal grub screen.

I then intervened with the bios on startup to ensure that the program load up was specifically directed toward the correct disk drive and not the HDD. That also failed.

I would appreciate any thoughts and suggestions.
Thanks

---

### Post by Fafler on 2010-11-25
Well, you most have done it once, so just try again until it works :-)

Another thing you could try is to press e from the grub menu and remove the two words "quiet splash" from the fourth line or whereever it is. Replace it with "1" and pres ctrl + x to boot. This will boot the system into singleuser textmode and from there you can do a fsck /

---

### Post by Buster95 on 2010-11-25
Thanks Fafler,
I had previously tried rebooting many times using all the options that appear to be available.

Tried the grub edit approach as you suggested -
"e" to enter grub edit
Deleted "quiet" from line 4
Inserted "1" at line 4
Tried "ctrl + x" but did not boot
Tried "b" to boot but it reverted back to the pre-edit boot menu and proceeded to launch into the diagnostic as before.

Also tried "ctrl shift F2" which I thought would get me into text mode but that didn't seem to work either.

Any other thoughts?
Thanks

Any other thoughts?

---

### Post by Fafler on 2010-11-25
Danm, now i can't make this work either. It  seems you should use "single" instead of "quiet splash"

Now, it should boot into a menu. Choose root and check you filesystem from there with fsck /

---

### Post by Buster95 on 2010-11-25
Tried replacing "quiet" with "single" in normal mode as well as adding "single" to recovery mode.
In neither case can I get a response from "ctrl + x"
What am I doing wrong?

---

### Post by Fafler on 2010-11-25
Well, that's weird. It works here. Does it say what the shortcut for booting is at the bottom of the screen?

---

### Post by Buster95 on 2010-11-25
"b" to boot
"e" to edit
"c" for command line
"o" for new line
"d" to remove a line
"esc" to return to menu

I have tried pressing "enter" after editing and then "b".
I have tried "b" without pressing enter".
I have tried "ctrl + x"
I have tried "ctrl + alt + f2"
I have tried "ctrl + alt + F3"
I have tried "ctrl + alt + F7"

When I press "b" after making the edits, instead of continuing the boot from that point, using the edit, it restarts the whole bios kick-off process, which in turn starts the original grub menu countdown.

Clearly, I'm missing something trivial.

---

### Post by Fafler on 2010-11-25
[http://dl.dropbox.com/u/3453954/grub.png](http://dl.dropbox.com/u/3453954/grub.png)

Doesn't your grub look like this? What version of Ubuntu are you running?

---

### Post by Buster95 on 2010-11-25
Sorry about the delay - had to sleep (time zones and all that).

Similar grub - but with different commands. I can't show you with a screen grab because (obviously) I can't access the system.
The OS is Ubuntu 10.04 and I first tried to reload 10.04 without success.

I've just about given up trying to get in to repair the file system. Reluctantly, I'm about to try to re-image it with a fresh burn of 10.10. If that doesn't work either, I'll assume that I have got a hardware failure.

---

