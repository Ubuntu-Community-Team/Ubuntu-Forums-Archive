---
title: "ver 8.10 installs but won't boot"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by gdskgs on 2009-03-15
Install went without hangup. But system stops at a beige screen with a mouse pointer during boot. If I try to boot from Live CD system stops at a black screen with mouse pointer. 

Should I try previous version?

Any help is appreciated.

---

### Post by wileybot on 2009-03-15
I have the same problem. Installing on a Dell Dimension 4500s. In my case you can sign on and then it hangs just as you described. Mouse works but keyboard is no good (ps/2).  Cant get to the command line control-alt-f2... I am a newbie so I am scouring the sites....

---

### Post by upchucky on 2009-03-15
are the above machines running a nvidia card, if yes, i recommend installing 8.04 instead. 8.10 is not a long term service release, and has known conflicts with nvidia. this is to say that it will work but it is not an easy task. there are known workarounds for nvidia but in the interest of a new user, the tried and true route is probably better. you can play with 8.10 and nvidia later if desired.

as may pc's are different even a long term service release commonly needs settings adjusted to work, so it may very well turn out that you need to set display settings at the command line even to get a display working.

check out resolution problems and cures in the forums.

---

### Post by wileybot on 2009-03-15
In my case the the mobo has onboard graphics and its an intel. None the less I think you are right on backing off and trying a previous release.  Its weird since all works well until I log in and then it locks on the beige screen.  Thanks again.

---

### Post by gdskgs on 2009-03-15
I have onboard intel video as well.

I just tried booting to the live cd again, this time selecting F4, then safe graphic mode, then enter to continue with boot from cd.

It boots now. So, it must be a graphics issue. Any chance there is a way to use 8.10?

---

### Post by avtolle on 2009-03-15
Not sure what intel graphics set you have, but when reviewing the release notes for 8.10, it is recommended that you boot in safe graphics mode; when reaching the desktop, disable visual effects; then install by selecting that from the desktop.

Alternatively, one might install in safe graphics mode (F4 at initial screen; select safe graphics; then install).

The issue is that the driver for certain intel graphics does not support visual effects (compiz), which results in the problem you are having.

---

### Post by wpshooter on 2009-03-15
Have you'all tried installing from the ALTERNATE (text based) CD version of 8.10 ?

---

### Post by avtolle on 2009-03-15
> **wpshooter said:**
> Have you'all tried installing from the ALTERNATE (text based) CD version of 8.10 ?
Another potential solution that I overlooked when posting earlier. Thanks, wpshooter, for bringing that to the attention of the posters having trouble.

---

### Post by wpshooter on 2009-03-15
> **avtolle said:**
> Another potential solution that I overlooked when posting earlier. Thanks, wpshooter, for bringing that to the attention of the posters having trouble.

You're welcome avtolle.

The ALTERNATE is a good solution to a world of problems if the live CD will not co-operate.

---

### Post by avtolle on 2009-03-15
> **wpshooter said:**
> You're welcome avtolle.

The ALTERNATE is a good solution to a world of problems if the live CD will not co-operate.
Boy, do I know that! Due to various issues with graphics on my Mac G4 cubes, extant since 6.10 or 7.04 (don't recall right now), I've not used anything but the Alternate Install image burned to CD since then; even on a newer laptop that likely doesn't have these issues, I use the Alternate as a matter of course.

---

### Post by gdskgs on 2009-03-15
Thank you for the info.

If I install again in safe graphics mode will that cause the OS to use safe graphics mode when booting? Or was there some option I missed during the original install? BTW: the first install worked without using safe graphics mode.

If I re-install 8.10 (or 8.04 to replace 8.10) do I need to do any thing special like clearing out or deleting partitions created during the first time.

---

### Post by wileybot on 2009-03-15
That was it! Thanks all. Basically just reinstall ubuntu and select f4 etc etc as the group instructs. The change is permanent. Now the quest to get away from 640x320 display...find a driver that will work with the intel vid onboard chipset.

---

### Post by davec01 on 2009-03-28
I just installed ubuntu on a 4500s and had the same problem. The graphical install worked perfectly, but it would hang at the orange graphical screen on bootup. With the help of some forum postings, I was able to get it working by doing the follow:

Restart and hit ESC at the grub prompt. Use grub to boot to a command line. Log in at the command line with your username and password.

type:
sudo update-rc.d gdm remove

Restart by typing:
sudo reboot
(maybe a reboot isn't really needed)

Log in again.

type:
sudo apt-get update
sudo apt-get upgrade
(might take a while)

I rebooted and logged in again at this point.

type:
sudo update-rc.d gdm defaults
sudo reboot

Hope this helps.

---

### Post by davec01 on 2009-03-28
Sorry, I posted the above in the wrong thread!

---

### Post by davec01 on 2009-03-28
My apologies, again! This IS the thread I intended to post to.

---

### Post by wileybot on 2009-03-29
I gave up on this issue a week or so ago, no matter what I tried it didn't work. Your solution along with me changing xorg to "intel" was the ticket. Thanks a bunch.

---

