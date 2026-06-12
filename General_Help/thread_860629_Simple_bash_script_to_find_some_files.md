---
title: "Simple bash script to find some files"
date: 2008-07-15
forum: General Help
---

### Post by ceviche on 2008-07-15
I have a series of directories with subdirectories with photos inside. I want to write a bash script that goes recursively through them and shows me a list of each file with the "]" character in it. Can anyone show me how to do this?

i.e. something like...

FOR EACH DIRECTORY RECURSIVELY
 ls -A | grep ]
END FOR

or better yet to a text file

FOR EACH DIRECTORY RECURSIVELY
 ls -A | grep ] > list.txt
END FOR

or better yet, with the path to the file /img/img2/img[1].jpg

Thanks!

---

### Post by sdennie on 2008-07-15
Try:

```

find . -name "*\[*"

```

You can use that as your loop like this:

```

for image in `find . -name "*\[*"` ; do
   echo Do something to $image
done

```

Or, if you are doing something fairly easy to each of those images, you can use regular find syntax like this:

```

find . -name "*\[*" -exec echo Do something to '{}' \;

```

---

### Post by ceviche on 2008-07-15
Gracias vor.

---

### Post by ghostdog74 on 2008-07-15
> **vor said:**
> Try:

```

for image in `find . -name "*\[*"` ; do
   echo Do something to $image
done

```


note that this will break if file name contains spaces. use a while read loop
```

find .... | while read FILE
do
 ....
done

```
or try putting double quotes around the find command
```

for image in "`find.....`"

```

---

