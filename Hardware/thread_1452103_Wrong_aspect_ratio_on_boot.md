---
title: "Wrong aspect ratio on boot"
date: 2010-04-11
forum: Hardware
---

### Post by x-shaney-x on 2010-04-11
So I posted a thread here about my plymouth resolution (kind of solved) but it got me thinking about the bigger picture (no pun intended).

Although my desktop, GDM, login resolution and aspect ratio are always displayed perfectly (1680x1050 - 16:10) this isn't the case with boot splash screens which means they always look warped.
I have had this with any distro using usplash and now plymouth on lucid.
Running vbeinfo only shows available resolutions at the wrong aspect ratio (1280x1024 and not 1280x800 for example).

Is there any particular reason for this and is there any way around it?
I know it's not a huge problem in the grand scheme of things but it is annoying and in some cases those pretty boot screens can end up looking downright ugly.
In fact the only distro I can think of recently that has displayed the correct aspect ratio on boot is openSUSE which leads me to believe it IS/SHOULD BE possible.

Incidentally, my GFX card is nvidia geforce 7600gs

---

### Post by x-shaney-x on 2010-04-11
Hmm, I tried 3 live cd's (a karmic cd, linux mint and the current lucid beta) and ALL 3 showed the correct resolution and aspect ratio when booting the cd but not during boot once installed.
So that is both usplash and plymouth getting it right.

I believe I have found the cause of the problem, the proprietary nvidia driver.

Using the lucid disc as an example, when I checked dmesg I noticed it was using nouveau fb but the installed lucid is using EFI fb (whatever that is).

So what can I do to get the aspect ratio correct with nvidia drivers?

---

### Post by x-shaney-x on 2010-04-13
So to bring this back up again.
It seems my card doesn't support widescreen console resolutions, according to hwinfo --framebuffer.

Well I decided to disable the proprietary nvidia driver and go back to nouveau.
With nouveau, hwinfo still shows the same non-widescreen resolutions but on boot it is displaying the full 1680x1050 perfectly.

I don't understand.

(In fact everything is working very nicely with nouveau and I would keep it but I would miss my compiz effects too much).

---

