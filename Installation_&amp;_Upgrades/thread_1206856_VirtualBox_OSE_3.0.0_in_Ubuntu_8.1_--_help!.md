---
title: "VirtualBox OSE 3.0.0 in Ubuntu 8.1 -- help!"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by nloding on 2009-07-07
I'm something a newbie when it comes to compiling software. Here's my ultimate goal: To build the 3.0.0 OSE edition on Ubuntu, make it a tarball, and be able to move it to another machine and install it there. So I'm compiling the binaries/install on one machine, copying the files to another and installing it there.

I've followed the "[build instructions]("http://www.virtualbox.org/wiki/Build_instructions")" but am still having issues. I installed all the required software and was able to run the ./configure (not hardened) and source ./env.sh commands without issue. I also ran kmk all and it worked just fine as well. This left me with the src and release directories. I tried just copying the release directory over, but that didn't work -- I couldn't make install it.

What files do I need to move over? How should I be doing this?

When I finally do the make and make install in the src directory for the kernel driver on the original machine, I am able to run the VBoxManage command, but it has to be run from the out/linux..... path, which is determined by where I extracted the sources.  How do I get it to work by just typing VBoxManage from anywhere, just like I had downloaded and installed the closed-sourced edition?

Thanks!!

--Nathan

---

### Post by Nero147 on 2009-07-07
Whenever you compile a program with the sudo ./configure command. What it does it it queries a number of libraries and adds some data. Then you sudo make. and finally sudo make install.

This is important, you cannot compile something on one machine and transfer it to another. You need to compile it on the other machine. or I suppose you could transfer it if you had the exact same hardware and software and versions of all software.

My assumption would be that you are transferring this to a computer without network access. Otherwise I would just say compile and install on it.

Assuming that you are transferring to a computer with no network connectivity, myy recommendation would be to get the .deb files from packages.ubuntu.com for the compiler and the dependancies. probably gcc build-dev build-essential g++ linux-sources. I forget exactly what they are but they are listed in the website. You can transfer those to your other computer and then install them and compile the code. You can even make a tarball if you really want to.

---

### Post by lukeiamyourfather on 2009-07-07
> **nloding said:**
> How do I get it to work by just typing VBoxManage from anywhere, just like I had downloaded and installed the closed-sourced edition?

Add the directory where VBoxManage is located to the system path. There are guides out there that explain it better than me so you should search for those too. I think its ~/.profile if you want to edit per user and maybe /etc/rc.local if you want the path to be changed for all users.

```
$PATH = "$PATH:/newPath/someFolder"
```

Don't forget the colon between each item in the path. Somebody please correct me if I'm wrong. Out of curiosity what's wrong with using the already available packages? Cheers!

---

### Post by nloding on 2009-07-07
I would be moving the package across identical hardware/software, but if it's easier to just compile it, I will do that.  I was just hoping to avoid the long process of compiling on multiple machines -- and we need to use the OSE package because we're using multiple machines, not just one per user like the PUEL license requires.

And -- there's no apt package for the 3.0.0 release of the OSE edition -- Hardy's repositories only have 1.5.6, which is hella old!!  I wish a repository had 3.0.0.

OK, so let's say I want to install VirtualBox to /mysoftware/virtualbox ... where do I plug that into the build process?  In the kmk line?

EDIT: And can I make that path /usr/bin/virtualbox?  Again, so that it's close to how the PUEL package installs?

And then I add /mysoftware/virtualbox to the PATH variable ...

Thanks for the quick replies!!

---

### Post by lukeiamyourfather on 2009-07-07
Are perhaps using this at a school, are you?

> In addition, academic use of VirtualBox is also permitted free of charge by the PUEL. 

That's from the download page for VirtualBox. If you still need the OSE you could make your own packages for Ubuntu instead of compiling it on every machine. Cheers!

---

### Post by nloding on 2009-07-07
No, not in schools.  I've scoured the PUEL but it doesn't cover our use, unfortunately.

One other person on the VirtualBox forums suggested using dpkg-buildpackage to create a .deb package, which is exactly what I want -- but I have no clue how to do that with the source that is provided from VirtualBox.  I didn't even know I could do such a thing!!

---

### Post by nloding on 2009-07-08
I used dpkg-buildpackage to made .deb install package for it.  It worked great.  Here's the solution if any are interested!

[http://forums.virtualbox.org/viewtopic.php?f=10&t=19713&start=0](http://forums.virtualbox.org/viewtopic.php?f=10&t=19713&start=0)

---

