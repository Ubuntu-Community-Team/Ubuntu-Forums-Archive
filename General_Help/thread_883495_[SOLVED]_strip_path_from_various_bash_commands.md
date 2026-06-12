---
title: "[SOLVED] strip path from various bash commands"
date: 2008-08-08
forum: General Help
---

### Post by PGScooter on 2008-08-08
Hi,

I suppose I could do this in perl, but I am assuming there is an easier way.

I used the du command with two folders because I wanted to compare folders to see which files had different sizes. I thought I could do this with diff, but I can't because every line is different! This is because the absolute path is included in the output of the following command:
```

du -ab folder1/

```

how can I strip the path so that just the filenames appear?

Thanks

---

### Post by damoxc on 2008-08-08
```
du -ab folder1 | awk '{print $2}'
```
That'll do the trick.

---

### Post by ghostdog74 on 2008-08-08
> **damoxc said:**
> ```
du -ab folder1 | awk '{print $2}'
```
That'll do the trick.

no, that will not work if the file name have spaces

---

### Post by damoxc on 2008-08-08
True, this will work
```
du -ab folder1 | sed -r s/[0-9]+\s*//g
```

---

### Post by decoherence on 2008-08-08
> **ghostdog74 said:**
> no, that will not work if the file name have spaces

This particular command's output separates each field with a tab, thus

```
du -ab folder1 | awk -F\\t '{print $2}'
```

should do the job. All we've done it set tab (the double-escaped t) as the field delimiter using the -F flag. as you saw, the default is any whitespace.

You can also use the command 'basename' though it expects just a path... not that other stuff your command outputs.

---

### Post by PGScooter on 2008-08-08
great, thanks! Yeah, I was trying to work with basename, but I guess that was the wrong approach.

---

### Post by PGScooter on 2008-08-08
How can I do this with a Perl filter?

---

### Post by PGScooter on 2008-08-08
nevermind, I got it. This is what I was trying to do:

```

du -ab /home/scott/ann\ data/ | perl -ne 'print "$1\t$2\n" if (/(\d*).*\/(hs.*\.dta)/)'

```

---

