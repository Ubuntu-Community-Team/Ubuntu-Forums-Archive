---
title: "Constant speaker clicking in ubuntu"
date: 2012-06-29
forum: Hardware
---

### Post by x-shaney-x on 2012-06-29
As I use the laptop I get a clicking sound coming from the speaker.
It is one short click every 2-3 seconds and just won't go away.

Altering the volume makes no different to the volume of the clicking.
It happens whether I am running applications or with an empty desktop.
Only noticed it happening today and there were a few updates yesterday, amongst them a kernel update.
This only happens when running ubuntu, no clicking in Windows 7 or Chromium OS.

Laptop is an Acer Aspire 5742G
According to lshw: ```
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:b4400000-b4403fff
```

I'm at my wits end with this!

---

### Post by hackbac on 2012-06-29
Same here. Just updated to Version 20.0.1132.47

---

### Post by x-shaney-x on 2012-06-30
Version of what?  Looks like a Chrome version, which isn't the problem.

Tried booting with the previous kernel (3.2.0-25) and not getting the clicking so looks like it was the kernel upgrade.

---

### Post by x-shaney-x on 2012-06-30
Spoke too soon.  The clicking started up again :(

---

### Post by AlanR8 on 2012-06-30
This was happening to me up until yesterday and had been happening for a few days.

I did a clean install last night, and did today's updates. All seems well.


Linux ACER 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by x-shaney-x on 2012-06-30
Well I had been thinking of doing a fresh install to put 64-bit back on (tried 32-bit this time around to see if there was any difference).

---

### Post by x-shaney-x on 2012-07-04
Well I did the fresh install of 64-bit and the problem took all of an hour to rear it's ugly head again.

This is really frustrating and is stopping me using ubuntu at all til I can find an answer.

I suspect it's yet another issue with this crappy Acer lappy.
One thing's for sure, whether I find a fix for this or not, I will NEVER touch anything by Acer again.

---

### Post by Redblade20XX on 2012-07-05
> **x-shaney-x said:**
> Well I did the fresh install of 64-bit and the problem took all of an hour to rear it's ugly head again.

This is really frustrating and is stopping me using ubuntu at all til I can find an answer.

I suspect it's yet another issue with this crappy Acer lappy.
One thing's for sure, whether I find a fix for this or not, I will NEVER touch anything by Acer again.

Does your problem occur when you also have headphones on?

---

### Post by x-shaney-x on 2012-07-05
Yes, it does.

I have tracked the problem down to [THIS]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201") bug

With [THIS]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201/comments/65") particular post supplying a workaround

I have added it to my "post install" document that lists all the steps, fixes and workaround I need to do after a fresh install to get everything up and running properly.

The list is becoming worryingly large...

---

### Post by AlanR8 on 2012-09-24
Some more info.....

This only happens when Google Chrome (NOT Chromium) is open. To refine things a bit more, if I have the Google search page open, no problems. Have gmail open....click....click. Facebook, click click.

Firefox, no issues at all

---

### Post by x-shaney-x on 2012-09-26
> **AlanR8 said:**
> Some more info.....

This only happens when Google Chrome (NOT Chromium) is open. To refine things a bit more, if I have the Google search page open, no problems. Have gmail open....click....click. Facebook, click click.

Firefox, no issues at all

Although I said the previous workaround solved the issue, the clicking has returned on a fresh install and the workaround didn't solve it.

After reading your post I have been messing around and it does indeed happen when Chrome is running (and on my comp, Chrome is always running).
Might have to switch to Chromium.

---

### Post by AlanR8 on 2012-10-09
This is beginning to annoy me a LOT!

I'm now on a fully updated install of Ubuntu 12.10 fully updated and it STILL happens.

Kill Chrome and fire up Firefox and all is well.

Has anyone got any ideas?

---

### Post by x-shaney-x on 2012-10-09
> **AlanR8 said:**
> Some more info.....

This only happens when Google Chrome (NOT Chromium) is open. To refine things a bit more, if I have the Google search page open, no problems. Have gmail open....click....click. Facebook, click click.

Firefox, no issues at all

Have you tried this?:
```
/usr/lib/pm-utils/power.d/intel-audio-powersave

I changed the line

INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}
to
INTEL_AUDIO_POWERSAVE=false
```

I said previously this worked for me but then wasn't working when chrome was running.
As it turns out, I did have a personal powersaving script running.
After disabling that, the above workaround stops all the clicking, even in chrome.

Incidentally, this appears to be something specific to ubuntu since in my fedora install, I haven't modified anything and there is no clicking at all.

---

### Post by AlanR8 on 2012-10-09
X-Shaney-X

You are a star! Thanks for that it seems to have cured my clicking for now.

Many thanks

---

### Post by AlanR8 on 2012-10-09
Woops....spoke to soon.

Clickity click click

---

### Post by AlanR8 on 2012-10-29
So...since my last post I've swapped to Firefox and that solves/hides the problem. Still clickty click if I use chrome.

---

### Post by AlanR8 on 2012-10-31
I think protocol suggests sufficient time has been given to suggest BUMP BUMP!!!!!!! :-)

---

### Post by NJPinator on 2012-10-31
I'm going to assume you did edit the file **/usr/lib/pm-utils/power.d/intel-audio-powersave** file's line **INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}** to **INTEL_AUDIO_POWERSAVE=false**, as was suggested by one user on this thread, and as I did when I was having this issue.

I myself am not still receiving the clicking whilst using Google Chrome, so I'm going to suggest that it is most likely down to your installation of Chrome, or one of the plugins that Chrome is using.

You can reinstall Chrome with the following command at a terminal:
```
sudo apt-get purge google-chrome-stable -y && sudo apt-get install google-chrome-stable -y
```

I would suggest trying this purely because it *might* be causing the issue. Also, if you could provide a screenshot of the page **chrome://plugins** within Chrome, as it could be one of Chrome's plugins that's causing the issue.

---

### Post by AlanR8 on 2012-11-01
Thanks fot that, will give it a try over the weekend.

---

### Post by AlanR8 on 2012-11-11
Version 23.0.1271.64 of Chrome seems to have solved my clicking issues!

I'll test for a few days before marking the thread as closed.

---

