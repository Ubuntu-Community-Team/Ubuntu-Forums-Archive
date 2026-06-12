---
title: "Remastersys Auto login problem"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by bansteen on 2009-04-23
Well, I am trying to make a live cd using remastersys. I choose backup instead of distro and set auto login in gdm. The autologin is not working even if I have enabled it to true in gdm.conf file.

Can someone please help. Its my 3rd day and I am trying continuously to solve this issue. :(

---

### Post by Ticketoride on 2009-04-23
Never got past the Login Prompt with any Distro or Backup I made, be it "Live" or "Install".

So I have several Coasters to show for it, and lost my Keyboard right after that.

I won't go near "Remastersys" again.

I have been running Windows ever since, because I don't have the Time to re-install everything from Square 1 for the umpteenth Time and the Keyboard cannot be gotten back under Ubuntu.

---

### Post by bansteen on 2009-04-23
I am still working on it. Trying to swap the squash file systems between a live dist cd and live backup cd. Lets see what happens.

---

### Post by inobe on 2009-04-23
reading about it for a few days now, very determined on making a distribution dvd.

---

### Post by hilather on 2009-06-16
I had the same problems.  Couldn't find anyone with a fix for it.  I changed the username in the config to be root instead of custom.  It works fine now.

If it only works with root, I don't know why the default user isn't set as root.  Anyways try it out.

---

### Post by [3w`Sparky] on 2010-04-26
i'm also having this issue, i'm wondering if there is something inside the initrd.gz file that needs changing, i tried full backup with remastersys which won't auto login even tho the conf file and gui menu tell it to, i even booted the live cd and run a mksquash on the hdd to see if it was the application but it still won't allow auto logins so beleive it to be an Ubuntu config issue rather than a remastersys one, which is why i now point to the initrd.gz 

?

---

### Post by [3w`Sparky] on 2010-04-26
note for all, it was the initrd.gz 

extract the contents and then goto /etc/casper.conf

this needs to match the account your wishing to autologin with 

re gzip it and place it where you boot from

---

### Post by Rishav Thakker on 2010-10-31
Uhm I've been using remastersys for backing up my Ubuntu, and even I've not been able to get rid of the login prompt. However, i've found a way to get past it.

The username is the distribution name (usually "custom"), and the password is blank.

It works everytime. :)

---

### Post by msn0 on 2011-01-20
I had the same problem. After creating backup with remastersys the file /etc/gdm/custom.conf is missing. Simply create custom.conf with the following content
```

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=yourlogin
AutomaticLogin=yourlogin
TimedLoginDelay=30
DefaultSession=gnome
```
and everything works fine :)

---

### Post by Bob Linuxcat on 2011-01-22
Okay, for all of you people that are having a hard time trying to get remastersys dist option to have autologin working after you are done creating your iso disc. 

System>Adminstration>Remastersys Backup

Then you click on Modify..

Then you need to change the user name to the user name you currently have on your system. It should be your only username on your current system.  Not root. Not guest. It has to be your current username.  You should try it with only one user name, not multiples.

The gdm config file will remain the same as the one on your current system as the one that will be on the finalised iso dist copy iso when you are done.. 

That's your answer.  I have no idea how to change it to something else..   Frag you make some awesome software.. Don't let anyone tell you differently.. Remastersys rocks!!

---

### Post by tjbradford on 2011-05-07
it lightly that this is due to an oversight or maybe just persons not being aware of the user settings that are created when doing an install. 

eg you install ubuntu and enter your name during the install.

once booted you login as that user and add a package or ten then wish to remaster, you need to not just edit the login settings to be automatic but also goto the user account that your using and ensure that the box is ticked (do not require password to login) or it will always stop at the login prompt. 

once done make sure your remastersys is set for the said user 

this should solve your problem's

---

