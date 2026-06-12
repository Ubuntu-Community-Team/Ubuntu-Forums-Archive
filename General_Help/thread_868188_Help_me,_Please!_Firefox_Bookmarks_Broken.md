---
title: "Help me, Please! Firefox Bookmarks Broken"
date: 2008-07-23
forum: General Help
---

### Post by ShinHadoken on 2008-07-23
Symptoms:

[LIST]
[*]Can't access bookmarks, even in the Bookmark Manager
[*]Not even default bookmarks
[*]Can't import from Foxmarks
[*]Can't use backup files, Firefox won't accept
[*]Won't allow me to make new bookmarks
[*]Opens to about:blank, not homepage
[*]Can't use back/forward arrows in browsing
[*]Tried COMPLETELY REMOVING Firefox 3 and reinstalling, no help.
[*]Starting Firefox 3 from Terminal yields the same results, and no error messages I could refer you to.
[/LIST]
Can someone please help me? I don't want to have to dump Ubuntu!

Thank you sooo much in advance, this is really bad for me!!!

-SH

---

### Post by ShinHadoken on 2008-07-23
Bump, please.

---

### Post by silkstone on 2008-07-23
This is fairly drastic, but I'm assuming that Foxmarks has your bookmarks on its server so you can get them back.

Go to .mozilla/firefox and delete the xyz.default folder. (xyz can be anything!) You may want to rename the file instead so you can get it back, although I suspect it's corrupted.

Restart Firefox and see what happens. You will need to reinstall all add-ons etc, reset your preferences, and import the bookmarks from Foxmarks.

EDIT/ You may also need to delete the profiles.ini file, and then completely remove and reinstall Firefox. (Thanks to SpikeyMike for this addition.)

---

### Post by chriskin on 2008-07-23
i had the same problem on both windows and linux at some time in the past, a computer restart made everything work ok though
on all times it happened after an update

it seems to be a firefox-related problem, not an ubuntu-related one

---

### Post by ShinHadoken on 2008-07-23
Thanks Silkstone, you helped solve the problem. I deleted the firefox folder in .mozilla directory, and *. then completely removed Firefox.* I had to reinstall a few add-ons, but now I'm good. And yes, I was able to get them all back with Foxmarks (thank God!).

---

### Post by oweise on 2008-07-28
For some future usage: I had an similar, if not the same, problem where bookmarks in ff3 were gone from one boot to the other, without possibility to sync foxmarks back in.

ff3 stores its bookmarks in a sqlite database file called "places.sqlite", which is located right inside the profile directory. It seems the database somehow crashed, leaving an - apparently unreadable - file "places.sqlite-journal" in the same folder. I think ff3 tries to read the journal on startup to get a consistent db again and fails.

When I renamed that file to, lets say "places.sqlite.off" where firefox would not find it, my bookmarks appeared again suddenly. Maybe not at the absolute last state, but better than nothing!

---

### Post by SpikeyMike on 2008-07-31
> **silkstone said:**
> This is fairly drastic, but I'm assuming that Foxmarks has your bookmarks on its server so you can get them back.

Go to .mozilla/firefox and delete the xyz.default folder. (xyz can be anything!) You may want to rename the file instead so you can get it back, although I suspect it's corrupted.

Restart Firefox and see what happens. You will need to reinstall all add-ons etc, reset your preferences, and import the bookmarks from Foxmarks.

thanks for your post, what I did was also delete the profiles.ini file and then completely uninstalled and reinstalled firefox 3 and it works, just deleting xyz.default wouldn't work for me

Spikey

---

### Post by silkstone on 2008-07-31
Thanks Spikey. I'll edit my post above to include that advice.

---

### Post by taurusvip on 2008-09-27
The problem that I have was with wireshark that changed some firefox permissions  to root that resulted on desapearing of favorites, blank adress bar, no forward backward, plugins etc...,  I just went to /home/jose/.mozilla/firefox/  folder  (console)   and changed the ownership and group to jose:jose  of all changed files like this  : 

sudo chown jose:jose / filename

jose is you login account to linux...

Jose :guitar:

---

### Post by kentpend on 2008-09-28
> **oweise said:**
> For some future usage: I had an similar, if not the same, problem where bookmarks in ff3 were gone from one boot to the other, without possibility to sync foxmarks back in.

ff3 stores its bookmarks in a sqlite database file called "places.sqlite", which is located right inside the profile directory. It seems the database somehow crashed, leaving an - apparently unreadable - file "places.sqlite-journal" in the same folder. I think ff3 tries to read the journal on startup to get a consistent db again and fails.

When I renamed that file to, lets say "places.sqlite.off" where firefox would not find it, my bookmarks appeared again suddenly. Maybe not at the absolute last state, but better than nothing!
Thanks, this worked.  places.sqlite had not been renamed, but apparently still corrupted.

---

### Post by AggravatedGestalt on 2010-12-03
> **taurusvip said:**
> The problem that I have was with wireshark that changed some firefox permissions  to root that resulted on desapearing of favorites, blank adress bar, no forward backward, plugins etc...,  I just went to /home/jose/.mozilla/firefox/  folder  (console)   and changed the ownership and group to jose:jose  of all changed files like this  : 

sudo chown jose:jose / filename

jose is you login account to linux...

Jose :guitar:
This works perfectly, without losing or reinstalling anything. But what a stupid bug!!!

---

