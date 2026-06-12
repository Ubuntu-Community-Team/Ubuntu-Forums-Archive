---
title: "fstab - mounting dependent on user"
date: 2008-09-25
forum: General Help
---

### Post by shraap on 2008-09-25
Hey,

My first post so please be gentle! Relative n00b to Ubuntu, but long-time professional techie (almost all Windows-based).

I'm in the process of getting an Ubuntu desktop connected to an existing Windows 2003 Server domain, and almost everything's working beautifully, thanks in no small part to all the community documentation and these forums, which have provided many answers for me. So it's all authenticating correctly against the user database on the W2k3 server, printing fine, etc, etc.

I need to mount some shares from the server for my users, and this too has been done with no problem, largely using the very helpful doc here [https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

One of the shares is a public drive to which all users have access, and while experimenting, I set it up just for the systemadmin user, mounting it via fstab in their home area as 'P' so it's nice and obvious for a user unfamiliar with the new OS. Line from /etc/fstab below:

```
//rmt-sr-001/RMPublic /home/RMTRAINING/systemadmin/P cifs iocharset=utf8,credentials=/home/RMTRAINING/systemadmin/.smbcredentials,gid=10000 0 0 
```

This works perfectly. It fell over when I started trying to be clever (possibly too clever for my own good!). What I'd like to do is map the 'P' drive to every W2k3 domain user and put it in their home area so that it's easy to find. With a bit of educated guesswork, I tried using the $HOME environment variable, so that the /etc/fstab line now reads:

```
//rmt-sr-001/RMPublic $HOME/P cifs ... (rest of line the same)
```

This fails! If I do a manual **sudo mount -a** once the user is logged on, I get the error:

```
mount error: can not change directory into mount target $HOME/P
```

My questions are:

1. Can you use env variables in fstab?

2. Is this to do with boot/execution order, in that when fstab is executed, there isn't yet a logged on user? (The results of the sudo mount -a suggest this isn't the case, but I'd be interested to learn any more about boot/execution order)

3. Am I just going about this the wrong way, and there's a much better/easier way of doing what I'm attempting?

Clearly, I could just bite the bullet and mount the share in a consistent location for all users, but playing around with this has thrown up gaps in my knowledge and I'd be interested in any suggestions or enlightenment you could throw my way!

Cheers,
Chris

---

### Post by caljohnsmith on 2008-09-25
> **shraap said:**
> 
My questions are:

1. Can you use env variables in fstab?

2. Is this to do with boot/execution order, in that when fstab is executed, there isn't yet a logged on user? (The results of the sudo mount -a suggest this isn't the case, but I'd be interested to learn any more about boot/execution order)

3. Am I just going about this the wrong way, and there's a much better/easier way of doing what I'm attempting?

Clearly, I could just bite the bullet and mount the share in a consistent location for all users, but playing around with this has thrown up gaps in my knowledge and I'd be interested in any suggestions or enlightenment you could throw my way!

Cheers,
Chris
About question 1 and 2, I think the entries in the fstab file get mounted with the S20checkroot.sh script in the /etc/rcS.d directory on start up. The scripts in the rcS.d directory are run before any other run level scripts are executed, and this all happens long before the user ever logs in as you surmised. :) And about your idea of use $HOME in fstab, I've never tried something like that so I don't know if it is possible; but even if $HOME does have meaning in fstab, I believe it would point to /root and not the user's home, since the script to mount everything in fstab is executed as root (and happens long before the user logs in anyway).

One idea that would probably work is if you create a really short shell script "mount_P_drive.sh" for instance that mounts the P drive to the users /home like you want to (you could for sure use $HOME in that script), and then in your sudoers file you could give all users permission to run that script as root without a password. Then in each users ~/.config/autostart directory, make another short script that calls the "mount_P_drive.sh" script with sudo:
```
#!/bin/bash
sudo /path/to/mount_P_drive.sh
```
I believe the $HOME environmental variable will be preserved as the user's $HOME and not root's home in /root since you are using "sudo" to run the script and are not actually logged in as root. Thus whenever a user logs in, the script in their ~/.config/autostart will be executed and mount P drive to their $HOME. 

That's the general idea of how I might go about it, so if you want any more specifics, just let me know. Otherwise let me know what solution you come up with as I would be interested. :)

---

### Post by shraap on 2008-09-25
Thanks for the prompt resonse, cjs :)

Some really good advice, and it's given me some progress, but inevitably more questions!

Created a shell script for mapping for a single test user (00student1), as follows:

```
#!/bin/bash

# Check for existence of P folder, create if not
if [ ! -d ~/P ]
then
   mkdir ~/P
fi

# mount it up
mount.cifs //rmt-sr-001/RMPublic ~/P -o username=00student1,password=password,ro

```

This works fine - if I drop it in the user's home folder, double-click to execute, up pops the P mounted share on the desktop. Similarly a "umount.cifs P" script for removing.

What I'm having trouble with is getting it to run automatically: it appears to be an issue with this user being one of the Windows domain ones, not a local Ubuntu one. Creating the necessary ~/.config/autostart folder and dropping in the 'trigger' script doesn't do anything at all. I experimented with the broader principle of "will any startup apps work?" by using the System - Preferences - Sessions GUI to add an arbitrary startup program, and as soon as I close the dialog box, then reopen it, the entry has disappeared. It does not do this for local users.

Scratching my head a little now to be honest - though you've also taught me about the '~' shortcut, which makes my original question about $HOME irrelevant, since "~/P" works fine in the bash script :)

Any suggestions at all, anyone?

Oh, and just to be properly irritating, I've also got some further questions about making my script generic to any user - not passing in explicit username/password so it inherits the current user, but this will only work when it's run in the terminal so that the password can be retyped and passed in. If I double-click and just select "Run", it fails to mount the share. This seems unaffected by the addition of the user to the sudoers. Perhaps I messed up syntax here? Line from sudoers:

```
00student1 ALL=(ALL) NOPASSWD: /home/RMTRAINING/00student1/mount_P_drive.sh
```

Yrs curiously,
Chris

---

### Post by prshah on 2008-09-25
> **shraap said:**
>  What I'd like to do is map the 'P' drive to every W2k3 domain user and put it in their home area so that it's easy to find. 


By now, you know that $HOME in fstab is a no no... what you can do real easy is mount the public share at a fixed mount point, and then add a link called P to the user's home directory, which will point to the (static) public mount.

You can create the link either on logon (with an autostarted shell script) or when you first create the user.

---

### Post by Æthelflæd on 2009-05-27
I want to do the same thing!  I work at a school and I am sick of students/viruses but I can't change the world, so I am using Ubuntu for lab computers.  Every student has a Windows AD account, and I have no problems logging into Ubuntu using those accounts.  Currently when students log into a XP box their 'My Documents' folder is redirected to a server so they can save thier work, because the computers are all 'frozen'.  I want to map those existing folders on the fly when the students log into a Ubuntu machine, so that they can access their work.
 
I did craft a script that asks the user for their username and password and saves the input as variables.  Now I just need a way to mount those folders on login or with just one click.
 
Their folders are located at [\\server\students\%username%]("file://\\server\students\%username%")

---

