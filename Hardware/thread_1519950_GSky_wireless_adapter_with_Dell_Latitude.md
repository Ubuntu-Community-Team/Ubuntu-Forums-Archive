---
title: "GSky wireless adapter with Dell Latitude"
date: 2010-06-28
forum: Hardware
---

### Post by Chuck_N on 2010-06-28
Dell Latitude
Ubuntu 10.04
Installed and working quite well.

Some time ago I was advised to get a GSky wireless adapter as appropriate for the Compaq Presario I've been having lots of blackout troubles with. 

I've run the laptop on Ethernet with no troubles. Thought I should try wireless. Attached the GSKY.  
It indicates Enabled.  I start FFox. go to GOOGLE or other site. 
Firefox says currently Offline.  I remove the checkmark.
then FFox cannot find service at the requested site.
FFox and/or GSky present a box requesting key or password.
I have a WEP password, 10 characters.
the two options are  WEP 40/128-bit key    or     WEP 128-bit Passphrase.
I tried each, putting in the 10-character password, but neither work.

Incidentally, the password HAD been WPA 8-characters but we had it changed to WEP with LinkSys's guidance, as we have a LinkSys Router.  Our OTHER machine operated well with the WPA and operates well now with the new WEP password.  I worked also with GSky on the phone, and got nowhere. They suggest I call the Ubuntu Company.    8-)

What can I do to get the wireless GSky working with my Latitude?  I suppose it's possible the GSky will not work with the Latitude.

---

### Post by Chuck_N on 2011-04-08
Okay, I'm back to my Presario again....
looks like I got NO replies b4, but I'll try again.....

Hooked up the GSky and it's working fine. However everytime I boot up I have to enter the 10-character password. Is there a way to avoid that?

Thanks, Chuck

---

### Post by pollywog on 2011-08-27
Go to Applications>Accessories>Passwords and Encryption keys. Once there, delete the "default" password. Next time that you reboot a dialog should come up asking for you to set a new password (protecting the other passwords). Don't enter anything, just enter a blank password. Another dialog should pop up asking if you want to use "unsafe storage" , let it know that that's what you want to do. That should fix what ails you.

---

