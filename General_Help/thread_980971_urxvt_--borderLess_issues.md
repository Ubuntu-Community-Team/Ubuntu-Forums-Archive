---
title: "urxvt --borderLess issues"
date: 2008-11-13
forum: General Help
---

### Post by dc-Ankan on 2008-11-13
When i start urxvt(or rxvt) with --borderLess or disable the border in .Xdefaults i cant resize, move or write anything in it.

It works as usual without the borderless option. I had no problems with 8.04.

Help plz

---

### Post by dxero on 2008-11-14
Hey
I have the same problem with urxvt.
Any solutions?

Thanks!

Edit: same with Kubuntu 8.10

---

### Post by invalid on 2008-11-30
Hello!

I am bumping this thread, as this is definitely a bug, and it affects me (using Gnome). 

Please note the details in the following bug reports:
[http://bugs.gentoo.org/show_bug.cgi?id=237271](http://bugs.gentoo.org/show_bug.cgi?id=237271)
[https://bugs.kde.org/show_bug.cgi?id=172028](https://bugs.kde.org/show_bug.cgi?id=172028)

A fix or workaround for the Ubuntu packages would be great!

Thanks,
Beau

---

### Post by hictio on 2008-12-01
Any of you running Gnome, or Metacity?
Yoou might try this as a temporary fix, while the bug fix is released...
Have you tried moving/ resizing the window using the keyboard + mouse combo?

- Alt (any where on the window) + right mouse button to move
- Alt (any where on the window) + left & right mouse button (or middle one) to resize

---

### Post by p_quarles on 2008-12-01
> **hictio said:**
> Any of you running Gnome, or Metacity?
Agreed - this is probably a window manager issue. urxvt's man page says that the X resources option in question sends a request to the window manager, which may or may not be honored. I would look into how your window manager handles window decorations.

---

### Post by bsb on 2009-06-08
I think -bl is falling back to  -override-redirect judging by the output of xwininfo "Override Redirect State: yes".

I'm using gnome and compiz with Jaunty (enlightenment prior to this upgrade so I don't know if this issue existed previously).
This effects both urxvt 9.06 (default installed) and the old urxvt 7.9 I had sitting around.
(There's also issues with urxvt's popups and the Xorg in Jaunty)

For now I've removed the borderless and added "Windows Rules" in Compiz to make it sticky, below and non-movable.  Then in  Windows Decorations", I followed step 2 of [these instructions]("http://ubuntuforums.org/showthread.php?t=694936") to switch of decorations and shadows.  The value in my case was "(any) & !(title=bw)".

This has restored the background console another way.

---

