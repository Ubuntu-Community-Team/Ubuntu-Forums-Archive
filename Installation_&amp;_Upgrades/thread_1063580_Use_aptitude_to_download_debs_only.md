---
title: "Use aptitude to download debs only?"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by infinitejones on 2009-02-08
Is there a way of using aptitude (or apt-get) to download a package and all its dependencies, but save the debs and not install them, so I can put all the debs on a USB key and use them on another machine?

In case you're wondering why - I have an Acer Aspire One and upgrading to kernel 2.6.27-11 breaks the network. I have found one potential how-to solution which involves downloading a madwifi driver source and building it, which of course would need build-essential, which isn't installed on the Acer.

The how-to just says "Do an apt-get install build-essential" which obviously ignores the fact that I don't have a working network  connection on the machine I need to install it on. So the obvious thing is to download on my working machine and transfer it all across.

The other thing that's just sprung to mind is that build-essential (and its dependencies) are already installed on my machine with a working network so I'd need to be telling aptitude/apt-get to just download all the dependencies anyway.

Alternatively, if anyone's got another solution to the network problem, let me know, although I realise that I'm not posting in the right forum for that...

---

### Post by taurus on 2009-02-08
Build-essential package is on the installation disc.  Pop it in and run these commands from a terminal.

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by infinitejones on 2009-02-08
The Acer Aspire One doesn't have a CD drive - I installed it from a USB key. How do I tell apt-get to assume the USB key is the cd-rom?

---

### Post by ugm6hr on 2009-02-08
> **infinitejones said:**
> The other thing that's just sprung to mind is that build-essential (and its dependencies) are already installed on my machine with a working network so I'd need to be telling aptitude/apt-get to just download all the dependencies anyway.

The build-essential dependencies on Hardy (likely similar for Intrepid)

```
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring gcc-4.2-doc libstdc++6-4.2-dbg glibc-doc manpages-dev
  libstdc++6-4.2-doc ed diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch

```

You probably have the relevant .debs in /var/cache/apt/archives/ - just find and copy across.  Remember you will need 32-bit debs (assuming you installed i386 Ubuntu on Acer).

However, I think the easiest solution is to boot into an older (WORKING) kernel from Grub, install build-essential from there, and then reboot to fix the new kernel (or just consider using the old kernel until it is fixed by the developers).

---

### Post by infinitejones on 2009-02-08
> **ugm6hr said:**
> 
However, I think the easiest solution is to boot into an older (WORKING) kernel from Grub, install build-essential from there, and then reboot to fix the new kernel (or just consider using the old kernel until it is fixed by the developers).

Good point. Does the final 8.10 iso contain an earlier kernel? (I just installed it all from that iso, but then let everything upgrade itself automatically, so I don't know if it upgraded the kernel or not). And if it does, how do I stop it from automatically upgrading to the new non-working kernel when it asks me to do an upgrade as soon as I've completed the installation?

Thanks for all suggestions so far, anyway. Can anyone confirm if the dependencies for build-essential on Intrepid as the same as for Hardy?

---

### Post by ugm6hr on 2009-02-08
So have you done the install or not?  I'm confused...

I would suggest you just let the update happen.  Then edit /boot/grub/menu.lst to remove the new kernel entry and reboot.

You can use Synaptic or apt-pin to prevent updates, but then you won't get the next update either (which may fix the problem).

---

