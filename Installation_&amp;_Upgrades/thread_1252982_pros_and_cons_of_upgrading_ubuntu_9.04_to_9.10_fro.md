---
title: "pros and cons of upgrading ubuntu 9.04 to 9.10 from update manager"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by samsamros on 2009-08-29
Hello, I've been using Ubuntu for nearly one year and a half. I want to start by saying that I only use ubuntu in my laptop and have no other system or partitioning. Every time theres a new version out i download it and install the system cleanly, this is a pain in the neck because i have to make a back up of all my files several times in a year. Some may answer I shouldn't make a clean copy of the system and stick with the one i have, but i love to explore and especially a fascinating system like this one. Last time i had to make a clean copy is when i installed 9.04 from 8.04. I now find out that an upgrade is possible without having to make a clean copy of the system (have to format and install the system), I want to know how stable does the system become after upgrade and some pros and cons from doing it the old school way of format-install. For example after i installed 9.04 cleanly i could really see the changes in the speed when turning on and off the PC, it really improved. My question is will I see this improvement by upgrading? Will it affect my current programs, Compiz effects, network configuration thank you all in advance

---

### Post by SoftwareExplorer on 2009-08-29
Well, I've had mixed results with updating that way, but that might be because it was from Intrepid to jaunty with old intel graphics. I wouldn't upgrade to 9.10 just yet because it's still alpha and therefore probably not all that stable. If you do decide to keep doing fresh installs, you could try this [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome"). It would let you replace the system, but leave your files there so you don't have to move them every time. What it does is make the files in /home (where most settings are kept, and also your home folder) are stored in a different section of the drive from the actual ubuntu install.

---

### Post by garvinrick4 on 2009-08-29
Actually it leaves everything with settings alone and my files are the same as when I started upgrade. Not really a bother at all. Now when a use alpha product it does sometimes fail but not during upgrade. I have had grub problems from aplha 3 to alpha 4
which has been fixed have printer problems now but ubuntu will fix that all in due time.
I to love to use Linux and have desire to help out in Alpha stages all I can. I am not a coder but believe I am just fine at command line and can work with GUI in positive manner
so as to help make this a product that will take a Lions share of market one day like it deserves. Upgrade instead of fresh install is my suggestion. Pain in rear getting everything back the way you like it. Seems if you do it enough you get fast at it but still a pain.

---

### Post by SoftwareExplorer on 2009-08-29
> **garvinrick4 said:**
> Actually it leaves everything with settings alone and my files are the same as when I started upgrade. Not really a bother at all. Now when a use alpha product it does sometimes fail but not during upgrade. I have had grub problems from aplha 3 to alpha 4
which has been fixed have printer problems now but ubuntu will fix that all in due time.
I to love to use Linux and have desire to help out in Alpha stages all I can. I am not a coder but believe I am just fine at command line and can work with GUI in positive manner
so as to help make this a product that will take a Lions share of market one day like it deserves. Upgrade instead of fresh install is my suggestion. Pain in rear getting everything back the way you like it. Seems if you do it enough you get fast at it but still a pain.

Let me clarify:If you upgrade through the update manager, then you files will still be there. If you do a fresh install, you will need to back them up or they will be erased. If you do the separate home partition, it will make it so you can do a fresh install without having to back up your files

---

### Post by Old_Grey_Wolf on 2009-08-29
I have some systems that upgrade without problems. The only changes I make to them are minor; such as, changing the wallpaper, themes, or Compiz settings. 

If I do more to them than that; such as, changing the default browser, change Desktop Environment from Gnome to KDE, installing applications that are not in the repositories, etc., then I have problems with upgrades.

It seems to be that the more I play/experiment with the system the more likely the upgrade will fail.

I always make a backup of important files before attempting an upgrade no matter what system it is.

---

### Post by samsamros on 2009-08-29
Oh no i'm planning to wait for the stable version to come out. but i'm planning to upgrade, but i want to see the advantages of doing it by upgrade, is it the same as a fresh install? i mean by that do i have all the system files as a fresh and clean install? because this time I really want to avoid the whole problem of back up. i know the situation not might be the same but some were upgrading Windows XP to Vista and having a hell lot of problems. so I want to avoid that also. does it slow down my system or it will leave it as fast as it is now, it turns on extremely fast works smoothly and it turns off in a matter of 1 sec to 2 sec. any further suggestions?

---

### Post by SoftwareExplorer on 2009-08-29
Well, I would still recommend the link I gave above. You don't even have to back everything up to do it. That said, I don't think you will have as many problems as XP->Vista. The worst I have had happen is that I picked a theme that wasn't in the new version by default and so everything was ugly until I picked a new theme. I had intel graphics and that stopped working on that computer, but that would've happened with a fresh install too.

---

