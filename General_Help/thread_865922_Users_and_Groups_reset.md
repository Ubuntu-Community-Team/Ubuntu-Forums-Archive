---
title: "Users and Groups reset"
date: 2008-07-21
forum: General Help
---

### Post by OsamaK on 2008-07-21
Hello! I used Ubuntu on a desktop computer, I changed my Users and Groups settings to set my log-in nickname *"osama"* as power as *"root"*. I think I didn't do it well, my log-in name "osama"  became unable to install programs, check updates or use *sudo*. I cannot even edit "User and Groups" again.

I wanna to reset my Users and Groups to the default setting, then I'll be able to (e.g. use sudo..) after inserting password for 'osama'.

---

### Post by Vishal Agarwal on 2008-07-21
what are the steps u followed ? need to know to solve your problem.

---

### Post by OsamaK on 2008-07-21
**Steps:**
System > Administration > Users and Groups > Unlock -> Selecting my login name -> Properties -> User Privileges.

But I'm not sure which check-boxes that I changed.

---

### Post by dracayr on 2008-07-21
So you unlocked the root user? In that case:
in the command line execute:

su

you should then be asked for the administrator password (NOT your password), and then you are root. execute 

users-admin

and you are able to change your settings. If you don't know your root password, boot in recovery mode, and select the resume option. Then you can also administrate the system.

dracayr

---

### Post by OsamaK on 2008-07-21
Hum.. What is an admin password? Ubuntu didn't ask me ever to set that password. When I insert mine, the ourput is the flowing:
[I]osama@osama-desktop:~$ su
Password: 
su: Authentication failure[/I]

---

### Post by sisco311 on 2008-07-21
Reboot in recovery mode and add your user
to the admin group from the root shell:
```
addgroup *osama *admin
exit
```boot in normal mode and add your user to the 
other groups from Users and Groups.

---

### Post by OsamaK on 2008-07-21
Great sisco311! Now I can edit Users and Groups, But which options should I use to use the default settings? for example, I still cannot use *su* command. This is my User Privileges, if that helps:

[IMG]http://osamakm.googlepages.com/Screenshot-AccountosamaProperties.png[/IMG]

Update: I can use check update, install programs, use sudo, etc.. So, I think alright. Thank you all!

---

### Post by sisco311 on 2008-07-21
run this from a terminal to add your user to the *default *groups:
```
sudo usermod -a -G osama,adm,dialout,cdrom,floppy,audio,dip,src,video,plugdev,fuse,lpadmin,admin osama
```(the GUI is confusing me:lolflag:)


su is for login as root.
In ubuntu the root account is disabled by default.
You can use *sudo command* to run a command as root.
Or *sudo -i* and *sudo -s* to start a root shell.
More info here:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by OsamaK on 2008-07-24
Another thank you :)

---

