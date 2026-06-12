---
title: "restoring Thunderbird backup"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by chamstar on 2008-12-28
I have just installed a fresh copy of Ubuntu (Ibex), after installing Thunderbird and then coping my .mozilla-thunderbird and .thunderbird folders from my backup I open Thunderbird and see one of my inboxes, but no email.

The previous version was 2.0.0.18 (20081105), the new version is 2.0.0.18 (20081125), so same version slightly different builds. I still have my old home folder, are there other files I need to copy across?

Many thanks, Cham.

---

### Post by albinootje on 2008-12-28
> **chamstar said:**
> I still have my old home folder, are there other files I need to copy across?

In my installation dot mozilla-thunderbird is a symlink to dot thunderbird.
.mozilla-thunderbird -> .thunderbird/

And that should be all you need to restore.
Everything, preferences, Local Folders, imap cache, cache, etc. should be all in that one dot folder.

Did you restore those files and directories with the correct permissions ?

---

### Post by callan79 on 2008-12-28
> **chamstar said:**
> I have just installed a fresh copy of Ubuntu (Ibex), after installing Thunderbird and then coping my .mozilla-thunderbird and .thunderbird folders from my backup I open Thunderbird and see one of my inboxes, but no email.


Hi chamstar,

If you look inside your (original) Thunderbird dorectory, whatever its name may be, you'll see a file called profiles.ini, plus a directory with a weird name of random characters.

The one with the random characters has your mail and address book etc in there.

So this is what you should do, it works for me every time :)

(1) Make sure you have the original backup still!
(2) Go to your home directory then .mozilla-thunderbird
(3) Delete the random-named-directory that's already there
(4) Grab a copy of your random-named-directory from backups, and copy it into the .mozilla-thunderbird folder
(5) Take careful note of the random name of your folder
(6) Edit profiles.ini, and where you see a line that refers to the old folder name, just put your new folder name instead.

Start Thunderbird and you will have all your mail :-)

Good luck

Callan

---

### Post by albinootje on 2008-12-28
> **callan79 said:**
> 
(1) Make sure you have the original backup still!

I got a bit confused about the original posting, but now I realise that the OP must have been using Thunderbird before restoring the old .thunderbird/ and .mozilla-thunderbird/

If that is correct (is it ?), and the backup is still available, then it would be a matter of starting Thunderbird with the -Profile-Manager option, to get to see the old profile, and then make that the default profile at startup.

Like this in a terminal :
```

thunderbird -Profile-Manager

```

---

### Post by darkstaar on 2008-12-28
I believe the command is "thunderbird -profilemanager" without the extra hyphen.

--Leisa

---

### Post by albinootje on 2008-12-29
> **darkstaar said:**
> I believe the command is "thunderbird -profilemanager" without the extra hyphen.

You're right, thanks for the correction, for the OP, see : 
```

thunderbird -h

```

---

### Post by chamstar on 2008-12-29
> **callan79 said:**
> Hi chamstar,

So this is what you should do, it works for me every time :)

(1) Make sure you have the original backup still!
(2) Go to your home directory then .mozilla-thunderbird
(3) Delete the random-named-directory that's already there
(4) Grab a copy of your random-named-directory from backups, and copy it into the .mozilla-thunderbird folder
(5) Take careful note of the random name of your folder
(6) Edit profiles.ini, and where you see a line that refers to the old folder name, just put your new folder name instead.

Start Thunderbird and you will have all your mail :-)

Good luck

Callan

Worked great, many thanks!

---

