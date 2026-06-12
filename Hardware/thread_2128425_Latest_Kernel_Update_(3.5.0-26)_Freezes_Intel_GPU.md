---
title: "Latest Kernel Update (3.5.0-26) Freezes Intel GPU"
date: 2013-03-23
forum: Hardware
---

### Post by phillipblake on 2013-03-23
Wow, super frustrated. I love Linux, especially Ubuntu, but the latest kernel update (3.5.0-26) has cause an apport error to keep popping up.  At its worst, it locks up my machine requiring me to do a hard reboot.

There error report shows this as the primary cause: /usr/share/apport/apport-gpu-error-intel.py

I'm running Ubuntu 12.10 on a Toshiba Satellite C850.  It's been running perfectly for months until I applied the update earlier this week.  Now it's rendered my machine almost unusable.  After some review, I do see that this issue is deemed fixed in the upcoming Raring Ringtail release.  That's fine... but what am I supposed to do for 4 weeks until it's officially available for download?  This is a work laptop which I use to code websites.  When it locks up, and I do a hard reboot, it destroys my Aptana Workspaces.  They then go through a rebuild which means I lose valuable development time.

Whilst super impressed with open source, yes I'm exploiting its benefits, leaving a gaping whole like this in current GPU support is a little concerning.  I'd say recent adopters, moving from Windows, might opt to go back.  I have to say, reluctantly, I did consider it myself just for hardware compatibility.  One compromise I accept using Linux is that GPU drivers are not truly optimised for the hardware they run on.  In other words you get a good performance but not really as good as it would normally be on an Intel specific driver.  Perhaps someone can correct me on this... I'm still only 12 months into using Linux but understand frame rates are lower - not withstanding Steams latest efforts.

Any advice would be really appreciated.  I've spent a considerable amount of time learning the GIMP, APTANA, INKSCAPE and other awesome Linux software.  I'd hate to have to roll back my decision because I can't find a suitable solution.  Gosh, the thought of going to Windows 8 is simply jarring... I hate the UI, it's just revolting.  And once upon a time you'd have had to saw off my arm to prise Windows away from me.

Cheers in advance for any help.

Phillip

Addendum: I have just read that apport itself can be the problem, particularly with the error message I'm receiving. It's recommended to temporarily switch it off.  I've done this, I'll report back how I go.

---

### Post by vanadium on 2013-03-23
You better revert to the older kernel that worked for you. I did the same. The last two kernel updates resulted in some slugishness in my otherwise quite fast system. What is a lot worse: I had random system freezes every now and then (keyboard dead, mous pointer moving but click not working). Clearly due to the kernel upgrade, because things are back to normal with the 3.5.0-24-generic kernel.

---

### Post by agurk on 2013-03-23
Same here. Unsurprisingly, disabling Apport itself didn't solve it. Have reverted to 3.5.0-25 for now.
Syslog snippet from 3.5.0-26:
```

kernel: [ 5674.691315] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
kernel: [ 5674.691320] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
kernel: [ 5674.701157] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
```

Edit: seems to be this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)

---

### Post by phillipblake on 2013-03-23
> **vanadium said:**
> You better revert to the older kernel that worked for you. I did the same. The last two kernel updates resulted in some slugishness in my otherwise quite fast system. What is a lot worse: I had random system freezes every now and then (keyboard dead, mous pointer moving but click not working). Clearly due to the kernel upgrade, because things are back to normal with the 3.5.0-24-generic kernel.

As I'm still a relative newbie, what's the easiest way to rollback to the previous kernel ?

---

### Post by agurk on 2013-03-23
> **phillipblake said:**
> what's the easiest way to rollback to the previous kernel ?
Unless you have purged them from your system already, you should be able to launch older kernels from your GRUB boot menu -> Advanced options for Ubuntu.
You may have to hold down <Shift> to see the boot menu.

---

### Post by phillipblake on 2013-03-23
> **agurk said:**
> Unless you have purged them from your system already, you should be able to launch older kernels from your GRUB boot menu -> Advanced options for Ubuntu.
You may have to hold down <Shift> to see the boot menu.

Ok, I see the older kernels in my GRUB boot menu.  Each kernel is represented twice, one with just its name and the other with (Recovery Mode) next to it.  Do I need to select the recovery one ?  And what about any updates that came with and post the offending kernel update - will they be impacted in anyway by rolling back?  FYI. I'll be rolling back to (3.5.0-25), this was working fine for me.

I really appreciate your help.  Thanks for this :-)

---

### Post by phillipblake on 2013-03-24
I went to the GRUB boot menu, selected 3.5.0-25, and then finished the boot sequence.  To my surprise, the error popped up again.  So now I'm thinking it's either the hardware failing or another update that came around the same time as the 3.5.0-26 kernel?  Just not sure now.  I selected the kernel without (Recovery Mode) written next to it.  Not sure whether I should have selected the recovery mode one?

---

### Post by agurk on 2013-03-24
phillipblake, it sounds like you selected the correct kernel. Apart from seeing error reports, do you still experience the freezes with 3.5.0-25?

---

### Post by phillipblake on 2013-03-24
> **agurk said:**
> phillipblake, it sounds like you selected the correct kernel. Apart from seeing error reports, do you still experience the freezes with 3.5.0-25?

Actually I switched back to the latest Kernel after the first error  message popped up.  I'd assumed that changing back hadn't actually  resolved the issue. Perhaps I should run the older kernel for a few  hours to see if indeed there is an improvement, minus any error  messages.  Obviously the OS freezing is my biggest concern; I'll test  against that scenario to see if 3.5.0-25 offers better stability.  Beyond  that, it might be time to look at whether the GPU itself is starting to falter.  I  do note that the GPU fan has always ran a lot more often under Linux than  Windows, for which the hardware was originally optimised.  Perhaps over time it's caused overheating or some kind of degradation, you never know.

Thanks 'agurk' for sticking with this thread :-)

Phil

---

### Post by agurk on 2013-03-24
phillipblake: You're welcome. Now, should you indeed find that 3.5.0-25 works just as well for you as it does for me (i.e., no GPU hangs), you can get rid of the annoying error messages by disabling error reporting:

```
sudo apt-get install xdiagnose
sudo xdiagnose
```

---

### Post by vanadium on 2013-03-25
Turning off apport error messages actually does not require installing anything. A slight edit to a system file will do it.
See [http://www.webupd8.org/2012/06/how-to-get-rid-of-internal-system-error.html](http://www.webupd8.org/2012/06/how-to-get-rid-of-internal-system-error.html)
Apport was disabled by default on older Ubuntu releases. Since 12.04, curiously, it is enabled by default. As a result, now you see the error messages and one thinks Ubuntu 12.04 is a lot less stable than its predecessors.

The "locking" issue is a different thing, and there, you should really confirm whether you also experience these lockups with an older kernel. As far as I can tell, making a choice from the grub menu only allows you to change kernels for the current session. To use an older kernel more permanently, I locked the 3.5.0-24 kernel packages using synaptic, then uninstalled the more recent ones (if someone knows a better procedure to permanently boot with an older kernel, let me know).

---

### Post by bluepicaso on 2013-03-25
> **agurk said:**
> phillipblake: You're welcome. Now, should you indeed find that 3.5.0-25 works just as well for you as it does for me (i.e., no GPU hangs), you can get rid of the annoying error messages by disabling error reporting:

```
sudo apt-get install xdiagnose
sudo xdiagnose
```

Hey I had same error and now posting this after switching to 3.5.0-25,
thanx to agurk.

I just wanted to know, I would get linux headers updated as i got them through update manager
Will i be always on 3.5.0-25 even after any new update. or it just automatically switches to new kernel version after update, lets say for "example 3.5.0-26"


thank you

---

### Post by phillipblake on 2013-03-26
Thanks for all your comments. I'll give that a go.  Looking forward to Ubuntu 13.04 - apparently the kernel update should address this.  Take care :-)

---

### Post by pfeiffep on 2013-03-27
I had similar issues with both 25 & 26 - I'm happily and stabily running 24!

---

### Post by aldeby on 2013-03-31
Thank you phillipblake for reporting. 
This helped me a lot in narrowing down the problem. I agree that such regressions are annoying, especially on a stable system. I hope this doesn't undermine your trust in open source. In fact, the power of open source is not being error free, but in patching the errors quickly and having a very supportive and active community. As a consequence errors are less in number, but unfrotunately always happen. Audit and Quality Assurance procedures are especially important here. I expected this critical regression to be spotted out while the kernel was still in the Proposed update channel, but apparently it didn't :(

The bug we are talking about is tracked at this address: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)

For the time being I am also deleting the latest kernel and running with previously installed 3.5.0-24 . Note that even if you are installing the system from scratch you can always choose the kernel version shipped with the 12.10 release and wait a while before installing kernel updates (not the best advice, but what shall we do until they pull 3.5.0-25/26 back?)

---

### Post by agurk on 2013-04-02
A small update, the [Apport problem]("https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1073626") mentioned in this thread may have been fixed in an updated xdiagnose package that hit the mirrors today.

---

### Post by ryanvade on 2013-04-02
Hello.  I don't mean to bring this back up, but I am using kernel 3.8.2-ck1 on Ubuntu 12.04 and experiencing the graphics lockups and the error message.  Does anyone have any suggestions for me? The older kernel (3.2) on my system is also having the issues.  I also have an optimus card for a Nvidia GT 630M, does this effect the issue in any way?

---

### Post by prusswan on 2013-04-07
This is another of those annoying regressions, affecting even the Intel integrated graphics on my MBA 4.1. Granted I shouldn't have installed this on the LTS... (I did while using boot-repair the other day)

---

