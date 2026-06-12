---
title: "using tar xvzf to install a program"
date: 2008-11-11
forum: General Help
---

### Post by p3tris on 2008-11-11
Hi, I've got a package called package.tar.gz. It's a program i need to install. The writer sais i should run the command:

tar xvzf /path/to/package.tar.gz through a terminal in my root directory.

I did in a another directory to see the outcome. I saw it extracts some files to several places (like ./etc ./usr etc etc)

I guess i will need to sudo this command to run in the root directory?
The questions are:

How safe is this?
How do i remove this app if i don't need it anymore? (it extracts 50-60 files, so deleting them 1-1 is not an option).


Thanks!

---

### Post by taurus on 2008-11-11
Personally, I would save package.tar.bz to my $HOME/temp directory first and unpack it there.  Then, look to see what are those files/directories that it created.  The worst thing you could do is to unpack it blindly as root.

---

### Post by p3tris on 2008-11-11
Hi, thanks for replying!

I did what you said and i saw the files extracted. The problem is i cannot run it from my home (searches for libraries). How can i tell if they are dangerous. Let's say i trust the writer and install it as root (extract it). If i want to remove the app, what do i do?

Thanks

---

### Post by taurus on 2008-11-11
Well, that is the price you have to pay if you download a binary so if you don't feel comfortable about it, don't install it.  What is the name of that program anyway and where did you download it?

But if you trust the source, then install it by unpacking it from / directory with sudo.  And if you want to remove it later, then you need to know every single file that you installed since you have to remove them by hand.  In other words, keep the package.tar.gz handy so you can unpack it in your $HOME later and see the name of those files.

---

### Post by Iowan on 2008-11-11
I presume you've already checked, but if not:
see if the program is available in the repositories - much less painful to install via apt-get, aptitude, or synaptic...

---

### Post by p3tris on 2008-11-12
unfortunately no synaptic, apt-get etc 

Thanks people.

---

