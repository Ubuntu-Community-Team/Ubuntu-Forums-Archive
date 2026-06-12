---
title: "shell script and sql"
date: 2008-08-08
forum: General Help
---

### Post by dapim on 2008-08-08
i have file with this numbers, 1 per line

345
456
7567
5785

and want that shell script, will catch this numbers and do this statment for all nunbers

update perdat SET age=354(alll the numbers i would like to put here);

how can i do this?

---

### Post by Titan8990 on 2008-08-08
Do you already know what the numbers are or do you need it to just read one line at a time?

---

### Post by dapim on 2008-08-08
i need to read the numbers from the file, each time can be diferent numbers

---

### Post by aaronanderson on 2008-08-08
How about something like this:

```

#!/bin/bash
allnumbers=
for number in `cat file`
do
    allnumbers=`echo $allnumbers $number`
done
echo update perdat SET age $allnumbers

```

This assumes the input file name is called file. Change the cat statement to whatever you need.

---

