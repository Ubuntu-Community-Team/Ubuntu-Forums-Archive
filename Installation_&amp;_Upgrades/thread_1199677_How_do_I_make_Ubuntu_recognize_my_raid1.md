---
title: "How do I make Ubuntu recognize my raid1?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by vectorm12 on 2009-06-29
I'm trying to install Ubuntu 9.04x64 Desktop on a HP DL160 G5 server with builtin raid1 support.

The system is set to run in raid1 and works without a hitch in CentOS 5 where the volume is recoginzed and installs perfectly.

However as I do prefer the Ubuntu build simply because it works right out of the box without any hassel (besides this ofc :) I'd like to stick with Ubuntu.

The problem is that when I run the installer the partition manager manages to sniff out the fact that there are two individual drives in the system and misses the raid volume.
Which means that if I install it onto one of the drives I end up with a system where one drive simply isn't being used for anything rendering the raid1 useless.

My question now is how do I make gparted recognize the raid volume instead of the individual drives? Do I really have to install seperate drivers for the controller since CentOS 5 manages on it's own? Is there someway I can load additional drivers before gparted is started and ofc is there is a way of doing this how do I go about doing so.

---

### Post by ronparent on 2009-06-29
Gparted will recognize the raid1 drives as one raid array only when the raid set is activated so that it may be acted upon in ubuntu. It is not clear from your post what your raid implementation is.

You may actually have what is called a fakeraid. So called because software is actually needed to access the drive set as one raid array. In windows that software is a driver provided by the mb manufacturer. In ubuntu it is called dmraid, which, you have to install and activate to see the raid set.

If that is the case the dmraid install process is itself easy if your computer has an internet connection active. Open a terminal - Applications>Accedsories>Terminal. Then write to the terminal sudo apt-get install dmraid -y. When the installation is complete, write sudo dmraid -ay. This last command will activate your raid1 array. If you now write **ls /dev/mapper** the output will show you the symbolic links that will permit you to access the drives as a set. The set must then be mounted in order to be able to actually use it.

---

### Post by vectorm12 on 2009-06-29
to be quite honest I haven't looked into if this server is infact implementing hardware raid or not but all things considered I'm gonna guess it's infact a fake raid. 

The setup is a basic set of two sata drives on a HP raid array controller running them in raid1 for reliablilty purpose. The idea being that the system is supposed to be installed on the raid array in order to provide redundancy incase of hdd failure.

I just got a little confused by the fact that CentOS handled this out of the box while ubuntu didn't.

Thanks for the info I'll get right on it and see what I come up with.

---

### Post by vectorm12 on 2009-06-30
just like you said installing dmraid worked perfectly.

However there are no less than four entries in dev/mapper

control, ddf1_system, ddf1_system1, ddf1_system2 I know "system" is the volume label I've set for the raid but then I'm back to guessing.

1. Control, No idea most likely related to dmraid?

2. I would guess this is the raid1 volume itself?

3. ddf1_system1&2 most likely represent the individual partitions that are currently on the first drive? 

So if I now run the installer from the livecd session I am in and choose to install will it work out that dmraid is required in order for the OS to work?

---

### Post by ronparent on 2009-06-30
Your observations on /dev/mapper are all correct. Just out of curiosity, did dmraid reconstruct the second drive so it matches the first? And for your final question, yes, dmraid is required for the OS to work as from a raid when booted. You can install it from the live cd if you follow this step-by step guide: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It sounds like you have a good understanding of your situation and are almost home free. Post if you run into any dificulties.

---

### Post by vectorm12 on 2009-07-01
No dmraid did not automatically restructure the second blank drive but as I was going to repartition the drive anyway that wasn't an issue. 

Might be a way of making it do that as well but I haven't looked into it at the present time. I do however have a second system with the same setup where I would like for it to restructure the second drive so I am going to read up on dmraid in general.

For now thanks for the help

---

### Post by vectorm12 on 2009-07-01
Hmm I keep feeling there is something that's not totally right here... After following those instructions and creating the required partions as well as making sure the data is being replicated across both drives I proceeded to install Jaunty but encountered a ubiquity crash.

The worrying thing about this is the fact that if I choose not to utilize dmraid I can install ubuntu just fine but whenever dmraid is loaded ubiquity crashes.

On launchpad I read about ubiquity having issues with installing on drives where there currently are active partitions so I decided to reboot and remove all partitions before once again attempting to install Jaunty.

However I still ran into the ubiquity crash. I've now decided to try out the system by simply running without the "fake raid" and using the builtin feature but I am a little less confident in the ability to handle realtime rebuilds etc of drives.

Anyone have any experience with that?

---

### Post by ronparent on 2009-07-03
Runing the "fake raid" is merely the equivalent of running windows with a raid driver. Running without it in ubuntu doesn't allow you to use the mb's built in raid harware. If access to the raid drives in a dual boot with windows, you could investigate setting up a software raid.

---

