---
title: "Intel ICH9R (P965) Raid not recognized"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by personificator_me on 2009-05-19
Hi all, anyone else come across this strange problem?

System Setup:
 2 WD 150 Raptors
ASUS P5B Deluxe

In Ubuntu 8.10 and earlier I had to manually remove the power to one of the drives or the install would see a raid setup even though I had the bios set the HDs to IDE and/or compatible mode (no joke). 

In Ubuntu 9.04 I cannot even get a raid volume!!! Even though the bios is set to RAID and the Intel Matrix Storage Volume creator says I have my Raid 0 volume. The Install (and fdisk) will report 2 separate drives, but the bios sees a Raid volume.

Now, that is something weird. Anyone shed some light here?

---

### Post by D1m3b4g on 2009-05-22
Yo, 

I think this is an ongoing thing, I've seen many another thread about the same "issues".
One of the replies I saw wasn't exactly shedding much light on it explaining the process is apparently very complex and tricky to sort out.

I'm a little bemused as I would have considered that a simple driver that allows the kernel to interface properly with the intel storage matrix would solve the issue, how to correctly query the thing for a list of raid sets and how to interperate the result... however it must be more complex than I am giving it credit for as it would have surely been implemented by now.

I'm in the same position as  you and have been for a very long time... I seriously want to use ubuntu as my main PC OS on this computer but I can't because I run a raid 0 for the system drive. It's a real shame.

If you look deeper you'll find out about something called "fakeraid" (as the intel storage matrix manager is really a fake raid solution I'm told) but it's apparently fairly complex to make work properly.

Cheers

Dime

---

### Post by ronparent on 2009-05-24
Not simple, but not that altogeter impossible. To get the raid set identified, youhave to install the dmraid software - ie **sudo apt-get install dmraid -y**. Next you have to discorer the raid configuration set up in raid bios. To do this you run sudo **dmraid -r**. If your raid is configured in bios, dmraid will read the so-called metadata created by the raid bios and present the findings. Your next step is to run s**udo dmraid -ay** which will load the symbolic links to the raid partitions into /dev/mapper. These links are what you use to mount the raid partions to whatever mount points you create in your filesystem to receive them (ie /media/winXP, etc). Although you can test all of the above commands from the live cd, it the results are tempoary and dissapear when you reboot. You can find specific instruction on how to install ubuntu on a raid drive on the following site:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I am uncertained whether the process has been updated for 9.04 and am currently having to mount my raid0 array manually to access it. Fortunately I inadvertently installed ubuntu 9.04 to a separate non-raided drive, so my main issue remains on how to mount the raid0 partitions automatically on boot and not on getting a ubuntu system up and running on the raid.

---

