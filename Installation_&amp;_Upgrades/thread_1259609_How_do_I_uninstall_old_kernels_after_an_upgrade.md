---
title: "How do I uninstall old kernels after an upgrade?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by Ubu4moi on 2009-09-06
After you upgrade to the latest kernel how do you get rid of the old one so it doesn't appear listed in the Grub boot loader?

---

### Post by x22 on 2009-09-06
1. goto /boot/grub and edit menu.lst--down toward the
bottom, either delete or comment # out references to the
unwanted kernels
2. goto /boot and delete the unwanted kernels, etc

---

### Post by drs305 on 2009-09-06
I'm a big fan of startupmanger for grub (legacy). It's a gui app that tweaks lots of grub settings. Including: how many kernels to display, menu timeout, default OS or kernel, and a lot more.

This guide discusses startupmanager as well as how to remove or hide extra kernels:
[ HOWTO: Grub Menu Kernel Display Options ]("http://ubuntuforums.org/showthread.php?t=818177")

You can either hide the kernels or completely remove them. That is also discussed toward the end of the guide.

---

### Post by falconindy on 2009-09-06
The problem with simply removing the entries from menu.lst is that they'll be back the next time a new kernel is released and installed. Two better options would be:

1) Comment them out in menu.lst rather than removing them. This way, the next time a new kernel is installed and the 'automagic' update of menu.lst happens, the old (unwanted) kernels aren't readded to the file.
2) Actually delete the kernel. In synaptic, do a quick search for linux-image and linux-header, and check off the old kernels for removal. I would **highly** encourage you to be extremely careful about this and make sure to leave your previous kernel intact in case you ever have issues with your current kernel and need to go back a release.

---

### Post by ddalley on 2009-09-15
I tried to remove extra kernels with APT, but they still remain.

In /boot, there are some files and drawers that have names similar/related to initrd.img-2.6.28-11-generic and I am not permitted to delete them directly.

How do I finally get rid of them?

---

### Post by drs305 on 2009-09-15
> **ddalley said:**
> I tried to remove extra kernels with APT, but they still remain.

In /boot, there are some files and drawers that have names similar/related to initrd.img-2.6.28-11-generic and I am not permitted to delete them directly.

How do I finally get rid of them?

Removing the older kernels is covered near the end of the guide I linked to earlier. The short story: run "uname -r" to check which kernel you are using. Then open synaptic, put "2.6.XX-" in the search window. You can safely remove unused "linux-image-2.6.XX-", "linux-headers-2.6-XX-X" . Many users keep at least one older kernel that they know works. The linux image may have the word "generic" attached at the end, depending on which kernels you are using.

---

### Post by slakkie on 2009-09-15
This is how I do it.. 

```

rmkernel () {
        sudo aptitude purge $(dpkg -l | egrep "linux-(image|headers)" | egrep -v  "$(uname -r | sed -e 's/-generic//' -e 's/-server//' -e 's/-virtual//')|linux-(image|headers)-(generic|server|virtual)" | awk '{print $2}')
}

```

---

### Post by The Thug on 2009-09-15
This is how I do it.

1. find out what kernel you are currently running by  opening terminal and type in "uname -r"
2. open Synaptics Package manager and search for "linux-image"
3. unselect those that you want to be removed ie old kernels
4. select "apply"
5. Old kernels will be removed and GRUB will be updated.

---

### Post by kvk on 2009-09-15
No hijack intended: what if I want to ADD an older kernel? I've enabled the Hardy repositories and run

sudo apt-get update

but the older kernels (rt kernels) don't appear in Synaptic. I've tried using

sudo apt-get install linux-image-2.28.xx.xx-rt

but it returns no such package.

---

### Post by slakkie on 2009-09-15
> **kvk said:**
> No hijack intended: what if I want to ADD an older kernel? I've enabled the Hardy repositories and run

sudo apt-get update

but the older kernels (rt kernels) don't appear in Synaptic. I've tried using

sudo apt-get install linux-image-2.28.xx.xx-rt

but it returns no such package.

```

aptitude search linux-image

```

Select the propper linux-image and then

```

sudo aptitude install linux-image-yourchoice-rt

```

You might want to install the kernel header files for that kernel as well, same procedure, just replace linux-image with linux-headers.

---

