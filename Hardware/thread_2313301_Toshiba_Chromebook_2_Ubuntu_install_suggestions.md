---
title: "Toshiba Chromebook 2 Ubuntu install suggestions"
date: 2016-02-11
forum: Hardware
---

### Post by UDroidie626 on 2016-02-11
Hi there,
So I have a Toshiba CB2 (1080p model) that I want to run a full fat version of Linux on, I would run something like arch but I cannot be bothered with the install, so Ubuntu should be okay, but I have some questions.

1st - When I have tried this before I cant connect to wifi, the wifi icon just looks as if it is trying to constantly connect to the network, any suggestions to a fix?
2nd - How do I keep the media keys the same, so volume, brightness, full screen back/forward etc, how do I set them up.
3rd - While I hear TLP is great, should I also upgrade its kernel to the latest branch? and should I also get proprietary drivers? is there a guide to installing Intel proprietary drivers?
4th - Ubuntu or a derivative? so like Lubuntu, or Kubuntu? I have 4GB of RAM so surely that should be enough for Ubuntu right?

Thanks

---

### Post by TheFu on 2016-02-13
Toshiba make 6 different models under the "CB2" name. You'll need to be exact or risk getting bad information.  For example, I have a CB35-C3350. Another model is the CB35-C3300 - there are "B" and "A" models too, each with different insides.

The "media keys" are just Function keys. Mapping those is easy. There are lots of guides for that specific to chromebooks out there.  Look at the "Captain's" guide if you are using a recent "2015" "C" model.

I don't touch drivers that work if there isn't an issue. I don't run distros that aren't LTS and that means staying with a specific kernel line.  [https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) - review that carefully. Not all released kernels are created equal. I'll be on 3.13.xx until June-ish when I'll likely move to the 16.04 LTS release.

RAM isn't an issue with the newer Chromebooks. The heavy GUI is an issue and highly dependent on the CPU.  That comes back to the A, B, or C model.  Both of the C models are fairly powerful. The "B" models .. er ... suck, IMHO.  Those CPUs are an embarrassment from Intel and never should have been released.  OTOH, the Celeron 2995U is an amazing CPU from 2+ yrs ago. I don't think Toshiba used this in any of the CBs, however.  Anyway, I had a 2G Acer with a 2995U CPU and it was amazing - great performance with openbox as the WM. I don't use DEs.

Any chromebook that you intend to run Linux on, still requires "bother", IME.  Let me look for the Captains guide ... [http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/](http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/)  and my CB35 insides are different from the photos he shows.  Got mine last month.  I've drafted a blog article about it ($400 ultrabook!), but it isn't ready to be published. I've been recording all the settings and packages to tweak along the way.  I'm not big on function keys not behaving as function keys, however, so my article won't help you. Sorry.  Also, since I don't run any DE, the way that keys are remapped is different - it is part of the window manager settings.xbacklight and xdotool are the tools used.  C-Delete remapping is critical!

I don't use wifi. Sorry.

Good luck!

Oh - I install Ubuntu Server, then add openbox for the GUI. This results in a very light desktop without all the bloat of the other desktop releases, but it only provides a minimal GUI, so it might not be best for everyone.

---

