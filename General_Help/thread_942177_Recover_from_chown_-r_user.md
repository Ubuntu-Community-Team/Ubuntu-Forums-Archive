---
title: "Recover from chown -r user: /"
date: 2008-10-08
forum: General Help
---

### Post by Locutus_of_Borg on 2008-10-08
I had ubuntu mounted in a directory and ran chown -r on its parent without first unmounting it....

i have run: chown -r root: /
and: chown -r user: /home
already but a few things still dont work right; sudo and networkmanager for instance

is there a way to recover this apart from reinstallaton? 

(this is my wifes computer and for some unfathomable reason she is insisting on using this installation despite there being a working install of 8.04 on her computer...)

:confused:

---

### Post by ARhere on 2008-10-08
uhh....   I hate to say this, but it will probably be easier to reinstall Ubuntu over the current installation.  If you choose not to format the current data, then Ubuntu will automatically import the user account from the original Ubuntu installation.

I accidently wrote over my MBR and had no choice but to reinstall.  When I did, I used the old partitions and did not format before installation.  After I rebooted my old desktop was waiting for me.

-AR

---

### Post by Locutus_of_Borg on 2008-10-08
thanks for the reply

if i install without formatting, does this mean essentially the installation just overwrites the existing files and leaves untouched everything that has been added since the initial installation?

---

### Post by ARhere on 2008-10-08
kind of...

Start the PC with the Live CD and back up her /home directory first to a custom folder, say "/backup".  Make sure to copy EVERYTHING!!!
```
sudo mkdir /backup
sudo cp -prv /home/<user> /backup
```
***EDIT:** Better make it a USB key or something removable to be safe.*

When you reinstall, it will overwrite everything except for the home directory which it will import.  When I did it my themes, wallpapers, and files in "/home" were untouched.  But I still had to redo the updates and any programs I installed.

-AR

---

### Post by Locutus_of_Borg on 2008-10-08
okay, i may have to resort to that, hoping not to have to though...

but i will begin the download of 7.1 in any case


thanks

---

### Post by ARhere on 2008-10-08
> **Locutus_of_Borg said:**
> okay, i may have to resort to that, hoping not to have to though...

but i will begin the download of 7.1 in any case


thanks

7.1 ??? :confused:  If you mean 7.10, then this is a perfect chance to upgrade to 8.04.  My wife likes it better then 7.10.

-AR

---

### Post by Locutus_of_Borg on 2008-10-08
i did mean 7.10

this whole accident occurred when i was setting up 8.04 on her computer (i was setting it up to automount 7.10 onto /previous, and symlink her home folder there to a file in her new home folder, then I chowned /previous so she could write to it...oops) but she just wants to continue using 7.10 for some reason...

---

### Post by ARhere on 2008-10-09
> **Locutus_of_Borg said:**
> i did mean 7.10

this whole accident occurred when i was setting up 8.04 on her computer (i was setting it up to automount 7.10 onto /previous, and symlink her home folder there to a file in her new home folder, then I chowned /previous so she could write to it...oops) but she just wants to continue using 7.10 for some reason...
Over my head on that one, except for the wife's reluctance.  My wife does not care about computers and just wants it to "just work".  In her mind any changes, even if better, simply change what works.

-AR

---

