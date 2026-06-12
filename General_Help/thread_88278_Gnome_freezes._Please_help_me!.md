---
title: "Gnome freezes. Please help me!"
date: 2005-11-09
forum: General Help
---

### Post by capcorn on 2005-11-09
Hi,

I was trying to configure the look and feel of my Gnome when the clock reports error and disappear from my panel. I did not pay much attention to it and logout. But when I login to Gnome the next time, it
just freezes after the splash screen. I have tried repeated login and Gnome just freezes.

Does anyone knows what's the problem here? 
How can I remedy this problem?

Thanks a lot for your time.

---

### Post by dbott67 on 2005-11-09
There are a few things you can try:

1. If you have a secondary account setup, try logging in via that account.  If successful, it may indicate that your primary account has some munged gnome-specific settings.

2. If you don't have a secondary account, select "Failsafe Gnome" at login.  If that fails, try "Failsafe Terminal"

3.  Once logged in to failsafe terminal mode, try deleting your gnome settings (well, don't delete them, just rename them forcing Gnome to recreate them upon login).

I'm going from memory of a post I read a while ago, so I may provide you with some bad advice, but we can always undo the damage if worse comes to worse.

1. Login via failsafe terminal
2. cd to your home directory
```
cd ~
```
3. Rename the various Gnome-related session folders:
```
mv .gnome .gnome.bak
mv .gnome2 .gnome2.bak
```
4. Logout & try to log back in normally
5. If it works, it was related the the settings stored in .gnome or .gnome2 hidden folders
6. If it doesn't help, log back in in failsafe terminal mode and rename the files back:
```
mv .gnome.bak .gnome
mv .gnome2.bak .gnome2
```
7. Pray for better advice! :)

Actually, if these steps don't work but you can login via failsafe terminal, you could always create a new account via the command line (using the command 'useradd' --- you'll have to search the forums for the exact details) and then try logging in via the newly created account.  If it fails, then the problem is probably a little more severe.

-Dave

---

### Post by capcorn on 2005-11-09
Thanks for the help, Dave.

I am going to try it tonight.

---

### Post by capcorn on 2005-11-10
I have tried out Dave's suggestion. 
I could not login in FailSafe mode.
Nothing can be done. 
Brown screen of death.

Did a reinstallation. 
Let's see how long I can last in using Linux.

Dave,
Thanks for your tip again. Appreciate it.

---

### Post by dott.malcom on 2005-11-10
there is already a discussion about this. I'm also fighting with the same problem.

Try write "login freeze" in search tool in the forum.

Anyway follow this thread
[http://www.ubuntuforums.org/showthread.php?t=87526]("http://www.ubuntuforums.org/showthread.php?t=87526")

---

### Post by ssam on 2005-11-15
[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

