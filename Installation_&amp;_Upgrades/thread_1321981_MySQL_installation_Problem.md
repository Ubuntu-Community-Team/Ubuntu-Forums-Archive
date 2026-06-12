---
title: "MySQL installation Problem"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by mi6crazyheart on 2009-11-10
Hello.....
After successfully installing APACHE & PHP when tried to install MySQL by giving this command " **[FONT=Verdana][SIZE=2]$sudo apt-get install mysql-server[/SIZE][/FONT]**  " I got this type of message.....

[B]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/B]

So, Please kindly any one tell me how to rid out from this problem.

---

### Post by trondhuso on 2009-11-10
It could seem like you have some package manager running. But I am not sure.

---

### Post by mi6crazyheart on 2009-11-10
Friend, I'm absolutely new to this world of Ubuntu. So, really don't know much about it. Please, can u tell me what i need to do exactly to solve this problem.

---

### Post by blueridgedog on 2009-11-10
Rather than go through hoops checking for a running package manager (which would probably just be synaptic open), reboot and try the command.

---

### Post by mi6crazyheart on 2009-11-11
@[blueridgedog]("http://ubuntuforums.org/member.php?u=459469")
Same error message is coming always even if rebooting and entering the command. Can't understand what's d wrong going at where.......

---

### Post by mi6crazyheart on 2009-11-11
Hey Guys, I've solved my problem.But, I technically don't know what was going wrong. What i just did is..... rather than giving the command " **[FONT=Verdana][SIZE=2]$sudo apt-get install mysql-server [/SIZE][/FONT]**"
I entered it as "**[FONT=Verdana][SIZE=2] sudo apt-get install mysql-server [/SIZE][/FONT]**" (remove that $ symbol from start of the command). That's all & my MySQL started installing & now running perfectly.

By d way, Guys thx u all to responding my query so quickly.

---

### Post by blueridgedog on 2009-11-11
Ah...yes, the $ is not part of the command and represents the command prompt, if you see it or # in commands at the start, they are representative of the command prompt and not part of the command.

---

### Post by mi6crazyheart on 2009-11-11
Oop's this is d thing. Any way thx man for this information.......

---

