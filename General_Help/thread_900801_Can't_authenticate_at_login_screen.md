---
title: "Can't authenticate at login screen"
date: 2008-08-25
forum: General Help
---

### Post by psylo on 2008-08-25
Hi all,

Any help on this would be much aprpeciated as I'm locked out of my box.

So I have 8.04 and had it running for a couple of months quite happily. I decided to try and get it onto our domain here at work as it would be useful to have the machine logging into our active directory.

Unfortauntely that didn't work so I decided to roll back the Likewise things and uninstall them.

Consequently I now can't log into the computer at all.

What's happening is at the GDM login screen when I put in my username it holds for a second, doesn't ask for my password then says "Authentication Failed" and drops me back to the username entry.

Trying this from command line results in the same thing.

Interestingly however if I login to a samba share on the box then there isn't an issue at all. 

Hopefully someone's had this type of problem before...

Cheers
AndrewF

---

### Post by psylo on 2008-09-01
Bump.

Any thoughts here at all? I can't login to this box at the moment for all the reasons given above and I'm sure its probably something to do with PAM going screwy but don't have any knowledge in this area to fix it...

Cheers
Andrew

---

### Post by signifer123 on 2008-09-02
Can you get into single user mode? It would be the recovery mode on the startup menu. (you may need to hit esc while starting up, when it says so).
If not see the end of my post.

now you should be able to look at dmesg to figure out whats could be wrong.
dmesg | grep pam

or auth logs
cat /var/log/auth.log

Though i'm guessing it may have messed up your pam configuration when you tried to authenticate to AD.

cd to /etc/pam.d  - cd /etc/pam.d
if you ls/dir now it will show all the different files with how pam authenticates certain programs.

edit gdm with whatever editor you use, i prefer vim - vim gdm

A simple replacement would use 
```

@include common-auth
@include common-account
@include common-session

```

or you could go all out and try a full replacement of the file, mine is:
```

auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

If you reboot and can login through gdm, i'll post the other pam configs, for login and the such.

If single user mode failed, when you get to the menu, highlight the recovery mode option, and press e. Scroll down to the line that says kernel, hit e again, and add init=/bin/bash to the end. This will start a shell early in the bootup.

---

### Post by EricBaenen on 2008-10-24
Oh boy... I should have checked the forums before I did the same thing!  Have an Ubuntu 8-04 box that I had installed Likewise Open on - but it was messing things up - kept throwing up an empty error dialog box every time someone tried to log in, but you could just click through it - also caused the user and groups tool to hang when you tried to authenticate... so I uninstalled Likewise Open --- now I can't authenticate at all to the system.  Will try the suggestion to get at the dmesg's, etc.

Beware Likewise Open!  For the time being I'd strongly recommend that if you have installed Likewise Open --- DO NOT un-install it!

---

