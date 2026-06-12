---
title: "Grep to remove files"
date: 2008-08-12
forum: General Help
---

### Post by VenisonMogambi on 2008-08-12
Is there a way to grab a bunch of files in a directory matching a text string, then delete them? This came up as I was capturing video using Kino and because of the way I had Kino set up, I ended up with dozens of these files in my directory. Rather than removing them one by one, I figured there must be some way to grep them all then pipe to delete them. For example, I tried something like this (all the files capture files are called kino_dv_capture001, kino_dv_capture002, and so on):

grep kino* | rm

But this command didn't work. Any ideas?

Thanks.

---

### Post by PGScooter on 2008-08-13
NOTE: I HAVE NOT TESTED ANY OF THE FOLLOWING CODE, ALWAYS BE CAREFUL WHEN DELETING, AND DO NOT DO SO UNDER ROOT (UNLESS YOU HAVE TO OF COURSE)

I think the following code should work:
```

rm kino*

```

I think you are using grep poorly there because if you give it files, it will look IN those files, not AT those files. However, you could pipe ls to grep, then that might be better. If you really want to do it like that, maybe you could do:
```

rm `ls | grep kino`

```
remember, those are backticks, not quotes.
did either of those work?

---

### Post by jerome1232 on 2008-08-13
another way, but rm kino* should work just fine
```
find kino* -delete
```

---

### Post by VenisonMogambi on 2008-08-13
Thanks for the tips, I'll try it out. I suppose I have to make sure I'm in that specific directory before I do a rm kino*, correct? Otherwise I'd remove all kino files throughout the entire filesystem, right?

---

### Post by jerome1232 on 2008-08-13
Yes with both commands, ie if the files were in /home/user/temp
then
```
rm /home/user/temp/kino*
``` is what I would use to guarantee it removes from the correct directory

or  

```
find /home/user/temp/kino* -delete
```

---

### Post by PGScooter on 2008-08-13
jerome's commands are the best because like he says, they make sure to get the right directory.

however, to directly answer your question, if you are in that specific directory and are lazy like me and don't want to write the long version, you can use the ones previously mentioned.

How can you be sure which directory you're in?
```

pwd

```

---

### Post by asnani_satish on 2009-08-02
grep -lir 'string to search in files'  * |xargs rm -rf

Options
l - for listing file name only
i - ignore case while searching
r - search recursively within sub directories also
xargs - the list of files from grep command are passed as parameter to "rm -rf" command

---

