---
title: "Is this code OK to run?"
date: 2008-09-26
forum: General Help
---

### Post by phr0ze on 2008-09-26
Hi, 

I just want to make sure this command wont erase my HDD or anything. Please see the snippet below which is supposed to make a small file a specific size. (Pad)

> ```
usage: ./script DesiredName.dmp

echo "Processing ${1}" nc -l 9090 > "$1" dd if/dev/zero bs1k count512 > zero dd if"$1" ofzero convnotrunc mv "$1" "old/${1}" mv zero "$1"

For those who don't know bash: it saves the raw dump as DesiredName.dmp, makes a 512k file filled with 00s, named "zero" then injects DesiredName.dmp into the beginning of "zero", moves DesiredName.dmp (the raw dump) into old/, and then moves the padded .dmp back to DesiredName.dmp
```


All I need to do is pad a batch of files out to a specified size.

Thanks

---

### Post by lewiz on 2008-09-27
looks reasonable to me.  you can see that all of the dd commands read from /dev/zero or write to basic files.  there's no /dev/sdaX, etc.

i have no idea why it reads from port 9090, but i guess you'll have a better idea

good luck

---

