---
title: "[SOLVED] I want to delete everything"
date: 2008-08-28
forum: General Help
---

### Post by Bliepo32 on 2008-08-28
Well, I ruined my install of xubuntu, so I want to reinstall it. I know I could just reformat it, but I want to use rm (with the option rf, and the root directory as the one to delete), but it won't work. It will say: "cannot delete root directory". Can I bypass this?

NOTE: I know the command will delete everything, which is exactly what I want. And please do not post the actual command (describe it like I did above), because someone with no knowledge about Ubuntu might decide to copy & paste it.

---

### Post by mellowd on 2008-08-28
why don't you just reformat it while reinstalling then?

and how can we show you the command if we can't type it?

---

### Post by unutbu on 2008-08-28
If you are hell-bent on destruction, use the --no-preserve-root flag.

---

### Post by Bliepo32 on 2008-08-28
> **mellowd said:**
> why don't you just reformat it while reinstalling then?
Because I always wanted to execute this command, and this is the perfect occasion for doing it. I wouldn't delete a 'healthy' system, but it is ruined anyway, and I need to reinstall, so...

---

### Post by Bliepo32 on 2008-08-28
> **unutbu said:**
> If you are hell-bent on destruction, use the --no-preserve-root flag.
Hooray! Killing time!

---

### Post by mellowd on 2008-08-28
I see, well have fun! :P

---

### Post by todak on 2008-08-28
No, you cannot bypass it due to the fact that the directory you are trying to delete is still mounted. #-o You must first unmount root to delete it, but if you unmount it first, then there is no way to run the command. Use the live cd or just reinstall. O:)

---

### Post by Elfy on 2008-08-28
It's all here [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

I know how you feel I wanted to see what would happen if I chmod 0000 /

---

### Post by Bliepo32 on 2008-08-28
> **todak said:**
> No, you cannot bypass it due to the fact that the directory you are trying to delete is still mounted. #-o You must first unmount root to delete it, but if you unmount it first, then there is no way to run the command. Use the live cd or just reinstall. O:)

Yeah, I noticed. Had fun trying it anyway.

---

