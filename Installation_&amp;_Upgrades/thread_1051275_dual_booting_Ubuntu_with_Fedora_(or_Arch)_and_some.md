---
title: "dual booting Ubuntu with Fedora (or Arch) and some more ??"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Strohfeuer on 2009-01-26
Hello, recently I switched from XP to Ubuntu. I have a Lenovo 3K 200 laptop and there is still the rescue & and recovery partition.

When trying Ubuntu I thought it's better to keep it for the time being but now that I know that I will never go back to Microsoft I will get rid off it and use the space to check out some other distros.

I have my hard drive divided into following partitions:

/      20GB
/home  130 GB
swap   4GB (logical)
R&R    6GB

I know the root partition is to big, half the size would be okay I have only 5.5 GB from it in use. But I didn't knew, XP had about 30GB full in use, lol.

The home and root partition is Ext3. 

Now to my questions: 

I read in another thread that I could use the /home partion for Ubuntu and Fedora if I assign another user name in Fedora, correct? Is the same valid for Arch?

If I remember the installation from Ubuntu correctly I could decide which partitions the Installer shouldn't touch. Do I have to say that it should not touch the /home-partition or how does it recognize that there is already data stored?

Are 6GB okay for Fedora or do I need more?

Any other things I have to consider during the installation?

Thanks for your time! :)

---

### Post by Strohfeuer on 2009-02-10
Just a small update in case someone stumbles about this post in the future.

I removed my rescue&recovery partition, decreased my swap-partition to ~3GB and my /-partition (where Ubuntu is installed) to 10 GB.
Then I created another partition (for Fedora) with a size of ~10GB.

Now I have 4 primary partitions:

1. 10GB
2. 10GB
3. 137GB (/home)
4. 3GB  (swap)

I made a big mistake now when installing Fedora. During the installation you will be asked where the boot loader should be installed. (I had no clue about this...)
I choosed the preselected option and so the boot loader was installed on the MBR. 

Now when booting, Fedora was booted immediately and I couldn't choose whether I want to boot Ubuntu or Fedora. I thought just deinstalling (or better formatting the partition lol) would solve the problem, instead I couldn't boot anything. There was a prompt showing '>grub' but I didn't know what do insert to proceed. 

So 'deinstalled' Ubuntu and installed it again, now I have the grub loader and can select between both operating systems.

So if anyone should have the same idea, install Fedora first then Ubuntu! :-)

Fortunately I have my /home on another partition so no important data was lost.

But on question I have is, is there a way to gain access to my Fedora-home folder after I installed Ubuntu? :confused:

During the installation of Ubuntu I was asked which data should be imported but I forgot to select the Fedora Folder (I only selected my old Ubuntu folder).

TIA

---

### Post by jjpcexpert on 2009-02-10
so that is recent and decent. also make sure they are all ext* or heck i will shoot myself in the foot.

---

### Post by Strohfeuer on 2009-02-10
> **jjpcexpert said:**
> so that is recent and decent. also make sure they are all ext* or heck i will shoot myself in the foot.

Except swap they are all ext3. I can see my all the different folders in my home partition since I used different usernames during the installation. Now if I only could change the permissions from the Fedora folder. Or wait maybe I can do it from Fedora, I will try it.

---

