---
title: "Sound popping and device appearing/disappearing."
date: 2014-07-07
forum: Hardware
---

### Post by S3loth on 2014-07-07
I'm having a problem with sound on my computer popping and in my Sound devices "Headphone" will appear and disappear. I've narrowed it down, and I believe it is the same issue as [this (unresolved) thread.]("http://ubuntuforums.org/showthread.php?t=2105433") In Windows I too had to run the Realtek software to disable the front panel detection, but I can't find a way to do this in Ubuntu.

Here is my hardware, pulled from [ALSA information script.]("http://www.alsa-project.org/db/?f=69f56d010cb19b26e72691c01bab0b373db36686")

---

### Post by S3loth on 2014-10-13
Just randomly bumping this since it really is the only thing keeping me from running Linux full-time.

---

### Post by Vladlenin5000 on 2014-10-13
> **S3loth said:**
> In Windows I too had to run the Realtek software to disable the front panel detection, but I can't find a way to do this in Ubuntu.


If so, you have an hardware problem -and- if you want to disable it anyway, why not just unplugged it from the MB? There... Problem solved.

---

### Post by S3loth on 2014-10-13
Sorry, I was a bit unclear;
The panel is listed as "front panel headphone", but it is integrated into the motherboard like so 
[IMG]http://www.gigabyte.com/fileupload/product/2/4139/5629_big.jpg[/IMG]

---

### Post by Vladlenin5000 on 2014-10-13
So you have no actual front panel connected?
If so, have you already checked for bent pins in its header, dust or debris or something else that might be causing an intermittent short-circuit?

---

### Post by S3loth on 2014-10-13
> **Vladlenin5000 said:**
> So you have no actual front panel connected?
If so, have you already checked for bent pins in its header, dust or debris or something else that might be causing an intermittent short-circuit?

Correct. There are also no bent pins or any dust or visible debris on the MB.

---

### Post by S3loth on 2014-10-15
SUCCESS!! I seem to have everything working now. As evidenced by [this bug report,]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1067434") this seems to be a known issue with the Gigabyte GA-Z77X-UD5H, so I'm going to post my steps for resolution here for anyone else having the problem (helped out by [this post]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1067434/comments/17")).

(Side note: I have my headphones plugged into the black port on the rear of the motherboard and they are working fine.)
[LIST][*]Install the "alsa-tools-gui" package and run HDAJackRetask.
[*]Under "Select a codec:" choose Realtek ALC898.
[*]Find the "Green Headphone, Front side Pin ID: 0x1b", check "Override" and in the drop-down select "Not Connected".
[*]Click "Install boot override".[/LIST]
You may want to try "Apply now" before changing the boot override, but this didn't work for me.


Again, there is no front panel on my computer, yet HDAJackRetasks lists multiple ones on the front panel. I'm thinking this whole issue is just poor support on Gigabyte's part.

---

