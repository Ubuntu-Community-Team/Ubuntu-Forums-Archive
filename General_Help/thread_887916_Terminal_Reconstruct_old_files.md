---
title: "Terminal: Reconstruct old files"
date: 2008-08-12
forum: General Help
---

### Post by NikolajFabriciusBjerre on 2008-08-12
Hey there.

Im coding a little bit c++.
Sometimes when I run my own apps with a code-fail,
it can be stuck and impossible to quit it, unless you close the terminal.
That's not the problem, but if this happens, the file is gone.

But then i wrote 'ls' in the terminal,
and the file was there with a '~' after the name.

Is it because it's not completely deleted?
Can I get the file back to my desktop?
Is there any kind of command you can use in the terminal to get it back?

Thanks :)

---

### Post by brunovecchi on 2008-09-21
To stop halted applications without closing the terminal, just press Ctrl+C. That should take you right back to the prompt without having to close it.
Now as of the ~ file, it's a sort of backup. If your original file is gone, you can rename the backup file to the original name (removing the ~). It's not always the last version of the file though.

---

### Post by Sorivenul on 2008-09-21
> **NikolajFabriciusBjerre said:**
> But then i wrote 'ls' in the terminal,
and the file was there with a '~' after the name.

As far as I know, the '~' you mention denotes a backup.  Some editors automatically create them.  Try and open the file and see what it contains.  If it's what you're looking for, just create a copy of the file with the '~' removed.  Good luck!

---

