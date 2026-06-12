---
title: "[SOLVED] Easy way to transfer FF3.0 Settings/Plugs from xp to linux"
date: 2008-10-22
forum: General Help
---

### Post by otz070 on 2008-10-22
Hello. I just got my ubuntu online and am using firefox 3.0 I have a lot of extensions/there are alot of settings to go through.
Is there an easy to transfer Firefox 3.0 extensions/settings/ect. from xp to linux. (When I Get ubuntu working on my other computers I will need to do this.) Preferably some method using a syncronization extension or saving to a flash card/usb stick. Though usb stick or flashcard is prefered.

Thanks for reading/help.:)

---

### Post by southerngrey on 2008-10-22
Yep, the answer is an extension called FEBE [https://addons.mozilla.org/en-US/firefox/addon/2109]("https://addons.mozilla.org/en-US/firefox/addon/2109")

Works great with FF3 and includes scheduled backups and works cross platform.  It backs up extensions as well as bookmarks and settings.

---

### Post by Nostalos on 2008-10-22
Or just copy your profile directory from your Windows box to your Linux box.  Do this quite often myself.

Start Firefox on Ubuntu to create a default profile.
Copy your profile from C:\Documents and Settings\{username}\Application Data\Mozilla\Firefox\Profiles to /home/{username}/.mozilla/firefox  

Profiles are usually named something similar to 5d313e32.default

From this point either delete the empty profile directory and rename it to the default one already there.  or edit your profiles.ini file to use the one you copied over.

[Profile0]
Name=default
IsRelative=1
[COLOR="Red"]Path=5d313e32.default[/COLOR]

---

### Post by otz070 on 2008-10-28
> Or just copy your profile directory from your Windows box to your Linux box. Do this quite often myself.

I always wondered If you could do this. I never tried because of fear of trashing my systems.

Thanks:)

---

