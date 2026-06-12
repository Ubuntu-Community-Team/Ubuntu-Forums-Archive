---
title: "Dell SPS M1710 hangs after login"
date: 2008-04-24
forum: Hardware
---

### Post by camino262 on 2008-04-24
I installed Ubuntu 8.04RC on a 4GB usb drive on a Dell XPS 1710 nvidia gpu.  All went well until I updated.  When I updated, when I loged in with my user name and password and I get a nice looking high resolution solid brown desktop.  My mouse works, but I get no icons or menus.  I tried the final release today hoping the issue would be resolved, however the same thing happens.  I can ctrl alt f1, and killall and then startx to login, but that is a pain.  

Anyone know what is going on and how to fix this?

---

### Post by riven0 on 2008-04-24
Perhaps something got messed up with your users settings. Have you tried deleting the Gnome preferences folders? Switch to a terminal, log in and try this:

**rm -r .gconf .gconfd .gnome .gnome2 .nautilus**

---

### Post by thejinx0r on 2008-04-24
I have a Dell D420 and I have the same problem.

At first I thought it was going from RC->LTS that was the problem. So I downloaded the new iso and still got the same problem...

---

### Post by camino262 on 2008-04-24
> **riven0 said:**
> Perhaps something got messed up with your users settings. Have you tried deleting the Gnome preferences folders? Switch to a terminal, log in and try this:

**rm -r .gconf .gconfd .gnome .gnome2 .nautilus**
I tried what you said, however I get the following message:
rm: cannot remove `.gnome': No such file or directory

---

### Post by riven0 on 2008-04-24
> **camino262 said:**
> I tried what you said, however I get the following message:
rm: cannot remove `.gnome': No such file or directory

Try taking that out and give it another go: 

**rm -r .gconf .gconfd .gnome2 .nautilus**

---

### Post by thejinx0r on 2008-04-24
It doesn't do anything, it still does not work.

I think it maybe related to this in GDM/when starting X:
(X starts if I do it manually, but not through GDM, so maybe something is stopping GDM from loading gnome properly)
> 
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc


---

### Post by riven0 on 2008-04-24
> **thejinx0r said:**
> It doesn't do anything, it still does not work.

I think it maybe related to this in GDM/when starting X:
(X starts if I do it manually, but not through GDM, so maybe something is stopping GDM from loading gnome properly)

It's possible. This is a long shot, but when I was having problems with GDM, I installed XDM, choose it as my default manager and rebooted. I logged in fine after that. But it seems like your problem is related Gnome, rather than the login manager.

---

### Post by camino262 on 2008-04-24
> **riven0 said:**
> It's possible. This is a long shot, but when I was having problems with GDM, I installed XDM, choose it as my default manager and rebooted. I logged in fine after that. But it seems like your problem is related Gnome, rather than the login manager.
I installed XDM as my default manager and was able to log in sucessfully.  It is not that pretty, but it will have to do for now.  Thanks for the help!

---

### Post by riven0 on 2008-04-25
> **camino262 said:**
> I installed XDM as my default manager and was able to log in sucessfully.  It is not that pretty, but it will have to do for now.  Thanks for the help!

Glad you got it worked out for now. I'm sure there is a solution somewhere on these boards, but since I rarely log out of my user account, I never thought to check.

---

### Post by thejinx0r on 2008-04-25
*Sigh*
That didn't work for me, installing XDM.
I just get sent back to the login manager... :S
I guess I'll just keep digging.

edit:
nvm, i reconfigured xorg with "dpkg-reconfigure xorg-server' and it works now with xdm.
Still a no go for GDM.

But, w/e.
It's weird that that the live cd works a million times better than the installed version.

---

### Post by camino262 on 2008-04-25
> **thejinx0r said:**
> *Sigh*
That didn't work for me, installing XDM.
I just get sent back to the login manager... :S
I guess I'll just keep digging.

edit:
nvm, i reconfigured xorg with "dpkg-reconfigure xorg-server' and it works now with xdm.
Still a no go for GDM.

But, w/e.
It's weird that that the live cd works a million times better than the installed version.
I agree.  The live cd works great for me.  This has to be a Dell specific issue.

---

### Post by doobydave on 2008-04-26
I have a hunch it's usb-install related.

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

---

### Post by riven0 on 2008-04-26
Interesting. I wonder if this problem would crop up if Gnome was uninstalled and KDE or Xfce was used instead. In either case, I'm hoping to upgrade to Hardy in a few weeks; I'll have to see if the problem replicates itself. Going by the bug thread, installing gnome-devel and recompiling the keyring manager seems to be the best option until this bug is fixed. I'll have to keep that in mind.

---

