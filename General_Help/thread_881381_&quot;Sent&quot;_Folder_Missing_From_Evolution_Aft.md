---
title: "&quot;Sent&quot; Folder Missing From Evolution After Upgrade to 2.22"
date: 2008-08-05
forum: General Help
---

### Post by jsym on 2008-08-05
After upgrading to Evolution 2.22 my sent folder has disappeared.  I can't see it in the folder-tree on the left side of the window and every time I send an email I get the following error message:

```
**Error while performing operation.**

Failed to append to mbox:/home/myaccount/.evolution/mail/local#Sent:
Cannot get folder `Sent': Value too large for defined data type
Appending to local `Sent' folder instead.
```

When I look in the folder it seems to be the case that the sent folder is there.  Perhaps I have overfilled my sent folder?

**What's happening here and how can I get my folder back in a useful state?  **

Looking around on the web it seems that issue has come up for other when they have changed their username, but I have not done this; just the upgrade through synaptic.

-John

---

### Post by dcstar on 2008-08-06
> **jsym said:**
> After upgrading to Evolution 2.22 my sent folder has disappeared.
......

[LIST=1]
[*]Exit Evolution
[*]Rename .evolution folder
[*]Restart Evolution
[*]If things now look ok, exit Evolution and copy folders with your old data from the renamed folder to the new .evolution folder.
[/LIST]

---

### Post by jsym on 2008-08-06
Thank you for the clear suggestion!

Everything went well up to and including step 3; I opened up evolution, it made a new folder and everything looked fine.

After copying over the contents of my old directory into the newly made directory I'm back to the same problem as before--No Sent Mail Folder. :(

Is it possible that I've "filled it up"?  I don't know if that question even makes sense, but I can't help but wonder given the cryptic error message.

---

