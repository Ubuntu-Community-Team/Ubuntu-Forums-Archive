---
title: "How do I import a user from an existing /home into a new install?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by mactece on 2009-05-12
Since I upgraded to Jaunty I have had trouble with my graphics (glx gears at 60fps with ati driver, 250 with opengl). So I created a new partition and installed a fresh copy of Jaunty, so I now I can dual boot between the two versions.

I keep my data on a separate /home partition. So I now have this setup:

partition 1 = Old Jaunty / (installed via upgrade from Intrepid)
partition 2 = New Jaunty / (fresh install from cd)
partition 3 = storage /home

When I installed New Jaunty I created a new user called David (that's me!) as part of the installation. When I boot into New Jaunty it has all my old settings. You can't tell the difference between New Jaunty and Old Jaunty.

THE QUESTION: how do I do this for the other 4 users of the machine, i.e. migrate them into New Jaunty. I'm worried that if I just create new users with the same names I'll overwrite all the data and settings.

Many thanks for your help,

David

PS my graphics now run at 1200 fps in glxgears on New Jaunty so that problem is (potentially) solved if I can complete the migration.

---

### Post by mactece on 2009-05-12
bump

---

### Post by lykwydchykyn on 2009-05-12
I'm not sure what GNOME's admin tool actually does, but usually such tools will not overwrite a home directory.  If you want to be safe, you can temporarily rename the home directories and then copy them back over the newly generated ones.

Biggest thing to be aware of is that filesystem permissions use UID (user id) numbers instead of actual names.  So if you don't create the users in the same order, you may have to change ownership of their home directories back, e.g.:
```

sudo chown -R someuser /home/someuser

```

Don't know if that helps.

---

### Post by jenkinbr on 2009-05-12
You could try backing up the previous users /home directories first by making copies.

Than you could add the users the normal way.

My story behind this is that whenever I upgrade, I always do a fresh install of ubuntu.  When I do this, I keep my home partition seperate and leave the formatting alone.  I always specify my username to be jenkinbr, and I have never had a problem with the Ubuntu Installer overwriting my settings.

I would assume the add user tool would behave in the same manner, as it is basically a frontend to the adduser terminal command.

---

### Post by mactece on 2009-05-15
thank-you and sorry I haven't replied before. back at the pc this weekend so will try your suggestions then and let you know what happens.

---

### Post by jenkinbr on 2009-05-30
> **mactece said:**
> thank-you and sorry I haven't replied before. back at the pc this weekend so will try your suggestions then and let you know what happens.
I would be assuming that this worked for you???

---

### Post by mcarni on 2009-06-18
Sorry for hijacking this thread but I am planning to do a new clean install on a computer with a separate /home and I am not sure I understood correctly.

As said I have a seprate /home partition with 4 users, I am thinking of installing ubuntu 9.04 (at the moment on this ocmputer there is ubuntu 8.04 installed)

my idea was to select "use existing /home" with the "no formatting" unchecked on the installation process, but I don't know what happens to the 4 existing users.

Will they be automatically detected in the new install? or will I have to re-add them?
If I re-add them with exactly the same name, will i automatically solve any permission problem?
or is it better to create 4 new users, copy as root the content and change the permissions accordingly with chown?

Thanks in advance for your help

M

---

### Post by lykwydchykyn on 2009-06-18
I think it would be helpful for you to understand basically what a user is.

A user is just a name assigned to a UID number in the /etc/passwd file.  All file permissions on the system are stored in the filesystem itself using UID numbers.

So right now your home directory has 4 home folders, most likely assigned to UIDs 1000, 10001, 1002, 1003.

When you set up a new system, you'll be creating users.  These users will be assigned UIDs starting with 1000 and going up incrementally.  

So to answer your questions:
 - It won't automatically detect or solve permission issues.
 - It will, by default, assign a new user "someuser" a home directory of /home/someuser.  If that directory exists, it will not overwrite the contents.
 - If your users are created in a different order, they will end up without permissions to their own home directories.  You can fix this with "sudo chown -R someuser /home/someuser"

---

### Post by jenkinbr on 2009-06-18
Readding them is what you will have to do, but permissions may be an issue.

You are goinging to want the output of the command 
```
cat /etc/passwd | rgrep 1[0-9][0-9][0-9]
```

What this looks like for me is
```
jenkinbr:x:1000:1000:Brian Jenkins,,,:/home/jenkinbr:/bin/bash
```

As you can see, there are several feilds here, seperated by a colon. We are going to be concerned with fields 1, 3, and 4, which are:
1: username (jenkinbr, in my case)
3: User ID (1000 in my case)
4: Group ID (1000 in my case)

So now, just run the command ```
cat /etc/passwd | rgrep 1[0-9][0-9][0-9]
``` and save the output somewhere.  Be sure to take a look at the entry with UserID:GroupID of 1000:1000, as this will need to be the initial user that you set up.

When you are ready to install, reboot, and load the liveCD.  Install as normal. When you get to the part about creating a user account, enter the details for the 1000:1000 user (This is important! If you put a different user here, permissions are going to be messed up on one of the systems!).  Continue with the installation.

When time to reboot, do so, and select the new OS on restart.

When the system loads, log in as the user you set up in the installation - none of the other users are there yet.

Now, I am assuming you are installing ubuntu, so I will post directions as such.  If you are using a different OS, you will need to find out how to translate these dirctions yourself or elsewhere.

So, Now go to System >> Adnimistration >> Users and Groups.  Unlock the applet.

Now enter the details for the second user on the list.  For example, if your second line reads
```
user2:x:1002:1002:User Two,,,:/home/user2:/bin/bash
```
Then you will need to enter user2 as the username and make sure it's home directory is /home/user2
Before clicking OK, click the advanced tab and set the User ID to what is on that line in the third spot, in this case '1002'

Do the rest of the users in a like manner.

Hope this helps, and please ask if you don't understand something.

---

### Post by jenkinbr on 2009-06-18
> **lykwydchykyn said:**
> I think it would be helpful for you to understand basically what a user is.

A user is just a name assigned to a UID number in the /etc/passwd file.  All file permissions on the system are stored in the filesystem itself using UID numbers.

So right now your home directory has 4 home folders, most likely assigned to UIDs 1000, 10001, 1002, 1003.

When you set up a new system, you'll be creating users.  These users will be assigned UIDs starting with 1000 and going up incrementally.  

So to answer your questions:
 - It won't automatically detect or solve permission issues.
 - It will, by default, assign a new user "someuser" a home directory of /home/someuser.  If that directory exists, it will not overwrite the contents.
 - If your users are created in a different order, they will end up without permissions to their own home directories.  You can fix this with "sudo chown -R someuser /home/someuser"
Will that last bit about chown not mess up the permissions on the other systems, if the /home partition is shared across multiple OS's?

chowning a home dir in one OS would mess the permissions up for the other OS.

---

### Post by lykwydchykyn on 2009-06-18
> **jenkinbr said:**
> Will that last bit about chown not mess up the permissions on the other systems, if the /home partition is shared across multiple OS's?

chowning a home dir in one OS would mess the permissions up for the other OS.

Yes, it will.

I was responding to mcarni who said he was going to do a clean install.

In the event of doing multiple linux installs on one machine, you have to synchronize the UIDs.  But that's a needless exercise for a single-install machine.

---

### Post by mcarni on 2009-06-18
guys,

you are just fantastic,

thank you very much, I think I have a much better understanding of what a user and user id and group id are.

it is not relevant in my case, because I will only do a clean install on my family's computer, but now you got me curious...
i tried to understand why chown is going to make a mess when multibooting, but I am not sure, could you give me some more detail?

thanks

M

---

### Post by jenkinbr on 2009-06-18
> **mcarni said:**
> guys,

you are just fantastic,

thank you very much, I think I have a much better understanding of what a user and user id and group id are.

it is not relevant in my case, because I will only do a clean install on my family's computer, but now you got me curious...
i tried to understand why chown is going to make a mess when multibooting, but I am not sure, could you give me some more detail?

thanks

M
Sure can.  Here's a hypothetical situation I made up, but it is entirely possible:

Suppose you had a user named johndoe on each system. He has a home directory located at /home/johndoe.  His userID is 1020 in Ubuntu 8.10, the orignating operating system. You decide you want to try out a new version of Ubuntu (Ubuntu 9.04), so you install to a different partition, and all goes well.  You have 20 other users, but you only want a few to have logins on this system, so you create the users and groups for them here.  Now on this freshly installed system, you accidentally set up johndoe with a UserID of 1005.  You then try logging johndoe in to ubuntu 9.04, but it won't work because the Ubuntu 9.04 johndoe (UID 1005) doesn't own /home/johndoe (which has permissions set for UID 1020, from the Ubuntu 8.10 install) So you log back in as the main user and run the command "sudo chown -R johndoe:johndoe /home/johndoe" This command will set permissions to /home/johndoe/* to be for UserID 1005.

Now, you reboot and try to log in as johndoe in Ubuntu 8.10, but now it doesn't work because johndoe (who has a UID of 1020 in ubuntu 8.10) no longer owns /home/johndoe (Instead, perhaps sherrydoe owns this directory, because she has a UID of 1005). Because of this, you log in as the main user and run 'sudo chown -R johndoe:johndoe /home/johndoe' again to revert the permissions back.  

Can you see how this creates a mess?

The best thing to do in this case would be to get a list of all the UID's from one system (the one that has the most users, in this case, Ubuntu 8.10) and set the UID and GID fields to be the same in Ubuntu 9.04.

Hope this helps clear things up a bit.

---

### Post by mcarni on 2009-06-18
> Hope this helps clear things up a bit.

it did indeed, very clear, thanks for the example.

I think I am ready to go, no more questions from this side.

THANKS
i really appreciate your help


M

---

### Post by jenkinbr on 2009-06-18
Glad to help :popcorn:

---

