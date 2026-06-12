---
title: "Home Folder Issues"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by salvador dali on 2009-04-24
Hey,

Just installed 9.04 and I'm having some issues. I was carrying over my old home partition with the new root install. During installation I designated my old home partition as the new /home but told the installer not to format it (obviously). Post install I click on my home folder and find that its a new home folder, completely blank, coexisting with my old one that I don't have permission to access. I tried user the System Settings-Advanced-User/Groups options to change my home folder back to my old one but that failed and the permission issue stayed the same (my pics were locked and belonged to User #1000?). So I restarted and then Ubuntu refused to read my $HOME because it said that it wasn't mine and that $HOME shouldn't allow access to other users. Consequently I was left with a black screen. Any help? Thanks!

---

### Post by pbpersson on 2009-04-24
If yours is a permissions problem, I would not be going into users and groups and changing it there.....well, you saw how that worked.

You will need to get into recovery mode which will give you root access, then go to your /home partition and fix the permissions using command-line stuff which I would need to research.

There might be people here who would know this right off the top of their heads.

Once you get the permissions fixed on both those folders and can reboot and get a GUI, then you can change the configuration in users and groups

---

### Post by sloppyc on 2009-04-24
What is your user#?

I ran into a similar problem running Fedora alongside openSUSE (Fedora's user IDs start at 500 instead of the more common 1000).  The user and group IDs have to match, or you won't have access to your /home folders.

You can edit /etc/passwd and /etc/group (sudo nano /etc/passwd and sudo nano /etc/groups) to change your user ID and group ID respectively (I don't htink user/group IDs can be changed via the users GUI) so that it all matches up.  You may need to run chown after this, I'm not sure if that would just be redundant, though.

---

### Post by salvador dali on 2009-04-25
[http://ubuntuforums.org/showthread.php?t=1043999&highlight=home+directory+issues](http://ubuntuforums.org/showthread.php?t=1043999&highlight=home+directory+issues)

So I followed this guide, specifically the section that suggested user the GRUB menu to log in as root. I altered my /etc/passwd and saved a backup. I changed the login and user name and the user # from 1001 to 1000. Then I saved the changes and rebooted. I got to a login screen (yay!) but then it wouldn't let me log in under any username that the machine had previously had. Any more advice? Thanks!

---

### Post by sloppyc on 2009-04-25
Did you edit /etc/groups as well as /etc/passwd?  If your user and group IDs are not consistent, you'll have problems.

---

### Post by salvador dali on 2009-04-25
I followed your advice and changed my id's in both etc/groups and etc/passwd and it still doesn't work. I'm contemplating a fresh install.

---

### Post by adm1968 on 2009-04-25
[FONT="Georgia"]Exactly the same problem here!
Can anybody help?:confused:

BTW, this issue bugged me also when upgrading to 8.10[/FONT]

---

### Post by sloppyc on 2009-04-25
> **salvador dali said:**
> I followed your advice and changed my id's in both etc/groups and etc/passwd and it still doesn't work. I'm contemplating a fresh install.

You may need to run chown, then.
sudo chown -hR user:group /home/user

---

### Post by adm1968 on 2009-04-25
[FONT="Georgia"]My apologies
I have just recalled I could solve the problem using some advice:
[http://ubuntuforums.org/showthread.php?t=1005794](http://ubuntuforums.org/showthread.php?t=1005794)

I have applied these instructions again, and it does work 
Good luck![/FONT]

---

### Post by salvador dali on 2009-04-28
Thanks for the help everyone. I followed the thread and the advice given here and it worked. Thank you all.

---

