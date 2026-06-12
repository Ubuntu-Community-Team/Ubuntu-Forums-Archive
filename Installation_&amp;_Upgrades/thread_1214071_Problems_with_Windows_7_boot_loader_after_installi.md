---
title: "Problems with Windows 7 boot loader after installing Windows 7  then Ubuntu jaunty"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by raveash on 2009-07-15
Hi, recently i made a clean instillation of windows 7, then afterward i installed Ubuntu jaunty on a separate partition. I installed Ubuntu after windows to avoid the possibility of grub being erased during a windows instillation.

After a successful instillation of ubuntu i decided to boot back into windows 7. The menu selection in grub did not say Windows 7, it said windows vista. I am not sure why.

After selecting the windows partition in the grub boot loader i encountered the following error(not exact but summarized):

***********************Error Output**************************************
Windows failed to start, a recent hardware or software change might be the cause.

       Insert your windows instillation disk and select repair computer.

Status:0xc0000225

info: The boot selection failed because a required devise is inaccessible.
**************************************************************************

I was considering taking the windows errors advise and repair the boot loader with the instillation cd but i was a bit scared that i would not
be able to boot back into ubuntu.

I was also considering reinstalling grub while booted into Ubuntu.But then i was also scared of not being able to boot back into windows 7.

Any one have any advise as to what steps i can take to be able boot into both windows 7 and ubuntu(my main operating system), given my situation and error above?

Thanks!

---

### Post by mynameinc on 2009-07-15
> **raveash said:**
> Hi, recently i made a clean instillation of windows 7, then afterward i installed Ubuntu jaunty on a separate partition. I installed Ubuntu after windows to avoid the possibility of grub being erased during a windows instillation.

After a successful instillation of ubuntu i decided to boot back into windows 7. The menu selection in grub did not say Windows 7, it said windows vista. I am not sure why.

After selecting the windows partition in the grub boot loader i encountered the following error(not exact but summarized):

***********************Error Output**************************************
Windows failed to start, a recent hardware or software change might be the cause.

       Insert your windows instillation disk and select repair computer.

Status:0xc0000225

info: The boot selection failed because a required devise is inaccessible.
**************************************************************************

I was considering taking the windows errors advise and repair the boot loader with the instillation cd but i was a bit scared that i would not
be able to boot back into ubuntu.

I was also considering reinstalling grub while booted into Ubuntu.But then i was also scared of not being able to boot back into windows 7.

Any one have any advise as to what steps i can take to be able boot into both windows 7 and ubuntu(my main operating system), given my situation and error above?

Thanks!

Never worked with Windows 7, but it's still in beta, isn't it?  Maybe this is a bug in Windows 7, or it isn't compatible with GRUB yet.  I don't know.

---

### Post by raymondh on 2009-07-15
> **mynameinc said:**
> Never worked with Windows 7, but it's still in beta, isn't it?  Maybe this is a bug in Windows 7, or it isn't compatible with GRUB yet.  I don't know.

I am multi-booting win7 and ubuntu, plus others at the moment.  So I know it works.

If you are afraid of losing GRUB, you can re-install GRUB, repair GRUB, and/or re-edit the menu.lst anytime.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Another option (since Ubuntu is your main OS) is to install virtualbox in Ubuntu and add/guest win7..... to play around with.

[http://www.knowliz.com/2009/01/install-windows-7-with-ubuntu-using.html](http://www.knowliz.com/2009/01/install-windows-7-with-ubuntu-using.html)

When done, you can convert the old win7 space for storage or whatever.  Of course, recovering GRUB as well after deleting the 'old' win 7 partition (as the MBR may be there).  

Herman's GRUB page and the GRUB manual.  Herman is a UF member and a great teacher.

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)
[http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents](http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents)

Herman's GAG page.  Good rescue disc.

[http://members.iinet.net.au/~herman546/p12.html](http://members.iinet.net.au/~herman546/p12.html)

Lastly, browse Herman's page for tips on installation and dual-booting.  Heck of a resource.

Back up your files..... Google, Research and Read up ... make a choice ... and act. If you want to, post your decisions in the forum for the members to see and comment upon.  The forum and help is just a liveCD away (at worst) :)

---

### Post by Mark Phelps on 2009-07-15
Did you resize your Windows Seven partition to make room for Ubuntu after you installed Seven?  If so, Seven appears to treat the disk partitioning as a "hardware change".  Yeah, I know ... strange.

Since you have an installation disk, you can boot that and run Startup Repair a few times -- but it will overwrite the MBR and you'll have to reinstall GRUB to fix that.

---

### Post by raymondh on 2009-07-15
> **Mark Phelps said:**
> Did you resize your Windows Seven partition to make room for Ubuntu after you installed Seven?  If so, Seven appears to treat the disk partitioning as a "hardware change".  Yeah, I know ... strange.



@ Mark Phelps,

Could it involve/relate to those darn [immovable files]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") that windows sets in odd places of the partition?  And if we force the issue by shrinking more than what windows allows, we get those errors?

In two win7 installs, I resized/shrank seven down (500GB > 100Gb and 320GB > 100GB).... and did not get that error.

Strange windows, indeed.

---

### Post by Mark Phelps on 2009-07-16
I was responding to questions about reactivation and don't believe that shrinking would affect that in any way.  In the cases where the beginning of the OS partition has been moved, that has affected booting (in some cases) such that Startup Repair had to be run to get booting restored.

So, I can't see how shrinking would affect activation.  To do that, the hash sum would have to include partition start and end information. I've done partition resizing numerous times in Vista and never had an activation problem.

As to the immovable files, the most notorious is the MFT, which is typically written at the "end" of the partition.  Howver, I've also seen cases where it was written in the middle of the partition.

---

### Post by raveash on 2009-07-16
My problem is now resolved. All I did was insert the windows install cd and start the repair.It seems that my grub instillation was not affected. Thanks guys for the help.

---

