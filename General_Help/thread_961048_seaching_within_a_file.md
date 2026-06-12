---
title: "seaching within a file"
date: 2008-10-27
forum: General Help
---

### Post by ali_williams on 2008-10-27
Hey guys I am looking for all documents on my pc that as the words "WebKmail" in it. I need it to pull together all of the documents for work. Anyway is there a way in ubuntu to search within a file?

---

### Post by ali_williams on 2008-10-27
> **ali_williams said:**
> Hey guys I am looking for all documents on my pc that as the words "WebKmail" in it. I need it to pull together all of the documents for work. Anyway is there a way in ubuntu to search within a file?

forgive me i forgot about the grep command.

---

### Post by alienprdkt on 2008-10-27
I'm imagining all you do is 
#grep "WebKmail" *


Heres an example: 
The simplest use of grep is to look for a pattern consisting of a single word. It can be used in a pipe so that only those lines of the input files containing a given string are sent to the standard output. But let's start with an example reading from files: searching all files in the working directory for a word--say, Unix. We'll use the wildcard * to quickly give grep all filenames in the directory.

    $ grep "Unix" *
    ch01:Unix is a flexible and powerful operating system
    ch01:When the Unix designers started work, little did
    ch05:What can we do with Unix?
    $

---

### Post by sdennie on 2008-10-27
As you said, "grep" is your friend in this case.  Other useful hints would be the "-r" (recursive) flag to grep, the find command and possibly the strings command.

---

### Post by alienprdkt on 2008-10-27
scrath that you need:
#ls -l | grep "WebKmail"
I believe this is correct...
example:
When grep searches multiple files, it shows the filename where it finds each matching line of text. Alternatively, if you don't give grep a filename to read, it reads its standard input; that's the way all filter programs work:

    $ ls -l | grep "Aug"
    -rw-rw-rw-   1 john  doc     11008 Aug  6 14:10 ch02
    -rw-rw-rw-   1 john  doc      8515 Aug  6 15:30 ch07
    -rw-rw-r--   1 john  doc      2488 Aug 15 10:51 intro
    -rw-rw-r--   1 carol doc      1605 Aug 23 07:35 macros
    $

---

### Post by sdennie on 2008-10-28
> **alienprdkt said:**
> scrath that you need:
#ls -l | grep "WebKmail"
I believe this is correct...
example:
When grep searches multiple files, it shows the filename where it finds each matching line of text. Alternatively, if you don't give grep a filename to read, it reads its standard input; that's the way all filter programs work:

    $ ls -l | grep "Aug"
    -rw-rw-rw-   1 john  doc     11008 Aug  6 14:10 ch02
    -rw-rw-rw-   1 john  doc      8515 Aug  6 15:30 ch07
    -rw-rw-r--   1 john  doc      2488 Aug 15 10:51 intro
    -rw-rw-r--   1 carol doc      1605 Aug 23 07:35 macros
    $

I think that depends on how you read the original post.  If "all documents with 'blah' in it" means "all documents named *blah*", then, yes you are correct.  However, your "ls -l | grep 'Aug'" matches those files because they were modified in August and not because they contain the string "Aug".

The way I read the post made me think what was needed was a:

```

grep -r "some_string_to_look_for" some_directory

```

That would find all the files in some_directory and its subdirectories that have the string "some_string_to_look_for".  You could further use grep flags to clean that output down to just a file list (and even unique file list if you wanted).

---

### Post by alienprdkt on 2008-10-28
I see what your saying.

thanks for the clarifacation :) 

I am still pretty new at this... (linux user 8months)

---

### Post by sdennie on 2008-10-28
> **alienprdkt said:**
> I see what your saying.

thanks for the clarifacation :) 

I am still pretty new at this... (linux user 8months)

It doesn't matter if it's 8 days, 8 months or 8 years.  You always learn more on the forums.  ;)

---

