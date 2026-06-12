---
title: "Forgot Password to login..."
date: 2008-08-30
forum: General Help
---

### Post by J.Byram on 2008-08-30
...maybe the login name as well.  I haven't used my Ubuntu partition in a while and I decided to play around with it tonight and low and behold...no dice.  My brain has forgotten the magic digits to get in.  Anybody have any suggestions?

Is there a default, hidden set (like an Admin account in XP:SafeMode?)

I have to stop using Windows so often.

Thanks
-John

---

### Post by Mister.Vash on 2008-08-31
Here are the instructions on reseting the password
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

If you forgot the logon name, you can ```
cat /etc/passwd
``` and search for the line with the user id 1000.  This will be the user registered during installation.

look for a line similar to this
*username*:x:**1000**:1000:*username*,,,:/home/username:/bin/bash

---

### Post by mb_webguy on 2008-08-31
Unless you've changed the Grub menu, there should be an option to start Ubuntu in recovery mode.  This will drop you into a shell prompt as root.  From here, you can figure out your username easily enough by looking for your home directory ("ls /home"), and then change your password ("passwd <username>").

---

### Post by mc4man on 2008-08-31
Just tried it to see and it's surprising how insecure ubuntu (or linux ) is. Not only does the recovery boot to root shell allow you to change the first user's (admin) password it also gives you the user name at the prompt. 

Sorta begs the question of what's the point of a password in the first place. (particularly in regards to first user with administrative rights

---

### Post by Oldsoldier2003 on 2008-08-31
> **mc4man said:**
> Just tried it to see and it's surprising how insecure ubuntu (or linux ) is. Not only does the recovery boot to root shell allow you to change the first user's (admin) password it also gives you the user name at the prompt. 

Sorta begs the question of what's the point of a password in the first place. (particularly in regards to first user with administrative rights

Actually any os where you have physical access to the computer is "insecure". BTW I can do the same thing to a windows box with physical access and a couple minutes.

---

### Post by mc4man on 2008-08-31
> Actually any os ...
I realize that, though I think in the case of some other Os's it may be a 'tad' more difficult than having it 'laid out in front of you'. Personally I'd be ok with if you forget the first user's password you lose the install.

It makes no difference to me, I was just a little surprised.

---

### Post by mb_webguy on 2008-08-31
You can password protect Grub.  

If I forgot my login password like the OP, I'd be slightly more inconvenienced, since my hashed Grub password for recovery mode is the same as my login password.

Of course, all I'd have to do is boot from a LiveCD, remove the Grub password, and log in using recovery mode...

And if password-protecting Grub isn't enough, you can password  protect your BIOS so your computer won't even POST without it.  Of course, even that can be bypassed if someone knows what they're doing.

No computer is ever *completely* secure, but no computer which is physically accessible is *ever* secure.

---

### Post by WJRobbins on 2009-01-26
> **Mister.Vash said:**
> Here are the instructions on reseting the password
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

If you forgot the logon name, you can ```
cat /etc/passwd
``` and search for the line with the user id 1000.  This will be the user registered during installation.

look for a line similar to this
*username*:x:**1000**:1000:*username*,,,:/home/username:/bin/bash


Saved my bacon!  Thanks!  :)

---

