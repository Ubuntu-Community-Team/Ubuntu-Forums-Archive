---
title: "Dual-Boot Installation"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by -tr on 2009-09-09
Hi there. My computer with windows 7 has been unable to boot for a few days and in the meantime I've been accessing the internet through the Ubuntu live disc. Thus, any documents or plug-ins etc are lost upon rebooting. So, is there any way that I can install ubuntu and keep my windows 7 installation and files completely intact?

I have looked at several guides on dual-booting but none really applied to this particular case and I wanted to be sure. Thanks! :)

---

### Post by epicoder on 2009-09-09
The installer on your live disc comes with a partitioner and the ability to accurately install and autoconfigure grub. I would give your Ubuntu installation at least 10 GB.

---

### Post by -tr on 2009-09-09
> **sh228 said:**
> The installer on your live disc comes with a partitioner and the ability to accurately install and autoconfigure grub. I would give your Ubuntu installation at least 10 GB.

Okay, so then on startup it will load ubuntu on default or load the grub loader which lets you choose?

---

### Post by raymondh on 2009-09-09
> **sh228 said:**
> The installer on your live disc comes with a partitioner and the ability to accurately install and autoconfigure grub. I would give your Ubuntu installation at least 10 GB.

Remember, if you choose side-by-side, to use the slider below (grab it with your mouse) and slide to allocate partition sizes.  Otherwise, you'll end up with the default 2.3GB install which is not even enough for the first update.

Have you considered separating your /home from your root (/)?  That way, should you need to reinstall for whatever reason, you just reformat over root effectively leaving your /home alone (hence retaining your original config files, settings, etc.)

Post back if you need assistance.

Back-up and defrag (at least 2X) windows first.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874) (thanks to Drs305)

---

### Post by raymondh on 2009-09-09
> **-tr said:**
> Okay, so then on startup it will load ubuntu on default or load the grub loader which lets you choose?

GRUB for you to choose.  You can also set which OS to default into.

---

### Post by -tr on 2009-09-09
> **raymondhenson said:**
> Have you considered separating your /home from your root (/)?  That way, should you need to reinstall for whatever reason, you just reformat over root effectively leaving your /home alone (hence retaining your original config files, settings, etc.)

Post back if you need assistance.

Back-up and defrag (at least 2X) windows first.

Not sure what you mean here. Aside from some commands I picked up in a Unix course, I'm pretty new to linux and this will be my first actual installation (with intent to use).

Also I have not been able to boot all the way into windows and can't backup or defrag at all. :(

---

### Post by executorvs on 2009-09-09
if you're going to dualboot are you also going to cleanly install windows?
if not you may want to try and fix windows first so you can repartition it using the windows utility. I say this because, in vista, repartitioning with gparted frequently messes up vista. this is not a problem in xp or 2000 and I have yet to have the /s pleasure /s of windows 7.

---

### Post by raymondh on 2009-09-09
> **-tr said:**
> Not sure what you mean here. Aside from some commands I picked up in a Unix course, I'm pretty new to linux and this will be my first actual installation (with intent to use).

Also I have not been able to boot all the way into windows and can't backup or defrag at all. :(

Use the liveCD and in live session (TRY UBUNTU ....), go to places and see if you can copy/paste your files into an external HD first just to save them.  If OK, exit and boot into your win7 disc to repair and fix your MBR.  Let's get it (windows) booting first.

1.  Boot into the win7 disc
2.  Go through the normal language, etc.
3.  Select repair computer
4.  Access a command prompt and type

bootrec.exe/FixMbr

* If that does not work (i.e. No SUCCESS message), try bootrec.exe/FixBoot

5.  If success .... type QUIT to exit and try out windows.

From there, we can work on getting your Ubuntu installed.  Post back.

---

### Post by -tr on 2009-09-09
Sadly I do not have an external HDD to use as backup which is why I was hoping to salvage the windows installation. Which is not going so well.

Some details of what I've done are in the thread below:
[http://www.techsupportforum.com/microsoft-support/windows-vista-windows-7-support/411910-failed-startup.h](http://www.techsupportforum.com/microsoft-support/windows-vista-windows-7-support/411910-failed-startup.h)


However the windows recovery partition is working and I think I can get a command prompt up so I'll give that mbr command a shot.

---

### Post by raymondh on 2009-09-09
While you're doing that (or after) ... some refereence materials to ponder on :

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Consider ROOT the "main avenue".  Within root are sub-streets like /var, /usr, /home, etc.  /home contains your personal configuration files, email settings, downloads, etc.  If /home were not separated from / (or ROOT), then if root collapses, so does your personal files (i.e. if you need to re-install because of a crash, etc.).  Because of this, it is suggested to separate /home from root.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  (this link is to create a seprate /home after/with an existing ubuntu install)

On installation, you can either create the partitions beforehand and then install unto it or, use the liveCD and avail of its' capabilities.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  (this has a nice tutorial on dual-boot)

Some decisions to make :

1.  How much space are you wanting to give to Ubuntu.
2.  Do you want a separate /home
3.  If not, do you want the automated approach (use the slider) or do you want to do it manual (to learn something new)

---

### Post by -tr on 2009-09-09
Oh so essentially the home and root separation works like having 2 HDD's with the OS and programs on one and personal files on the other, no? That would be quite helpful with my windows install but as for ubuntu, I'll mainly have programs etc that aren't available on windows (ie: aircrack suite :)) and what not. 

And as far as space goes, I have a 1TB drive and don't foresee much more than 500 GB being used in windows so ubuntu will have plenty of space.

Finally by manually do you mean running the commands for partition creation and such? I suppose I could do that. 


Oh and thanks again for your help! :)



EDIT: Okay, I know this is the ubuntu forums and everything, but here's where I'm at with my windows repair:

I ran the mbr command and received the success message right away. Then I tried booting into the disc again (which was previously not working), and went into the repair section. It said that it was repairing some kind of errors and to restart. After that, it detected no issues.

However after the logo screen, it now shows the mouse pointer and a completely black screen. Any ideas on this?

---

### Post by raymondh on 2009-09-09
> **-tr said:**
> 
However after the logo screen, it now shows the mouse pointer and a completely black screen. Any ideas on this?

At this point, I'm stumped.  Maybe someone can provide further assistance.  You can try to PM forum member [presence1960]("http://ubuntuforums.org/member.php?u=657448") (as I know he is a windows tech) and request him to look at this thread.

Let's work on Ubuntu when you have windows (and your files) saved.

---

