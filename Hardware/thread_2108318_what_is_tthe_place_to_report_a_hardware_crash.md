---
title: "what is tthe place to report a hardware crash?"
date: 2013-01-24
forum: Hardware
---

### Post by valugi on 2013-01-24
Sometimes when I remove my USB headset from the USB slot, the system gives this error and freezes. I see launchpad is organized by packages and I dont know to which package this error belongs.
Also I can only do a photo of the error, I dont know if this error is actually logged anywhere.
[IMG]http://farm9.staticflickr.com/8508/8410365819_280ea2ebba_z.jpg[/IMG]

Image [here]("http://www.flickr.com/photos/valugi/8410365819/")

---

### Post by Cheesehead on 2013-01-24
> **valugi said:**
> Sometimes when I remove my USB headset from the USB slot, the system gives this error and freezes. I see launchpad is organized by packages

Please file the bug against the 'linux' package. mikewhatever's post below is the right way to do that.

1) Usually, the triager will first ask you to to try the latest development kernel in case the bug has already been fixed someplace else. So do that before you even file the bug.

2) Use the command [FONT="Courier New"]lsusb -v > lsusb-v.log[/FONT]  to create a detailed hardware description of the USB headset in the file *lsusb-v.log*. Attach the file to the bug report. Do NOT paste the (quite long) content into a comment or description - really attach it as a separate file.

3) Remember to attach that photo to the bug report, too.

4) You must be willing to help test proposed fixes, and say so in the bug report. The engineer or developer working on your report probably doesn't have that piece of hardware handy to text the fix. Without a test, the fix cannot be committed.

---

### Post by mikewhatever on 2013-01-24
This is not a "hardware crash", whatever that means, it's a [kernel panic]("https://en.wikipedia.org/wiki/Kernel_panic").

To report it, open a terminal window, and run **ubuntu-bug linux**.

That should collect all relevant logs, and attach them to the bug report. All you need to do is explain what happens - you remove the USB headset, and it freezes, and so on.

---

### Post by valugi on 2013-01-25
Thanks to both. Done
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1104843") is the bug report if anybody has the same problem.

---

