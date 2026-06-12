---
title: "Installing a Wacom tablet is really this convoluted?"
date: 2010-02-08
forum: Hardware
---

### Post by hxcobd on 2010-02-08
I was under the impression that Wacom tablets were at least RELATIVELY well supported in linux nowadays... But after reading that 76-page thread on getting them installed and working, I'm certainly no closer to getting my Wacom tablet to work.

Is it really that complex? Something about having to edit a xorg.conf just to get a tablet to work seems strange to me... 5-6 years ago, maybe, but is it really required nowadays?

Am I overcomplicating the process? I have the wacomtools package installed from the repositories, as well as the pre-built wacom drivers, but my tablet is definitely neither recognized nor working.

I apologize if this is beating a dead horse, I'm just kind of taken aback by how ridiculously difficult this is. I mean, I'm familiar with editing xorg.conf and have done some pretty complex symbolic linking and text editing in my day, but this just seems sad.

---

### Post by Favux on 2010-02-08
Hi hxcobd,

Not really able to help you because you haven't said what release of Ubuntu you are using and what Wacom tablet (& model number) you have.  Editing xorg.conf isn't usually needed in Jaunty or Karmic.

---

### Post by benmoran on 2010-02-08
For those lucky enough to have one of the better supported Wacom tablets (like the Bamboo), it's just plug and play. Hopefully yours is better supported in the future.

---

### Post by hxcobd on 2010-02-09
Hey guys,

I am on 9.10 (Karmic Koala), and have the proper drivers installed, but my system still isn't seeing the tablet.

It is a Bamboo, also. Bamboo Pen, to be exact.

---

### Post by Favux on 2010-02-09
Hi hxcobd,

OK, the Bamboo Pen (CTL460) was new when Karmic came out so the default linuxwacom 0.8.4-1 in Karmic doesn't support it.

Ayuthia and others developed patches to support it and they are in the process of being submitted to the LWP.  Linuxwacom 0.8.5-10 is due out any day and hopefully it will support the Bamboo P & T's.

In the meantime there are at least 3 patch sets that will support your stylus.  See [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") for links.  On the same thread as post #384 post #2 links you to the HOW TO for the first patch set that will also support your Pen.

---

### Post by hxcobd on 2010-02-09
hey favux,

many thanks for the link. Still looks like a painful process, but considerably less painful than the other thread I had been referencing.

will give it a shot later today.

---

### Post by hxcobd on 2010-02-09
I really didn't want this to become a "help me install my tablet" thread, but I feel like I'm THIS close to getting it to work properly.

I've found every walkthrough on this topic incredibly poorly-written and borderline impossible to understand. Ultimately, I'd like to understand the entire process and all the steps and actually make a video walkthrough or something for people who aren't as tech-savvy as the "rest of us."

Here's my most recent series of steps:

1.) I tried the "wacomtools" and "xserver-xorg-input-wacom" packages from the repo, but as stated, these current repo versions don't support the Bamboo Pen, which is what I have.

2.) I then went to Linuxwacom's site and downloaded their newest development package, 0.8.5-9, assuming it would have better support for the Bamboo Pen, if any.

3.) Tried installing from a prebuilt 32-bit install of the Linuxwacom driver, this failed due to non-existent directory paths, I believe. Instead, I built the source from scratch and installed it. This worked.

4.) At this point, wacomcpl would not even work, I believe it was giving me a dependency issue. I resolved this somehow, though lord knows how.

5.) After getting wacomcpl to work, it loads, but does not display any devices. Also, my /dev/input directory does not contain any files or folders containing the word "wacom."

My /proc/devices also doesn't list anything called "wacom." Neither does /proc/bus/input. It's safe to say my tablet is not even being seen.

I have rebooted numerous times. I have my xorg.conf edited with the changes stated from the walkthrough thread.

I'd love any suggestions. I'm fairly sure the driver is installed correctly and there are no major errors glaring at me, so I'm confused as to what the issue is...

---

### Post by Favux on 2010-02-09
Hi hxcobd,

Remove the Wacom stuff from xorg.conf and try either of the two .fdi's in post #384.  More complete instructions for installing a .fdi are on [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by hxcobd on 2010-02-09
Hey Favux,

I completely uninstalled/removed any of the Linuxwacom drivers, as well as any of the Wacom entries in my xorg.conf.

I then reinstalled the repo's Wacom drivers, despite that you said they may be too old to support the Pen.

Then, I tried both of your modified FDIs.

Nothing with either of them. Still not showing any Wacom input device in any of my output files whatsoever, and nothing in wacomcpl either.

Just to be clear, I should only "need" 3 things:
1.) wacom-tools (from the repo)
2.) xserver-xorg-input-wacom (from the repo)
3.) One of your modified .FDI files to replace the one the repo files install

Correct?

Or should I be using Linuxwacom's newest development drivers INSTEAD of the repo's?

---

### Post by Favux on 2010-02-09
Hi hxcobd,

No to all of that except 3), the .fdi's.


You have to patch linuxwacom.  The drivers in the repostory (Synaptic) or at LWP do not support your tablet yet.  With luck 0.8.5-10, due out in a few days, will.

To get it working you have to apply patches.  I've linked you to three different patch sets.  Any will work for the Pen.  The earliest and simplest are on post #2 of the "New Wacom Bamboo not working" thread.  See:  [http://ubuntuforums.org/showpost.php?p=8099002&postcount=2](http://ubuntuforums.org/showpost.php?p=8099002&postcount=2)  This is the same thread post #384 is on.  Be sure to remove the debugging code otherwise your log files will fill up.

---

### Post by dyslexia on 2010-02-09
> **hxcobd said:**
> But after reading that 76-page thread on getting them installed and working, I'm certainly no closer to getting my Wacom tablet to work.

It's all very "sensitive". LOL

---

### Post by ionospheric on 2010-02-10
Hi hxcobd,

I got my Wacom Bamboo Touch to work with the instructions from

_[http://ubuntuforums.org/showthread.php?t=1321238]("http://ubuntuforums.org/showthread.php?t=1321238")_

using option A (prepatched kernel).

You can also use

_[http://ubuntuforums.org/showpost.php?p=6546012]("http://ubuntuforums.org/showpost.php?p=6546012")_

if you want a detailed explanation of each step.

The only issue I had is that I had to logout and login again, and after that, xsetwacom worked as expected.

I did encounter some stumbling blocks, though. When I installed at first, I had kernel 2.6.31-17, and the driver worked. When I agreed to update to kernel 2.6.31-19, it stopped working. I recompiled, but xsetwacom would not work because some obscure lib was missing.

I had to completely reinstall Ubuntu 9.10, but it was worth it. The install apparently downloaded and installed the latest kernel 2.6.31-19 during the installation process, so I had the latest kernel right after installation. How many operating systems can do that?!?
I then followed the instructions from the first wacom bamboo thread, and it worked on a completely new install.

---

### Post by dyslexia on 2010-02-13
I had one period where my iBook G4 was up for 11 months non-stop (except for backups) .

---

