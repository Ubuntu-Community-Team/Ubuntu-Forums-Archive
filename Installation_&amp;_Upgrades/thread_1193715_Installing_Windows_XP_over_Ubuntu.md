---
title: "Installing Windows XP over Ubuntu"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by aeitos on 2009-06-21
Hey guys,

I recently bought a new computer and everything has been working fine. It originally had Windows Vista but the reason I bought the computer was so I could experiment with Debian and Ubuntu so I have done that.

After awhile of using Debian and Ubuntu, I decided I wanted to reinstall Windows XP for awhile or maybe even just dual boot them both.

I thought it would be simple. First I just tried putting in the Windows Setup CD and restarting the computer and it loaded up.. but after the setup of copying files the setup crashed give me a blue screen of death.

At first I thought it was something wrong with the Windows CD so I burned another one and tried installing it but got the exact same error message during the setup.

I then did some research and figured maybe I had to format it or something first so I reinstalled ubuntu and tried messing around with gparted and ntfs and not really having luck with that because the operating system was running at the same time.. so then I tried downloading the gparted cd and running it on boot and I was able to delete the partitions and create a new partition but the same issue after restarting with the windows cd.. and then I just tried it with deleting the partitions and then trying the setup but no luck :(

Anybody have any ideas?

---

### Post by Xylar Wasterend on 2009-06-21
If you have Ubuntu already installed on the first partition, you're out of luck as far as I know. [I was told]("http://ubuntuforums.org/showpost.php?p=7396677&postcount=3") (and found out) that Windows likes to be first OS on the system and thus cannot be placed after Ubuntu...

---

### Post by presence1960 on 2009-06-21
> **Xylar Wasterend said:**
> If you have Ubuntu already installed on the first partition, you're out of luck as far as I know. [I was told]("http://ubuntuforums.org/showpost.php?p=7396677&postcount=3") (and found out) that Windows likes to be first OS on the system and thus cannot be placed after Ubuntu...

Not true, when I first started using Ubuntu I formatted my hard disk to all Ubuntu because I was one of those people who didn't read prior to trying to install a new OS. Afterward I created a second partition for windows and it worked fine. It was sda2 and it booted up fine!

---

### Post by presence1960 on 2009-06-21
maybe you can try dban to totally overwrite your disk and make it clean : [http://www.dban.org](http://www.dban.org)

Then try reinstalling.

---

### Post by aeitos on 2009-06-21
> **presence1960 said:**
> maybe you can try dban to totally overwrite your disk and make it clean : [http://www.dban.org](http://www.dban.org)

Then try reinstalling.

Thanks! That seems logical to try. That crossed my mind for a second before but then I completely forgot about it. I'll try it and get back to you guys if It doesn't work.

---

### Post by aeitos on 2009-06-21
awww :( I tried installing debian and then trying the XP installation but still no luck :(

anybody else have any ideas??? there must be some way to install xp


edit: ooooops I just noticed you said 'dban' :P thought you ment debian. ok lol i'll try that thanks :)

---

### Post by presence1960 on 2009-06-22
> **aeitos said:**
> awww :( I tried installing debian and then trying the XP installation but still no luck :(

anybody else have any ideas??? there must be some way to install xp


edit: ooooops I just noticed you said 'dban' :P thought you ment debian. ok lol i'll try that thanks :)

I gave you a link to get dban...lol

---

### Post by aeitos on 2009-06-22
ahh.. ok :( I tried using dban and I keep getting the following error

DBAN finished with non-fatal errors,
This is usually caused by disks with bad sectors

I have tried going through the troubleshoot hints in dban and also the FAQ at dban.org/faq but still not able to resolve the issue :(

I can't see our there are any issues with the disk and bad sectors. It was a computer that was just bought and it was already running Windows just a few weeks ago until I installed debian and ubuntu.. and those both still appear to be working without any issues.

Any other suggestions?


Update:


YAY!! It's fixed! I knew there couldn't have been any bad sectors or anything with my Hard Drive!!

I had to change the Sata Controller option in the BIOS settings to IDE. Apparently, this seems to have made the Hard Drive unreadable by Windows XP.

I'm thinking it was on IDE previously and then when I formatted the computer with Ubuntu/Debian, it changed this from IDE to whatever.

Anyways! Thanks for the help! :)

---

