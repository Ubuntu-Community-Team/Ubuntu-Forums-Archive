---
title: "Updated + Fixed wireless, now I can't boot latest kernel?"
date: 2008-10-22
forum: General Help
---

### Post by TrikeKid on 2008-10-22
I did my usual updates this afternoon, and didn't restart until I got home from work tonight, when I realized that the updated had killed my wireless... again. Plugged into the wall and reinstalled madwifi, and now I can't boot using the 2.6.24-21 kernel, I have to get into GRUB and boot from the -19 kernel to boot fully and use my computer. What should I do to fix this?

Mods-If this you feel this is beneath this forum, feel free to move it to beginner talk.

---

### Post by Vadi on 2008-10-22
It seems that there have been issues for some people with the kernel upgrade: [http://ubuntuforums.org/showthread.php?t=948584](http://ubuntuforums.org/showthread.php?t=948584)

I didn't find a clear solution to this, as various resources recommended compiling madwifi on your own or doing other stuff. Easiest thing to do would be just to make the -19 kernel the default really - you can do so by installing the start up manager ([click]("apt:apt:startupmanager")), and going to system - administration - start up manager and setting 19 default.

---

### Post by Vadi on 2008-10-22
I believe this is the bug report you can follow to know about the status on this issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251252)

---

### Post by dinofelis on 2008-10-22
> **TrikeKid said:**
> I did my usual updates this afternoon, and didn't restart until I got home from work tonight, when I realized that the updated had killed my wireless... again. Plugged into the wall and reinstalled madwifi, and now I can't boot using the 2.6.24-21 kernel, I have to get into GRUB and boot from the -19 kernel to boot fully and use my computer. What should I do to fix this?

Mods-If this you feel this is beneath this forum, feel free to move it to beginner talk.

I came here for exactly the same problem.  I'm also used to have to run a sudo make install of my madwifi thing, and now I get kernel panic with the 2.6.24-21, even in recovery mode.  I also have to boot again from the -19 kernel...

---

### Post by TrikeKid on 2008-10-22
> **dinofelis said:**
> I came here for exactly the same problem.  I'm also used to have to run a sudo make install of my madwifi thing, and now I get kernel panic with the 2.6.24-21, even in recovery mode.  I also have to boot again from the -19 kernel...

Run synaptic and get start up manager, then set -19 for your default OS. Doesn't fix -21, but it works until someone does.

---

