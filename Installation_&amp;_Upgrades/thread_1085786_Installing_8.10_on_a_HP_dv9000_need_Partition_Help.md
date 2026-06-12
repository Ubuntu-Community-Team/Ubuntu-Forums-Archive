---
title: "Installing 8.10 on a HP dv9000 need Partition Help"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by Sinning_Sinner on 2009-03-03
Okay, so after going insane and installing XP again on my laptop I have decided to go back to Ubuntu, more specifically 8.10. Previously I used 7.10 on my laptop and there was a nice little guided tutorial on the forums for it but now there is nothing.

So getting to the root of it all I need to know how I can have ubuntu delete the windows partion and Ubuntu be the only OS on the laptop. I have four options:

1.) Guided - resize SCSI1 (0,0,0), partion #1 (sda) and use freed space

2.a.) Guided - use entire disk
  2.b.) SCSI1 (0,0,0) (sda) - 120 GB ATA ST9120821AS

3.) Guided - use the largest continuous free space

4.) Manual


Any help would be appreciated. Thanks in advance.

---

### Post by InspiredIndividual on 2009-03-03
What's the desired result? If Windows XP is the only installed OS at the moment, you can choose 'Guided - use entire disk'. This will format your entire hard disk and install Ubuntu on it. So afterwards Ubuntu will be the only installed operating system on your computer.

It may well be worth a little of your time to make a more conscious decision how you want to partition your hard drive. In this thread you can find all the information about partitioning you need: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
If this thread is a bit text heavy for you, scroll down to the references. There's a link to a graphical guide to Gparted, and aysiu's article on partitioning basics may be more what you're looking for. It's very concise, clear and illustrated. He starts out with an explanation about dual boot, so just skip reading that part if you don't need it.

EDIT: by the way, if you've got any specific questions, I'll be happy to try and help you out.

---

