---
title: "New laptop - wanting to install Kubuntu"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by feb3 on 2009-04-11
I have purchased a new laptop specifically for Linux.
It has a 160GB hard drive - single partition with Vista Home Basic OS. The DVD that came with it is the operating system recovery DVD which says that it allows you to restore the OS.
I would like to preserve the option to go back to Vista if necessary in case I pass the computer on at some point.
My questions are as follows:
Will the DVD reinstall Vista to a machine that has had it wiped off?
Would it be better to create a small partition to house Vista and use the remaining (larger) one for Kubuntu and if so, how would I do this please?
Next, if I preserved Vista on a small partition I would prefer the computer to boot straight into Kubuntu so in effect I could 'forget' about the Vista bit - can this be achieved?
Hope that someone can help or point me in the right direction regarding links as I am very inexperienced in these matters, although I did manage to get Ubuntu running on another laptop with Wubi (now deleted). Prefer it to be properly installed separately. I have tried 3 live CDs i.e. PCLinoxOS, Ubuntu and Kubuntu but think I like the latter best.

---

### Post by Raptor Jesus on 2009-04-11
I used vista for a long time. I was referred to *nix by some friends. I decided to start off small and use Kubuntu.

To answer your question about the dual booting. I don't believe you can make it boot up on kubuntu automatically. I suggest just doing a full installation.

---

### Post by sgosnell on 2009-04-11
I know nothing of Vista and that's more than I want to know, especially about OEM restore DVDs. You **should** be able to restore from the DVD even if Vista has been wiped, but I won't guarantee that.

You can easily leave Vista on a smaller partition and boot to Kubuntu automatically.  Just download the live CD .iso, burn it to a CD, set the laptop to boot from the CD, and boot the live CD.  Choose Install, and you will be taken through the steps by the install software.  Choose to keep Vista, and you can choose the size of the partitions and how you want to set things up.  Kubuntu should boot automatically unless you press Esc during the boot startup.

---

### Post by feb3 on 2009-04-11
The problem with doing a full installation and wiping Vista is that I am suspicious that the recovery disk that was supplied with the machine is just what it says and would not re-install the OS if it wasn't already on the hard drive.
I have read about partitioning the hard drive with the Vista partitioning tool so I wonder if that is the best thing to do and then I could do a proper install of Kubuntu on the remaining bit.
Thank you for your reply - all suggestions appreciated.

---

### Post by feb3 on 2009-04-11
Thank you sgosnell - that sounds pretty much on the lines of what I was thinking. This new laptop has nothing on it except Vista so doesn't require a deal of space. I am just defragmenting it prior to using the Vista partitioning tool.
I was advised to shrink it to 50% which would leave more than enough for Kubuntu as it is a 160GB hard drive.
I already have the CD of Kubuntu and have tried it as a live CD.
Also liked PCLinuxOS.
When I install Kubuntu on the new partition, I had read that you need to allocate 2GB as a swap file so if I do this, how much should I allocate to Kubuntu? When I previously tried Ubuntu with Wubi it used the full partition of 10GB on another computer that we have.
Any advice very welcome.

---

### Post by Gen2ly on 2009-04-11
You don't not necessarily Need a swap partition if you have enough RAM.  I use KDE with 2 GB of RAM and don't have a swap.  Icommonly have open Firefox a notetaking app and run games and wine and have never had a problem.  If you plan to use programs like Blender I'd definitely create a swap for them.

---

### Post by sgosnell on 2009-04-12
The install program will automatically allocate the swap partition unless you do a manual partition.  You don't really need to worry about it.  I'm not using a swap partition at all, because I have an SSD drive and 2GB of RAM, and never use hibernate.  I also don't often open enough programs and Firefox windows to need to swap RAM to disk.  YMMV, but even if you do need a swap partition, the install will do that automatically.  Just make sure it isn't wiping out your Windows partition.  Don't click Forward until you're certain that's what you want to do.

---

### Post by Gen2ly on 2009-04-13
Good point sgosnell.  If you wanthibernate you'll want swap.  For me though suspend-to-ram works just fine and I don't need swap.

---

