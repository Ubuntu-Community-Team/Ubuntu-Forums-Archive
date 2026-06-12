---
title: "Broacom 43xx in Feisty or Gutsy"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by InvIsiBlekID on 2007-10-16
Hello everyone.
I spend alot of time helping people in the #ubuntu room on freenode, and I've noticed a lot of people asking about installing Broadcom wireless cards in ubuntu.  A lot of the time they don't realize that their card is even a Broadcom chip, and most of the time they are following other posts that use ndiswrapper to load a windows driver to get their wireless working.  I don't know if there's a post about this anywhere else, but I'm going to make one anyways.

First off there are a lot of cards that are actually the broadcom 43xx.
You can issue the command:

```
lspci | grep Network
```

You can see what the wireless card you have is.  Although it may not say that it is a Broadcom 43xx, check at [this link]("http://linuxwireless.org/en/users/Drivers/b43/devices") to see if it actually is.

Now I have only helped people set up this for 4306, 4311, and 4318, but I have no reason to believe that any other one wouldn't work.

Now, on to the install, its actually a lot easier than you would think.

First off you will want to remove ndiswrapper:
```
sudo apt-get remove ndiswrapper
```

I have posted the firmware in a tarball [here]("http://www.mediafire.com/?bqn8x4eancv").

You will need to download that file.  (It says bcm4311_firmware.tar.bz2 but it will work for others too)

Next you will want to extract the files.  So open up a terminal and cd to the directory where you downloaded it, usually your desktop and then extract:

```
cd ~/Desktop
```
```
tar -xjvf bcm4311_firmware.tar.bz2
```

Don't be alarmed because a bunch of files appeared on your desktop, we need to move them to /lib/firmware, but we need to use sudo because your user doesn't have permissions:

```
sudo mv bcm43xx* /lib/firmware
```

And finally you need to load the bcm43xx kernel driver:

```
sudo modprobe bcm43xx
```

After that you should be good to go, and no ndiswrapper, which I always found to be quite unstable.

Good luck everyone!
My nick is MasterShrek in #ubuntu on freenode.  Holla at me if you need some help.

---

### Post by Ripfox on 2007-10-16
In Gutsy all you have to do is go to system/admin/restricted drivers manager  and enable them.

---

### Post by dugh on 2007-10-16
bcm43xx does not work well.

ndiswrapper works great.  However, the gutsy version at the moment I believe may have issues.  I use ndiswrapper from the ndiswrapper site.

Follow these instructions: (change the windows driver (.inf) to the correct one for your computer)

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by Ripfox on 2007-10-16
Works fine here, although on my gf's laptop I had to implement ndiswrapper because the broadcom driver with fwcutter  method causes her synaptic pointing device to go all whacked. Every other time I have used it though it was fine.

---

