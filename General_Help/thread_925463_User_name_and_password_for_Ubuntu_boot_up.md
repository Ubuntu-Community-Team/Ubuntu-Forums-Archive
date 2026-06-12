---
title: "User name and password for Ubuntu boot up?"
date: 2008-09-20
forum: General Help
---

### Post by iStack245 on 2008-09-20
Well I finally got Ubuntu to start up, but now I need a username and password to log on. I never set one of those O_o:mad:

---

### Post by iStack245 on 2008-09-20
Help please?

---

### Post by Patrick793 on 2008-09-20
Are you sure you just don't remember the login information? You need to setup a username and password when installing. It's one of the required steps in the installer.

---

### Post by iStack245 on 2008-09-20
Even if I did set it up, I set it up the same way everytime 

didnt work

---

### Post by stickmangumby on 2008-09-20
Did you try turning caps-lock on or off? 

Was your username made up of all lowercase letters? Did you enter it that way to log it?

What version of Ubuntu have you installed?

---

### Post by jiggygent on 2008-09-20
Maybe this will help...

[http://linux.about.com/od/linux101/l/blnewbie3_2_3.htm](http://linux.about.com/od/linux101/l/blnewbie3_2_3.htm)

---

### Post by mick222 on 2008-09-20
this page has screenshots to help reset your password same as above only easier to follow for a newbie.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
stick with linux it's worth it in the long run.
 Bye the way have you installed linux or are you running the live disk or wubi.

---

### Post by Sef on 2008-09-20
1) Please don't bump your thread unless 24 hours have gone by.   We are all volunteers here and it takes time to answer forum posts - sometimes fast, sometimes slow.

2) > Well I finally got Ubuntu to start up, but now I need a username and password to log on. I never set one of those O_o:mad:


Have you installed Ubuntu?  If you have, you should have been asked to set a name and password.

Or are you running the Live CD?  If you are no password is needed to run it.

3) In the Live CD, instead of booting or installing go down to check disk for errors and see if it gives you any.

---

### Post by mc4man on 2008-09-20
what's somewhat interesting about the 'recovery mode' - recovery menu is when you drop to the root shell prompt you are *given the user name in the prompt*. So basically you can 'recover' the user name and reset the password right there. (and technically so can anybody else

Note that this is a 'one time' thing, once you've changed the password at that prompt you can no *longer access the root shell prompt without the password.*
So if you ever change your password, don't forget it.

edit: so in other words if the the password has never been reset anyone can boot to the recovery menu, drop to the root prompt, acquire the main user name, reset the password and lock out use of the root shell prompt (without knowing the new password

---

### Post by mb_webguy on 2008-09-20
> **mc4man said:**
> what's somewhat interesting about the 'recovery mode' - recovery menu is when you drop to the root shell prompt you are *given the user name in the prompt*. So basically you can 'recover' the user name and reset the password right there. (and technically so can anybody else

Note that this is a 'one time' thing, once you've changed the password at that prompt you can no *longer access the root shell prompt without the password.*
So if you ever change your password, don't forget it.

edit: so in other words if the the password has never been reset anyone can boot to the recovery menu, drop to the root prompt, acquire the main user name, reset the password and lock out use of the root shell prompt (without knowing the new password

You shouldn't set a password for root.  That's [why we have sudo]("https://help.ubuntu.com/community/RootSudo") in the first place.  You can easily [password-protect the recovery option using Grub]("https://help.ubuntu.com/community/GrubHowto#Security").  You can even use an md5 encrypted password, if you want.

---

### Post by mc4man on 2008-09-21
> You shouldn't set a password for root. That's why we have sudo in the first place. You can easily password-protect the recovery option using Grub. You can even use an md5 encrypted password, if you want. 

I'm not referring to that at all,  (I don't think).  I was only referring to changing the main (*first user's login* ) password, the topic of this post. Nothing else.

And to that I was simply commenting on the results of the typical method to change your (*first user*) password (ala the psychocats link)( boot to grub -> choose recovery mode -> drop to root shell prompt,ect.) and the *slight difference* from what is shown there ( entering the username is not needed 

All I was saying is ubuntu (maybe others, I don't know or care) gives you 1 free pass at forgetting your password and however unlikely, your username because the *prompt is at the username already*. 

This is the root shell prompt I'd see and the same basically anyone would see. (Techically the tilde is a little higher

root@doug-desktop:~#

All you need to do is type passwd, press enter, enter a new password, confirm and you (*first user*) have a *new login password*. ( nothing to debate there

My comment on that was this is the last time you can set a new password from the the recovery menu without knowing the password.

All future attempts to access the the recovery menu's root shell prompt will *require entering the password first.*  (*first user's login)* (ala the comment best to not forget it a 2nd time.

The final comment was simply that this one free pass to see user name (first user)and change password was available to anyone.( one time only)

As far as security ect. I'm not saying there is an issue  there due to the one time deal. Myself, I don't care at all, the main reason I choose ubuntu last yr. when I wanted to try linux out was it was the only one where I could choose 1 as a password. (grew up when typing was not something you learned in school****

---

### Post by meierfra. on 2008-09-22
> root@doug-desktop:~#

All you need to do is type passwd, press enter, enter a new password, confirm and you (first user) have a new login password. 

No! "passwd" (without a username) sets the password of the current user. In the recovery console one is logged in as root. So this sets the root password. 


To change the user  password you have to use:

```
passwd username
```

To find out your username type "ls /home"

But actually the current case sound more like a corrupt LiveCD.

---

### Post by mb_webguy on 2008-09-22
I didn't misunderstand your post, but you apparently misunderstood mine.  There are two things wrong with this statement from your original post:> what's somewhat interesting about the 'recovery mode' - recovery menu is when you drop to the root shell prompt you are given the user name in the prompt. So basically you can 'recover' the user name and reset the password right there. (and technically so can anybody else
First, root (in recovery mode) uses the bash shell, which has a default prompt of "user@computername:currentdirectory$".  For example, my username is "matt", and my computer name is "the-tardis".  When I boot into recovery mode, my prompt is "root@the-tardis:~$" -- which, if you'll notice, doesn't have "matt" anywhere.  Your computer, Doug, is apparently named "doug-desktop".  Booting into recovery mode *doesn't* reveal your username in the prompt (though you can simply change to the /user directory to see the home directories for all users on the system).

Second, if you just type "passwd", then you're *not* changing your user password.  You're *setting a password for the root* account -- which is why you're asked for it the next time you boot into recovery mode, and is what I was saying you shouldn't do.

---

### Post by mc4man on 2008-09-23
Good ,now I'm learning something but still a little confused. After changing the password as described by me (let's say I change it to 2) when I come to the ubuntu login screen I now need to use 2 as the password. (the orig. user password when I set up the install was 1)

In any instance where I need to enter a password I now have to use 2 instead of 1

So is 'setting a root password' the same as changing the user password? (in the case of the first user)

Or is this only the result of when installing using the 'default computer name' which is set to <chosen user name>-desktop ?

---

### Post by concord on 2008-09-23
Follow the steps here

[http://ubuntuforums.org/showthread.php?p=5844228#post5844228](http://ubuntuforums.org/showthread.php?p=5844228#post5844228)

10 minutes - tops.  :)

---

### Post by mc4man on 2008-09-23
> This will fix it
If that was for me, there's nothing to fix (to the extent I've observed).
More of an understanding thing.

Both meierfra and mb_webguy have said that setting a password directly from the recovery mode's root shell is setting the 'root' password, not the user password. I'd have to think they're 100% correct.

I think it's just when the computer name is the same as the first user's username then in essence the passwords are the same. So nothings really changed in terms of use except access to the root shell prompt. Now a password is needed to access. (root password/first user password

In a nutshell
fresh install - chose a username -doug, choose a password 1, accept default computer name, doug-desktop.

root password - unknown value - no reason to know or use
first user password - 1 - used to login ,access root functions

After changing root password at '....shell prompt' to 2

root password - 2 - still no reason to use (except '..prompt access'
first user password - 2 - used to login ,access root functions, access '...shell prompt'

I haven't noticed any thing wrong or any change with the sole exception that access to the root shell prompt from the recovery menu now requires a password. ( previously access was open


So the question is 'has something negative happened (by setting the root password to a known value?'

---

### Post by jerome1232 on 2008-09-24
Well what has happened is you enabled the root account, an account that has god-like priviliges over your system, the main negative I know of is say you installed an ssh server on your computer and you have your password of '2' on your root account.

In the above scenario your computer will be cracked and rooted in less than a day probably. If not sooner.

You can password protect grub with an md5 encrypted password and encrypt your entire drive to prevent anyone having access to a password-less root prompt via recovery mode.

---

### Post by mc4man on 2008-09-24
I think i get it now.
Obviously if security was any concern here i wouldn't be using 1 or 2 as a password.

I wasn't 'getting' that when a 'root password' is set, *the first user's password is also set to the same value*. (which lead me to believe I was changing the (my) user password.

---

### Post by eentonig on 2008-09-24
> **jerome1232 said:**
> ....

In the above scenario your computer will be cracked and rooted in less than a day probably. If not sooner.

....


That's some negative attitude. I agree that it's stupid to hook an ssh server on the internet with root account/ssh-access enabled. But being cracked and rooted within a day would require a very dumb and easy password. The times I had an ssh server exposed on the internet, it never had anybody been able to guess the password being used.

---

### Post by jerome1232 on 2008-09-24
Well the op set a single character password on the root account, I feel that qualifies.

---

