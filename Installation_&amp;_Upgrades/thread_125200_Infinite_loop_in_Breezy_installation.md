---
title: "Infinite loop in Breezy installation"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by jonnnny on 2006-02-03
I tried to install ubuntu 5.10 onto my ibm thinkpad t41p and I keep on encountering this infinite loop when I get to the stage that asks me for name of user, username and password.  After I enter the password and confirm, it'll go back to the screen where it asks for name of user.
I am 100% positive I am formatting the username correctly (i.e. no special characters or uppercase letters). I've tried all combinations of words/case and it just keeps on going back to the screen where it asks for the name of the user.

I'm not a beginner with computers, so its not like I'm not reading the instructions or anything.  I tried default installation, expert installation, different partition set ups, you name it I've tried it.
The closest I got was I skipped that step of the installation, then try to run base-config and from there, it tells me that I entered an empty password, and that I should enter a new one.

I enter the new password, and at the bottom of the screen, I see something popup very quickly that says "user does not exist, changes not made" and it'll ask me for the password again.

So this time I exit to shell, login with root and manually 'adduser'.  I repeat the previous step and everything seems to be ok until i boot up Ubuntu and the login/password doesn't work to login, and it won't let me log in with root.

So my question:
Has anyone else gotten this 'infinite loop' with choosing a username/password before?

I figure I'll download kubuntu on my other computer, burn it and give that a shot. btw I'm using pressed ubuntu cd from shipit.

---

### Post by LotsOfPhil on 2006-02-25
It says your post is "3 weeks old" but I hope this helps someone in the future.
I ran into the same problem. I quit and reinstalled. The first time I had something like 
4.0 GB /ext3
35.0 GB /FAT32 mount in /home
1.0 GB swap

That didn't work. I changed to
4.0 GB /ext3
35.0 GB /FAT32 mount in /windows
1.0 GB swap

And had no problems.

---

### Post by awreneau on 2006-03-01
I'm having this exact problem.....still looking for an answer.

I'm on a GW laptop 2.4 ghz, 1gb ram, 20Gb Ram.

I broke up the disk as follows:
8.0 GB /windows
2 GB /home (this is a fat32 partition, so I can share it with windows, it's a dual boot)
768 mb swap
the rest is left for /

I'm going to leave windows out of the loop this next install, I'll post back my findings.

---

### Post by awreneau on 2006-03-01
Looks like it's a problem sharing a /home partition formatted from windows.

Post is here.
[http://www.ubuntuforums.org/showthread.php?t=134430&highlight=user](http://www.ubuntuforums.org/showthread.php?t=134430&highlight=user)

---

### Post by awreneau on 2006-03-01
Yep, apparently thats what it was, I'll have to edit the fstab to mount the other partitions.

---

