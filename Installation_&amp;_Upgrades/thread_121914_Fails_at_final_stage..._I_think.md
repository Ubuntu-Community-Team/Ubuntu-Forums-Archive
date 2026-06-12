---
title: "Fails at final stage... I think"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by GeordieDS on 2006-01-26
Hi, I'm having problems with installation hanging for no apparent reason. Also, it doesn't appear to be the same as the many other hangs described on thread on this forum.

Using Ubuntu 5.10 intallation disk. Have successfully installed on another machine using this disk so that's unlikely to be the problem. Machine is an ancient and slightly cobbled together 500 Mhz AMD K6-2. 

Problem is the installation continues until it completes the "installing additional packages" this reaches 100%, then it just hangs. I've tried with the noapic/nolapic options and the "server" option as well. Doesn't like it.

Any thoughts? Or should I give up and use better hardware!

thanks all.

---

### Post by public_void on 2006-01-26
Have you tried using the live CD to see if all hardware is detected. I expect it is, otherwise the installation wouldn't get so far, but its best to check. At 100% is there any signs of processing, the hard drive light etc, or does it just fall silent?

I have Ubuntu on a 533Mhz AMD K6, 128MB RAM, I think you have will have met the hardware requirements.

---

### Post by GeordieDS on 2006-01-27
Live CD doesn't work either, though a Knoppix LiveCD works fine. 

There's no sign of any activity. Pushing the power button has no effect, but the reset button works ok. I've tried the install without the network connect so its not trying any background downloads. 

Actually, looking at the HD with Knoppix running, I can see a full file system there, but the computer refuses to boot from it. 

Would the IDE bus the HD on make a difference. I've been running it as a slave on the channel that the CD drive is the master. Would this be an issue?

---

### Post by Jucato on 2006-01-27
Linux isn't picky whether it's a master or slave, or whether it's on IDE 0 or 1 (unlike some other OS...). Did you check to make the  /  partition bootable? How about other distros? One possibility is that the CD installer or Live CD might not be working properly, since Knoppix works. But that's just a another theory.

---

### Post by public_void on 2006-01-27
If the Live CD doesn't work then it suggest Ubuntu isn't liking some hardware, or configuration. But...

> Would the IDE bus the HD on make a difference. I've been running it as a slave on the channel that the CD drive is the master. Would this be an issue?

You should change your HD to master, it could be a problem, TBH I'm not sure. If you want to be certain try (if you can) connecting you HD and CD-ROM into seperate IDE slots on your motherboard. Set both to master, then they shouldn't be an issue. If not have your HD as master and CD-ROM as slave. Post back the results.

---

### Post by GeordieDS on 2006-01-27
ok, i've got both cd drive and hard drive on separate channels, both as master.

How do I make the hard drive bootable? For partitioning I format the drive to the defaults offer (not using the LVM). Not dual booting, its a 4.2Gb drive, all for ubuntu.

cheers.

---

### Post by Jucato on 2006-01-27
During installation, choose manually edit partitions.  When you have created the partition that will be mounted as / (root), there is an option there to make it bootable. But this is all during installation. I don't know how to do it after installation.

Btw, why doesn't ubuntu make it a default in the installation that the partition that will be mounted as root should be bootable?

---

### Post by GeordieDS on 2006-01-27
Ok! I'm getting there.

Actually hit a whole bunch of other problems but I now know what the original problem is. 

Its the Timezone setting. That's where its freezing. Big blue screen with nothing on. Any ideas anyone?

---

