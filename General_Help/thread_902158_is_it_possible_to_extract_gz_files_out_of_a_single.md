---
title: "is it possible to extract gz files out of a single file?"
date: 2008-08-27
forum: General Help
---

### Post by windreiter on 2008-08-27
Hi,

Because of a misuse of the gzip-command, several files from subfolders where written into one single file:
```
gzip -rvc -1 /destination/folder/* > /target/folder/output.gz
```

Is it now possible to extract these single gz-files, that were written appendingly bit by bit, e.g. with "sed"? Is there a specific byte sequence like "EOF" in txt-files that can be used for determination if a "new" gz-file begins?

Thanks in advance,
windreiter

---

### Post by amitkher on 2008-08-27
You can gunzip this gz file, and you will get a concatenation of your input files. It would be easier to figure out file boundaries as the content will be readable
```

gunzip /target/folder/output.gz

```

---

### Post by windreiter on 2008-08-27
Using ghex, I figured out that every gz-file starts with the byte-combination "1F 8B 08 08".
Several "random" bytes are following, then the original file name is printed as plain text. A gz-file stops with "00".

What possibilities do I have to get my single gz-files back?
What would be appropriate sed options (for example: "put everything between two "1F 8B 08 08" in a new file and add "1F 8B 08 08" at the beginning?

Thanks!

---

### Post by amitkher on 2008-08-27
Why don't you gunzip the whole gzip file like I mentioned above?

I don't see any header or filename appearing when I gzip 2 files using the command you gave.

---

