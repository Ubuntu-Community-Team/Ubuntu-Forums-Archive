---
title: "Bash script help"
date: 2008-10-21
forum: General Help
---

### Post by theacoustician on 2008-10-21
Hey all.  I'm trying to write a small bash script and not having any luck getting it to work properly.  I was hoping that someone here could take a look and tell me where I'm going wrong.  The script is supposed to pull an archive file, replace all the dates in the file with today's date and tomorrow's date, spit out a new file, and then load it into Oracle.  Here's what I've got:

```

#script tester.sh
#!/bin/bash
#Define variables
todaysDate=$(date +%Y%m%d)
tomorrowDate=$(date --date=tomorrow +%Y%m%d)
path=/home/scripts
cd $path
rm skedbase.txt
sed -e "s/20080729/$todaysDate/g" -e "s/20080730/tomorrowDate/g" skedbase.txt.old > skedbase.txt
su -l oracle -c "cd /oracle/scripts; ./runLoader.sh &"
exit 0

```

So I'm hitting two errors I don't understand.  First :
```
cd: 7: can't cd to /home/scripts
```
It doesn't say why it can't change directories.

The second problem is that it performs the sed operation correctly, but it spits out a file named 'skedbase.txt?' instead of 'skedbase.txt'.  I can't figure out why its doing that or how to fix it.

Suggestions?

---

### Post by Titan8990 on 2008-10-21
You should not us cd in a script. You should always use absolute paths. Example:

Instead of:

path=/home/scripts
cd $path
rm skedbase.txt

Do:

rm /home/scripts/skedbase.txt

---

### Post by theacoustician on 2008-10-21
> **Titan8990 said:**
> You should not us cd in a script. You should always use absolute paths. Example:

Instead of:

path=/home/scripts
cd $path
rm skedbase.txt

Do:

rm /home/scripts/skedbase.txt

Ok, good to know.  Any idea on why I keep getting a ? added to the end of the sed output file?

---

### Post by geirha on 2008-10-21
Firstly, make sure the sh-bang (#!/bin/bash) is the first line of the script.

The problem with the filename sounds like you've edited the file in windows, which uses \r\n instead of \n for a new line. So the ? in the filename probably represents a \r.

Use sed to remove \r from the end of the lines
```
sed -i 's/\r$//' script.bash
```

EDIT: Oh and to spot these things in the future try ```
cat -v script.bash
``` which will represent '\r's as ^M.

---

### Post by theacoustician on 2008-10-23
> **geirha said:**
> Firstly, make sure the sh-bang (#!/bin/bash) is the first line of the script.

The problem with the filename sounds like you've edited the file in windows, which uses \r\n instead of \n for a new line. So the ? in the filename probably represents a \r.

Use sed to remove \r from the end of the lines
```
sed -i 's/\r$//' script.bash
```

EDIT: Oh and to spot these things in the future try ```
cat -v script.bash
``` which will represent '\r's as ^M.

Just wanted to update and say this worked.  Thanks!

---

