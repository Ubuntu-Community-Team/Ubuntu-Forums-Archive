---
title: "Bash script to backup and clean junk from Music collection"
date: 2008-12-01
forum: General Help
---

### Post by Jive Turkey on 2008-12-01
I want sort through about 90GB of files for non-music junk files and I have a script that almost does it.  I am copying (i hope) the deleted files to a scratch area for final review before losing them altogether.  My problem is the files with spaces in the names are not picked up.

```
#!/bin/bash
#Based on code posted in this thread: http://ubuntuforums.org/showthread.php?t=822256&highlight=recursive+rm+file+type
SEARCHDIR=/home/ck/Music
DESTDIR=/home/ck/Desktop/nf
EXTS=(nfo m3u txt sfv wmv doc csv torrent)

for EXT in ${EXTS[@]}
do
	COUNTER=0
	for file in $( find $SEARCHDIR -name "*.$EXT" -type f )
	do
		BASENAME=$(basename $file .$EXT)
		FILENAME=$BASENAME
		while [ -e ${DESTDIR}/${FILENAME}.$EXT ]
		do
			COUNTER=$[$COUNTER+1]
			FILENAME=${BASENAME}${COUNTER}
		done
		cp $file ${DESTDIR}/${FILENAME}.$EXT
		rm -i $file ${SEARCHDIR}/${FILENAME}.$EXT
	done
done
```

Big thanks for any help picking up files with spaces in the names or for otherwise improving the script.

---

### Post by Wayne_V on 2008-12-01
You need to wrap the filenames, e.g:

BASENAME=$(basename "$file" .$EXT)

               FILENAME="$BASENAME"
        while [ -e "${DESTDIR}/${FILENAME}.$EXT" ]

---

### Post by Jive Turkey on 2008-12-01
> **Wayne_V said:**
> You need to wrap the filenames, e.g:

BASENAME=$(basename "$file" .$EXT)

               FILENAME="$BASENAME"
        while [ -e "${DESTDIR}/${FILENAME}.$EXT" ]

I don't think that will work since $file only gets the portion of the name before the space whether it is in quotes or not.

---

### Post by Wayne_V on 2008-12-01
You can change
                            for file in ...
to
                            find ... -type f | while read file
                            do
                                (whatever)
                            done

---

### Post by kaibob on 2008-12-02
Post deleted by Kaibob

---

