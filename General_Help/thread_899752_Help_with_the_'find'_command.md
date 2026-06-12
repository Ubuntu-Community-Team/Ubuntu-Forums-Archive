---
title: "Help with the 'find' command"
date: 2008-08-24
forum: General Help
---

### Post by risager on 2008-08-24
I have what should be a simple problem with the find command. 

Short story:
I want to run a specific command in all folders below a certain level. How do I do that using find?

Long story:
I have a bunch of mp3's stored in folders according to artist and album. Each album folder contains the mp3's and a file called folder.jpg which contains the Cover of the album. I want to embed the folder.jpg into the mp3's which can be done using 

```
eyeD3 --add-image=folder.jpg:FRONT_COVER *.mp3

``` 

executed within each directory. How do I do that recursively for all the directories. I know that 'find' but cannot find out how!

---

### Post by spupy on 2008-08-24
For example
```
cd Music/
find . -mindepth 3 -name *jpg
```

Also, thanks for the program! I was looking for something like eye3D for a long time. When you write your script to embed the folder.jpg please paste it here. :)

---

### Post by risager on 2008-08-24
> **spupy said:**
> When you write your script to embed the folder.jpg please paste it here. :)

This finds all my folder.jpg files which is not exactly what I wanted to do. I dont even intend to write a shell script but just one find command to do the whole thing a la

```

cd /mp3/
find "all folders" -exec 'eyeD3 command executed in the folders found by find' 
```

I just do not know how to convert that into proper find syntax.

---

### Post by spupy on 2008-08-24
How about that:
```
find . -type d -exec eyeD3 --add-image="{}/folder.jpg":FRONT_COVER '{}'/*mp3 \;
```

I haven't tried it yet. Beware!

---

### Post by risager on 2008-08-24
> **spupy said:**
> How about that:
```
find . -type d -exec eyeD3 --add-image="{}/folder.jpg":FRONT_COVER '{}'/*mp3 \;
```

I haven't tried it yet. Beware!

Outputs:

```
find . -type d -exec eyeD3 --add-image="{}/folder.jpg":FRONT_COVER '{}'/*mp3 \;
File Not Found: ./*mp3
File Not Found: ./Till the end of time/*mp3

```

---

### Post by spupy on 2008-08-24
> **risager said:**
> Outputs:

```
find . -type d -exec eyeD3 --add-image="{}/folder.jpg":FRONT_COVER '{}'/*mp3 \;
File Not Found: ./*mp3
File Not Found: ./Till the end of time/*mp3

```

This one is close to working. "dirname {}" should return the path of the file, here it alsways returns "." which is of no use. We need a command that given a filename returns its full path.

**DONT RUN THIS ONE**:
```
find . -name *mp3 -exec eyeD3 --add-image=`dirname {}`/folder.jpg:FRONT_COVER '{}' \;
```

---

### Post by spupy on 2008-08-24
This is what I got:
I can't do it without an extra small script. This is the script:
```
#!/bin/bash
fpath=`echo "$1" | grep -o "^.*/" | sed 's/\/$//g'`
folderJpg=$fpath/folder.jpg
eyeD3 --add-image=$folderJpg:FRONT_COVER "$1"
```

Place it in your Music folder where you invoke find:
```
find . -name *mp3 -exec putPic.sh '{}' \;
```

---

### Post by panayk on 2008-08-24
> **spupy said:**
> This one is close to working. "dirname {}" should return the path of the file, here it alsways returns "." which is of no use. We need a command that given a filename returns its full path.

**DONT RUN THIS ONE**:
```
find . -name *mp3 -exec eyeD3 --add-image=`dirname {}`/folder.jpg:FRONT_COVER '{}' \;
```

The problem is that bash is doing command substitution before executing find, i.e. you are running dirname on the raw string "{}".

How about this (not tried):

```
find . -name *.mp3 -exec bash -c 'eyeD3 --add-image=`dirname {}`/folder.jpg:FRONT_COVER {}' \;
```

---

### Post by ghostdog74 on 2008-08-24
> **risager said:**
> I have what should be a simple problem with the find command. 

Short story:
I want to run a specific command in all folders below a certain level. How do I do that using find?

Long story:
I have a bunch of mp3's stored in folders according to artist and album. Each album folder contains the mp3's and a file called folder.jpg which contains the Cover of the album. I want to embed the folder.jpg into the mp3's which can be done using 

```
eyeD3 --add-image=folder.jpg:FRONT_COVER *.mp3

``` 

executed within each directory. How do I do that recursively for all the directories. I know that 'find' but cannot find out how!

you can try the find command with the -execdir option
```

find /path -type f -name "folder.jpg" -execdir yourcommand {} +

```
check the man page of find for syntax and usage

---

### Post by risager on 2008-08-25
OK, I think I solved it. The one line that does the job is 

```
find -type f -name "*.mp3" -execdir eyeD3 --add-image=folder.jpg:FRONT_COVER {} \; 
```
I couldn't get it to work for some time but the problem was in the existing id3 tag. I was using an old v1.1 and apparently eyeD3 wasn't able to embed the image into that. So after converting all my mp3's to v2.4 the above worked smoothly. The conversion to v2.4 can be done using the command

```
find . -name "*mp3" -exec eyeD3 --to-v2.4 {} \; 
```

Thanks for all the pointers

---

