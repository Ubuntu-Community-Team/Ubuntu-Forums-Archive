---
title: "[SOLVED] Unable to delete files with unusual names"
date: 2008-08-25
forum: General Help
---

### Post by someone13 on 2008-08-25
Fantastic.

So I got these two files on my system that don't wanna be deleted.  Here's the filenames:
```
Â¤CÂ¼C1[1].5ÃÂ²Â¸Ã.w3x
Â¯uÂ¤TÂ°ÃªÂµLÃÃ¹V3[1][1][1][1].7d.w3x
```

Nice, eh?

rm -f won't work.  I've tried deleting them by their nodes and that won't work.  No matter what I do, I get the message: 
```
rm: cannot remove `Â¤CÂ¼C1[1].5ÃÂ²Â¸Ã.w3x': No such file or directory
```

Hell yeah.

Anyone have any idea as to how I can delete these two very annoying files?

Thanks,
Someone13

---

### Post by aloshbennett on 2008-08-25
try 'rm -i *'

worst case, take out everything else and delete the directory

---

### Post by ghostdog74 on 2008-08-25
> **someone13 said:**
> Fantastic.

So I got these two files on my system that don't wanna be deleted.  Here's the filenames:
```
Â¤CÂ¼C1[1].5ÃÂ²Â¸Ã.w3x
Â¯uÂ¤TÂ°ÃªÂµLÃÃ¹V3[1][1][1][1].7d.w3x
```

Nice, eh?

rm -f won't work.  I've tried deleting them by their nodes and that won't work.  No matter what I do, I get the message: 
```
rm: cannot remove `Â¤CÂ¼C1[1].5ÃÂ²Â¸Ã.w3x': No such file or directory
```

Hell yeah.

Anyone have any idea as to how I can delete these two very annoying files?

Thanks,
Someone13

try rm *.w3x

---

### Post by agasamapetilon on 2008-08-25
Try also:
```
rm -Rf /$HOME/directory
```

What this commands does is to remove recursively and if needed forced any directory or file, the example shows how it has to be used.

Be careful using it 'cause you could erase your entire disk if you made a type mistake.

---

### Post by BTMark on 2008-08-25
Be very careful with the above posted command, if executed improperly (in the wrong directory), it can cause severe damage.


asasamapetilon, you probably shouldn't be posting that kind of help, but if you have to (this thread can sort of apply), be sure that you outline the [COLOR="Sienna"][_possible outcomes_]("http://ubuntuforums.org/announcement.php?f=331")[/COLOR] of entering that command wrong.

---

### Post by Bachstelze on 2008-08-25
Tab or quotes are your friends. No need to use [FONT="Courier New"]rm -rf[/FONT].

```
rm "Â¯uÂ¤TÂ°ÃªÂµLÃÃ¹V3[1][1][1][1].7d.w3x"
```

or

```
rm Â<TAB>
```

---

### Post by agasamapetilon on 2008-08-25
> **BTMark said:**
> Be very careful with the above posted command, if executed improperly (in the wrong directory), it can cause severe damage.


asasamapetilon, you probably shouldn't be posting that kind of help, but if you have to (this thread can sort of apply), be sure that you outline the [COLOR="Sienna"][_possible outcomes_]("http://ubuntuforums.org/announcement.php?f=331")[/COLOR] of entering that command wrong.

Thanks BTMark, no prob.. I updated the post :)

---

### Post by prshah on 2008-08-25
> **someone13 said:**
> 
So I got these two files on my system that don't wanna be deleted.  Here's the filenames:
```
Â¤CÂ¼C1[1].5ÃÂ²Â¸Ã.w3x
Â¯uÂ¤TÂ°ÃªÂµLÃÃ¹V3[1][1][1][1].7d.w3x
```


Doesn't deleting it from nautilus work? 

It's the square brackets ("[]") that's causing problems, probably, try escaping them with "\". Autocompletion with tab should also work.

Failing all that, those filenames don't look valid to me. Maybe a fsck is in order (w3x is _supposed_ to be a World of Warcraft file).

---

### Post by someone13 on 2008-08-25
Thank you all for the replies.

Here's what I've tried thus far:
 - Command: rm -i ./*
 - Result: rm: cannot lstat `./¤C¼C1[1].5Â²¸Ë.w3x': No such file or directory
 - Command: rm ./"¤C¼C1[1].5Â²¸Ë.w3x"
 - Result: rm: cannot remove `./¤C¼C1[1].5Â²¸Ë.w3x': No such file or directory
 - Command: rm ./¤C¼C1\[1\].5Â²¸Ë.w3x
 - Result: rm: cannot remove `./¤C¼C1[1].5Â²¸Ë.w3x': No such file or directory

In Nautilus I can see the files, however the second I click on either file, they do a magic trick.  They're gone!  This is basically my own pencil-to-the-eye trick.

I'll try fsck later on, when I bring the server down.

These files are on a server, using an EXT3 partition on an external hard drive.  I've been trying to delete them through SSH on either Windows or Linux.  They do not show up in the Samba shares.

Outside, of fsck are there any other suggestions?

Thanks,
Someone13

---

### Post by ghostdog74 on 2008-08-25
> **someone13 said:**
> 
Outside, of fsck are there any other suggestions?

use ls -li to list the files' inodes (column 1). Take note of them, and use find to remove. eg 12345
```

find /path -name "*.w3x" -inum 12345 -exec rm -f {} \;

```

---

### Post by someone13 on 2008-08-26
Interesting, thank you for the suggestion.  Unfortunately when I try to get the inodes for those specific files using ls -li, I get this:

```
total 0
??--------- ? ? ? ?                ? ¤C¼C1[1].5Â²¸Ë.w3x
??--------- ? ? ? ?                ? ¯u¤T°êµLÂùV3[1][1][1][1].7d.w3x
```

I just now completed fsck, and prshah you were correct.  There were some corrupted files on the drive, and they were corrected by fsck.  After fsck was done, I went to go see if they had inodes now, and they did.  So I went to go delete them, and...

...I finally could.  Thanks a lot, everyone.


Someone13

---

### Post by prshah on 2008-08-26
> **someone13 said:**
> There were some corrupted files on the drive, and they were corrected by fsck.


OK! Now you probably should mark this thread solved; near the top right hand side of this page, click on "Thread Tools"-"Mark thread as solved".

---

