---
title: "Grub / chroot question"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by raydot on 2009-11-08
Hi All,

I'm having trouble getting past the grub loader in Ubuntu 8.1.4 and I came across this post:

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Message #9 seems to be my solution but I don't understand it and maybe you can help.

I do not at all get what the purpose of the chroot step is that the author suggests, or why it is that it's necessary for what follows?

I also wonder if I haven't picked an out-dated way of doing things, and so maybe I should skip this version for 9.10?

Thanks,

Dave.

---

### Post by slakkie on 2009-11-08
What do you mean, I don't see how this post relates to your problem:

> **NewJack said:**
> I recommend  Ubuntu Kung Fu.  Great reference easy to pick up and read. 

A thanks goes out to Keir Thomas for offering this guide.

Anyways, this seems to be want you are looking for: [http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

---

### Post by raydot on 2010-03-18
Ha ha, I don't either.  Must have not copied and pasted the link correctly, or something....sorry about that...

---

### Post by srs5694 on 2010-03-19
Since the link was to the wrong thread, I can't comment on it; however....

The chroot command name is short for "change root" -- it alters the root directory of the system as far as subsequent commands are concerned. For instance, you could set up a little mini-Ubuntu installation in some directory (/mini, say) and then chroot into that directory to use it. Some distributions, such as Gentoo, use this facility when you install them, and some servers use chroot environments as a safety feature to keep the server from accessing inappropriate files. I suspect if it's something to do with GRUB, it's related to getting the GRUB utilities to recognize certain versions of themselves or to understand the correct location of files in /boot, similar to what the Gentoo installation procedure does.

---

### Post by raydot on 2010-03-20
Very good to know.  Thanks!

---

