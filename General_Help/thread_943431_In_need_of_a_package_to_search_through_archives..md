---
title: "In need of a package to search through archives."
date: 2008-10-10
forum: General Help
---

### Post by porchrat on 2008-10-10
Hello all hopefully I can get some suggestions from you.

I'm looking for a package of some sort (preferably from the repositories although I'm not shy about having to use build-essential and dpkg if necessary).

Basically I need a package that will perform a find or grep function, but will take archived files (at least these types: .zip, .tar.gz and .tar) as well as normal uncompressed files as input.  I have a lot of files to search through (many of which are large archives) and I really don't want to have to do it manually (i.e. open each one...do a grep...move on).

i.e. it needs to open the archive, look through it and move on.  Preferably without extracting anything, but again if it has to extract things I'll clean up the mess afterwards.

It needs to be automated, i.e. I give it a large input and I walk away and when I come back it has given me a list so that I can then narrow my search.  I really don't want a browser that also happens to be able to open archives, I need either the "find" or "grep" functions.

If any of you know of something like this please let me know.

---

### Post by porchrat on 2008-10-10
I wouldn't mind a shell script that did that either by the way...I managed to locate this...looked promising, but there seems to ba a syntax issue:

 grab () {
find / -iname "*.tar.gz" -exec tar tz -f '{}' \; | grep $1
find / -iname "*.tar" -exec tar t '{}' \; | grep $1
find / -iname "*.zip" -exec unzip -l '{}' \; | grep $1
}
grab file-you're-looking-for

Anyone got any ideas on refining this little bugger?  obviously I wouldn't be looking through nearly as high up as root.  All I'll do is place everything I need to search through in a file on the Desktop, thus it would read "find ~/Desktop" instead of "find /".

---

### Post by porchrat on 2008-10-10
OK refined it a little:

```
#!/bin/sh

 grab () {
find ~/Desktop/filename/ -iname "*.tar.gz" -exec tar tz -f '{}' \; | grep $1
find ~/Desktop/filename/ -iname "*.tar" -exec tar t '{}' \; | grep $1
find ~/Desktop/filename/ -iname "*.zip" -exec unzip -l '{}' \; | grep $1
}
grab "string"

exit 0
```

Let me know what I'm doing wrong as it seems to do nothing.

---

### Post by hyper_ch on 2008-10-10
maybe Tracker helps... it's a file content indexing tool and it seems it will also look into archive files... not sure though.

---

### Post by porchrat on 2008-10-10
> **hyper_ch said:**
> maybe Tracker helps... it's a file content indexing tool and it seems it will also look into archive files... not sure though.

Will take a look...thanks for the tip :)

---

