---
title: "Raid on Ubuntu"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by Akinraze on 2005-07-30
Hi I am relatively new to Linux, I have used Mandrake a few differant times and Redhat too, both before they forked to the new names, neither of which I have attemtep using Raid on, my question is on bot Raid and a specific Mobo....


Does Ubuntu have Raid support and does the Gigabyte GA7VRXP work well under this distro?

If so on both, could someone provide links for drivers that would obviously be needed during setup?

I am in the middle of downloading the Live CD, but I am relatively sure that it would not attempt to recognise that my system is running Raid, but I am completely impressed by the setup screenies that have been provided to insure each step during setup is being double checked for accuracy and am exited to install this over my current Windows XP Pro setup if infact, it will run on Raid with this Mobo.

Even tho I current run Microsoft products primarily, I feveroushly keep up on who is in the scene hoping that one day, somone gets it right, and helps Linux make the jump to mainstream, and I think Ubuntu is on the right track in this manner, I am not in any way saying that Mandrake has not cought my interest in linux, as it has been my main focus in winging myself from Windows, but Mandrake has not (atleast in the versions I have tested out) re assured me that everything is being verified functional during installation, giving me additional chances to alter the settings as I go through the setup like the screenshots show, Mandrake simply asks what you have, sets you up, then you enter the GUI, and then you hang on for the results, and if your not Linux savvy, well, your somewhat screwed.

Thanks in advance for **Any** help you might provide me.

P.s. Keep up the impressive work Guys/Gals

---

### Post by jasmuz on 2005-07-30
I hope this can help a bit:

[http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID](http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID)

---

### Post by moffa on 2005-07-30
Is there anyway that could be explained in noob terms?

I am trying to install Linux but the partition manager only sees two separate hard drives not the striped raid set.  I read the link provided above, but I do not understand how I am supopse to run those linux commands if I cannot install Linux in the first place.

Since this is my first time in a while trying to install Linux, I am very open to some suggested reading.

Regards

---

### Post by moffa on 2005-07-31
Everything I have found has told me that Linux cannot be installed on a raid, just a single drive.  This is disturbing because I have Windows installed on a raid.  I'm sure there is a way to do it, if anyone would help out.

---

### Post by kosmic on 2005-07-31
The only way to install to a RAID device is if the RAID device is a HArdware implementation with a processor, in this way you can install has a RAID, if your RAID system needs drivers or is a soft RAID is not possible.

Yes I know Red hat can do it, but don't know what hacks they use to acomplish that...:(


The only solution is to install to 1 disk and after the installation then start to change the system to RAID...[http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID]("http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID")

---

### Post by snoochems on 2005-08-01
i'm new to linux.  I haven't even 'obtained' a distro yet.

I'm trying to decide whether or not i really want to.  If Linux can't be installed on a RAID0 drive, then i think that is a real shame.  That is all i have, and i love it for video editing and the general 'quickness' of having two HDD's working together.

---

### Post by moffa on 2005-08-01
[QUOTE=kosmic]The only way to install to a RAID device is if the RAID device is a HArdware implementation with a processor, in this way you can install has a RAID, if your RAID system needs drivers or is a soft RAID is not possible.

Yes I know Red hat can do it, but don't know what hacks they use to acomplish that...:(


The only solution is to install to 1 disk and after the installation then start to change the system to RAID...[http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID]("http://www.ubuntuforums.org/showthread.php?t=2557&highlight=RAID")[/QUOTE]

How can I tell if my raid card is a hardware raid?  When I boot it has its automatic raid setup built in, so I can change things on startup.

I would install it to 1 disk but the installer cannot find any partitions on my raid or other drives.  If I were to install it on just one particular drive, I think I would end up corrupting my raid array completely.

---

### Post by jek on 2005-08-02
[QUOTE=kosmic]... if your RAID system needs drivers or is a soft RAID is not possible.

Yes I know Red hat can do it, but don't know what hacks they use to acomplish that...:(
[/QUOTE]

It is incredibly important that simple software RAID configuration works "out of the box".  Especially base RAID1 implementations.  Without it, Ubuntu is not competitive with distros like Centos.

---

### Post by heltreko on 2005-08-22
Here's some info on how to install debian linux on a root raid system.
[http://alioth.debian.org/projects/rootraiddoc](http://alioth.debian.org/projects/rootraiddoc)

Came across it while searching for a Ubuntu Raid howto...

---

