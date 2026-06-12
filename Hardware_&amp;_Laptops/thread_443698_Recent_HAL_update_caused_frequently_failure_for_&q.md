---
title: "Recent HAL update caused frequently failure for &quot;suspend when lid closes&quot;"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by su99 on 2007-05-14
Around May 10th, my 7.04 on 3 laptops (a thinkpad t42, an old thinkpad 600e, and a dell inspiron 710m) all received update notifications and i chose to install the updates on all of them. I took a glance at the updated libraries, all seemed to be "hal" (hardware abstraction layer) related.

After updating, I see some good and bad changes. The bad one bothers me a lot:

1. [good] It looks like the ACPI lid status issue on my dell 710m (see [http://ubuntuforums.org/showthread.php?t=406250](http://ubuntuforums.org/showthread.php?t=406250) ) was fixed. Now my dell 710m can successfully detect the correct lid state, after removing my modifications to the power.sh script.

2. [neutral] This one doesn't really affect any end users. I just realized this when observing my acpi log: there is some significant changes to the UID of abstract hardware names. For example, the laptop lid was called /org/freedesktop/Hal/devices/acpi_LID0, but now /org/freedesktop/Hal/devices/computer_logicaldev_input_2. And the last digit ("2" in this case) could vary every time the computer resumes from sleep. For example, it could be "0", "1", or so. This made it more difficult to write a script that forces to get/set the lid state using hal-get/set-property because you can no longer use a hard-coded UID. You must dynamically check the type of these logic devices. Luckily, since #1 showed that the lid state issue is fixed, I don't need any manual script any more, so this didn't become a real problem for me. At least not for now.

3. [bad] This is the real problem I met over the weekend. After this hal update, all my 3 laptops (models listed at the beginning of the post) intermittently fail to suspend upon lid close. For every 1 out of 3-5 tries, the laptop just keeps running as if nothing happened when I close the lid (I use gnome-power-manager and the lid close action is set to "suspend"). Before this HAL update, all 3 laptops were doing a very good job on suspending upon lid close (not 100% success, but the failure rate is so low that you don't even notice it. And of course, for 710m I used my own power.sh script mod as described in the link of #1). The difference is so obvious that it made me think the recent HAL update is the only possible reason.

Did any laptop user meet the same issue as #3 here? How's your laptop doing on suspend-upon-lid-close after the HAL updates of last week? Any comments on how to diagnose and track down the root cause or find a workaround? (other than rollback the updates)

Thank you!

---

### Post by aysiu on 2007-05-14
The HAL update totally screwed up my working suspend. Everything was working perfectly on my Dell Inspiron 500m until I installed that update... Argh!! Friggin' Ubuntu updates. That X server breakage thing last year didn't affect me, but this HAL update messed up everything... geez...

Rant over.

I'm trying a clean reinstall (I have a separate /home partition on my laptop and not a lot of tweaks in system config files). If that doesn't work, I may just switch back to Windows for this computer. Working suspend is a pretty big deal for me.

---

### Post by su99 on 2007-05-15
> **aysiu said:**
> The HAL update totally screwed up my working suspend...

thanks for sharing this info with me.

i feel a little better now because someone else had problem with the recent updates too. that usually means it's not my individual problem, and thus it will eventually receive sufficient attention and finally get fixed...

actually, the current situation for me isn't that bad. at least all my 3 laptops are still working well, except that i have to watch them for up to half a minute every time i close the lid, and if it fails, open the lid and close it again. it's inconvenient for sure, but still bearable. for now, the 2nd attempt always worked, and i haven't seen 2 failures in a row.

anyways, look forward to the fix.

---

### Post by su99 on 2007-05-15
someone already reported this issue on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595)

---

### Post by aysiu on 2007-05-15
> **su99 said:**
> someone already reported this issue on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595)
Thanks for finding that bug report. I've tacked on a short comment.

---

### Post by whayong on 2007-05-15
I purposely skipped on the hal update when it first popped up.  I didn't see any posts about it screwing up anything so I decided, just a few minutes ago to go ahead and do it.  I close the lid on my laptop and still could here the HD.  I thought it was a fluke.  Then I stumbled on this post and was able to reproduce what the OP said.  It sucks, hopefully there will be a fix because suspend didn't work for me in Edgy and works wonders on Feisty, until hal that is.

---

### Post by aysiu on 2007-05-15
> **whayong said:**
> hopefully there will be a fix because suspend didn't work for me in Edgy and works wonders on Feisty, until hal that is. Same here.

---

### Post by aysiu on 2007-05-15
I'm thinking about manually downgrading the packages using the older ones here:
[http://archive.ubuntu.com/ubuntu/pool/main/h/hal/](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/)

Would that make a difference?

---

### Post by whayong on 2007-05-15
I don't know man.  I wouldn't know where to begin so I'm affraid I won't be of any help to any of us with this problem.

---

### Post by su99 on 2007-05-15
I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":
```

Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)
```

3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

I just did it to one of my laptops. So far it seems to suspend ok when lid closes, but I'm not 100% sure before sufficient tests and observations.

---

### Post by aysiu on 2007-05-16
Thanks for that. I'll give it a shot.

---

### Post by aysiu on 2007-05-16
Turns out a fresh install gave me those package versions already.

I guess I'd had the proposed/experimental repositories marked and that's why it upgraded. So I've now unchecked those repositories, and used the old versions of those packages, and everything's working fine again.

---

### Post by whayong on 2007-05-16
So you ended up doing a fresh install of Feisty?  I'll go ahead and give this a try when I get home.  I would like to stay away from fresh installs as much as I can this time around.  Been there, done that, with Edgy, loL!

---

### Post by aysiu on 2007-05-16
A fresh reinstall isn't necessary--it's just what I ended up doing before I realized I could downgrade the relevant packages.

---

### Post by meldroc on 2007-05-17
I'm getting the same thing (Asus A8Js) - recently, my system fails to suspend-to-RAM when I close the lid.  It makes me feel better that others are experiencing this issue - I was starting to wonder if the lid switch on my laptop was failing.

---

### Post by mr bob on 2007-05-17
HAL has caused me a number of problems. I have forced to an older version as instructed and fixed the problems.

The only minor problem is the Update Manager permanently thinks it needs updating and the little orange starry icon is sitting there in the top panel. 

Is there any way I can tell the Update Manager I do not want to update HAL?

---

### Post by aysiu on 2007-05-17
> **mr bob said:**
> HAL has caused me a number of problems. I have forced to an older version as instructed and fixed the problems.

The only minor problem is the Update Manager permanently thinks it needs updating and the little orange starry icon is sitting there in the top panel. 

Is there any way I can tell the Update Manager I do not want to update HAL?
Turn off the "proposed updates" in Synaptic Package Manager preferences.

---

### Post by su99 on 2007-05-17
> **mr bob said:**
> HAL has caused me a number of problems. I have forced to an older version as instructed and fixed the problems.

The only minor problem is the Update Manager permanently thinks it needs updating and the little orange starry icon is sitting there in the top panel. 

Is there any way I can tell the Update Manager I do not want to update HAL?

A few ways:

1. Goto menu system / admin / software sources / updates, turn off proposed and unsupported/backports". This time the broken hal is in backports.

2. Or turn off "check for updates" at all.

3. Or use Synaptic's "lock version" to lock those hal libs to be the current version. i believe this can also prevent the notification of the hal.

Please be aware that some methods above might also prevent you from seeing good fixes.

---

### Post by aysiu on 2007-05-17
I'd strongly advocate for #1.

---

### Post by meldroc on 2007-05-17
I just reverted my hal packages (as mentioned above) to straight feisty versions instead of feisty-backports versions.  I guess we'll see how things go...

---

### Post by whayong on 2007-05-17
Did anyone have to restart/log off after reverting to the old version?  Reason I ask is when I finished reverting to the old version, I immediately tried to suspend by closing the laptop lid and suspend didn't work.  I restarted and everything was dandy.  I will try to do more testing later to see if it really is fixed because I only did suspend 2x last night.

---

### Post by aysiu on 2007-05-17
> **whayong said:**
> Did anyone have to restart/log off after reverting to the old version?  Reason I ask is when I finished reverting to the old version, I immediately tried to suspend by closing the laptop lid and suspend didn't work.  I restarted and everything was dandy.  I will try to do more testing later to see if it really is fixed because I only did suspend 2x last night.
I don't know. I did an entire reinstall, so my experience isn't going to help here.

I would imagine a restart of some kind would be necessary.

---

### Post by mr bob on 2007-05-17
> **su99 said:**
> A few ways:

1. Goto menu system / admin / software sources / updates, turn off proposed and unsupported/backports". This time the broken hal is in backports.

2. Or turn off "check for updates" at all.

3. Or use Synaptic's "lock version" to lock those hal libs to be the current version. i believe this can also prevent the notification of the hal.

Please be aware that some methods above might also prevent you from seeing good fixes.

I tried 1. I turned off unsupported/backports and that worked (proposed was already unchecked).

Thanks to all who gave advice.

---

### Post by whayong on 2007-05-18
> **aysiu said:**
> I don't know. I did an entire reinstall, so my experience isn't going to help here.

I would imagine a restart of some kind would be necessary.

Well, I tried to suspend a couple more times in a row on a single boot and everything seems to be back to "normal."  Anyone with these suspend issues after the HAL update should definitely go back to the old version if you value your suspend capabilities.

---

### Post by meldroc on 2007-05-18
Yep, the revert seems to work for me - my system's suspending with no problems when I close the lid, and resuming with no problems.

---

### Post by cbrese on 2007-05-22
I just reverted using apt-get and now my problems are solved.  This is the command I used:

```

sudo apt-get install hal=0.5.8.1-4ubuntu12 libhal-storage1=0.5.8.1-4ubuntu12 libhal1=0.5.8.1-4ubuntu12

```

---

### Post by jamieplucinski on 2007-05-25
That HAL update is EVIL. After installing it on a 200m based laptop (which is probably the evil chipset to blame here) nothing works, none of my network cards are detected and I have to manually mount my USB sticks when inserting... re-installing the packages didn't work for me, so I had to clean install... I couldn't get online to find out otherwise.

Skipping those ftw...

---

### Post by xadder on 2007-05-25
I'm having the same suspend problems, in that closing the laptod lid sometimes workss, sometimes doesn't. I can always suspend by going through the "exit" menu though.

Still, the hal update seemed to fix another problem, the one where discs couldn't be unmounted using their icons. Using umount /media/disk or similar  worked, but I was really happy when the icon-method came back.
I assume that reverting to the older hal will bring back that problem?

---

### Post by jamieplucinski on 2007-05-25
Depends on what problems are you getting with the new HAL updates, if nothing is broken, keep it. The only reason I'm ignoring the update is that it breaks everything it is supposed to enable.

If you want to give it a try, go for it, just save this page so you can remove the packages using the command listed above if/when it goes nasty.

---

### Post by jamieplucinski on 2007-05-26
Was just prompted for new updates and installed all of the ones from this morning, and, the HAL ones. I don't know if the remote packages were changed or not, or I was missing a dependency but they're in and working fine now.

I'm guessing an unclean install last time around, either way, no nasty unable to initialize HAL errors on startup now :D

---

### Post by Abdi110 on 2007-06-28
Thanks for the help!

---

### Post by whayong on 2007-06-28
So I guess this hasn't been fixed yet.

---

### Post by phuonglh on 2007-07-03
I have the same problem, that is my laptop Thinkpad T42 does not suspsend when I close the lid, although lastweek it worked perfectly.

I follow this thread and found that I haven't upgraded hal package yet. Instead I upgraded the package linux-restricted-modules from version 26.20.5-16.28 to version 26.20.5-16.29.

I try to rollback to the previous version and hope it works.

---

### Post by Abdi110 on 2007-07-07
So it seems like this has sort of fixed the problem, that or it just takes a long time for it to initiate sleep. It works flawlessly about 1 out of 5 times now.

---

### Post by louieb on 2007-07-07
Don't know if this is related. But found the UUID of my swap partition had changed and swap wasn't being used. To get hibernate to work again had to put correct UUID in 2 places.
/etc/fstab
/etc/initramfs-tools/conf.d

Then  had to run ```
sudo dpkg-reconfigure  initramfs-tools
``` Tired to find the thread where I got this info but could not locate it.

---

