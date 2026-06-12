---
title: "Version 10.04 Menus Went Whacko.."
date: 2010-06-28
forum: Hardware
---

### Post by oldefoxx on 2010-06-28
Okay, I've got a nasty one.  Notebook has been fine for awhile with 10.04 on it, except it does not support HID, which is short for Human Interface Devices, with the USB ports.  Sort of an issue if you only have USB ports for attaching external devices, typical of notebooks, but an increasing issue in an age when new PCs are coming with no PS/2 ports for hooking up a mouse of keyboard.  You have to be able to use both with USB ports instead.

I got another post out there about this problem.  Still working on the problem myself.  A really difficult case can be dealing with a Netbook, such as the HP Mini 1000, which only offers two USB ports,  There you may need to go with a 4-port hub for adding attachments.  I was having some results in doing that, when Whacko! My drop down menus under Applications, Places, System, and trhe icons on the top right bar, only showed me a few choices like Help, Edit Menus, Lock Panel, and I think one or two others.

I tried Edit Menus, which looked fine for selection, but nothing changed  in what was displayed, no way to shut down normally, no way to enter into terminal mode the menu way, and no real idea of at least 3 things:

(1) What went wrong and how it caused this effect  Suspect it was some combo of keys pressed on the lower right side of keyboard, when a cord was caught there as the lid was closed to set it aside to go to dinner.

(2) A reinstall with the /home left intact does not fix the problem.  In fact, it stays exactly the same.  Seems obvious that there must me at least one configuration file under the user account that that persists unless you agree to a reformat of the partition that houses /home.

(3) An effort at Reset under Edit Menus appears to do nothing.  Now why isn't there a clearly defined way to restore an install to a state close to that obtained during and following the install?   I mean take some or all the config backup files and overwrite the new versions per our instructions?  Maybe allow us to try the old version first, then either stay with it or switch back to the new one.  And include the name of the files involved, so that they can become the matter of discussion on forums like this.

What is obvious at this point is that maintaining config files under user accounts lets each user have their own preference, and many of those preferences can carry forward with new installs replacing the old, as long as the structure of the config files remains intact.  But as I have found, not being able to obtain a clean reinstall while still keeping user accounts fully intact is a gapped area of concern.

---

### Post by quixote on 2010-06-30
Any time the gnome desktop manager loses its mind is a Bad Thing.  Your suggestion about having a rollback option is good and should have been implemented in Breezy! Fixing gdm issues is a can of worms, so take my suggestions with a grain of salt.

First, test whether the issue is really limited to the config files in /home/your-user. Open a terminal (Applications > Accessories > Terminal)  Create another user:```
sudo useradd newuser
``` 
then```
sudo passwd newuser
```the system will prompt you to enter a password and then repeat it.  

Then log out and log in as the new user you just created.  If the menus are fine, then it really is just the gdm config files.

Okay, this is where my knowledge breaks down because I'm not sure where gnome keeps the relevant files.  I thought there was a ".gdm" directory, but I see that there isn't.  I'm pretty sure the ones we need here are .gnome and .gnome2, but I'm not positive.  For now, let's pretend they are.  What I'd do next is this:

Login as your real user.  If the desktop is unusable, hit Alt-F2 to get a command line window. The following commands assume you're running them from your home directory.  You can check by typing "pwd" (without quotes) and making sure it returns "/home/your-user".  What you'll be doing is first rename your existing gnome dirs so you don't overwrite them just in case it turns out you need them for something, and then copy newuser's pristine gnome dirs to your own /home/your-user:
```
mv .gnome oldgnome
mv .gnome2 oldgnome2
cp /home/newuser/.gnome .gnome
cp /home/newuser/.gnome2 .gnome2
```

Then logout or reboot (commands are those words, reboot may need to be run as sudo. not sure)

Login as your real user and hope for the best.  If everything works and you want to get rid of the newuser the command is:```
sudo userdel newuser
```

---

### Post by oldefoxx on 2010-06-30
I appreciate the ideas you contributed.  I hope I don't have to try them, because for the moment I already into a series of reinstalls.

What I am hoping right now is that the effected install, which is on /dev/sda1, and I am currently working with /dev/sda2 and /dev/sda3. still has its /home largely intact and accessable.  The idea then would be to use something like cp -R to copy from that /home to the current /home.  But a feature I was hoping would be present with cp is not there:  It does not have an --EXCLUDE opion, where I could exclude all folders and files that begin with a period (.) or any that include this as part of the name: ,con.

There is a lot of programming might in Linux, and I am sure there is a way to script the process, but I've not ventured down that road before.  I can go and do just individual folders and/or files, but I don't want this to be a forever job.  Once I get what I consider most valuable from my user account on /dev/sda1, I may try your approach to see what benefit it gives,

And, in the mean time, some others may come forth with their own ideas as well.  So we will see.

I did a quick search with Google using the following expression:

ubuntu Or linux copy recursively exclude

And found several replies suggesting rsync be used , and one that mentioned tar and zip.  But then there were two that really seemed to get to the heart of it.  And this seems to be the winner:

cp -r [!.]* destination 

What is in the square brackets is an expression, and the ! stands for a logical NOT, the period stands for itself, and the trailing * means whatever follows.  So this would copy a file or folder which does not lead off with a period.  But now I have to consider how to expand the expression to include the exclusion of files that contain .con.   I will get back to that later.  I need to go clean up and see about a bite of food first.

You may think you know a bit of something, then you run into someone that really knows something, and their something seems so much more than your something, that you see no basis of comparison.

---

