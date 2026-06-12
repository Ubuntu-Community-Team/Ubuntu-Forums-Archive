---
title: "Use terminal to add new line to start of file"
date: 2008-08-03
forum: General Help
---

### Post by scott_g on 2008-08-03
Hi;

This may be simple, but I can't seem to get it to work.  I'm building a website, and need to add a few lines to the start of every file in the site (60+ files).  I'd prefer not to do this by hand, so I've been trying to get a script that'll do it for me...  So far, I've tried:

```

sed '1 i this is first line' file

```

This does what I want, but displays it in the terminal; I need it to update the file...

Anyone have any ideas?

Thanks,
Scott

---

### Post by squaregoldfish on 2008-08-03
Normally, you'd simply direct the output to the file to get the contents into the file. However, since, you're reading and writing to a file, you can't do it - you end up with an empty file. Instead, write the output to a new file, and then move it back over the top of the original:

```
sed '1 i this is first line' file.new
mv file.new file

```

Hope this helps,
Steve.

**UPDATE:** See below. Much better.

---

### Post by dexter.deepak on 2008-08-03
i remember -i option to sed makes inline editing,which saves you from creating an extra file....but i am not sure.

---

### Post by squaregoldfish on 2008-08-03
> **dexter.deepak said:**
> i remember -i option to sed makes inline editing,which saves you from creating an extra file....but i am not sure.

You're right. Wish I knew that before....

---

### Post by scott_g on 2008-08-04
The -i option worked perfectly.  Thanks a lot; saved a lot of time...

Scott

---

