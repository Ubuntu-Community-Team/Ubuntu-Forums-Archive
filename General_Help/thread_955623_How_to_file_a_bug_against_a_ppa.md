---
title: "How to file a bug against a ppa?"
date: 2008-10-22
forum: General Help
---

### Post by javierrivera on 2008-10-22
Hi,

I have installed openoffice 3 in Intrepid using the following ppa:

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Everything went well, but when I try to install the pdf import extension, it didn't work.

After a little checking I found that it was unable to link libstlport_gcc.so, this was not very surprising as I only had libstlport_gcc.so.4.6 on /usr/lib/. Just adding a symlink solved the problem, and the extension is working nice.

But when I try to check if some bug has been filed or if I should open a new one, I'm lost. I can't file a bug in that launchpad, nor can I find another place to place openoffice bugs that are ubuntu-only.

Where should I file it?. Is it already filed?. Is there a place to file bugs against OOo extensions?. Upstream ? . I'll love that this small problem will be fixed some day.

Javier.

---

### Post by Steveway on 2008-10-22
Uhmmmm... I just clicked on Bugs at the top of the page and got to this page here:
[https://bugs.launchpad.net/~openoffice-pkgs](https://bugs.launchpad.net/~openoffice-pkgs)

---

### Post by hugmenot on 2008-10-22
Go to the source from where you got the information about the PPA. In your case post[ in this thread]("http://ubuntuforums.org/showthread.php?t=889093"), I&#8217;d say.

---

### Post by javierrivera on 2008-10-22
@Steveway:

I can't find a buttom to place a bug there.

@hugmenot.

Thanks, seems like the right place.

---

