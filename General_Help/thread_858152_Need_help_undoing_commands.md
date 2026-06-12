---
title: "Need help undoing commands"
date: 2008-07-13
forum: General Help
---

### Post by ardathwest on 2008-07-13
So I was trying to make a user account for guests that didn't require a password for login; and came across a site that provided me with instructions on how to do it. I made a new user account, named it guests, and typed the following in terminal:

> 
sudo passwd -d guest
sudo sed -i 's/#PasswordRequired=false/PasswordRequired=false/' /etc/gdm/gdm.conf
sudo sed -i 's/nullok_secure/nullok/' /etc/pam.d/common-auth


It didn't work. And now I wish to undo these commands. Is there any way for me to do it? Please help. Thanks.

---

### Post by Vishal Agarwal on 2008-07-13
Go to the System-> administration-> login window.

There are many options which will help u in solving your problem.

But I don't know how to undo the other commands.

---

### Post by spiderbatdad on 2008-07-13
the first command deletes the password for the account named guest...if you have a user named guest. If you wish to set a password for a user named guest:
```
sudo passwd guest
```you will then be asked to type a password...this will create a new password for that account.

The second two command are substitution command using sed. The commands edit two files, the first:
/etc/gdm/gdm.conf
the second:
/etc/pam.d/common-auth

To re-edit the files, just swap around the first and second parts of the substitution: ie, ```
sudo sed -i 's/PasswordRequired=false/#PasswordRequired=false/' /etc/gdm/gdm.conf
sudo sed -i 's/nullok/nullok_secure/' /etc/pam.d/common-auth 
```

See, it says substitute "PasswordRequired=false with #PasswordRequired=false in the file /etc/gdm/gdm.conf" Effectively, this means to comment the line "#" so it it not read by the program. Similar for the final command.

---

### Post by ardathwest on 2008-07-13
Thank you for the quick replies. I typed in those 'switched' commands like you said. I hope my tinkering with the terminal didn't do any permanent damage to my system. I'll be more careful next time. Again, thanks.

---

### Post by spiderbatdad on 2008-07-13
I'm sure your system is fine. The best part of using linux in tinkering with files, so don't be afraid.
However, if this is a production type  machine, or you do financial transactions and such, then I would recommend learning as much as you can stand about security, and avoid making changes to files that weaken security...like no password logins...
You can view the contents of the above files with the "cat" command, to verify your changes. Also the system should have backed up those files when  they were changed.

To see /etc/gdm/gdm.conf type in the terminal:
```
cat /etc/gdm/gdm.conf
```

You should find: ```
# "PASSREQ=[YES|NO]"
#PasswordRequired=false

```  about 36 lines down.

---

### Post by ardathwest on 2008-07-13
Found those lines. Not entirely sure what they mean, but I will trust that everything is fine. Thank you for your help.

Oh and btw, my computer is just for home use. Save for my music files and some documents, there isn't much in terms of sensitive files.

---

