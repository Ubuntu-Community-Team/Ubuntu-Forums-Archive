---
title: "Server-only install (No desktop) - possible?"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by sjtravers on 2006-01-28
Hi all,

I have installed Ubuntu (currently upgrading from hoary to breezy) on a PC which is only used as a "server", ie it runs Samba, IMAP, Apache2, PHP, Mysql and a couple of other things, and the server is set to start in Console Multi-user mode (I removed GDM from rc3.d).

It seems a waste to me to have Gnome and all those other GUI-based apps on the system when I NEVER log onto it in GUI mode.

Is it possible to remove all the GUI stuff in a simple way? I saw there's a "ubuntu-desktop" package. If I ran "apt-get remove ubuntu-desktop", would that be enough?

Cheers,
Stu

---

### Post by BenTyreman on 2006-01-28
ubuntu-desktop is a metapackage. When you install it, it ensures that a large number of packages are installed with it. Unfortunately, when you remove it, you only remove the metapackage, not the additional packages it installs.

Perhaps removing it and running something like deborphan might do the trick, but I imagine the easiest way to ensure you have the lightest possible package selection is to reinstall, selecting a server installation at the boot menu.

---

### Post by sjtravers on 2006-01-28
Thanks Ben, I also came across this thread:

[http://ubuntuforums.org/showthread.php?t=96046](http://ubuntuforums.org/showthread.php?t=96046)

But I think I decided it's not worth it. I'm not desperate for disk space yet, and as long as gdm isn't in rc3.d (and I'm booting into runlevel 3) I think it's ok.

Cheers,
Stu

---

### Post by TheForumTroll on 2006-01-29
May i ask why you want to use Ubuntu on a server?
imho a server needs as little software installed as possible. More software = bigger chance for bugs and security issues.

Ubuntu is great, but for a server i would choose something else that isn't made for desktop use :rolleyes:

---

### Post by encompass on 2006-01-29
OOPS!  wrong post...

---

### Post by Ocxic on 2006-01-29
when yo install ubuntu at the boot prompt instead of just pressing enter type```
server
```
that will do a server install without the gui

---

### Post by sjtravers on 2006-01-29
Thanks Oxcic, but unfortunately like your sig says:

There is an easy way, and a hard way to do things.
If you're anything like me, you've tried to do things things the hard way,

and broke something.......


I ended up doing the uninstall of all those packages as per my note above, all looks good.

So maybe I didn't broke something after all, but I certainly did do it the hard way.

Cheers,
Stu

---

### Post by sjtravers on 2006-01-29
Oh, and ForumTroll, you're right, I should have chosen something else. I have no good explanation for my choice of distro, other than I happened to have a copy of Warty on my desk, and once I'd got everything working right, including upgrading to Hoary and then to Breezy, I didn't really feel like a clean install of something else.

---

