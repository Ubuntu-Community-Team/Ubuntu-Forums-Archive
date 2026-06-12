---
title: "newbie questions - how to remove password prompts"
date: 2008-11-26
forum: General Help
---

### Post by sthapit on 2008-11-26
Hi.  I installed intrepid ibex as a dual boot with XP and it's working great. But it would be perfect if I could get rid of the password prompts.  

1.  When I start the computer for the first time, it asks to "Enter password for default keyring to unlock".  (I think this is before it connects to my wifi)

2. When I try to access my windows partition (Places -> preload) I get prompted to enter a password

3. When I SSH to my server (with key) I get prompted to "Enter login password to unlock keyring"

Can someone tell me how to turn all of these password prompts off?  Thanks :)

---

### Post by PocketDog on 2008-11-26
If you change your keyring password to match your login password it won't bother you again. Instructions  [here](http://ubuntuforums.org/showthread.php?t=974199).

---

### Post by sdennie on 2008-11-26
I think that behavior only happens if you either a) Don't have a login keyring or b) Have the password for the login keyring set to something different than the login.  Try going to System->Preferences->Encryption and Passwords and changing the login keyring password to your login password.

---

### Post by sthapit on 2008-11-26
I went to "System->Preferences->Encryption and Passwords" but there's no option to change the password or settings.  Screenshots are attached.

---

### Post by sdennie on 2008-11-26
> **sthapit said:**
> I went to "System->Preferences->Encryption and Passwords" but there's no option to change the password or settings.  Screenshots are attached.

In the first screenshot, click the large button labeled, "Change Unlock Password".  ;)

---

### Post by sthapit on 2008-11-26
> **vor said:**
> In the first screenshot, click the large button labeled, "Change Unlock Password".  ;)

i tried that...  and i've also used only one password on my computer.  any other suggestions?

---

### Post by mariane_08 on 2008-12-05
> **vor said:**
> I think that behavior only happens if you either a) Don't have a login keyring or b) Have the password for the login keyring set to something different than the login.  Try going to System->Preferences->Encryption and Passwords and changing the login keyring password to your login password.

I'm having the same problem. My passwords are the same too and its driving me crazy! I'm wondering...just wondering if something need to be added in "Add Keyring"

Any ideas?

---

### Post by cosmolee on 2009-01-19
Ubuntu 8.04 Hardy.

Anybody get anywhere with this issue?  I've been having the same issue.  I've tried repeatedly changing the "unlock" password.  I set it to the same as my login password.  

When I try to ssh to a remote system, I get the pop-up window from the keyring asking for the password to unlock the private key. But despite entering the password, the pop-up repeatedly asks me for the password again and again.  

I can't go any further, and thus I can't use my friggin ssh with key authentication at all because the keyring is blocking my use of it.

This is really teeing me off!!

---

### Post by cosmolee on 2009-01-20
It's a bug.  A truly sucky, sucky bug.  It's been around for more than a year.  The fix is at:

   [http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

I ran:  $ gconftool-2 --set -t bool /apps/gnome-keyring/daemon-components/ssh false

Then you must log out for the change to take place.  


More bug info: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127)

---

