---
title: "Feature available only with HAL"
date: 2008-07-16
forum: Hardware
---

### Post by Eugene RIMMER on 2008-07-16
Hi there. Got a strange bunch of problems with Kubuntu 8.04 (PRIOR to 8.04.1 updates, they are yet to try).

I think these all are of the same kind. 
First, I somehow got nothing but just "Log out" button in Log out dialog window, opened from K Menu. No shutdown, no reboot, no hibernate, nothing, just Log out. Pressing it turns screen black and hangs the system.

Then, after reinstalling the system (it was pretty fresh, /home on another partition, nothing to lose there), I got the same trouble plus total inability to shutdown the PC (it hung for a long time on the very last stage of shutdown process). I had to cut the power off by the hand.

Now I found the way to put back the log out dialog buttons (it's all about editing the ksmservicerc somewhere inside my ~/). Then I had a couple of smooth sessions. But after last reboot my Dolphin reports me "Feature available only with HAL" when I try to access any of my other partitions. Even the list of those disks changed dramatically, now showing 2 entries for my 2 hard drives instead of about 6 ones for all partitions. The most funny thing is that Krusader in root-mode sees all partitions and mounts any of them without fail, as it was once before. Also, adding those partitions to fstab didn't help, they didn't mount on boot. And btw, from now on almost every time the PC shuts down normally, only one time I had that nasty hangout on halt.

**About how I could screw up my system so much**. Every time I installed this version, I tried to setup Compiz and fusion plugins (and of course nvidia-glx and all that stuff also). This might be the poison for HAL, though Compiz works superb. 

After lurking around forums I thought that HAL is root of all my troubles. Is it so?

How should I fix my disk mounting? Generally speaking, I'd like to see this mount-on-my-demand turned off for some partitions, having them mounted upon the boot (mounting them from desktop session screws up Amarok music collection - Amarok starts automatically and watches the folders on that partition).

Is my shutdown trouble also based on HAL and what should I do to fix it anyway?

---

### Post by Eugene RIMMER on 2008-07-18
[STRIKE]OK, solved it by myself. Just added my user account to disk and haldaemon user groups (gooroos please tell me wich one is inappropriate here). HAL loves me again and mounts my drives on demand. 

Let's see how it survives the upgrade to 8.04.1 tonight.[/STRIKE]

[UPDATE]: Actually,** not working**.

The most interesting thing is that HAL is working fine in any *secondary *session (with [FONT="Courier New"]hald [/FONT]having been run under primary session). By saying secondary I mean the X session, started after any other session (with previous session still active in some another terminal). For example:
[LIST=1]
[*]Under [FONT="Courier New"]sudo[/FONT]|[FONT="Courier New"]kdesu [/FONT]("root" session in the same terminal) called from first, HAL-unseccessfull KDE session - HAL/mounting works perfectly (and not asking for passwords because I'm root then)
[*]After usual KDM logon (HAL not working properly yet) I do "Start another session" or "Lock this session and start another" and do another usual KDE logon - HAL/mounting works (asking for passwords, naturally)
[*]Terminal session trick [LIST=1]
[*]*Before *usual KDM logon do Ctrl+Alt+F2 and start a new terminal session with my usual credentials, 
[*]then return to KDM and perform a usual KDE logon with the same credentials
[*]HAL/mounting is **not working** with the same symptoms
[/LIST]
[*](Almost the same) The **true terminal session trick **[LIST=1]
[*]*Before *usual KDM logon do Ctrl+Alt+F2 and start a new terminal session with my usual credentials, 
[*]run there ```
$ hald 
```
[*]then return to KDM and perform a usual KDE logon with the same credentials
[*]HAL/mounting **works perfectly!!**[/LIST]
[/LIST]

Naturally, I used the last variant for my last 2 boots. It allows me to use everything I need withoud losing much horsepowers for the fisrt, HAL-unsuccessful session. But such a tricky logon ritual scares my wife away from using Linux at this machine. 

I suspect HAL is just not starting up at some bootup or logon stage. Can anybody help me with this?

---

### Post by Eugene RIMMER on 2008-07-22
It's a rather strange community. Reminding a private blog a little bit. I write something, some very few ones read it but no one replies, except for me.

---

### Post by Eugene RIMMER on 2008-07-28
OK, last and queer but clear and working trick:

- when a PC boots up and shows KDM logon screeen [drumroll] just wait a minute or so. To find out the exact time when I can log in, I switch to terminal 1 (Ctrl+Alt+F1) and wait there until (!) i get a login prompt. As time passes, the computer seems to do nothing first, but then it obviously polls every removable drive and then offers me a login prompt. After that I can safely switch back to terminal 7 and continue normal KDE login and work. Everything's fine.

This is how I work now.

Can anybody tell me, WHAT THE HECK?

---

### Post by applegrew on 2008-11-09
Thanks man.... U made my day. :) I too was plagued by this problem for past 3 days... I was way too much frustrated.. As I understand the problem now, is that hald is taking too much time to start and when we login before it starts then we face this problem. Hence I tried logging off then relogging in when hald has started and it worked perectly. :D

In linux there r way too many developers who test their own packages and put them in the repo, but their interaction and effect on other packages r not tested leading to these kinds of weird problems. :(

---

### Post by applegrew on 2008-11-10
Hi, again. I timed the time taken by hald to start. It took more than 3 mins!!!!

---

### Post by alesh_nitre on 2010-02-18
Trick posted on July 28th, 2008 05:57 PM also worked for me.. Thanks dude! :p

---

