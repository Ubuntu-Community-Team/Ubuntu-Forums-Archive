---
title: "reinstalling applications after new ubuntu install"
date: 2008-10-14
forum: General Help
---

### Post by gopher38 on 2008-10-14
Hello all,

I'll try not to make this too long.  Question might be addressed elsewhere, but I couldn't find anything on a search.

A couple of times, I've either wanted to or had to reinstall ubuntu starting from LiveCD, but wanted to save the settings for a particular application.  Take Thunderbird, for instance, where I've got a bunch of email accounts, and lots of settings for delete mail after X days, send in HTML anyway, use signature Y, etc., etc.  I'm not a pro in Ubuntu, and this is probably a gross exaggeration, but I thought that one of the advantages to Linux over Windows was that Linux didn't leave lots of loose threads to registries and dll files all over the machine; that the application was largely self-contained in a few folders that could be cleanly deleted from (or recopied to?) the computer.

So the question is: is it at all possible to reinstall programs after a clean install by saving certain folders and then recopying them back afterwards?  Would this by a bad idea?  If so, is there a general rule of thumb regarding which folders I'd have to copy (for instance, the .app_name folder in the home folder and the /user/lib/app_name folder)?  For instance, what would you have to copy for Thunderbird or GIMP?  Or am I way oversimplifying things?

Muchos gracias.

---

### Post by Cool Surfer on 2008-10-14
i hink some of these can be installed in home directory, make a separate partition for /home. N dont format it.

---

### Post by geirha on 2008-10-14
Whenever you reinstall, you should back up your homedir(s) and /etc. /etc typically contain settings for all users, while the homedirs contain the settings for individual users. In the case of thunderbird, you only need ~/.mozilla/thunderbird to get your settings back.

---

### Post by gopher38 on 2008-10-14
> **geirha said:**
> Whenever you reinstall, you should back up your homedir(s) and /etc. /etc typically contain settings for all users, while the homedirs contain the settings for individual users. In the case of thunderbird, you only need ~/.mozilla/thunderbird to get your settings back.

Good to know.  Thanks for that.  I'm still fairly new to Linux, and I've had to reinstall Ubuntu a number of times over the last few months when I foul things up.  Just getting Thunderbird back the way I want involves probably 40 minutes of downloading extensions, clicking on options, and changing folders.  This will help.

---

