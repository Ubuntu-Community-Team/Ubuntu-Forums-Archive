---
title: "How to upgrade ssh on Ubuntu 8.04?"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by NiceGuy12 on 2009-10-27
Hello everyone,

I have a pretty simple question. I need to upgrade my version of ssh to ssh 4.8 or greater. 

I need only (and for safety reason) upgrade the one package. Could I get some assistance on the best way and on how to do this?

Sorry for being a newbie.
Thanks

---

### Post by jjcv on 2009-10-27
> **NiceGuy12 said:**
> Hello everyone,

I have a pretty simple question. I need to upgrade my version of ssh to ssh 4.8 or greater. 

Have you tried the following:

sudo apt-get update

then

sudo apt-get upgrade

?

---

### Post by shaggy999 on 2009-10-28
> **jjcv said:**
> Have you tried the following:

sudo apt-get update

then

sudo apt-get upgrade

?

I think he only wants ssh upgraded, not all the packages.

There are technically two ways to do this that I can think of. First thing to do is make sure your sources are up to date so:

sudo apt-get update

Then what you can do is specifically tell the system to install ssh eventhough it's already installed. Just:

sudo apt-get install ssh-client ssh-server

I think those are the packages anyways. If there are newer versions of the packages in the repositories then it should understand what you mean and install the newer version.

The other way to do it is to go into synaptic, select all of your currently installed packages and "pin" them. This tells synaptic to NOT upgrade those packages. Just make sure ssh is unpinned and then do:

sudo apt-get upgrade

Now, if the version you need is NOT in the repositories then I would suggest finding the ssh website and see if they have newer debs. If not, you'll probably have to uninstall ssh and then download the source packages to the version you need and compile and install them yourself.

---

