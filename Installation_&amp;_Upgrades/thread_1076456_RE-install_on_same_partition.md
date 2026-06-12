---
title: "RE-install on same partition?"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by landshrk on 2009-02-21
Okay, I'm an idiot. Fairly new to the whole linux/ubu thing, but diggin it a lot. I had noticed a few days ago, after a recent update, that my GRUB was getting kinda cluttered. Looked into it, found my solution, used Synaptic to clean things up.

Unfortunately, I cleaned a little too well... Now, all I have left of my wonderful Ubu is memtest, and a large portion of now unused space on my HD.

I've got a USB flash drive set up to install and run Ubu (which works quite well), but I want to know if I can re-install it on the same partition I had it on previously, with all my data and what not.

If not, it's no real biggie, but it'd be nice cause I have a few dozen pictures I never got around to backing up...

Any helps yous mights haves would be greats!

Thanks!

p.s. Running on a Dell 1501 dual-booted (at least, it WAS dual) XP SP3/I.I.

---

### Post by taurus on 2009-02-21
If you want to reinstall on the same partition(s), then you need to use the Manual option when you get to the disk/partition screen.  Then, mount whichever partition you have Ubuntu on before to /.  Remember, you have to include the mount point (/) or the installer will complain about no root filesystem.

---

### Post by landshrk on 2009-02-21
Please excuse the n00biness here...

I ran the installer again, this time selecting the 'Manual' radio button. Clicked Forward.

Selected (out of /dev/sda1, 5, 6, or 7) /dev/sda6 (where it was before), and clicked edit.

1st question: What format should it be? I believe it was ext3 journaling before, as that's what it's showing in the dialog, but I'm not sure...

2nd: In the box for 'mountpoint,' used /. Is that right?

When I've selected ext3, and / for the mountpoint, and click Forward, I get this message:

"The file system on /dev/sda6 assigned to / has not been marked for reformatting. Directories containing system files (/etc, /lib, /usr, /var...) that already exist under any defined mountpoint will be deleted during the install.

Please ensure that you have backed up any critical data before installing."

So, I quit, and came back here, as I'm trying to be able to do this without losing the data already on that partition.

Is that even possible? Am I just nuking this thing beyond all reason? Am I just being too noob at this?

Thanks for your patience and all your help.

Nova.

---

### Post by Bölvaður on 2009-02-21
Well I think you have just tackled the problem from the wrong angle.

I'd check what is on the partition with live-cd or any other mean I'd think of. Then I'd either back up the data that you got there.

You can back up the data by just creating a new partition and move the data over there, and then when you do an installation you can select that partition to be mounted as /data without formating it.

---

### Post by landshrk on 2009-02-21
If it's already there, can I just create a new partition onto which I can install Ubu, and then access it afterwards? If I can do that, then I'll just allocate 5GB to the new Ubu partition, access the old info, and then incorporate all that (now) unused space into the Ubu partition.

Is that possible?

---

### Post by Bölvaður on 2009-02-21
not 100% sure if I understood you, but if you mean something like this

If you find file,
then you will:

  Create new partition
  Copy the files onto the new partition

  Select the old partition as / during the installation
  Select the new partition as /data during the installation


then yes :P

---

### Post by landshrk on 2009-02-21
Basically, that's what I was getting at. I just don't have the lingo down quite yet. I like layman's terms!

Thanks for all the help, and I'll definitely be posting to let y'all know the outcome.

Nova.

---

### Post by landshrk on 2009-02-21
Alright, got it on, up and running, updated fine (though I'm still putting off the restart for a minute...), looks like it's all going smoothly, but...

I'm helping out a friend, was running XP SP2 on an Inspiron E1505. Had LOTS of trojans and whatnot, so backed up all the important stuff, wiped the HD, and installed Ubu. Unfortunately, I can't get any connectivity on it. The ethernet isn't working, the wireless isn't working, and I need to get the updates going.

Any idea where I might be able to find the driver(s) necessary to get this thing on the move?

Again, thanks so much. Ubuntu is outstanding, if a bit more difficult to get the hang of than other commercial OS, and I LOVE the fact that there are resources out here for people like myself, wanting to switch, but having some difficulty.

Okay, enough for now. Any ideas would be greatly appreciated.

Time to go hit up Google!

---

### Post by Bölvaður on 2009-02-21
I have never witnessed any computer that has ethernet card being unable to connect unless if there are some special settings demanded by the router.
did you check if the hardware wasnt detected (command : lshw)

---

