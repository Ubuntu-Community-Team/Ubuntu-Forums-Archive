---
title: "New Install"
date: 2008-11-06
forum: General Help
---

### Post by apollo23 on 2008-11-06
Alright, I finally decided to try a dual boot with XP Pro and Ubuntu (8.10).  I did the install like normal allocated 70% HD space to XP and 30% to Ubuntu.  The once I got to the long install part I walked away and did something else.  When I came back I got a message that I had be away for more than 10 seconds and I needed to log in.  I tried but I couldn't remember my password (pathetic I know).  I then rebooted to find the system went straight to XP and I was never presented the option to go into Ubuntu.  I then went to my computer in XP and found my C: drive was as expected 70% its original size.  I did not however find another drive or another partition.  I then rebooted the computer with the Ubuntu cd in the drive and went through the installation process until I had to dedicate a portion of the drive for the new Ubuntu.  At this I had both an XP partition, an Ubuntu partition and was being asked what size I wanted to make an additional Ubuntu partition.  I then quit installation and got back into Windows.  Any suggestions on how to solve this issue?  I would like to uninstall the Ubuntu on the system the XP doesn't show and reinstall Ubuntu or get this issue fixed so I can use Ubuntu.  Thanks for all the help in advance.

---

### Post by ad_267 on 2008-11-06
If partitions have already been created for Ubuntu then you can select the manual partitioning option, then select the Ubuntu partition to be mounted at "/" and tick the option to format it. There should also be a Linux swap partition that is selected to be used as swap.

I don't think that's normal that you would get locked out when using the Live CD. The password should be just blank anyways.

---

### Post by amgalitz on 2008-11-06
Ok couple things.

Windows can't see linux file systems. That is why you only see the original windows partition, but shrunk down, and see your new linux installation partition when you went back with the livecd. This is actually good, we don't want windows getting confused and relettering your partitions on drives after your boot drive if you have any.

Sounds like you might have interrupted the installation so that GRUB (the boot loader that the livecd usually installs) never got installed. Thus your MBR (master boot record) is untouched and loads windows as before installation.

Probably best to use the installation partitioner to delete the first installation of ubuntu and do it over. My experience is that it is tricky to use the livecd installation session to start in the middle. Use a password you can remember <G> this time.

Once you are installed, you will need to remember the root or superuser/administrator password you defined during installation to alter the menu.lst file to control how your initial boot menu works.

Learn about GRUB menu timer [[COLOR="Cyan"]Here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#timer").
Learn about setting which OS your GRUB menu defaults to [[COLOR="Cyan"]Here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc").
Explore the page I've directed you to above for a great tutorial about playing with boot options. Since you want to dual boot you will benefit from this.

cheers

---

### Post by williamts99 on 2008-11-06
> **apollo23 said:**
> Alright, I finally decided to try a dual boot with XP Pro and Ubuntu (8.10).  I did the install like normal allocated 70% HD space to XP and 30% to Ubuntu.  The once I got to the long install part I walked away and did something else.  When I came back I got a message that I had be away for more than 10 seconds and I needed to log in.  I tried but I couldn't remember my password (pathetic I know).  I then rebooted to find the system went straight to XP and I was never presented the option to go into Ubuntu.  I then went to my computer in XP and found my C: drive was as expected 70% its original size.  I did not however find another drive or another partition.  I then rebooted the computer with the Ubuntu cd in the drive and went through the installation process until I had to dedicate a portion of the drive for the new Ubuntu.  At this I had both an XP partition, an Ubuntu partition and was being asked what size I wanted to make an additional Ubuntu partition.  I then quit installation and got back into Windows.  Any suggestions on how to solve this issue?  I would like to uninstall the Ubuntu on the system the XP doesn't show and reinstall Ubuntu or get this issue fixed so I can use Ubuntu.  Thanks for all the help in advance.

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) in case you forget or it gets lost again Related to this, everything in Linux is case sensitive, so apollo23, Apollo23, and APOLLO23 are all different.

You will probably want to go through the install process again as it seems to not be complete.  This time though you will manually select the already made partitions for the install and swap.

Also, if you want to be able to access your Linux partition(s) from windows you can use the open source [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) or the freeware [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
Just be aware that if you can access you Linux partitions from Windows, so can a Windows virus/spyware/badware.

Best Regards

---

### Post by apollo23 on 2008-11-07
> Probably best to use the installation partitioner to delete the first installation of ubuntu and do it over. My experience is that it is tricky to use the livecd installation session to start in the middle. Use a password you can remember <G> this time.

How do I delete this partition?  I would assume I go into the Ubuntu set-up from the cd again but when I get to the part to create a new partion where do I find the option of deleting an existing partition?  Is it under the manual option?  Thanks for all of your help thus far, it is very much appreciated.

---

### Post by caljohnsmith on 2008-11-07
> **apollo23 said:**
> How do I delete this partition?  I would assume I go into the Ubuntu set-up from the cd again but when I get to the part to create a new partion where do I find the option of deleting an existing partition?  Is it under the manual option?  Thanks for all of your help thus far, it is very much appreciated.
You don't need to delete your current Ubuntu partition, just use the "manual" option in the installer when it comes to partitioning, and then specify your existing Ubuntu partition with a mount point of "/", and click the format box for that partition. That should be all it takes.

---

### Post by ad_267 on 2008-11-07
> **apollo23 said:**
> How do I delete this partition?  I would assume I go into the Ubuntu set-up from the cd again but when I get to the part to create a new partion where do I find the option of deleting an existing partition?  Is it under the manual option?  Thanks for all of your help thus far, it is very much appreciated.

Yeah the manual install option is a lot easier than having to delete your two Ubuntu partitions, resize your Vista partition to take up the full space, then get the installer to shrink your Vista partition again. Really not worth it.

---

