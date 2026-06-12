---
title: "updating to new version with fresh install"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by pbpersson on 2009-05-03
One of the most upsetting things about updating to a new version through a fresh install is re-adding all the packages.  I have 1685 packages installed in Intrepid and re-installing all of them is not an attractive thought.

I know I should just be able to upgrade but if that goes wrong I will be forced into a fresh install.

Is there a way in Synaptic to make a script of all the packages I want to add and then once I am on Jaunty just feed that script into the Jaunty machine to get all my packages installed?

More importantly, has anyone actually done this?

---

### Post by lovinglinux on 2009-05-03
Simple. Works like magic!

See instructions below:

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

BTW, I have done this several times.

---

### Post by logos34 on 2009-05-03
> **lovinglinux said:**
> 
See instructions below:


+1

either that or go through synaptic>file>generate pkg download script

---

### Post by lovinglinux on 2009-05-03
> **logos34 said:**
> either that or go through synaptic>file>generate pkg download script

That never worked for me, unless the package is not installed and you mark it for installation first, then generate the package.

If you know how to do it, please explain. Just doing synaptic>file>generate pkg download script will create an empty file.

---

### Post by logos34 on 2009-05-03
> **lovinglinux said:**
> That never worked for me, unless the package is not installed and you mark it for installation first, then generate the package.

If you know how to do it, please explain. Just doing synaptic>file>generate pkg download script will create an empty file.

You're right, I don't know what I was thinking.

I mean, you *can* select all installed pkgs, mark for 'reinstall', select download script option, then cancel, but that will give a list like this:

> #!/bin/sh
wget -c [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_3.2-0ubuntu18_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_3.2-0ubuntu18_amd64.deb)
wget -c [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-23-rt_2.6.24-23.52_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-23-rt_2.6.24-23.52_amd64.deb)
wget -c [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-22-rt_2.6.24-22.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.24-22-rt_2.6.24-22.45_amd64.deb)

...etc

but that's of no use with distribution upgrade/fresh install because you will want the version for the new release.

So it appears that the option is only good for maybe backup or (re)install of same release, on same or diff machine

---

### Post by pbpersson on 2009-05-03
> **lovinglinux said:**
> Simple. Works like magic!

See instructions below:

BTW, I have done this several times.

OK, I am trying this right now going from my production Intrepid machine to a test Jaunty machine, all the packages are installing on Jaunty now.

Now.....assuming I have the /home in its own partition with all my preferences, email, and settings, when I am done with the entire operation won't this mean 95% of my packages will also be setup how I want them on the new version of Ubuntu?

---

### Post by lovinglinux on 2009-05-03
> **pbpersson said:**
> OK, I am trying this right now going from my production Intrepid machine to a test Jaunty machine, all the packages are installing on Jaunty now.

Now.....assuming I have the /home in its own partition with all my preferences, email, and settings, when I am done with the entire operation won't this mean 95% of my packages will also be setup how I want them on the new version of Ubuntu?

Yep 8-)

Beautiful, isn't it?

---

### Post by pbpersson on 2009-05-03
> **lovinglinux said:**
> Yep 8-)

Beautiful, isn't it?

Ummm.....sort of shocking, really :o

Thank you so much for your help - this is a wonderful way to upgrade!  :)

---

