---
title: "Undeletable files in the trashcan"
date: 2008-08-21
forum: General Help
---

### Post by TimboUK on 2008-08-21
Hi!

I copied some files off a coverdisk (python source and a few bmp's) and I deleted fine.  When I went to the trash can to empty them, they would not delete.  I get the message: "Error removing file: Permission denied"

If I try to edit the properties to change permissions I get:
"Sorry, couldn't change the permissions of "backdrop.bmp": Operation not supported by backend"

I am logged in as root user. I cannot think how else to remove these files.

(Hardy Heron)

---

### Post by rainwalker on 2008-08-22
Don't log in as root.

Instead, as a normal user, use the "sudo rm" command to delete things

---

### Post by jerome1232 on 2008-08-22
Sometimes a sudo rm -f is in order get rid of the reluctant-to-die file.

Seriously can't you just let it sit in it's Trash in peace?

---

### Post by TimboUK on 2008-08-22
Thanks for the quick replies.  How do I get into the trash via terminal?  I cannot find the trash directory.

Thanks in advance.

---

### Post by Cresho on 2008-08-22
```
sudo rm -rf /home/putyourusernamehere/.local/share/Trash/*
```

it just tells it to delete the stuff in the trash..anything in there.  one more thing.  THis is a powerfull command.  if you do it wrong, you can delete alot of crap if not done correctly.

---

### Post by TimboUK on 2008-08-22
And its gone!

Thanks very much. (all of you)

Once again Ubuntu community is the solver of my problems!

Kind regards,
TimboUK

---

### Post by cybrsaylr on 2008-08-22
I had this problem also.
Here's that solution that a poster gave that worked for me.

> this code above will delete all in trash with one shot

sudo rm -rf ~/.local/share/Trash

---

### Post by Cresho on 2008-08-22
ya the tilda works, but I wanted him to see the exact directory since some people don't understand it.  Am I assuming?

---

