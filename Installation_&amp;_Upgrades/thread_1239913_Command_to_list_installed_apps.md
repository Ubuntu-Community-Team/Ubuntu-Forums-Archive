---
title: "Command to list installed apps?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by gobuntu on 2009-08-14
Hi dear forum members.
I want to upgrade from Ubuntu 7.10 which has worked just fine till now, since it came out, to the latest Ubuntu version.

I want to do a new total installation of the latest Ubuntu version, but would like to have a file that lists the names of the applications that I have installed in 7.10 so that I can add them on a one by one, selective basis, on the latest version. 

I already have a backup of the existing system, in case I need to go back to it. I have all data on a separate partition, which will stay as is. All partitions will stay same size.

So all I need (I think) is a list of all the installed applications as is. Is that possible, and please, how?

Thanks!

---

### Post by Katalog on 2009-08-14
I suppose you could go into the terminal and type "cd /usr/bin", hit enter and then type "ls" and it should give you a list of every single binary on your system. It would probably tell you more than you want to know, but it would most certainly give you a list of almost *everything* you have installed on your machine.

---

### Post by gobuntu on 2009-08-14
Thanks Katalog.

Actually, I figured out how with this console command:
---------------------------
dpkg --list > 'FileName'
---------------------------

dpkg --    (just with the two hyphens, lists the installed packages to the console), otherwise, it pipes the output to 'FileName' of one's choice.

I think there may be some apps that are not installed and managed conventionally that don't show up, so, if anyone has some more tips, please do provide them.

Thanks everyone!

---

