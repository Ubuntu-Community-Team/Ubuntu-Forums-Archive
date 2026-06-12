---
title: "Previously installed packages"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by zacktu on 2009-04-28
I've read lots of suggestions about how to do a new installation over an existing installation.  Many posts say to 1) have a different /home partition; 2) back up your /home partition 3) tell the new installation not to format the /home partition; 4) do it. I did it. 

Another suggestion was to have Synaptic generate a package download script.  I did that, but the only line in the script is !/bin/sh. I thought that was going to be a script for synchronizing the packages installed in my previous system with those already installed by 9.04.

As an example, thunderbird wasn't installed.  I was hoping that since it was one of my installed packages it would be installed by Update Manager.  Have I missed doing something to cause this to happen?

I'm doing all this in a nonessential system that I have set up in order to understand how to do a new installation over an old one, so I have nothing to lose here.  I'll be upgrading a system that matters one of these days, so I want to understand how to make everything go smoothly.

Thanks.

---

### Post by shatterblast on 2009-04-28
Ubuntu seems to leave all data alone on each reinstall or upgrade.  Firmware drivers and certain programs tend not to survive how ever, and they have to be reinstalled.  The easiest way to use a Synaptic script is after an update.  It can also be used after a clean reinstall, but then, the sources for the previous version of the installation would have to be re-added to the Software Sources, which is under System then Administration.

---

### Post by lovinglinux on 2009-04-28
> **zacktu said:**
> Another suggestion was to have Synaptic generate a package download script.  I did that, but the only line in the script is !/bin/sh. I thought that was going to be a script for synchronizing the packages installed in my previous system with those already installed by 9.04.

As an example, thunderbird wasn't installed.  I was hoping that since it was one of my installed packages it would be installed by Update Manager.  Have I missed doing something to cause this to happen?

You need to mark the packages first. That never worked well for me. What I use is this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

It works beautifully. Please keep in mind that it won't install packages installed manually. Nevertheless, Jaunty came with a lot of new software that I had to install manually before on Hardy.

---

