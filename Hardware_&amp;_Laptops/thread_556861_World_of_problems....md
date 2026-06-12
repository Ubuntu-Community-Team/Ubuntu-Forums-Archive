---
title: "World of problems..."
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by kmac on 2007-09-21
Where to start?

Ok so I installed Ubuntu's latest version on to my Compaq V2000 Notebook, and everything was working great! So excited, this was my first time booting a Linux OS on my own computer. Being a PHP veteran, I figured I knew my way around Linux quite well, so when my wifi was not working, I figured I'd have no problem installing the drivers.

Wrong.

I've tried everything. Everything these bloody forums tell me to try. I think I'm secretly blond. Well, to make an ugly story short. My Desktop Environment on my main user no longer loads. (which happens to be the only administrative user). All my other users load fine, but  the "Biggie" is shot. I think I killed it from trying to install wifi drivers and not knowing exactly what I was doing. 

Here are the stipulations:

I'm dual-booting XP. My Ubuntu has no internet access because my ethernet card fried and the obvious lack of WLAN. I'm on XP at the moment to post this. I need to know how to restore my desktop and hopefully it would be a plus if someone could help me install my wifi drivers as well.

Thank you,
Kmac

---

### Post by trippinnik on 2007-09-22
In the account with admin access try deleting all of the .Something ie .gnome .amarok etc directories.  these hold your accounts personal settings.  Be careful not to delete the directories not preceded by a '.' You can do this easily enough from teh command line.  When the computer starts up pre Ctrl F2, and login as the admin user.  then you can use 
rm -R .gnome
etc.  you can probably focus on the gnome directories.  Do you know what the error when you try to login using the admin account?  Also when you say the latest do you mean 7.10 or 7.04?  7.10 is alpha and not really ready yet.  It may have more Wifi drivers though.

---

