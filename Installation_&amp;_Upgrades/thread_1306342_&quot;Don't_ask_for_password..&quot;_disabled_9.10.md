---
title: "&quot;Don't ask for password..&quot; disabled 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by kimbroBranch on 2009-10-30
Just upgraded to 9.10.

 In Users Settings 
"Don't ask for password on login" is grayed out (disabled) for both root and user.

Am I supposed to change my password to get this to work?  If so, do I manually change root password to the same?

---

### Post by kimbroBranch on 2009-10-30
Changed user password and option still disabled.

---

### Post by izzaboo on 2009-10-31
I did a fresh install of 9.10 on my mini 9.  I, too, have "Don't ask for password on login" greyed out.

It is also interesting to look at the User Privileges tab.  Although I am currently connected to a wireless network (and was previously connected to an ethernet network), that privilege is *not* checked.

So what's up with Users Settings?  Is it normal, for instance, that root has no privileges assigned?



**Update:** It looks like the place to "bypass" the login screen on login is in System->Administration->Login Screen

---

### Post by tonyyarusso on 2009-11-01
The Login Screen settings only allow you to set it to autologin for a particular account; they don't allow creation of accounts that don't need a password to login.

---

### Post by branstrom on 2009-11-20
It can be enabled manually by inserting:

[B]# Selected users can login locally without a password
auth sufficient pam_listfile.so item=user sense=allow file=/usr/local/etc/nopassusers onerr=fail[/B]

before the **@include common-auth** in **/etc/pam.d/gdm** and then creating /usr/local/etc/nopassusers along the lines of

```
user1
user2
anotheruser

```

Would like to see that checkbox enabled. Why is it there, if it's not enablable? :(

---

### Post by lavinog on 2009-11-20
> **branstrom said:**
> 
Would like to see that checkbox enabled. Why is it there, if it's not enablable? :(

GDM has been through a lot of changes. It might be a future setting for setting up restricted users.  Obviously it would be a bad move to have this setting available without addressing all of the security issues first.

---

### Post by clhp on 2009-12-01
This was an option on 9.04 installation and it makes sense for some users, myself among them.  I thought it over before accepting it and was very pleased with the option.

I think it should be made available again.

---

### Post by dasbooter on 2009-12-06
Good deed for the day....

Your probably looking for System->Administration->login screen automatically login as "your user here"

Have a nice day... and god help pulse audio, cd/dvd burning and ipod support for my beloved distro ;)

---

### Post by tigon5 on 2009-12-16
> **branstrom said:**
> It can be enabled manually by inserting:

[B]# Selected users can login locally without a password
auth sufficient pam_listfile.so item=user sense=allow file=/usr/local/etc/nopassusers onerr=fail[/B]

before the **@include common-auth** in **/etc/pam.d/gdm** and then creating /usr/local/etc/nopassusers along the lines of

```
user1
user2
anotheruser

```

Would like to see that checkbox enabled. Why is it there, if it's not enablable? :(


That's the one! Thanks!!!!!
Finally my wife can stop complaining about having to enter her password when in our living room! AND she gets her own desktop to pollute!

admin->login is for auto logging in after 30sec, not autologging on clicking which user - which btw seems to open the same security hole as this option would - so I don't understand why it's greyed out.  No matter this solution works for me.

---

