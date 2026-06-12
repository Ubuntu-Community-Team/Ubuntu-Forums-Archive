---
title: "[SOLVED] Argument into Variable in a BASH script"
date: 2008-08-27
forum: General Help
---

### Post by neur0 on 2008-08-27
OK, I'm not really sure the topic makes sense, but heres what I mean.
I have a one line command that uses some script to work with files. To make it simple I'll use this example:
```

Uberscript <file> && convert <file>.foo <file>.moo && rm <file>.foo

```
(Uberscript makes <file> into <file>.foo)

Now whenever I want to run this command(s) I need to copy/paste the file names or type them manually for every occurrence in the command. Since the file names are long and with spaces, I was wondering if theres some simple way to put this command in a script and then only execute:

me@ubuntu$ Myscript <file>

and have the script automatically replace "<file>" in the command with the filename.


I have just started to learn bash and I'm sure I'll learn this along the way, but I need it sooner if possible.
Both solutions and links to documentation is welcome. I can't Google it as I wouldn't know what to search for.

---

### Post by aloshbennett on 2008-08-27
if you have a loop like this:
> 
for i in *; do
  echo $i;
done;


you can loop thru all the files in the directory.

You could replace * with A* if you want all files starting with A :)

---

### Post by justleen on 2008-08-27
something like this? will take all files found by "ls -1" and convert them...
[/code]
for FILE each in `ls -1`; do 
 Uberscript $FILE  
 convert $FILE.foo $FILE.moo 
 rm $FILE.foo
done
[/code]

---

### Post by Dougie187 on 2008-08-27
Or, if you called your script like that
```
Uberscript temp
```
then in your script $1 would be temp.
If you had multiple arguments, they would just increment that variable, so you would get $2, $3 and so on.

---

### Post by neur0 on 2008-08-27
Thanks for the replies, but I don't need iteration (yes it would be easier if I used something with find and for, but thats beyond my current brain-scope)
I will do it for every file manually, no problem.

@Dougie187
I think that may be the right track, but since files contain spaces, I get:

Script This\ is\ The\ File
File "This" doesn't exist
File "is" doesn't exist
File "The" doesn't exist
File "File" doesn't exist

I tried with 
Script "This\ is\ The\ File"
same error...


EDIT: It worked when I put the $1 in "$1"
Thanks

---

