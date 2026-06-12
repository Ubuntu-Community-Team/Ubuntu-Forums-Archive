---
title: "How stupid am I ?????"
date: 2008-09-17
forum: General Help
---

### Post by bork21 on 2008-09-17
I was told to leave the username and password blank when I did the set up, by my students. So now as I try to login to my computer it asks me for this info that I left blank... So I guess what I'm asking is how do I get back to the set up page so I can do it correctly....Thanks

---

### Post by anotherdisciple on 2008-09-17
Are you talking about when you installed ubuntu?  I didn't know you could even do that?

---

### Post by EmanresuusernamE on 2008-09-17
Could you be a little more specific?  Is this for an Ubuntu install?  Cause it won't let you have a blank username and password when installing Ubuntu.

---

### Post by directcharitycontribution on 2008-09-17
same here, its gonna ask u phone home. whatever prolife u r on there must be a root profile somewhere

---

### Post by anotherdisciple on 2008-09-17
> **directcharitycontribution said:**
> same here, its gonna ask u phone home. whatever prolife u r on there must be a root profile somewhere

Ummm... is anyone else confused about this or is it just me?

---

### Post by russlar on 2008-09-17
> How stupid am I ?????

not as much as this guy:

> **directcharitycontribution said:**
> same here, its gonna ask u phone home. whatever prolife u r on there must be a root profile somewhere

---

### Post by philinux on 2008-09-17
+1 :lolflag:

---

### Post by Casper Hansen on 2008-09-17
+2 :lolflag:

---

### Post by Nameless_one on 2008-09-17
If nothing works, you can always repeat the installation and not leave the fields blank.

---

### Post by bork21 on 2008-09-17
Okay if I did type in a password and a username...I always use the same thing and I must have entered a typo, because I tried that and no go...So what I'm really looking for is that original page where I would have put the username and the password. How do I get there from the page that just wants my username 1st and then my password. Yes this is an ubuntu installation, and my very 1st time on a pc....Thanks bork21

---

### Post by mali2297 on 2008-09-17
Check here:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by EmanresuusernamE on 2008-09-17
Sounds like it would be best for you to reinstall Ubutnu then.  If you don't know the administrative password, you're not going to be able to change it at all.  No root access in Linux means no ability to change key files.  Backup anything you want to keep before you reinstall.  Use a LiveCD if you can't get access to your data through your current installation.

---

### Post by bork21 on 2008-09-17
Hey thanks mali2297...I did all that and it still tells me that I have an incorrect username or password, and I've got it all right because when I typed in ls /username  that which I use all the time came up so I continued to change the password, and then exit, and then it didn't work.... 
I wiped this computer clean when I installed ubuntu, so there is nothing on it to worry about.... How about if I start from the beginning again.....
How do I do that.... I have ubuntu on a disc that is in the computer at this time. How do I reinstall it, and please remember, I've never had anything but a Mac so I know nothing about the "F button" commands..... Thanks for all of your help so far...bork21

---

### Post by mali2297 on 2008-09-17
Reboot the computer with the installation CD inserted. Do you reach an Ubuntu menu with the option *Install Ubuntu*? Select that and you will be lead through a guided installation. 

Since there is not any other operating system on the computer, just choose to use the entire disk when the partitioner comes up.

---

### Post by bork21 on 2008-09-17
If I do that it just directs me to Ubuntu and it wants to know my username... How do I reboot from the disc in the computer...on a Mac you hold down the "C" key

---

### Post by CleverJake on 2008-09-17
Are you usign an alternative install disc?
Because you shouldnt have to uise any of the F keys on teh GUIed verison

either way, youre going to have to go into your BIOs settings and make sure the boot order is set to boot to disc first

how you do this is different depening on what motherboard you ahve, but no worries, all you have to do is pay attention when you boot upyour computer. There should be a screen with an icon in teh middle that is a brad of some kind, like compaq or dell, or whoever made the PC, and someone on that screen should be a small lsit of options like , hit ESC to escape, F11 for settings, etc
you want to get into the settings menu, or something called something similar,and once inside of that, look for a section withthe words boot order (or, again, soemthing similar) and move your disc drive to the top

taht should let you get into the install screen

---

### Post by mc4man on 2008-09-17
If you boot up to the recovery mode, then choose root shell prompt, in the [I]prompt will be the user name.
[/I]
note it and then type in > passwd
Enter a new password and note that also

then enter exit, press enter and then Esc. button to boot up normally

---

### Post by bork21 on 2008-09-17
Okay all of you THANKS so much with your help I now know a little bit about navigating a PC and I've reinstalled from the disc... I wrote everything down and I'm waiting to try again.... This is a fabulous board with many very friendly people watching. I'm sure I'll be back with other questions..... Thanks again

---

### Post by mc4man on 2008-09-17
After a bunch of reboots on some various installs to figure this one out (I think)
You can only _reset the password from a root shell once_ without then having to enter the password to gain access to the root shell

The exact procedure (for a one time reset without password

Boot to grub
Use down arrow button to choose (recovery mode), press enter
After a while you'll come to recovery menu, use arrow button to choose 'Drop to a root shell"
There should be a root prompt at bottom of screen showing user name.
If so type in passwd, press enter
Enter a new password and note user name To escape type exit, press enter and the  Ecs button.

If you see instead of a root prompt this
It
Give root password for mantenance
(or type control_D to continue): 

Then you'll need  the password to continue

Every install I have would drop immediately to a root shell (no password needed

After changing the password once, _then that no longer happens_, a password is needed to get to the prompt from then on


In other words you get 1 free shot at forgetting both the user name and password to acquire the username and reset the password (and so does anybody else who boots up your machine

---

### Post by mb_webguy on 2008-09-17
Boot into recovery mode, then look in the /home directory.  The only contents should be a directory with the same name as your username.

Now change your password with "passwd <username>", where <username> is the username of the account whose password you want to change.

---

