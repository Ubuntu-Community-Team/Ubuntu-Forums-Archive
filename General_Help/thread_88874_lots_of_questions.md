---
title: "lots of questions"
date: 2005-11-11
forum: General Help
---

### Post by spyke01 on 2005-11-11
ok, its been over 2-3 years since ive used linux, and never any that looked as good as these, ive got a few questions, they may be that these coimmands arent around any more, or ive forgotten them, and others are general questions

_**Commands:**_
*ls -al* i thought that this would print out all my files and folders, hidden or otherwise, including etc, tmp, and the others, but it doesnt am i just typing it wrong?
*ls -?* i cant remember what will display the group, user and permissions a file belongs to/has
*?command?* what command lists all current daemons running?

_**The OS Itself:**_
1. can i make it so that 1 user uses the ubuntu interface, 1 uses kubuntu, and another 2 use edubuntu? if so how?
2. why cant i login in as root? or for that matter, why does ubuntu not has a shadow passwd file so that i can add other users, and turn on root?
3. in kubuntu whenever i turn on the root account and give it a passwd, why can i not run the package program in anything but read-only mode? 
4. can i make it so when i run the install cd that it install packages that i have chosen automaticcly?

sorry for all the questions, like i said its been awhile, the last linux i used was mandrake 8.0(kept crasing with my sound drivers) and redhat8(for only 8 minutes)

also one other thing, if i want to download a prepackage program instead of trying to compile the source code, what os can i download for? when i was trying to make a file it said BSD but arent the packages we dl deb files?

---

### Post by taurus on 2005-11-11
Try

ls -la /

1.  Yes. each user can picks whatever window manager he/she wants to use.  One person can use Gnome while another can pick KDE or even Xfce...
2.  The reason you can't log in as root due to security.  If you need to do something with root, use sudo or if you really want to, run

sudo passwd root

3.  You cannot modify system files unless you are root!!!
4.  You can choose to install whatever you want.  If you don't like something on your system, remove it with apt-get...
5.  If you want to install a binary program on your ubuntu, you need to get the file with .deb extension...  As long as the file says it's for Linux with deb extension, it should work with your ubuntu!  I don't think you can install BSD binary on your ubuntu and expect it to run unless you have an emulator!

---

### Post by earobinson on 2005-11-11
Well im second guess you get 2 answers :)

> ls -al i thought that this would print out all my files and folders, hidden or otherwise, including etc, tmp, and the others, but it doesnt am i just typing it wrong?
ls -? i cant remember what will display the group, user and permissions a file belongs to/has
?command? what command lists all current daemons running?

The man command will help you find this out. Im not on linux right now but I did a google search and it seems that.
>  -a      Include directory entries whose names begin with a dot (.).
> -A      List all entries except for . and ...  Always set for the super-user.

1. To my understanding yes and no, during the logon screen there is the option to change the desktop enviorment so simply by installing kubuntu-desktop and what i assum is eubuntu-desktop this could be done I think. you can install them using synaptic or apt-get.

2. A simple search of the forums for: root password solved this problem [http://www.ubuntuforums.org/showthread.php?t=88820&highlight=root+password](http://www.ubuntuforums.org/showthread.php?t=88820&highlight=root+password)

3. Im not sure I understand the Q

4. Not that I know I think the cd has maybe 3 tops default install settings, normal, server and no clue what the third might be!

question the last. .deb is what ubunut uses, but it only supports ubuntu debs not debian debs, however some debian debs will install.

---

### Post by spyke01 on 2005-11-11
[QUOTE=taurus]Try
5.  If you want to install a binary program on your ubuntu, you need to get the file with .deb extension...  As long as the file says it's for Linux with deb extension, it should work with your ubuntu!  I don't think you can install BSD binary on your ubuntu and expect it to run unless you have an emulator![/QUOTE]

[QUOTE=earobinson]question the last. .deb is what ubunut uses, but it only supports ubuntu debs not debian debs, however some debian debs will install.[/QUOTE]

ok, so i can dl a deb package but not a debian deb package, how will i be able to tell the difference?

also, taurus, i want to be able to burnm a cd install, that will install a set of packages automaticlly each time i install with the disk, that way i dont have to keep choosing packages over and over again on each system

the link about root also helped alot 

does anyone know what command lists all current daemons running? like the ones in the background? and does anyone have any security suggestions?

---

### Post by taurus on 2005-11-11
If you want to see what is running on your system, use

ps -A

And for security, you can try firestarter...

---

### Post by earobinson on 2005-11-11
> ok, so i can dl a deb package but not a debian deb package, how will i be able to tell the difference?
The site will tell you if its a ubuntu deb, but some debian debs install just not all. I just usualy try it, if it works great if not i move on.

> does anyone know what command lists all current daemons running? like the ones in the background? and does anyone have any security suggestions?
gnome has a manager i think its gnome-system-manager
ps -a also works, ps -awx will list everything (type man ps for more info)
> -a      Display information about other users' processes as well as your own.
-x      Display information about processes without controlling terminals.
(the w is just a formating thing)

> i want to be able to burnm a cd install, that will install a set of packages automaticlly each time i install with the disk, that way i dont have to keep choosing packages over and over again on each system
You could do this, I would just write a little sh script with a bunch of apt-gets

---

### Post by spyke01 on 2005-11-11
awesome thanx guys, this has really helped alot ^^

---

### Post by taurus on 2005-11-11
Also, you may want to take a look in /var/log/dpkg.log for all the programs that you've upgraded or isntalled with apt-get...

---

