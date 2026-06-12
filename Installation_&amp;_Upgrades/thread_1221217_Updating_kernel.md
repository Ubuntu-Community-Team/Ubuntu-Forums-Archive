---
title: "Updating kernel"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by estanton on 2009-07-23
So I'm considering trying to update my kernel. I've been having some problems with my Dell laptop, which is running Ubuntu 9.04. Right now I'm running 2.6.24-21-generic (checked uname -r for the kernel version) and compiz won't work. During bootup if I select an earlier version of the kernel say 2.6.24-11-generic in GRUB then compiz will run but flash on full screen is all choppy.
It wouold be nice if I could have both, I checked Wikipedia and it says the current kernel for 9.04 is 2.6.28, so am I out of date on my kernel and should I upgrade it? If so how can I do that? Thanks!

---

### Post by quixote on 2009-07-24
Do you have automatic updates turned off?  If they're on, no way you should be so far behind.  Or have you perhaps been telling the updater to "keep local version of grub"?  (Or whatever the exact words are.)  Then it has the default to put the new kernel on your system, but grub doesn't even offer it as a choice.  That's useful in some situations, but kind of a dumb way to do things for regular users.

If you've been telling it to keep local version of grub, then look in /boot. Find the "initrd.img" and "vmlinuz-" with the highest numbers, and edit /boot/grub/menu.lst to add an entry with your recent kernel. First make a backup copy. You can use gedit or nano as editors.  ```
sudo cp /boot/grub/menu.lst /boot/grub/menu-lst.backup
gksudo gedit /boot/grub/menu.lst
or
sudo nano /boot/grub/menu.lst 
```  It goes toward the end, after ## END DEBIAN AUTOMAGIC KERNELS LIST, and then put it first if you want it to be the default.  (Assuming you have default=0 at the beginning of that file.)

If automatic updating is turned off, then I'd do ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```as many times as needed to get it up to date.

You can install just the new kernel, but unless that's really what you want to do, why risk broken dependencies and do it the hard way?

---

### Post by quixote on 2009-07-24
Oh, and one other thing.  If you're running 64-bit jaunty on a specific subset of laptop, there's a [rather fierce bug]("http://ubuntuforums.org/showpost.php?p=7382178&postcount=29") associated with the 2.6.28-11 kernel.  In that case you're much better off with the 2.6.29-04 kernel, which does need to be installed separately.

---

