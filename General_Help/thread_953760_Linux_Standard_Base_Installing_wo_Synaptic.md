---
title: "Linux Standard Base: Installing w/o Synaptic"
date: 2008-10-20
forum: General Help
---

### Post by alnilamski on 2008-10-20
Hey all,

I need to install something that wants Linux Standard Base libraries to be on the (Hardy Heron) computer. The thing is, this particular machine, my boss doesn't want hooked up to the internet. This complicates things a little - it's no longer so easy as just using Synaptic to get it.

So I looked around a bunch, and the best I could find is a tarball of LSB 3.2 that says it's for DEBIAN, not Ubuntu. See: [http://packages.debian.org/lenny/lsb](http://packages.debian.org/lenny/lsb)
**Q1. Ubuntu is based on Debian, right? So this should work? Or do I have to look somewhere else?**

This comes as a tarball (.tar.gz). I have limited experience installing tarballs - I know how to extract it, but other than that I thought you just typed things like:
```

./configure
make
make install
install
```
but this one doesn't seem to let me do any of that. It says there is nothing to make, or that there are no instructions to make anything, and there is no configure either. There is a readme, but it's about LSB itself - it doesn't give any installation instructions.
**Q2: Assuming I even have the right package at all, how do I install it?**

I'd appreciate any help on the matter.
Thanks!
-Alni

---

### Post by jocko on 2008-10-20
Why not just download the ubuntu .deb file instead of complicating things?
Search for it [here]("http://packages.ubuntu.com/"), download it (and any dependencies that you may need) and then install it by:
```
sudo dpkg -i [COLOR=Red]/path/to/filename.deb[/COLOR]
```

Note that you may need to download a lot of different packages in order to get them to install, as there are lots of dependencies to some packages.

---

### Post by alnilamski on 2008-10-20
Wow, that's much much better.
Hah, thanks! I'll post again if that doesn't work.

For anyone who finds this thread searching and wants where I found it, http://packages.ubuntu.com/hardy/lsb">here is the .deb package for hardy

Hope this works. Thanks!
-Alni

---

