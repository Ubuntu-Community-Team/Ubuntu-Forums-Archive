---
title: "686, what is it good for."
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by kroiz on 2006-04-29
Hi,
I have an IBM t41. I saw posts of ppl with similar configurations that had installed the package linux-686.
Will I gain anything by installing this package? (performance , stability ...)
why wasn't it installed by ubuntu installer?

---

### Post by Qrk on 2006-04-29
Ubuntu's stock kernel is compiled for i386, which is the intell architecture from the '80's. It isn't really important to have a kernel compiled for i686, which is more modern, but you'll get a slight performance benifit. 

Ubuntu is i386 by default so it can be installed on more types of systems. It shouldn't hurt anything to install *linux-686* 

Ubuntu has to fit on one cd, so something has to give.

---

### Post by kroiz on 2006-04-29
Thanks Qrk.
I installed linux-686 and believe it or not things feel faster now.
can I now safly uninstall:
linux-386
linux-image-386
linux-image-2.6.12-10-386
linux-restricted-modules-2.6.12-10-386
linux-restricted-modules-386

---

### Post by Qrk on 2006-04-29
Yes

---

### Post by kroiz on 2006-04-29
The description of mono-jit:
This package contains the Virtual Execution Environment and code
generator (Just-in-Time and Ahead-of-Time) "mono" which runs CLI (.NET)
applications, currently available for [COLOR=Red]i386,[/COLOR] powerpc and amd64 architectures
[COLOR=Red]only.

[COLOR=Black]Does this means that this package wont work for me now?[/COLOR]
[/COLOR]

---

### Post by Qrk on 2006-04-29
That will still work. i686 won't prevent you from running i386 applications. Indeed, everything available in the repositories is still i386, you've only changed the kernel.

i686 is in the same class as i386. It isn't like the difference between 64 and 32 bit.

---

### Post by kroiz on 2006-04-29
thanks Qrk, got it.

---

### Post by mattyj on 2006-04-29
Hello,

I am new to Ubuntu and a relatively novice Linux user.

I installed the initial ubuntu Dapper Drake Beta CD and then went through the nVidia installed instructions as noted here:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

When I did so I used the linux-restricted-modules-686.

When I restarted there was a new install version in my grub menu and now my system sees both Pentium D processors(did not prior).  Did I update the kernel to the 686 by doing this(it seems faster).

1.  Do I need to remove the old versions as suggested in this thread?  
2.  How would I do that?
3.  How do I remove the old kernel installations from my grub loader menu(now three are listed)?

Thank You,

MattyJ

---

### Post by Qrk on 2006-04-29
Yes, you did get the i686 kernel. Make sure you have the metapackage, linux-686, as it will prevent many  problems with upgrades.

```
sudo apt-get install linux-686
```

You don't need to remove the 386 versions at all. But if you want to, you can go into synaptic, do a search for "linux" and remove linux-386 and assorted packages. Unless disk space is a problem, there isn't really a reason to bother. 

You can also remove older versions of both kernels, such as linux-image-2.6.15-19-386, along with linux-headers and linux-restricted-modules corresponding to that architecure and version number.

Once you remove a kernel, whether 686 or 386, its entry will be removed from Grub automatically. 

Because Dapper isn't released yet, there are a lot of kernel upgrades. Once released, they should be rare. But in the meantime, you may have to clean out old kernels once in a while.

---

### Post by Omnios on 2006-04-29
I had 386 and lm sensors would not work properly for certain pannel apps which 686 fixed. So it does have some uses.

---

### Post by kroiz on 2006-04-30
mattyj, search in synaptic for 386.
I also found that there is mplayer-386 which I removed and installed mplayer-686

---

