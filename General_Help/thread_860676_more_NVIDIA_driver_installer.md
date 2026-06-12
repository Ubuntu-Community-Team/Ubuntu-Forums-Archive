---
title: "more NVIDIA driver installer"
date: 2008-07-15
forum: General Help
---

### Post by Canuck in Carolina on 2008-07-15
Have made great progress thanks to UpChucky.  However the NVidia installer indicates that I need to compile  the kernel interface.  Their README indicates that I must install the 'kernel-sources' package for my kernel.  (I just installed UBUNTU but am very green.)  How do I check for it?  Is there something special I need to do to get the package to compile?:confused:

---

### Post by jonian_g on 2008-07-15
Are you trying to install the nvidia drivers manualy? If so, there is no need to do that because you can install them from the repositories or by using EnvyNG.

---

### Post by Canuck in Carolina on 2008-07-15
There is a driver installer supplied by NVIDIA (nvidia-installer) that appears to automate a bunch of stuff.  However I seem to have gotten myself jammed up in the middle of the process.
This is supposed to replace ENVY.

---

### Post by jonian_g on 2008-07-15
EnvyNG is a program that downloads and installs the nvidia drivers. Can you tell me exactly what you're trying to do?
There is no need to use anything else...

---

### Post by Canuck in Carolina on 2008-07-15
Have an old PIII Gateway machine (ca 1999) with a NV5 TNT2/TNT2 Pro  graphics card.

Using the procedure suggested by Upchucky and originally documented by starcannon I get to the point where the installer is trying to compile the kernel and comes up with the error: You do not appear to have libc header files installed on your system.  Please install your distribution's libc development package.

Do I need to download the development verison of UBUNTU?

---

### Post by jonian_g on 2008-07-15
You have to install the package libc6-dev.

sudo apt-get install libc6-dev

or you can install it through the synaptic package manager.

But I recommend to install the drivers for your card like this:

System>Admin>Hardware Drivers and just check the box on the window that appears to enable and install the nvidia drivers.

---

### Post by Canuck in Carolina on 2008-07-15
Does not appear to find the libc6-dev file.

When I try using the simple GUI it comes back with "No proprietary drivers are in use on this system."

---

### Post by sdennie on 2008-07-15
To fix this problem you will probably need to install build-essential.  Try:

```

sudo apt-get install build-essential

```

And then try the installer again.

---

### Post by jonian_g on 2008-07-15
Go to Synaptic package manager and on the window that appears click Settings>Repositories and on the first tab check all the checkboxes and uncheck "Cdrom with Ubuntu....". On the second tab check the two checkboxes. Press close and then refresh.

Then try again to install the driver with the GUI way.

---

### Post by Canuck in Carolina on 2008-07-15
jonian_g:  no change - still no proprietary drivers.

vor: comes back with message: 
E: Couldn't find package build-essential

---

### Post by jonian_g on 2008-07-15
Silly question. Is the ubuntu computer connected to the internet?

---

### Post by Canuck in Carolina on 2008-07-15
Yep

---

### Post by jonian_g on 2008-07-15
Weird...
Can you install anything on that computer? Go to add/remove and try installing "NVidia binary X.Org 'legacy' driver".

---

### Post by cariboo on 2008-07-15
Have you had a look here:

[http://albertomilone.com/guides.html](http://albertomilone.com/guides.html)

It is a little out of date. This is  the guy that looks after the nvidia drivers for Ubuntu. I submitted a bug concerning one of the new drivers for Intrepid and he had it fixed in a couple of days.

Jim

---

### Post by Canuck in Carolina on 2008-07-16
Thanks guys.  I had to shut down last night.
Have tried the how-to from Sr. Milone and am attempting to contact him for assistance.  Thanks for the lead.  He has some great stuff on his site.
Still working on it.

---

