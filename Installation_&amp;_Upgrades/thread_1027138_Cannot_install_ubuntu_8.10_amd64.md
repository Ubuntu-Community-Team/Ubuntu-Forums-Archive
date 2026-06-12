---
title: "Cannot install ubuntu 8.10 amd64"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by pancham on 2008-12-31
I have ubuntu 8.1 i386 installed and is working... but since my comp is amd 64 dual proccesor I downloaded ubuntu 8.10 amd64.iso from net and created a cd, but it is not booting,,, comp says boot error and if I open it inside ubuntu it says-- Cannot extract , maybe not a debian disc--- what sould I do now...

---

### Post by djbushido on 2008-12-31
So you can boot into the live cd? Or not?

Make sure your computer is set to boot from cd as well.

And finally: did you burn the disc as an image? or just as a data CD/DVD?

EDIT: are you trying to install an x86_64 on top of the i386? If so, there's your problem. Since the system architectures are different, ubuntu probably won't let you install it, as this could very well break the system. if you really want to use an x86_64 install, you need to copy out your personal files, reinstall as x86_64, then copy your files back in.

I repeat: do not continue trying to install 64 bit on top of 32, as this could wreck your system. copy out needed files, then re-install, rather than install on top of.

---

### Post by Coder543 on 2008-12-31
Are you currently running 8.04? If so, do a distro update (no need for cd)
Are you certain that you are 64 bit? If not, try 32 bit
Are you sure you computer is capable of booting from cd? (it should be able to though)
Have you tried the alternate installer?

---

### Post by pancham on 2009-01-01
I burned the image on cd --- Ubuntu 8.10 amd64.iso---  Even when I started fresh installation from cd it is coming as error

---

### Post by djbushido on 2009-01-01
So to confirm, you are doing a complete re-install right?
There should be an option to check the cd for errors, try that. If it comes back that something was messed up, you need to do a re-burn.  if so, do it at a speed like 8-4x.

but, check the cd for errors.

---

