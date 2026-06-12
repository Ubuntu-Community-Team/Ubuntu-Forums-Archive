---
title: "No 3D with Intel HD P3000 (Xeon Variant of i7)"
date: 2012-01-09
forum: Hardware
---

### Post by archimedesmp on 2012-01-09
Hi Forums,

I just upgraded my system to a Xeon E3-1235.
Ubuntu boots as nice as ever, but I don't get 3D acceleration (and thus no gnome3).

System is uptodate and rebooted to current kernel:

> archi@thor:~$ uname -a
Linux thor 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

archi@thor:~$ glxinfo 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


Packages libdrm-intel1 and xserver-org-video-intel are installed and there is no xorg.conf

Complete Xorg.0.log is at [http://pastebin.com/T5x1nGwU](http://pastebin.com/T5x1nGwU)

It throws one error:
> [    38.529] (EE) GLX error: Can not get required symbols.

I still have fglrx drivers installed, but the ATI card (HD3870X2) is not plugged in all the time, as I don't want to waste power.

I also updated to xorg-edgers. I still have X (*phew*), but still the same symptoms like before :(

Any ideas?

//edit: Maybe updating to kernel 3.x with better support for sandy bridge would help?

---

### Post by archimedesmp on 2012-01-10
Ok, I did not require a Kernel Update :)

Linux was still running on fglrx libgl, so I had to change that.

Usually choosing mesa instead of fglrx in update-alternatives should be enough:
> 
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf
$ sudo ldconfig


And than restart X (service lightdm restart).



I did a bit more, but that shouldn't have changed anything...

I purged the old links (optional) and reinstalled the mesa stuff.
Reinstalling mesa things installed other libs as well, maybe I was missing those (can't recall which).
> 
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
$ sudo ldconfig


Good luck :)

---

### Post by sjuranic on 2012-05-16
Wow!  I'm starting to feel kind of dumb now.  I can't tell you how long I fought with this issue.

Thanks for the post!

---

