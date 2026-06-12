---
title: "newbie question: Problems with adding a new user"
date: 2008-07-23
forum: General Help
---

### Post by ConanCimmerian on 2008-07-23
I added a new account and set up a password. Let's call the new account "new".Then when I tried to log in, it said that the directory "home\new" does not exist and IIRC asked me if I wanted to log in as root or something to that effect. And I said no and just logged into my regular account. Should I just add a directory called "new" under "home" using my regular account?

Thanks in advance.

---

### Post by ad_267 on 2008-07-23
How did you add the user? From the command line or using the gui? Usually the directory should be created automatically.

Yeah you might as well just try adding the directory. In a terminal do:
```
sudo mkdir /home/new
sudo chown new /home/new
sudo chgrp new /home/new
```

---

### Post by ConanCimmerian on 2008-07-23
I used the command line. I'll give your commands a try, but what do the last two commands do?

Thanks

---

### Post by df6269 on 2008-07-23
Change directory owner and group of /home/new.

---

### Post by ConanCimmerian on 2008-07-23
Thanks for the explanation. I'll try those commands. But could you elaborate further as to what they do? The directory owner thing makes sense(although please explain that some more too), but what exactly does "group" mean?

---

### Post by ad_267 on 2008-07-23
Do a search for Linux file permissions. I came up with this: [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

Also enter "man chmod" and "man chgrp" for information on the commands.

---

### Post by ConanCimmerian on 2008-07-23
Thank you. btw, the commands you posted worked. My new directory exists.

But, for some reason, when I log in as the new user, my volume does not work. It says no control or gstreamer or something. It works fine with my original account. Any idea what that could be?

Also, I can't do sudo stuff under my new account. It says it isn't in the list. Would it be wise to add it, or should I just reserve that right for my main account? Ubuntu doesn't really have a "root" user and you have to enter a password every time you use sudo, so it should be fine if I enter the new user in the sudo list right? What do you recommend? btw, I'll be the only person on the other account too.

---

### Post by ad_267 on 2008-07-24
I think because you used the command line to add a new user it didn't automatically add the user to different groups required.

In your account go to System - Administration - Users and Groups. Click Unlock and enter your password. Click on the "new" user and select properties. Go to user privileges and tick the stuff you want the user to be able to do, eg "Use audio devices." This will add the user to different groups that are allowed to do these things.

If you want to be able to use sudo on the new account, you need to tick "Administer the system." It would be fine to have more than one user who can use sudo.

You can also add a user to a group using the command line. If you enter "groups" you can see what groups you are in. You can use "sudo adduser user_name group_name" to add a user to a group.

Eg, I can do this:
```
$ groups
adam adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
$ sudo adduser new adm
$ sudo adduser new dialout
$ sudo adduser new cdrom
$ sudo adduser new floppy
$ sudo adduser new audio
$ sudo adduser new dip
$ sudo adduser new video
$ sudo adduser new plugdev
$ sudo adduser new fuse
$ sudo adduser new lpadmin
$ sudo adduser new admin

```
Then the new user can do everything that I can.

---

### Post by ConanCimmerian on 2008-07-24
Thanks. It makes a lot more sense now. It would have been more efficient to use the GUI. I didn't know how to use the GUI, but I probably would have used the command line anyway because I wanted to learn the commands. But now I know how to do both the *right way*(ie. that I need to add new users to groups if I want full functionality). 

When I was looking at the list of users in the GUI, I noticed root was there, and when I clicked properties I saw it had a password associated with it. First of all, I didn't think you could log in as root on Ubuntu and you could only administrate using "sudo". It looks like I was wrong on that. Secondly, the password for root that was entered, is that the same password I've been using for my primary account all this time? If I entered a password for "root" specifically and I cannot remember it, can I still change that password since I do have admin privileges on my main account(and now my secondary account too)?

---

### Post by ad_267 on 2008-07-24
I think this explains things well. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You can enable the root account and give it a password but by default there is no root password and the root account is disabled.

If you forget your password or accidentally delete your admin privileges you can always log in as root by restarting and selecting recovery mode.

---

### Post by ConanCimmerian on 2008-07-24
Thanks ad.

---

