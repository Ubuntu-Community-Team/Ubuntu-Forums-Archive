---
title: "grep - how to show only filenames with hits"
date: 2008-07-15
forum: General Help
---

### Post by Hopworks on 2008-07-15
I hope this isn't too stupid of a question but I didn't even know about grep until this morning.

I've been using ```
find . | xargs grep -snH "my text" --color
``` to search for text inside a directory and the sub directories. It works great, but I can't figure out how to show just the filenames and not the line that had the hit. Actually, I would like to know how I can format that output in a custom way.

I feel I'm on the edge of a Linux breakthrough (for me that is) here, something I didn't know for a long time and are about to find out. An 'AH!' moment. :)

Oh, I tried the -c option but it lists ALL the files. I want the ones that have 1 or more occurrences of 'my text'. 
A small portion of the output...```
./phpBB2/includes/auth.php:0
./phpBB2/includes/template.php:0
./phpBB2/includes/bbcode.php:0
./phpBB2/includes/db.php:0
./phpBB2/includes/sixmods_welcome.php:2
./phpBB2/includes/functions_search.php:0
./phpBB2/includes/xs_news.php:0
```
I'd prefer to have this listing with just ```
./phpBB2/includes/sixmods_welcome.php:2
```outputted.

Thank you for your time!

EDIT: I realize that the --color option won't be necessary when I figure out how to just list the files with a hit.

---

### Post by jonlemur on 2008-07-15
If the filenames are all listed first, and they are separated by a space, you should be able to use something like```
find . | xargs grep -snH "my text" --color | cut -f1 -d' '
``` where f1 tells it to cut field 1 as separated by the delimiter ' ' (space).  If that doesn't work, try "man cut" to see more options for that commands.

EDIT: [This site]("http://www.computerhope.com/unix/ucut.htm") may also help figure out cut.

---

### Post by inteluser on 2008-07-15
You could add another grep in the pipeline: | grep :[^0] will get rid of all the lines that have :0 in them.

---

### Post by jonlemur on 2008-07-15
Ah, I think I misunderstood the question.  I was thinking that there was more output after the filename that you wanted to truncate.  It looks like grep again should do it.

---

### Post by lswb on 2008-07-15
grep itself has an option to list only filenames with matches;

grep -l "searchstring" filespec

From "man grep"

 -l, --files-with-matches
              Suppress  normal  output;  instead  print the name of each input
              file from which output would normally have  been  printed. ...

---

### Post by Hopworks on 2008-07-16
> **lswb said:**
> grep itself has an option to list only filenames with matches;

grep -l "searchstring" filespec

From "man grep"

 -l, --files-with-matches
              Suppress  normal  output;  instead  print the name of each input
              file from which output would normally have  been  printed. ...the rest of the man grep for that option also says...
 The scanning will stop on the first match.

which is why I am not using it. I need to find all the files recursively. Sorry I didn't mention that earlier.

> You could add another grep in the pipeline: | grep :[^0] will get rid of all the lines that have :0 in them.
This worked great for me. Thank you!
EDIT: I found a small issue with this approach. If the filename is, say, 'my_file 0.text' with a space before the zero, the above approach will not list it, even if it has the search text in it. I need to expand my knowledge of regular expressions to find a way to get around that. The files I am searching have no spaces in the file names so this still works for me, but if I use it for other needs, this problem can occur.

> If the filenames are all listed first, and they are separated by a space, you should be able to use something like
Code:

find . | xargs grep -snH "my text" --color | cut -f1 -d' '

where f1 tells it to cut field 1 as separated by the delimiter ' ' (space). If that doesn't work, try "man cut" to see more options for that commands.

EDIT: This site may also help figure out cut.
Thanks for that. I didn't know that was possible. I'm tinkering with that ability now.

---

### Post by inteluser on 2008-07-16
> **Hopworks said:**
> 
EDIT: I found a small issue with this approach. If the filename is, say, 'my_file 0.text' with a space before the zero, the above approach will not list it, even if it has the search text in it. I need to expand my knowledge of regular expressions to find a way to get around that. The files I am searching have no spaces in the file names so this still works for me, but if I use it for other needs, this problem can occur.

It works fine for me:
```
$ echo "my_file 0.text:4" | grep :[^0]
my_file 0.text:4
```

I think the problem is in "find . | xargs":
```
$ find .
.
./searchtext.cgi
$ cat searchtext.cgi 
#!/usr/bin/perl

$ echo "perl" > my_file\ 0.text
$ cat my_file\ 0.text 
perl
$ find . | xargs grep -snHc "perl"
.:0
./searchtext.cgi:1
$ mv my_file\ 0.text my_file0.text
$ find . | xargs grep -snHc "perl"
.:0
./searchtext.cgi:1
./my_file0.text:1
```

Ordinarily xargs splits arguments on any whitespace, not just newlines.  You can use NULL-terminated lines to do this:
```
$ find . -print0 | xargs -0 grep -snHc "perl"
.:0
./searchtext.cgi:1
./my_file0.text:1
$ mv my_file0.text my_file\ 0.text
$ find . -print0 | xargs -0 grep -snHc "perl"
.:0
./my_file 0.text:1
./searchtext.cgi:1
```

The "-print0" tells find to print a \0 at the end of each filename (a null byte).  The -0 tells xargs to split arguments at \0, not whitespace or newlines.

---

### Post by lswb on 2008-07-16
"the rest of the man grep for that option also says...
The scanning will stop on the first match."

It is somewhat ambiguous, but that refers to stopping the scan within a particular file. (No need to continue scanning a file once one match is found, unlike default behavior, where all matching lines are printed.) It does not skip any files.

---

### Post by Hopworks on 2008-07-16
> **lswb said:**
> "the rest of the man grep for that option also says...
The scanning will stop on the first match."

It is somewhat ambiguous, but that refers to stopping the scan within a particular file. (No need to continue scanning a file once one match is found, unlike default behavior, where all matching lines are printed.) It does not skip any files.
Yes, thank you. It certainly reads like it stops at the first match. Would have never known had you not said something.

Thanks inteluser for explaining the xargs. I had no idea what that was.

---

### Post by bodhi.zazen on 2008-07-16
To be honest, I think you are under utilizing the power of find.

```
find . -type f -name "*my text*" -exec basename '{}' \;
```

The only "new" command here is basename, which strips the path off the file found by find.

---

### Post by unutbu on 2008-07-16
Building on bodhi.zazen's suggestion, you can use this to find files that contain the words "my text":

```
find . -type f -exec grep -q "my text" '{}' \; -print
```

---

### Post by Hopworks on 2008-07-17
> **bodhi.zazen said:**
> To be honest, I think you are under utilizing the power of find.

```
find . -type f -name "*my text*" -exec basename '{}' \;
```

The only "new" command here is basename, which strips the path off the file found by find.
I like that -exec basename '{}' \; since I didn't know that could be done. I'm reading that man page also.

But I tried it for my scenario and it didn't work, at least not for finding text in the files. If it did, I'd have to leave off the -exec part because I need to see the path, since the search is recursive throughout a complex directory tree. The "*my text*" seems to match file names, not what's inside them. Am I misusing it somehow?

Eventually, I'll want to narrow the files searched down to just PHP, HTML, INC, JS. I'm sure some time with the man page for find will show me how to list multiple file types for the search.

Again, thanks everyone for helping me with this. So many things I need to get my head around and this was one of them. Thank you!

---

### Post by Hopworks on 2008-07-17
> **unutbu said:**
> Building on bodhi.zazen's suggestion, you can use this to find files that contain the words "my text":

```
find . -type f -exec grep -q "my text" '{}' \; -print
```
Ah, ok, that answered that question about the internal text search.

---

### Post by unutbu on 2008-07-17
This will limit the search to files whose basenames end in .php:
```

find . -type f -name "*.php" -exec grep -q "my text" '{}' \; -print
```

This will limit the search to files whose basenames end in .php or .html:
```

find . -type f \( -name "*.php" -o -name "*.html" \) -exec grep -q "my text" '{}' \; -print
```

---

### Post by Hopworks on 2008-07-17
> **unutbu said:**
> This will limit the search to files whose basenames end in .php:
```

find . -type f -name "*.php" -exec grep -q "my text" '{}' \; -print
```

This will limit the search to files whose basenames end in .php or .html:
```

find . -type f \( -name "*.php" -o -name "*.html" \) -exec grep -q "my text" '{}' \; -print
```
Thank you. Works great, and as I look at man pages and google for the example you wrote, arguments, like [COLOR="Navy"]**-o**[/COLOR] and [COLOR="Navy"]**\(**[/COLOR], I am learning something as well.

---

### Post by spupy on 2008-07-17
Ahem

```
grep -R findme * | grep -o "^.*:" | sed "s/://g"
```

For .php
```
grep -R findme * | grep -o "^.*\.php:" | sed "s/://g"
```

EDIT: But it can't look in files with different extensions. (Unless you change the regular expression of the second grep, but I don't know how)
EDIT: It does:
```
grep -R findme * | grep -o "^.*\.\(php\|html\):" | sed "s/://g"
```
But it gets clunky with more extensions.

---

### Post by ghostdog74 on 2008-07-17
> **spupy said:**
> Ahem

```
grep -R findme * | grep -o "^.*:" | sed "s/://g"
```

it seems you want to get the filename ? there's a grep option for just printing the file name when pattern is found

---

### Post by unutbu on 2008-07-17
Hm. Yes. This also finds all files containing "my text" whose basename ends with html or php:

```

grep -Rl "my text" . | grep "\.html$\|\.php$"

```

---

### Post by spupy on 2008-07-17
> **ghostdog74 said:**
> it seems you want to get the filename ? there's a grep option for just printing the file name when pattern is found

Then
```
grep -R -l findme *
```
Isn't this what OP is trying to do? Or did I misunderstand someone?

EDIT: I'm slow. ;)

---

### Post by ghostdog74 on 2008-07-17
> **unutbu said:**
> Hm. Yes. This also finds all files containing "my text" whose basename ends with html or php:

```

grep -Rl "my text" . | grep "\.html$\|\.php$"

```

no need for extra grep. KISS
```

grep -Rl "my test" *.html *.php

```

---

### Post by unutbu on 2008-07-17
> **ghostdog74 said:**
> no need for extra grep. KISS
```

grep -Rl "my test" *.html *.php

```

This fails to find .html and .php files in subdirectories.

---

### Post by ghostdog74 on 2008-07-17
> **unutbu said:**
> This fails to find .html and .php files in subdirectories.

you are right my bad
```

grep -rl --include '*.html' --include '*.php'  "my pattern"  *

```

---

### Post by bodhi.zazen on 2008-07-18
LOL, I am not sure where we are going either, I think this is a meandering learning kind on thread. The OP asked "how to show only filenames" which is why I used basename.

Other things of interest, not to digress mind you, are egrep and regular expressions.

In general, use grep to directly search the contents of a file or in a pipe to filter the output of a command.

ie grep sda1 /etc/fstab

rather then cat /etc/fstab | grep sda1

In general user find to find files.

find foo -options

rather then ls -lA | grep .html$

egrep is used with "extended" regular expressions.

Of course you can grep -E, (or grep -F or fgrep) lol

See the top of this man page :

[http://www.mkssoftware.com/docs/man1/grep.1.asp](http://www.mkssoftware.com/docs/man1/grep.1.asp)

And for find :

[http://www.linux.com/articles/55377](http://www.linux.com/articles/55377)

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

And regular expressions (just in case you have insomnia)

[http://www.northernjourney.com/opensource/newbies/newb011.html](http://www.northernjourney.com/opensource/newbies/newb011.html)

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

Happy reading :)

---

### Post by unutbu on 2008-07-18
Thanks, ghostdog74, your command is significantly faster:
```

right@intersection:~/test% time for ((i=1;i<=1000;i+=1)); do grep -Rlq "foot" . | grep "html\|php" ; done

real	0m4.021s
user	0m3.068s
sys	0m0.960s
right@intersection:~/test% time for ((i=1;i<=1000;i+=1)); do grep -rlq --include '*.html' --include '*.php'  "foot" *; done

real	0m2.236s
user	0m1.268s
sys	0m0.960s

```

---

### Post by Hopworks on 2008-07-18
> LOL, I am not sure where we are going either, I think this is a meandering learning kind on thread.
Yes it is, and I couldn't have asked for more! :)

What I like about this is that I'm picking up a ton of other knowledge. I appreciate all the attention to this subject. Speed really hadn't been a concern, but with an intense search, it can matter.

My personal wiki entry I've created on this topic has become quite large thanks to this thread, and again, thank you for your time and efforts! =D>

---

### Post by bodhi.zazen on 2008-07-18
> **Hopworks said:**
> My personal wiki entry I've created on this topic has become quite large thanks to this thread, and again, thank you for your time and efforts! =D>

Link ?

---

### Post by just_linux on 2008-07-18
Hi Every one, 
I am very new to linux and I am just learning basics. :lolflag:
Just for start I want to learn how to write a code. 
If you might know In DOC we could change all files which starts with a to b. 
So it the file was ahjg.txt it became bhjg.txt with only one commend ren a*.* b*.*
 Or if we wanted to change all txt file to doc we just type ren *.txt *.doc

So Now I want to write a code that does the same thing "It might be there already but I want to learn how to do it"

So please let me know "And if you are very kind, please write it out " 
So I could put rename *.txt *.doc and just work and echo the number of files and path of each one. 

Thanks A LOT :guitar:

---

### Post by unutbu on 2008-07-18
```
rename -nv 's/^a/b/'
```
This will simulate the renaming of all files that begin with a to a filename beginning with b.

s/^a/b/ is a perl expression. 
s means substitute
^ means match starting at the beginning of the line
a means match a literal 'a'
b means replace with a literal 'b'.

If after reviewing the simulated actions you are happy, then you can execute the real command:

```
rename 's/^a/b/'
```

If you want to recurse through subdirectories, you can use
```
find * | rename 's/^a/b/'

```

Edit: Before I had suggested
```

find * -exec rename -nv 's/^a/b/' {} \;
```
on the basis that it may be faster to execute. I was mistaken:
```
engine@idle:~/test% time for ((i=1;i<10;i+=1)); do find * | rename 's/^a/b/'; done

real	0m0.227s
user	0m0.188s
sys	0m0.028s

engine@idle:~/test% time for ((i=1;i<10;i+=1)); do find * -exec rename 's/^a/b/' {} \;; done

real	0m11.254s
user	0m9.581s
sys	0m1.480s

```

---

### Post by ghostdog74 on 2008-07-18
> **just_linux said:**
> 
 Or if we wanted to change all txt file to doc we just type ren *.txt *.doc

rename is a good tool to have, however for a beginner like you, i would rather you learn from scratch. to manipulate strings in bash, there are tools available to do that, even bash itself.
Examples of tools to change strings are sed, awk and tr just to name a few.
In bash, you can take a look [here](http://tldp.org/LDP/abs/html/string-manipulation.html) ( or my sig for the bash manual).
to rename files, i believe you already know about mv. For what you are trying to accomplish, i believe you would also need to loop over files. So you can see [here](http://tldp.org/LDP/abs/html/loops1.html) for looping methods.
Example using sed.
```

# FILE="afile.txt"
# echo $FILE|sed 's/^a/b/'
bfile.txt

```
i leave it to you to do the rest

---

### Post by Hopworks on 2008-07-20
> **bodhi.zazen said:**
> Link ?

Wiki on my LAMP server, sorry. I don't maintain or even have a public one.

---

### Post by Flou on 2011-02-09
> **jonlemur said:**
> If the filenames are all listed first, and they are separated by a space, you should be able to use something like```
find . | xargs grep -snH "my text" --color | cut -f1 -d' '
``` where f1 tells it to cut field 1 as separated by the delimiter ' ' (space).  If that doesn't work, try "man cut" to see more options for that commands.

EDIT: [This site]("http://www.computerhope.com/unix/ucut.htm") may also help figure out cut.

Perfect. Thanks!

---

