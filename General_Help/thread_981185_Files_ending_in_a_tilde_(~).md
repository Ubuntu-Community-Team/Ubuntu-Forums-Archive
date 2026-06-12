---
title: "Files ending in a tilde (~) ?"
date: 2008-11-13
forum: General Help
---

### Post by blis102 on 2008-11-13
Hey everyone,

I have noticed that a TON of files that I have used, created or edited on Ubuntu 8.1 (with gedit mostly) have a version with a tilde at the end of them. For example:

something.html
something.html~
foobar.txt
foobar.txt~

This is a bit strange and does not seem right to me, is this normal or do I have something going on with my system? Is there a way around having these files created?

Thanks for any help

---

### Post by philinux on 2008-11-13
They are backup files. :)

---

### Post by kaivalagi on 2008-11-13
Files ending in tilde "~" are backup files created when you edit an existing file in most applications.

Most of the time it is safe to remove them as they'll be obsolete, but they can be handy if you need to revert to the previously saved file.

Edit: beat me to it :)

---

### Post by blis102 on 2008-11-13
Oh Ok well that makes a bit of sense :)

Its sort of strange that the files sit around even after the file is saved though...

Thanks for the info!

---

### Post by jespdj on 2008-11-13
The file with the tilde is the previous version of the file (the version before the last time you saved it). It's there so that if you edit something wrong and you want to get the previous version back, you still have it. It wouldn't make sense if it would be deleted if you save the file...

If you are sure your edits are OK and you don't need the old version anymore, you can safely delete the tilde files.

---

### Post by kaivalagi on 2008-11-13
I run the following to move tilde files from my home directory to the trash:

```
find ~/ -type f -iname "*~" -print0 | xargs -0 sudo mv -fv --target-directory=/home/**USERNAME**/.local/share/Trash/files/
```

Just change the username to suit...

Just thought it might be useful to you :)

---

