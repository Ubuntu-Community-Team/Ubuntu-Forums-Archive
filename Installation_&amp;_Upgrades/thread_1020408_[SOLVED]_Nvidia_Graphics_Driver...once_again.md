---
title: "[SOLVED] Nvidia Graphics Driver...once again"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Blueball32 on 2008-12-24
Hi, I'm new to Ubuntu, just finished installation last week (8.10) and now I have some troubles with the graphics driver.

I can't install the driver manually because I'm not really familiar with Linux environments (coming from Windows), so I hoped that the auto-install would work fine, but it doesn't. If I click at "activate driver" it should download the selected one, but it simply doesn't. I can see a new window for half a second which should obviously be an "%-install bar" but it is terminated before I can do anything...

I'm sure you can help. ;)

blue

---

### Post by zoundz on 2008-12-24
Hmmm...make sure you're connected to the Internet.  When I tried to install my driver on Kubuntu, the install exited instantly, and I believe it was because I wasn't connected to the Internet.

---

### Post by gettinoriginal on 2008-12-24
System > Admin > Synaptic Package Manager  (it will ask for your password)
Type Nvidia into the search and make sure the following things are checked, if not, then install them:

Nvidia-Settings
linux-restricted-modules

Now try the System > Admin > Hardware Drivers

---

### Post by Blueball32 on 2008-12-24
Ok, those packages are not installed, but I'm not able to install "Linux-resrtictred-modules". How can I do that?

P.S.: Internet-Connection is OK. :)

This Error occurs:

Dependency is no satisfiable

---

### Post by gettinoriginal on 2008-12-24
System > Admin > Software Sources, make sure first 4 boxes are checked, then copy and paste the following via terminal

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Now you should have it.

---

### Post by Blueball32 on 2008-12-24
Yeah now we're talking!!!

After 3 reboots and 200mb updates it finally works! Thanks man

just one more question:

I just wrote those commands in the terminal...what did I do...?;)

THX³

---

### Post by gettinoriginal on 2008-12-24
You just added apps and libraries to, and updated your synaptic package manager.  :popcorn:

And please go to tools and mark this as solved, thank you.

---

### Post by zapree on 2008-12-25
So I had the same problem and i did what you told, it worked, but after i installed the tons of restricted things from the repository somehow my sound got messed up??

---

