---
title: "Pidgin not able to connect anymore after update to 9.04"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by fgysin on 2009-08-12
I got problems with my Pidgin IM recently. I have been using it for quite a while on Ubuntu 8.04 where it worked more or less stable. (It did work after all.)
After updating to 8.10 and from 8.10 to 9.04 pidgin is not working properly anymore. (I did the update in one go, so I don't know for sure if this is a problem of 9.04 or 8.10 as well.)
I can start it up, but none of my accounts is able to connect. I got ICQ and MSN accounts.

The errors I get are:
"Could not connect to authentication server: Access denied: HTTP proxy server forbids port 5190 tunneling." for ICQ
and
"Connection error from Notification server: Unable to connect" for MSN respectively.

Allthough this looks like a proxy problem it is most definitely not:
a) I did not change proxy settings.
b) A colleague has his PC right next to mine, is sitting on the same subnet (and proxy) and has no problems with the same proxy settings - all is working fine with his pidgin accounts. He still uses Ubuntu 8.04 though.
c) I made sure to try the correct proxy settings my inserting them manually (instead of using environmental/gnome settings) - but it still did not work.

I tried to purge and reinstall Pidgin, but it didn't help. I also tried getting the latest update from the official pidgin repo, but this did not help either. Any suggestions?

I hope someone can help me, I really need my messenger back. :?
thx,
florian


PS: I kind of did not manage to really purge Pidgin with all its data from my system. I installed it a while ago with apt-get and now killed it with apt-get remove --purge. (Removed the dependant lib and the pidgin-data package as well.)
Then I deleted the ~.purple folder and the remaining folders in /urs/lib. I even manually tried to find an delete each and every folder/file that has to do anything with pidgin/purple as apt-get (and synaptic while we're at it9 were not able to clear all files.

But still, after each fresh reinstall Pidigin has magically added my two accounts allready. How can this be? Where the hell does Pidgin save its user data?

---

### Post by fgysin on 2009-08-18
Bump.

---

