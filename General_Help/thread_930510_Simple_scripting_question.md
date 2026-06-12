---
title: "Simple scripting question"
date: 2008-09-26
forum: General Help
---

### Post by b166er on 2008-09-26
Hi

I'm currently writing a script that will run on schedueld intervals using cron but I came across a litle problem.

The script's main purpose is to keep a folder-structure clean.
And one task it has is to keep the folder "jpegs/" clean from any files that are not jpegs.

I know how to use wildcards to delete all files in a folder that ends with the extension "jpg" (rm *.jpg).

But what should I type if I wanted to remove every file that does not end with the extension .jpg?

---

### Post by kpkeerthi on 2008-09-26
To print all files that does not end with .jpg
```
find -regex '.*\.[^jJ][^pP][^gG]'
```

To remove the files that does not end with .jpg
```
find -regex '.*\.[^jJ][^pP][^gG]' -exec rm '{}' ';'
```

---

### Post by Greyed on 2008-09-26
Er, why do a find?  Shouldn't the shell be able to grok that regex and glob accordingly?

```

{grey@igbuntu:~} touch test foo.jpg
{grey@igbuntu:~} ls *.[^jJ][^pP][^gG]
dovecot.pem  rute.pdf
{grey@igbuntu:~} ls *.???
dovecot.pem  foo.jpg  rute.pdf

```

---

### Post by kpkeerthi on 2008-09-26
[http://www.faqs.org/docs/abs/HTML/globbingref.html](http://www.faqs.org/docs/abs/HTML/globbingref.html)

---

### Post by Greyed on 2008-09-26
Well, there's your problem!

```

{grey@igbuntu:~} grep grey /etc/passwd
grey:x:1000:1000:Steve Lamb,,,:/home/grey:/bin/zsh

```

'sides, your link says Bash does use ^ for a negative match so the find is superfluous in your example regardless of a primitive or advanced shell.  :)

---

### Post by b166er on 2008-09-26
Ok
So I'm a bit confused, can you explain more detailed?

anyway those two suggestions where cool, but they didn't really work.

```

tvrepan@tvrepan:~/Pictures/test$ ls -l
total 0
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:43 test
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:44 test.gmp
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:44 test.gmx
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:45 test.gpg
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:43 test.jpg
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:43 test.mpg
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:43 test.txt
tvrepan@tvrepan:~/Pictures/test$ 
tvrepan@tvrepan:~/Pictures/test$ 
tvrepan@tvrepan:~/Pictures/test$ ls -l *.[^jJ][^pP][^gG]
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:44 test.gmp
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:44 test.gmx
-rw-r--r-- 1 tvrepan tvrepan 0 2008-09-26 12:43 test.txt
tvrepan@tvrepan:~/Pictures/test$ 
tvrepan@tvrepan:~/Pictures/test$ 
tvrepan@tvrepan:~/Pictures/test$ find -regex '.*\.[^jJ][^pP][^gG]'
./test.txt
./test.gmp
./test.gmx
tvrepan@tvrepan:~/Pictures/test$ 

```

---

### Post by Greyed on 2008-09-26
Yeah, the problem with both is that it won't catch anything that doesn't have the exact number of characters that are being checked.  EG test is missed and anything like foo.baboozled would be missed, too, since baboozled is more than 3 characters.

Hm, actually, this might be the domain of something else.

Two questions with two different trains of thought.

#1: Do the files need to be named jpg or jpeg or do they have to **be** jpegs regardless of what they are named?

If the latter then maybe using file would be preferable since file will identify jpegs from non jpegs regardless of their name.  EG:
```

{grey@igbuntu:~} file .mozilla/firefox/btcff7fk.default/Cache/*          
.mozilla/firefox/btcff7fk.default/Cache/00CE9193d01: gzip compressed data, from Unix                                                                            
.mozilla/firefox/btcff7fk.default/Cache/02D88A00d01: HTML document text         
.mozilla/firefox/btcff7fk.default/Cache/038E1F52d01: gzip compressed data, from Unix                                                                            
.mozilla/firefox/btcff7fk.default/Cache/0408127Fd01: PNG image data, 250 x 132, 8-bit/color RGBA, non-interlaced                                                
.mozilla/firefox/btcff7fk.default/Cache/060045E4d01: JPEG image data, JFIF standard 1.01                                                                        
.mozilla/firefox/btcff7fk.default/Cache/0904FCBBd01: JPEG image data, JFIF standard 1.02                                                                        
.mozilla/firefox/btcff7fk.default/Cache/099F2305d01: gzip compressed data, from FAT filesystem (MS-DOS, OS/2, NT)                                               
.mozilla/firefox/btcff7fk.default/Cache/0A8972C6d01: PNG image data, 220 x 136, 8-bit/color RGBA, non-interlaced                                                

```

#2: If the former does this have to be written in shell?  Or would Python do?

```

import os
for file in os.listdir('.'):
    ext = os.path.splitext(file)[1].lower()
    if ext != '.jpg' and ext != '.jpeg':
        print file
        # os.unlink(file) # uncomment to delete


```
```

{grey@igbuntu:~} ls foo.jpg ; echo And the test... ; python test.py | grep foo
foo.jpg
And the test...
foo

```

Please note that is proof-of-concept code and not something you would **EVER** want to run with the comment line uncomment before:

A: running it with that line comment as it is and...
B: modifying it to suit your tastes, running with the line commented out, and repeating until it got exactly the results you wanted.

I say that because if you ran it blindly it would wipe your directory of all files, including hidden files (which many not be what you want) from the get go.

---

### Post by b166er on 2008-09-26
Well I like the idea to use the output of "file" to identify if it's a jpg or not. 
But how does "file" work if someone has created a new directory in the "jpeg-directory"? Would that be ignored?

And I'm sorry to say that i don't know any python, so is there really no way to use it with bash?

Although I found a way to get around the problem, but it's not really preferable.

If you move all the jpeg files into a temporary directory with a dot in the start of the name (i.e hide them) and then do a simple "rm -r **" it cleans the folder. but that wouldn't work if someone was working with the files.

```

mkdir .hide
mv *.jpg .hide
rm -r **
mv .hide/** .
rm -r .hide

```

I learnt from the link above that the wildecards would ignore files starting with a dot :)

But this is not a very good solution though. cause it's really not watertight, worst case it would delete all the jpegs if someone is working with them.

---

### Post by spibou on 2008-09-26
Without using file
```

for a in * ; do
    if [ -f "$a" ] ; then
        case "$a" in
           *.jpg ) ;;
           *     ) rm "$a" ;;
        esac
    fi
done

```

With using file
```

for a in * ; do
    if [ -f "$a" ] && ! file "$a" | grep -iq jpeg ; then
        rm "$a"
    fi
done

```

Neither script is fully tested and they won't pick up files whose name starts with dot (.)

---

### Post by b166er on 2008-09-30
Oh ok that's really cool. But can you explain what all that stuff is actually doing? It would be great to know in the future.
Thanks!

And I don't meen to complain but theese scripts also ignore folders.

---

### Post by Greyed on 2008-09-30
> **b166er said:**
> And I don't meen to complain but theese scripts also ignore folders.

You're right, the original post did say folder structure.  Judicious use of os.walk() will meet that requirement in the Python variant.  It would also need a check of os.path.isdir(file) to prevent it from unlinking subdirectories.

---

### Post by ghostdog74 on 2008-09-30
> **b166er said:**
> 
But what should I type if I wanted to remove every file that does not end with the extension .jpg?

```

# ls -1
test.jpg
test1.jpg
test2.jpeg
test3.png

# shopt -s extglob
# ls !(*.jpg)
test2.jpeg  test3.png

# rm !(*.jpg)
# ls -1
test.jpg
test1.jpg
           

```

---

### Post by b166er on 2008-09-30
Ok I must admit that I'm starting to regret that I titled this thread "Simple" =)

But I must ask how does this command work? 
```
# shopt -s extglob

```

Cause it seams like the best one so far. Lists folders and everything
What exactly does it do?

---

### Post by ghostdog74 on 2008-09-30
it just turns on extended pattern matching. so you can use things like ! (means not) etc.. you should read the [bash manual](http://www.gnu.org/software/bash/manual/bashref.html).(go to section 3.5.8.1 Pattern Matching)

---

### Post by spibou on 2008-09-30
b166er, I hadn't realised what "folder-structure" meant. "Directory hierarchy" is clearer. The following should cover you:
```

find . -type f | while read a ; do
     case "$a" in
         *.jpg ) ;;
         *     ) rm "$a" ;;
     esac
done

```
As for explaining, I would need to write a shell programming tutorial and others have done it already. If you read what the BASH man page says about the commands I use and experiment a bit you should be able to figure it out.

---

### Post by b166er on 2008-09-30
> **ghostdog74 said:**
> it just turns on extended pattern matching. so you can use things like ! (means not) etc.. you should read the [bash manual](http://www.gnu.org/software/bash/manual/bashref.html).(go to section 3.5.8.1 Pattern Matching)

Ok I've read it now, and I think I get it.

The line "shopt -s extglob" basicly means turn on some "extra-wildcards".
one of them is the "!" sign witch means "do not include the folowing". and the part (*.jpg) tells the "!"-sign what to not include.

I know I might sound a bit slow, but I just wanna recap in case someone else is reading this.

The difference between this method and Spibou's Method is that the lather Leaves folders intact (witch could be very useful, but not for this script).

But all in all, I'm very happy with what I've Learnt in this thread. 

great thanks to everybody who responded :)

---

