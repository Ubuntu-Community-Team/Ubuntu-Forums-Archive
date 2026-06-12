---
title: "[SOLVED] how to find files without entire filename"
date: 2008-08-03
forum: General Help
---

### Post by Pacopag on 2008-08-03
Hi.  I'm sorry to create a post about something that I should be able to find myself, but I just can't seem to find it.

What I'd like to know how to do is to find a file when I only know part of the filename.  I can't seem to just use the "find" command.  I think there's something that I can do using grep, but I can't remember how.
Any help?
Thanks

---

### Post by dentaku65 on 2008-08-03
You can use locate, first update the slocate db
```
sudo updatedb
```
Then:
```
locate <whatever>
```

---

### Post by Pacopag on 2008-08-03
Can I use "*" in <whatever> to fill in the parts I don't know?

---

### Post by coffeecat on 2008-08-03
I'm fairly sure this is working, but you might want to check it out in your directory structure.

```
find /path/to/folder/ | grep string
```When I do that, I get a recursive search in all the folders subordinate to /path/to/folder/ and all files **and** subordinate folders with 'string' in their name listed in the terminal.

And if I...

```
find /path/to/folder/ | grep string > /home/myusername/find.text
```... I get a nice text file that I can read at my leisure.

---

### Post by dexter.deepak on 2008-08-03
> **Pacopag said:**
> Can I use "*" in <whatever> to fill in the parts I don't know?

yes of course !!

---

### Post by Pacopag on 2008-08-03
Purrrrfect.  Thanks a bunch.

---

### Post by Pacopag on 2008-08-03
Yep.  Both methods work.  Thanks guys.

---

### Post by drs305 on 2008-08-03
Another option that doesn't require looking at a stored database:
```
sudo find / -type f -iname *allorpartofthename*
```

You can use wildcards...

---

