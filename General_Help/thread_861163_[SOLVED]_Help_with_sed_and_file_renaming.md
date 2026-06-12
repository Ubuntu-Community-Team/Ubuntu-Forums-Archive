---
title: "[SOLVED] Help with sed and file renaming"
date: 2008-07-16
forum: General Help
---

### Post by peeple on 2008-07-16
Im trying to rename multiple files by changing spaces and dashes to periods (decimals) and removing anything in square brackets and/or parentheses. that also doesn't leave two periods in a row. (ie NOT file.beta..1..ext)

in essence: filename - date (created by).avi --> filename.date.avi

if anyone can give me some more presice direction id appreciate it.

ive been looking at [this]("http://www.grymoire.com/Unix/Sed.html") sed tutorial with [this]("http://6v8.gamboni.org/Mass-renaming-with-linux-shell.html") script but havent gotten my head around sed yet.

maybe seeing something im trying to accomplish will help me out. thanks.

---

### Post by apswartz on 2008-07-18
```
echo "filename - date (created by).avi" \
  |sed 's/ - /\./' \
  |sed 's/ ([ a-zA-Z0-9]*.)//'
```

is the basic code you want.

Try this...

```
#!/bin/sh

TEMPLIST=/tmp/tempfile.`date +%s`_$RANDOM
ls -- *.avi  >$TEMPLIST 2>/dev/null

while read FileFromList
   do
      NewName=`echo "${FileFromList}" \
         |sed 's/ - /\./' \
         |sed 's/ ([ a-zA-Z0-9]*.)//'
      # to create a new file with new name
      cp "${FileFromList}" "${NewName}"  
      # to rename the file (a little more dangerous)
      #mv "${FileFromList}" "${NewName}"  
    done < $TEMPLIST

rm -f $TEMPLIST
```

---

### Post by mc4man on 2008-07-18
@ apswartz
If you have a moment, what is the reason the script moves in, then out? Appears to be in spaces of 3.

---

### Post by dcstar on 2008-07-18
> **mc4man said:**
> @ apswartz
If you have a moment, what is the reason the script moves in, then out? Appears to be in spaces of 3.

Writing any code with indents makes it easier for humans to understand. Indents show blocks of code controlled by various sections.

It is standard practice for anyone who has elevated themselves from the knuckle-dragging beginnings of writing computer code (where the code language allows it).

---

### Post by apswartz on 2008-07-18
dcstar is correct. The whitespace is for the benefit of human readers.

For the same reason a long line can be broken up such as...

```
    NewName=`echo "${FileFromList}" \
        |sed 's/ - /\./' \
        |sed 's/ ([ a-zA-Z0-9]*.)//'
```

Notice the first two lines end with a \ character, which in bash means the command continues to the next line. In other words, those three lines are actually 1 long command.

---

### Post by ghostdog74 on 2008-07-18
don't even have to use sed 2 times. you can use -e option of sed.

---

### Post by peeple on 2008-07-21
thanks, now if i could only use it. :'(

haha, i ran > ls > ../rename.sh and that obviously didnt work.


do i need to put this in my nautilus scripts or somethin?

---

### Post by KeyserSoze93 on 2008-07-21
make a shell scipt with this in, then run it:

> #!/bin/bash

for i in *.avi
do

a=`echo $i | sed 's/ /\./g'`

mv "$i" "$a"

done

---

### Post by apswartz on 2008-07-21
> **peeple said:**
> thanks, now if i could only use it. :'(

haha, i ran  and that obviously didnt work.


do i need to put this in my nautilus scripts or somethin?

To create a shell script you need to create it with a text editor.
Copy the text of the script you want to use in your text editor and save it.
Open up a terminal window and cd to the directory where the script is.
     e.g., **cd /path/to/script**
when there, make it executable.
     e.g., **chmod +x script**
Then you can run the script...
     **./script**
Or, if you didn't save the script where your avi files are, go there
     e.g, **cd /path/to/avifiles**
Then run the script...
     **e.g., /path/to/script**

That should work.

---

### Post by peeple on 2008-07-21
> 18: Syntax error: EOF in backquote substitution


i think that red one was missing

```
#!/bin/sh

TEMPLIST=/tmp/tempfile.`date +%s`_$RANDOM
ls -- *.avi  >$TEMPLIST 2>/dev/null

while read FileFromList
   do
      NewName=`echo "${FileFromList}" \
         |sed 's/ - /\./' \
         |sed 's/ ([ a-zA-Z0-9]*.)//'[COLOR="Red"]`[/COLOR]
      # to create a new file with new name
      cp "${FileFromList}" "${NewName}"  
      # to rename the file (a little more dangerous)
      #mv "${FileFromList}" "${NewName}"  
    done < $TEMPLIST

rm -f $TEMPLIST
```

---

### Post by apswartz on 2008-07-21
yep, you are right!

---

