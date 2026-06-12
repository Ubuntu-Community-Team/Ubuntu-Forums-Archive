---
title: "[SOLVED] your home directory is listed as /home/brandon but does not appear to exist"
date: 2008-10-17
forum: General Help
---

### Post by Brandon81 on 2008-10-17
I have absolutely no idea what I could have done last night to my Ubuntu desktop to cause this issue. It appears to be a permissions issue, but so far everything I've tried on other forums regarding this error has not worked. 

I get the error: your home directory is listed as /home/brandon/ but does not appear to exist. 

Then I get the "User's $HOME/.dmrc file is being ignored" error and it will not boot into the desktop. The only thing I can boot into is the failsafe terminal. 

I've tried doing mkdir /home/brandon and it says that the file exists, so I know the folder is still there. 

I've tried sudo chmod 700 /home/brandon and nothing appears to happen. 

I was told in the failsafe terminal to type /home, but it says that that's a folder and doesn't do anything.

The last thing I've done in the terminal is

sudo chmod 644 /home/brandon/.dmrc
(nothing happens, goes to next line)
sudo chmod 700 /home/brandon
(nothing happens, goes to next line)
And rebooted. 

Same error. Please help.

---

### Post by phidia on 2008-10-17
Try > sudo chown username /home/username

Obviously in place of username  
insert your actual username.

---

### Post by Brandon81 on 2008-10-17
Okay, this is what the terminal looks like:
brandon@brandon-desktop:/$ sudo chown brandon /home/brandon
[sudo] password for brandon:
brandon@brandon-desktop:/$

Should it say anything indicating it worked or didn't work?

Do I need to reboot the whole computer after that or just exit and try again? Exiting and then choosing (Run XClient Script session) which is what it was normally on gives the same error unfortunately. I am trying to reboot now. 

Thanks for the help. Anything else I can try? I just finally got my desktop all set up the way I like it. It wouldn't be a tragedy to have to make a new user and start over, I don't have anything too important on there, but it would be a pretty big PITA because everything I've downloaded and done is in some subdirectory of /home/brandon.

EDIT: It may have something to do with proftp? I have been trying to get an FTP server going now for linux as I had one running on my XP OS before, and I messed with a couple things in gproftp, but I didn't understand it or get it to work. Maybe that messed it up? I don't know. 

Rebooting gave same error.

Tried the following:
sudo chown brandon /home/brandon/.dmrc
sudo chown brandon /home/brandon
sudo chmod 644 /home/brandon/.dmrc
sudo chmod 700 /home/brandon
reboot.

Still no go. Same error

---

### Post by Brandon81 on 2008-10-17
I don't know if this helps but from another forum info I typed this:

df -hT
And received this:
(I am typing all of this obviously so bear with me, I am leaving out the unnecessary drive info. The disk is not even close to being full) 

Filesystem   Type   Size   Used   Avail   Use%  Mounted on
/dev/sdf1    ext3                               /
varrun       tmpfs                              /var/run
varlock      "                                  /var/lock
udev         "                                  /dev
devshm       "                                  /dev/shm
ile          "                                  /lib/module/2.6.24-19-generic/volatile
then my other harddrives in the computer...

Should /home be there?

It's ignoring spacing for formatting.... All the "'s are just representing tmpfs under type.

---

### Post by dave.com on 2008-10-17
I believe the correct syntax for issuing the chown command is: ```
chown brandon:brandon /home/brandon/.dmrc
```
of course use sudo in front of that line and feel free to correct me.

---

### Post by Brandon81 on 2008-10-17
Thanks. 

Tried that. Nothing appeared to happen in the terminal. Exited and same error unfortunately. 
sudo chown brandon:brandon /home/brandon
sudo chown brandon:brandon /home/brandon/.dmrc

I can't imagine wtf is going on here... 

Thanks for the help, but still lookin for a fix.

---

### Post by dave.com on 2008-10-17
Well, you still have to set the permissions now that you own your home. That's the next thing you have to do now I imagine. Feel free etc ;p

---

### Post by Brandon81 on 2008-10-17
How can I tell what the current permissions are?

Would this be easier to do from the live cd?

EDIT: I am a relatively new user to Ubuntu and linux in general. Please if you don't mind, give me step by step instructions from the terminal. 

It starts at 
brandon@brandon-desktop:/$

Thank you so much.

EDIT #2: I just ran this from the terminal:
sudo chown brandon:brandon /home/brandon
sudo chown brandon:brandon /home/brandon/.dmrc
sudo chmod 644 /home/brandon/.dmrc
sudo chmod 700 /home/brandon

And same error. LHome user /home/brandon does not appear to exist, then the /dmrc error. Then it says "your session only lasted less then 10 seconds," blah blah and then goes back to the main Ubuntu sign in screen.

---

### Post by dave.com on 2008-10-17
Sry for dbl post... Also double check that the partition device is mounted!

```
brandon@brandon-desktop:/$ sudo su -
brandon@brandon-desktop:/# ls -la /home
brandon@brandon-desktop:/#chmod 644 /home/brandon/.dmrc
```

---

### Post by Kralizec on 2008-10-17
If you're receiving no message after the chown commands, that indicates they have executed successfully. chown only yields a message if an error occurs. Same with chmod.

---

### Post by Brandon81 on 2008-10-17
> **Kralizec said:**
> If you're receiving no message after the chown commands, that indicates they have executed successfully. chown only yields a message if an error occurs. Same with chmod.

That's what I figured because I did misspell the folder name once and received an error. 

> ```
brandon@brandon-desktop:/$ sudo su -
brandon@brandon-desktop:/# ls -la /home
brandon@brandon-desktop:/#chmod 644 /home/brandon/.dmrc
```

root@brandon-desktop:~# ls -la /home
Total:20
drwx------ 5 root root 4096 2008-10-17 12:07
drwxr-xr-x 21 root root 4096 2008-10-16 00:24 .
drwx------ 58 brandon brandon 4096 2008-10-17 11:57 brandon
drwxr-xr-x 2 root nogroup 4096 2008-10-16 23:57 ftp
drwxr-xr-x 2 test test 4096 2008-10-17 12:07 test

I tried to make a test user in the terminal from another thread somewhere but it didn't indicate a password or how to make one, so I never was able to log in with test. Also I think the problem may be coming from me messing with setting up an FTP server if that helps.

Thanks so much for the help guys! I really am enjoying this OS, even troubleshooting it has been somewhat of a blast because I'm learning it. This particular error is kind of getting frustrating because I'm concerned I'm going to have to reinstall and that would take a while to re-set up the way I had it because I did so much that I'm not that familiar with, I'd have to reblunder through a lot of it again. I would really like to fix this and be able to log back in to my own user ID. 

Thanks again.

EDIT: BTW I tried the chmod from the root. No error upon running the command, but I still can't get back into my desktop.

---

### Post by Brandon81 on 2008-10-17
Any ideas from anyone?

I am at a complete loss here. What does the permission list thing I just posted tell you? I have no idea how to read that unfortunately to know what's what. 

I know others have had similar problems and that they've been fixed by doing what I'm doing. What could be wrong? Is there any way to unmount the FTP service that's booting up? Maybe that's the answer? Is there a configuration file I can load that will allow me to undo the changes made by the FTP service? I am kind of lost here.

EDIT: And is there any way to successfully add a new user? I added test, but I have no idea what the password would be or how to set one. If I could load into the desktop with a different user, maybe I can see what's going on, or uninstall the FTP software?

EDIT #2:

Don't know if this helps but: 
```
sudo fdisk -l /dev/sdf 
device boot     start   end    blocks     ID    System
/dev/sdf1           1   18890  151733893+ 83    Linux
/dev/sdf2       18891   19457    4554427+  5    Extended
/dev/sdf5       18891   19457    4554396  82    Linux swap/Solaris
```

---

### Post by Brandon81 on 2008-10-17
Solved!
finally.

Followed the steps here:

[http://ubuntuforums.org/archive/index.php/t-524986.html](http://ubuntuforums.org/archive/index.php/t-524986.html)

sudo chmod -R a-x+X /home/brandon/*
sudo chown root:root /home

Success!

Thanks to all who helped and offered suggestions.

---

### Post by bconover on 2008-10-17
Pfft, wish I'd known that when I got this error a while back. I reinstalled Ubuntu! ](*,)

---

### Post by laceration on 2008-11-28
Brandon81, I solved my own problem once too in a thread!  What you figured out helped me too, thanks for sending me right direction.

---

