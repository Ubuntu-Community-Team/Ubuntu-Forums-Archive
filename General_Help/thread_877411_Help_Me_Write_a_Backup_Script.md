---
title: "Help Me Write a Backup Script"
date: 2008-08-01
forum: General Help
---

### Post by moon2js on 2008-08-01
Can anyone lend me a hand with authoring a script?

I don't know a lot of intermediate or advanced stuff on the command line. And I haven't done something like this since the days o' DOS batch files.

What I want is a script that will grab a bunch of XML files on a public site and save them to /home/me/XMLbackup/dateofbackup on a weekly basis.

I have the list of files I want to grab and I can grab them with wget, but how do I save them into a folder named with the date of the backup? And how do I automate this to happen weekly (on a computer that is often on but not always)?

Any tips would be welcome.

---

### Post by scragar on 2008-08-01
store settings in a file in the download directory in a file called **list.txt**
```
#!/bin/bash
DATE=`date +%d%m%Y`
cd "/directory/to/store/files/in"
mkdir $DATE
cd $DATE
for i in $( cat ../list.txt ); do
  wget $i
done
```

[http://ubuntuforums.org/showthread.php?t=102625](http://ubuntuforums.org/showthread.php?t=102625) <-- look into crontab, there's also acron(which is best if the computer isn't on all the time), but there arn't any good guides covering that.

---

### Post by moon2js on 2008-08-02
That's awesome. Thank you.

I just noticed that the files I want to backup have really cryptic unhelpful (auto-generated) names, and when I save them to my computer, I'd like to rename them descriptively.

Can I adjust the for loop somehow to name appropriately? Maybe if my list.txt is laid out like this:

```
htpp://somewhere.com/asdfasdfasdfa.xml part_one.xml
http://somewhere.com/gasdgasgadsgg.xml part_two.xml
http://somewhere.com/gasgdafhrrfrg.xml part_three.xml
```

Or anything that works really.

---

### Post by scragar on 2008-08-02
```
**part_one.xml** htpp://somewhere.com/asdfasdfasdfa.xml
**part_two.xml** http://somewhere.com/gasdgasgadsgg.xml
**part_three.xml** http://somewhere.com/gasgdafhrrfrg.xml
```

and edited version of the code:
```
#!/bin/bash
DATE=`date +%d%m%Y`
cd "/directory/to/store/files/in"
mkdir $DATE
cd $DATE
tmp=""
for i in $( cat ../list.txt ); do
  if [ $tmp = "" ]; then
    tmp=$i
  else
    wget -O $tmp $i
    tmp=""
  fi
done
```although I haven't had a chance to test the edited version yet.

---

### Post by geirha on 2008-08-02
You could also make the file contain wget-arguments on each line. e.g.
```

htpp://somewhere.com/asdfasdfasdfa.xml -O part_one.xml
http://somewhere.com/gasdgasgadsgg.xml -O part_two.xml
http://somewhere.com/gasgdafhrrfrg.xml -O part_three.xml

```
And loop through it with:
[php]
#!/bin/bash
DATE=`date +%d%m%Y`
cd "/directory/to/store/files/in"
mkdir $DATE
cd $DATE

while read line; do wget $line; done < ../list.txt
[/php]

---

### Post by scragar on 2008-08-02
ooh, much shorter and easier, I have to learn more bash. :P

---

