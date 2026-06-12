---
title: "Extract certain bytes from a huge file"
date: 2008-08-29
forum: General Help
---

### Post by phroughy on 2008-08-29
Basically my question is, Is there a way to extract say 3k bytes before and after byte 11081576517 in a file?

Background Story:
So, me being a moron, never backed up any of the stuff on my web server. And for reasons unknown, certain portions of my home folder have been deleted/disappeared. Nothing of irreplaceable value was lost, however much of my web development portfolio is missing :(

I have looked in lost+found, and I have tried running various undelete software on the drive but to no avail. I have read several places that things like debugfs won't work on Ext3.

So, in a last ditch effort i created a very large file (18gigs) with a dump of everything on the drive (luckily its a small drive). I have run several grep commands looking for things that I need most. For example: search for "define(WEB_ROOT," and tell my what byte its at.

```
grep -ba "define(WEB_ROOT," "Server.dsk" >> grep_out_webroot
```

returns:

```
436326469:define(WEB_ROOT,"http://mywebsite.com/"); 
436330565:define(WEB_ROOT,"http://mywebsite.com/"); 
444612677:define(WEB_ROOT,"http://mywebsite.com/"); 
444616773:define(WEB_ROOT,"http://mywebsite.com/"); 
453050419:define(WEB_ROOT,"http://mywebsite.com/"); 
470487109:define(WEB_ROOT,"http://mywebsite.com/"); 
470491205:define(WEB_ROOT,"http://mywebsite.com/"); 
470503493:define(WEB_ROOT,"http://mywebsite.com/"); 
470556741:define(WEB_ROOT,"http://mywebsite.com/"); 
11081572421:define(WEB_ROOT,"http://mywebsite.com/"); 
11081576517:define(WEB_ROOT,"http://mywebsite.com/"); 
```

So the question is this: I know that a portion that matches a file i want is at byte 11081576517. How do i extract for example 3k bytes before and after that? I have tried looking at sed but can't really make heads or tails of it.

Thanks for your help!

---

### Post by monkeyking on 2008-08-29
I think grep matches lines not bytes.

So the number you have are the line numbers.

But check it, if it is the line numbers,
you can extract certain line ranges using head tail.

get line 75-100 a file would be

```

head -n100 INFILE |tail -n25

```

sorry, I just saw you used -ba in your grep

---

### Post by monkeyking on 2008-08-29
I just checked your command,
why exactly isn't it working with 
grep -b INFILE

remember to give an offset after -b like grep -b10 INFILE

---

### Post by phroughy on 2008-08-30
Yeah, i should have mentioned about the -ba part, the first time i tried without the a it didn't work at all. 

So I tried this

```
grep -a -b100 "define(WEB_ROOT," "Server.dsk" >> grep_out_webroot2
```

and it turned out all kinds of interesting things, including the files i want (multiple times i'm afraid, i assume that they are different like different saves, but i haven't looked close yet) the files are easy to tell apart since there are usually lots of null chars between them, This is going to work i think!

I looked in **grep --help** and **man grep** and i have no idea what the -b100 does. i tried experimenting and i think that it gets 100 lines before and after, which is exactly what i want, but i don't see it documented...

Thanks again!

---

