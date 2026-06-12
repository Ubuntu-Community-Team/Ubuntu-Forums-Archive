---
title: "VMwareServer install problem"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Bapu on 2009-04-15
In following the Instructions to insatll VMwareServer 2 on Ubuntu 8.10, I am required to enter the following:

sudo apt-get install build-essential linux-headers-`uname -r`

I am told (something like) build-essential does not exist.

What could be wrong?

Even though that failed I though I would at least execute this patch command:

cd vmware-server-distrib
sudo patch ./bin/vmware-config.pl ~/vmware-config.pl.patch.txt

the second command results in the message that patch is an unrecognized command.

That leads me to believe I am either doing something grossly wrong or something failed in my installation (yet I was not informed of any failures during my install).

Any help would be appreciated as I am VERY new to Ubuntu.

---

### Post by BryanPearson on 2009-08-03
Sorry if I am too brief here, but here goes...

The first part is probably easy.  You run the command:

uname -r

and get a kernel version, like "2.6.28-14-generic" which you put into the apt-get command like so:


sudo apt-get install build-essential linux-headers-2.6.28-14-generic

The second part is more complex.  I believe you are trying to apply a patch described elsewhere in the forum.  To do that, FIRST obtain the patch by downloading it.  Then, make sure you have the "patch" program by using apt-get like this:

sudo apt-get install patch

This downloads an ubuntu "package" and installs it for you.

Then you follow the instructions for the patch file for vmware-config.pl by (sorry this is so brief) extracting the vmware-server-distrib folder from the tar installer for VMware server (latest version) and then put the patch file vmware-config.pl.patch.txt in the vmware-server-distrib/bin folder where the vmware-config.pl file is, and then execute the patch command, with the name of the vmware-config.pl and the patch file as parameters.

Was that helpful?  Sorry I don't have more time, but this may give you a better idea of what you are trying to do.

---

