---
title: "Hoary Sound was working, now it's not!"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by ebib on 2005-05-24
I'm hoping someone can help.  Sound was working just fine until I installed the Kernel update that was displayed in the Ubuntu update manager.  Now, I've got no sound at all!  No system sounds, no music, etc.  ](*,) 

Everything else (Network, DVD, CD drives, printer) seems to function perfectly as before.  Any ideas/suggestions on what is wrong and how to fix it?

FYI, I DID NOT install any special drivers to get my sound working during the original install.

Thanks,
Evan

---

### Post by ebib on 2005-05-24
Just an update to my original post:

-- I tested the computer speakers using an iPod.  Great sound.
-- I booted the comptuer itself with the same speakers using the Ubuntu Live CD and lo and behold, the sound worked again.

++This leads me to believe that there is some compatibility issue, if not between the kernel update and my soundcard, then between something that was done to the system configuration during the kernel update and my soundcard.

1) IS THERE ANY WAY TO AVOID A COMPLETE REINSTALL?
2) IF I REINSTALL BY DOWNLOADING A NEW ISO IMAGE FROM THE UBUNTU SITE, WILL THIS INCLUDE THE NEW KERNEL?  (JUST LOOKING FOR A WAY TO AVOID RUNNING INTO THIS PROBLEM AGAIN RIGHT AWAY).
 
A thousand excuses if this all sounds very vague, but I am a relative newbie to Linux and Ubuntu.

--Evan

---

### Post by lakcaj on 2005-05-24
Just a shot in the dark, but try running alsamixer and see if there is a "headphone jack sense".  If there is, try muting it.  I had a similar problem when I lost sound, and this ended up being the cause.

---

### Post by ebib on 2005-05-24
Thanks for the suggestion: I will give it a shot as soon as I get home this evening!

---

### Post by daageep on 2005-05-24
Caveat: I am a total newb, so what I am about to say worked for me and might not be a real solution.  :grin: 

I installed Ubuntu Hoary Hedgehog yesterday and immediately downloaded XMMS (clone of winamp) and VLC (awesome video player; plays everything and anything you throw at it). VLC would play my video files but no sound. XMMS would crash on me and not play anything. After a long search and looking under Systems -> Preferences -> Multimedia systems selector, I downloaded something called "VLC-ESD", and VLC *and* XMMS started working! 

I don't know if that will do anything but good luck.

---

### Post by ebib on 2005-05-24
Ubuntu has been healed!  And the Doctor with the magic potion was...

LAKCAJ

Thanks!  After fiddling a bit with the headphone setting you mentioned in your post and then rebooting for the umpteenth time in 24 hours, my sound is once more loud and crystal clear!

---

### Post by adbak on 2005-05-24
I tried running alsamixer and got this: ```
alsamixer: function snd_ctl_open failed for default: No such device

```
I also tried aumix but got this: ```
aumix:  error opening mixer
```
Can anyone help me?

---

### Post by wormeyman on 2005-05-25
i'm getting the same problem as the user above me i just don't have aumix?

---

### Post by wormeyman on 2005-05-26
bump

---

### Post by wormeyman on 2005-05-28
I googled the error we are having and nothing turned up :(

---

### Post by adbak on 2005-05-29
I noticed that there's no volume applet anymore.  You can Add to Panel, but nothing shows up.

---

