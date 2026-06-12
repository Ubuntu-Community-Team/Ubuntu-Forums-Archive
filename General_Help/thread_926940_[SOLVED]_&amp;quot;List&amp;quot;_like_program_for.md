---
title: "[SOLVED] &amp;quot;List&amp;quot; like program for CLI?"
date: 2008-09-22
forum: General Help
---

### Post by Krupski on 2008-09-22
Hi all,

Is there a command line program for Ubuntu / Linux that functions like Vern Buerg's "list.com" for DOS?

In case you're not familiar, "list.com" when run displays files in the directory it's started from. Arrows scroll through filenames and "enter" displays the text of the file selected.

It's useful for browsing in a directory looking for a particular file by it's text.

Anything like this for Linux?

Thanks!

-- Roger

---

### Post by retrow on 2008-09-22
Since most of the documents have some kind of encoding it should be difficult to read the contents of files directly on the command line. On the other hand it should be very easy to search for contents of script files or .csv files where the contents are stored in normal ascii/unicode formats. This can be done with the help of a small shell script.

---

### Post by oldos2er on 2008-09-22
I could've sworn there was a *nix version of list, but I can't seem to find it. You might want to try the CLI file manager "mc," which has some list-like properties. mc is also called Midnight Commander.

---

### Post by PurposeOfReason on 2008-09-22
You could try 'ls 'directory' | less'

EX: 
ls /storage/music | less

---

### Post by koenn on 2008-09-22
> **Krupski said:**
> ...

It's useful for browsing in a directory looking for a particular file by it's text.

Anything like this for Linux?

Thanks!

-- Roger


```
grep -lr  "text you look for" /directory
```
will list all files in directory that contain "text you look for"

```
grep -r  "text you look for" /directory
```
will list all files in directory that contain "text you look for" + the lines of those files where 'text you look for" occurs

---

### Post by Krupski on 2008-09-22
> **PurposeOfReason said:**
> You could try 'ls 'directory' | less'

EX: 
ls /storage/music | less

I meant something more like this:

Initial view of a directory:


[IMG]http://home.roadrunner.com/~krupski/images/list-ex-1.jpg[/IMG]



Select a binary file:



[IMG]http://home.roadrunner.com/~krupski/images/list-ex-2.jpg[/IMG]



It's binary... so I want to view it in HEX mode:



[IMG]http://home.roadrunner.com/~krupski/images/list-ex-3.jpg[/IMG]



See? Kinda like that...


-- Roger

---

### Post by Krupski on 2008-09-22
> **oldos2er said:**
> I could've sworn there was a *nix version of list, but I can't seem to find it. You might want to try the CLI file manager "mc," which has some list-like properties. mc is also called Midnight Commander.


AWESOME!!! I just installed it! That's EXACTLY what I needed!!!

Thanks!

-- Roger

---

### Post by damis648 on 2008-09-22
Are you looking for 'ls'?

---

### Post by cariboo on 2008-09-22
Something else you may want to have a look at is mc, If you are old enough to remember Norton Commander, then you'll love mc. MC is available in the repositories. 

Jim

---

