---
title: "shell script - swap file contents"
date: 2008-09-30
forum: General Help
---

### Post by madhatter563 on 2008-09-30
If I am writing a shell script and I want the script to swap the contents of two files I give it, how would I go about doing that?  I'm used to thinking in JAVA, which would require a printstream.  Any ideas? Thanks!

---

### Post by kk0sse54 on 2008-09-30
Here are two links that I hope will help 

Shell scripting resource with a bunch of links to tutorials and such:
[http://www.shelldorado.com/](http://www.shelldorado.com/)

in depth view into Bash scripting:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by spibou on 2008-09-30
```

#!/bin/sh
f=tyfg345
i=1
while [ -e /tmp/$f$i ] ; do
    i=$(( $i + 1 ))
done
mv "$1" /tmp/$f$i
mv "$2" "$1"
mv /tmp/$f$i "$2"

```
Not tested.

---

### Post by ryanhaigh on 2008-09-30
If just moving the files isn't what you want you can use cat, this still requires a temp file though.

```

#!/bin/bash
#$1 is the first argument aka filename, $2 is the second
#both should be quoted to avoid issues with spaces is names
#eg. script.sh "~/file name1.txt" "~/filename2.txt"
TEMP=/tmp/tempfile
#copy from file 2 to tempfile
cat "$2" > "$TEMP" &&
#copy contents of file 1 into file 2
cat "$1" > "$2" &&
#copy from tempfile to file 1
cat "$TEMP" > "$1" &&
echo "done"
exit

```

---

