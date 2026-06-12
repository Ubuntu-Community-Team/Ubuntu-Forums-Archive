---
title: "[SOLVED] possibly corrupted data in an .tar.gz file"
date: 2008-10-10
forum: General Help
---

### Post by porchrat on 2008-10-10
OK here is my problem, when I attempt to take a look into an archive (it is a .tar.gz) using "tar":

```
tar tzvf foo
```

I have no problem.  It lists the contents of the archive.

However when I attempt to pipe a grep onto the tar command like this:

```
tar tzvf foo | grep "bar"
```

I get this creepy ouput:

```
gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors
```


The archive manager GUI can't open it either for pretty much the same reasons.  I looked it upa nd it seems like it could be an indication of corrupted data.  Is this data corrupted or what?

---

### Post by Pro-reason on 2008-10-10
It looks like it's corrupted.  Not much you can do about that.

---

### Post by porchrat on 2008-10-10
Can't extract for basically the same reasons mentioned above, but you know what don't worry about it I've managed to locate a copy (ordinary .tar not a .tar.gz) that extracts just fine and basically contains the same information so no worries.

Thanks anyway though...will mark thread as solved.

---

