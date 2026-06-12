---
title: "ls &gt; output file"
date: 2008-08-16
forum: General Help
---

### Post by heiNey on 2008-08-16
Hi,

I was wondering if it was possible to use the ls > command to output the result to a file AND append a text string to the end.

For example, if I ls a pictures directory, i want the output file to have:

picture1.jpg:textstring
picture2.jpg:textstring
picture3.jpg:textstring etc...

as of right now, it just lists:

picture1.jpg
picture2.jpg
picture3.jpg etc...

---

### Post by ghostdog74 on 2008-08-16
```

for files in *.jpg
do
   echo "${files}:textstring"
done

```

---

### Post by heiNey on 2008-08-21
great...thank you

another question...is there a way to randomize this output instead of alphabetical order?

and also put the output to a file...what im having to do is copy and paste to a file and would like to eliminate that step.

EDIT: nevermind, figured out the outputting to a file; used >>.  still need help with the randomizing though.

---

### Post by ghostdog74 on 2008-08-21
> **heiNey said:**
> great...thank you

another question...is there a way to randomize this output instead of alphabetical order?

what do you want to achieve?

---

### Post by heiNey on 2008-08-21
> **ghostdog74 said:**
> what do you want to achieve?

basically im trying to use dvd-slideshow to create slideshow and it needs a listing of all the pictures in a directory in a txt file.  right now its just  creating the dvd with the pictures in alphabetical order, since thats how theyre being listed in the txt file

---

### Post by ghostdog74 on 2008-08-21
```

awk '{ a[++d]=$0 }END{for(o in a) print a[o]}' file_to_shuffle

```

---

