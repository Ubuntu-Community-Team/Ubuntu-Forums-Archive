---
title: "cannot create user accounts: chown &quot;not permitted&quot;"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by nmsmith on 2006-01-28
I have only managed to boot into failsafe mode and the shell so far on my new install (hp nx9005 laptop). The install process twice asked me to create user accounts, but didn't seem to think I had typed passwords. In the end it seems no account was created.

So all I can do is login to the shell as root.

I tried to use [FONT="Courier New"]adduser test[/FONT] (no arguments) to create an account. But the [FONT="Courier New"]chown[/FONT] stage of the process claims [FONT="Courier New"][COLOR="DarkGreen"]Operation not permitted[/COLOR][/FONT]. 

I did manage to use [FONT="Courier New"]useradd test[/FONT] to make a user, and to do [FONT="Courier New"]mkdir /home/test[/FONT], but still I can't use [FONT="Courier New"]chown -R test:test /home/test[/FONT] to give the directory to the user. Thus I can't login to a desktop, and am chucked out after a couple of seconds.

One further issue (probably just a corollary of the above) is if I now log in as test to the shell and try [FONT="Courier New"]sudo[/FONT] I get told that test is not in the list of sudo enabled users. I'm sure this is just because test's account hasn't been properly created.

I had originally posted this in the laptop area, but have realised this is probably a better place for it.

Nick Smith

---

### Post by aysiu on 2006-01-29
Are you doing an expert install?

---

### Post by nmsmith on 2006-01-29
Nope: I did the standard install, but when prompted for new user accounts I couldn't enter the passwords.

Pre-reboot (CD still in drive) I typed but nothing appeared at the cursor (not even asterisks)

Post-reboot (CD out) I was prompted again, but this time I was told my passwords didn't match, no matter what I tried (even simple stuff e.g. "a1").

The only account it let me create was root, with the root password. That's what I have used to try to make the user accounts, but with little success, as detailed above.

~nick

---

### Post by teataster on 2006-03-10
I had a similar problem- have you tried this?

[http://www.ubuntuforums.org/showthread.php?t=123425&highlight=user+creation+problem](http://www.ubuntuforums.org/showthread.php?t=123425&highlight=user+creation+problem)

---

### Post by nmsmith on 2006-03-10
Thanks for the suggestion. I can see how FAT32 might be the root (oops) of the issue, but to my recollection I had specified ext3.

I was using the hp laptop special edition of Hoary. In the end I just decided to try the standard Breezy CD instead, and installed with no problems. I don't know what features I lost out to the laptop version, but I'm largely happy, and Ubuntu's power managment seems pretty good. I get around 1h50m at minimal loads, upwards if the computer is just sitting there, and that on an 18month old laptop.

Mind you I've changed the subject now. Thanks for the link though.

---

