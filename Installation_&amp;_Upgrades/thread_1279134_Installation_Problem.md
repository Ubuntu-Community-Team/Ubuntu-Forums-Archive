---
title: "Installation Problem"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by tlinux on 2009-09-30
Until a few days ago I had a dual boot setup with Kubuntu 8.04 and Windows XP. Then I decided to "upgrade" to Kubuntu 9.04. That was a mistake. Kubuntu 9.04 doesn't work as well and is more difficult to use than the previous version.

I've read that Ubuntu 9.04 is much more polished and effective than Kubuntu 9.04 so I want to try it. I want to erase Kubuntu or overwrite it with Ubuntu 9.04.I tried to do this using the live CD for Ubuntu 9.04 but had problems. It wouldn't let me erase the Kubuntu files and it wanted me to change my partition settings. I'd rather just put Ubuntu in the same place that Kubuntu now occupies.

Can I do this easily? If so, how? If not, what do you suggest? I'd prefer not to wipe out my Windows XP files.

Thank you!

---

### Post by AlanQ on 2009-09-30
I believe that the only difference between Ubuntu/Kubuntu/Xubuntu is, essentially, the desktop. 

So just install **ubuntu-desktop** and (if you need to) uninstall **kubuntu-desktop**.
(System > Administration > Synaptic Package Manager)
If you keep Kubuntu-desktop they should both be options when you log in, so you can switch back-and-forth.

Should just be the opposite of the instruction under "I already have Ubuntu installed, how can I get Kubuntu?" here [http://www.kubuntu.org/faq](http://www.kubuntu.org/faq)

---

### Post by tlinux on 2009-09-30
There is no Synaptic Package Manager in Kubuntu. It used to have one called Adept, but that name seems to have disappeared. I found a package manager(of sorts) and used it to find the ubuntu-desktop package. I tried to install it but it froze up after installing 5% of the package. I want to switch to Ubuntu 9.04 to avoid problems like this.

I'd prefer to delete Kubuntu completely and install Ubuntu, but without changing the partitions. Is there any way I can do this?

Thank you.

---

### Post by Mercury_Alpha on 2009-09-30
You can install Synaptic in KDE, it will just require additional libraries because the dependencies aren't in place. (Most folks I know who use KDE use Synaptic anyway.)

Just do this in a terminal to grab it:

```
sudo apt-get install synaptic
```

Then in Synaptic, you can search for the "ubuntu-desktop" package that AlanQ mentioned, install it, then remove "kubuntu-desktop." That will give you pretty much the same result as a clean install of regular Ubuntu.

---

### Post by oboedad55 on 2009-10-01
> **tlinux said:**
> There is no Synaptic Package Manager in Kubuntu. It used to have one called Adept, but that name seems to have disappeared. I found a package manager(of sorts) and used it to find the ubuntu-desktop package. I tried to install it but it froze up after installing 5% of the package. I want to switch to Ubuntu 9.04 to avoid problems like this.

I'd prefer to delete Kubuntu completely and install Ubuntu, but without changing the partitions. Is there any way I can do this?

Thank you.

I'm confused. You ran 8.04 which worked well, you upgraded to 9.04 which didn't go so well, and now you want to do a clean install of 9.04? 8.04 is the LTS version. If that works for you why not just go with it? It's supported until 2011, I think.

---

### Post by AlanQ on 2009-10-01
> There is no Synaptic Package Manager in Kubuntu.
Of course. That was silly of me.

If Mercury_Alpha's solution doesn't work out (and if you have **/** and **/home** on different partitions -- best practice anyway), you could just do a fresh install of Ubuntu 9.04 .

---

### Post by Rayve on 2009-10-07
> **AlanQ said:**
> (and if you have **/** and **/home** on different partitions -- best practice anyway)

I've seen this recommended a bunch - how do you go about doing that?  This is likely more for future reference when I get my sole Linux system instead of dual booting with a main Windows machine, but just in case, can I move my /home to a different partition (4th partition I think it would be now) of this Windows machine?

And since I've run into some Windows issues lately, if I have to hard reboot from Windows, is there a chance that will damage my Linux partition, small though it is?  Makes me nervous.  :(

---

### Post by AlanQ on 2009-10-08
Rayve:

_Putting **/home** on a different partition_
As this might be getting a bit off-topic, I decided to post my reply in a new thread here: [http://ubuntuforums.org/showthread.php?t=1285883](http://ubuntuforums.org/showthread.php?t=1285883)

_Can Windows damage a GNU/Linux partition_

(Guess this is off-topic too but is just a quick one-off reply.)

There's always a danger that an Operating System could damage a partition of another OS. It's one of the risks of dual booting. As long as Windows doesn't have a Linux partition 'mounted' (not even sure if that's possible) at the time you hard reboot, it should be fine.

Doubtless you are using GRUB to boot whichever OS you want at boot time so, even if the hard reboot damaged the Windows boot files, the MBR (Master Boot Record) of the disc should be fine.

Given that you are making the move from Windows to GNU/Linux, the next step from dual-booting is to run Windows in a virtual machine. I use VirtualBox for this purpose: Windows runs inside a virtual machine which is in turn running on Linux -- keeps your Linux machine safe. If you are as geeky as many of us here, an analogy is the holodeck in Star Trek. Inside the VM, Windows (or any other OS) 'thinks' it has control of an entire real computer.

---

### Post by raymondh on 2009-10-08
> **Rayve said:**
> I've seen this recommended a bunch - how do you go about doing that?  This is likely more for future reference when I get my sole Linux system instead of dual booting with a main Windows machine, but just in case, can I move my /home to a different partition (4th partition I think it would be now) of this Windows machine?

And since I've run into some Windows issues lately, if I have to hard reboot from Windows, is there a chance that will damage my Linux partition, small though it is?  Makes me nervous.  :(

I prefer to create the partitions before installing.  During install, I would then mount the appropriate 'points' (i.e root, /home and swap) to their respective partitions.

Which type of partition to create depends on what your HD currently has.  We're allowed 4 primary or...... 3 primary + 1 extended.  If able, I would put ubuntu inside an 'extended' partition with root (/), /home and swap as logical partitions. 

After creating the partitions and during install, in step 4, you select manual > edit > use as > the appropriate mountpoint > format type

With regard to moving /home now and mounting that to a fresh install ... it is possible.  I don't know the if the config files between kubuntu and ubuntu could create problems/conflicts.  If so, I would just start fresh.

Back-up.  There are no guarantees.

Happy ubuntu-ing.

---

