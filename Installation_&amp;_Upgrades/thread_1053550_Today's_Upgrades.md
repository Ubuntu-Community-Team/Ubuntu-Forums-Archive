---
title: "Today's Upgrades"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by jacklawrence84 on 2009-01-28
Each day, I automatically download the updates.  I do not study them or try to understand them.

After doing this today, I found that I cannot operate Pidgin IM or Skype.  Both have worked fine until now.  Both are affected the same way.  When I press "enter", the program shutsdown.

Is anyone else having this program?  If so, what is the cause and the solution, please.

Jack

[email]jack@giraffefactory.com[/email]

---

### Post by tmcarson1 on 2009-01-28
Perhaps you could go to the Synaptic program manager and mark those two for uninstallation, and try installing them again?

I am not on my ubuntu machine at the moment to test it out and see if mine are messed up also.  But it may be worth a try to uninstall/reinstall them and see if that fixes it.

Good luck!

---

### Post by cmermag on 2009-01-28
I'll see if I'm suffering from a similar problem, but when I upgraded to -11 today it seemed to cause a problem with my wintv pvr usb2 driver and it's insertion into the kernel.. I had to revert back to the prior kernel to get it working again.

---

### Post by johann_p on 2009-01-29
Same here. My WinTV-PVR USB2 stopped working after the update.  Skype does not work any more either. This is VERY bad indeed.

Is there a chance to undo that update?

---

### Post by johann_p on 2009-01-30
UPDATE: I have found a solution/fix for both problems (wintv-pvr-usb2 and skype) see here: [https://bugs.launchpad.net/ubuntu/+bug/323146](https://bugs.launchpad.net/ubuntu/+bug/323146)

---

### Post by Trekrider58 on 2009-01-30
> **johann_p said:**
> UPDATE: I have found a solution/fix for both problems (wintv-pvr-usb2 and skype) see here: [https://bugs.launchpad.net/ubuntu/+bug/323146](https://bugs.launchpad.net/ubuntu/+bug/323146)

I have also lost Skype (well part of it) after upgrading. Initially it gave an error 'no sound output' and wouldn't connect. After some fiddling with the sound settings I can connect and hear the other person and they can see and hear me as normal but no video at my end (theirs or my own).

I followed the link you provided but as a relative newbie what does

'The Skype problem could be fixed by moving away ~/.Skype and starting from fresh. After adapting the audio configuration everything works as before. I have no idea whhich of the old settings caused the problem though.' 

mean?

Thanks,

---

### Post by johann_p on 2009-01-30
> **Trekrider58 said:**
> 
'The Skype problem could be fixed by moving away ~/.Skype and starting from fresh. After adapting the audio configuration everything works as before. I have no idea whhich of the old settings caused the problem though.' 

mean?

Thanks,

Skype - like many other programs - creates a hidden directory in your home directory where it keeps all configuration and other data. All files and directories with a name that starts with a dot are not shown in most default directory views.
In this case, skype creates a directory called ".Skype" in your home directory (usually /home/<youruserid>, but the home directory can be abreviated with "~" in most command line situations.
So I moved this directory, essentially renaming it. Skype could not find its configuration files any longer and created a new ".Skype" directory, and in my case my problem was solved. Since I do not know which configuration option or file in the old directory was actually responsible for the problem, this approach is not very satisfying but at least Skype works again.
Also, be aware that there might some important data in that directory, e.g. chat logs or other stuff .. this is why I just renamed it and did not delete it.

---

### Post by Trekrider58 on 2009-01-30
Thanks Johann, Did as you suggest and test call works after fiddling with audio settings again. Webcam test works as well.

Edit: I have just tried talking to someone and still have the original problem - they can see me and hear me, I can hear them but can't see either them or myself.

Any suggestions anyone?

Regards,

---

### Post by j.h.klein on 2009-02-11
Hi,
After upgrading from 8.4 to 8.10 Skype just stopped working. I press the Icon and nothing happens. I tried to reinstall Skype from Medibuntu as I found recommended somewhere and it did not help. I tried to erase every file and directory with "Skype" in its name and I accidently erase the Ubuntu icons directory. After erasing (rm) installing Skype did not change anything. It seems that Johann Petrak's solution will not help me because I did erase all Skype directories: I will recheck that I erased also the directories starting with a dot.
Thanks for any hint.
Joshua

---

