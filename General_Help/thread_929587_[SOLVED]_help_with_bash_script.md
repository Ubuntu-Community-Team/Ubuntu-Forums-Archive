---
title: "[SOLVED] help with bash script"
date: 2008-09-25
forum: General Help
---

### Post by porchrat on 2008-09-25
Hello once again to the netizens of Linuxland!

I want to write a bash script that takes a text file and creates multiple files from that original text file (perhaps a grep of some kind).

Basically I need the file to be separated into smaller files based on the occurrence of a word.  As an example I'd like a new file to be created and outputted to whenever the word "pie" appeared in the text of the original file.  Is this possible?

Another possibility would be to create a script with the name I need to grep out as an argument ($1 most probably) and then have it grep out every line after (and including) that name and stop grepping when it encountered "pie".  Obviously all ouputted to another file named something like $1extract.txt.

Any ideas would be appreciated.

Thanks guys

---

### Post by cicatrix1 on 2008-09-25
Might be time to learn perl or python :)

---

### Post by porchrat on 2008-09-25
NOOOOOOOOOOOOOOO!!!  Object-orientaton fills porchrat with fear!  :eek:

I was really just looking for a quick fix to the problem, don't really know if my beloved bash is up to this particular problem though.

Well I will attempt to find a solution regardless...still if anyone has any ideas...let me know.

---

### Post by tonybaqain on 2008-09-25
let me simplify grep for you :
[HTML]
-m NUM, --max-count=NUM
              Stop reading a file after NUM matching lines.  If the input is standard input from a regular file, and NUM matching lines are  output,  grep  ensures  that  the
              standard  input is positioned to just after the last matching line before exiting, regardless of the presence of trailing context lines.  This enables a calling
              process to resume a search.  When grep stops after NUM matching lines, it outputs any trailing context lines.  When the -c or --count option is also used,  grep
              does not output a count greater than NUM.  When the -v or --invert-match option is also used, grep stops after outputting NUM non-matching lines.
[/HTML]

this means if you use "-m 1" with grep , it stops grepping after the first oocurance. one point solved.
[HTML]
-A NUM, --after-context=NUM
              Print NUM lines of trailing context after matching lines.  Places a line containing a group separator (--) between contiguous groups of matches.  With the -o or
              --only-matching option, this has no effect and a warning is given.
[/HTML]
this means if you use "-A 1" with grep, you'll have the matching line, and the line after it. two points solved.

so lets collect everything in a useful way:


first i have to learn the line which the "pie" word appeared in the file: 

```
grep -m1 -n pie [textfile] | awk -F: '{print $1}'
```
this will print out the line number.

it is now easy, i want to grep all matches from line 1 to the line "pie" word appeared in :

```
head -[the line number] [textfile]
```

this prints out the content of the file from line 1 till the line number

```
head -[number] [textfile] | grep -A 1 [criteria]
```

it will output your desired results.

as in combination, this what the script will look like :

```

#!/bin/bash
######
# usage ./script [textfile] [stop word] [criteria]
######
$textfile=$1
$stopWord=$2
$criteria=$3

stopLine=`grep -m1 -n "$2" "$1" | awk -F: '{print $1}'`

head -${stopLine} "$1" | grep -A 1 $3

exit 0

```


and have fun :)

---

### Post by TeXtonyx on 2008-09-25
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
This tutorial assumes no previous knowledge of scripting or programming, but progresses rapidly toward an intermediate/advanced level of instruction . . . all the while sneaking in little nuggets of UNIX® wisdom and lore. It serves as a textbook, a manual for self-study, and a reference and source of knowledge on shell scripting techniques. 
TeX: I assume you've already Mastered Regular Expressions   :-\"
The good gnus is [http://bashscripts.org/](http://bashscripts.org/) And they take Requests, Need a script? Ask here. 
Yar parrot, awk-awk, ain't just whistlin' Dixie :wink:

---

### Post by porchrat on 2008-09-25
> **tonybaqain said:**
> 
as in combination, this what the script will look like :

```

#!/bin/bash
######
# usage ./script [textfile] [stop word] [criteria]
######
$textfile=$1
$stopWord=$2
$criteria=$3

stopLine=`grep -m1 -n "$2" "$1" | awk -F: '{print $1}'`

head -${stopLine} "$1" | grep -A 1 $3

exit 0

```



Firstly...thank you so much for your reply...I hadn't thought of doing something like that and it looks very promising.

I do have a few questions though:

What would be used under the argument [criteria]?  Would it be "pie"? and in that case it would ouput the line containing "pie" and one line following it...unfortunately there are a variable numbers of lines between each occurrence of "pie" that need to be included in the new files, not just one line after "pie".

Also why would you stop counting after one occurrence with "grep -m1"?  There is more than one "pie" occurrence in this file.  More like thousands.

One more question...Is it possible to output to a different filename each time a "pie" is encountered and form the filename from another field within the line containing "pie"?

I realise this is a rather strange request.  If I had had my way I would've kept it all in the original text file and used a "sed" to insert a new line before each "pie".

---

### Post by tonybaqain on 2008-09-25
First: criteria means the search word but not the stop word.

means if i would search for "A" occurrence until i find "T" ill use :
./script textfile.txt T A
where T will define where the script will stop at a specific line
and A is the search word where i want to output it and the line after it also.



Second: at least so i can help you, please paste a sample of the textfile with some rich content so i can determine what to do after that.

thanks and have fun :)

---

### Post by mbeach on 2008-09-25
perhaps if you provided a really small sample of what you have and what you want to end up with.

a
b
c
pie 1234
d
e
f
g
pie

would yield
file1
a
b
c
pie 1234

file2
d
e
f
g
pie

---

### Post by porchrat on 2008-09-25
> **TeXtonyx said:**
> [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
This tutorial assumes no previous knowledge of scripting or programming, but progresses rapidly toward an intermediate/advanced level of instruction . . . all the while sneaking in little nuggets of UNIX® wisdom and lore. It serves as a textbook, a manual for self-study, and a reference and source of knowledge on shell scripting techniques. 
TeX: I assume you've already Mastered Regular Expressions   :-\"
The good gnus is [http://bashscripts.org/](http://bashscripts.org/) And they take Requests, Need a script? Ask here. 
Yar parrot, awk-awk, ain't just whistlin' Dixie :wink:

I am actually busy working my way through that first link...it is exceptionally helpful, thank you for the other link though.  I'm always looking for things to improve my knowledge.

As for what I'm trying to do unfortunately I can't print any of it as I'm not really allowed to.  However this is basically what I want to do:

pie
a
b
c
End of File

pie
a
b
c
d
e
End of File

pie
a
b
End of File

Over and over and over...there are around 960000 entries in this text file (at least thats what "wc -l" tells me), so basically I need a script to run right through it separating "pie" and all the info underneath "pie" out into a separate text file ending just before the next instance of "pie"...for every instance of "pie".  I know this is a lot to ask of you guys, working with something you can't see  I was just hoping there was some sort of general practice that could work for this, obviously it is a little more complex than I thought.  Especially the outputting to multiple files problem.

Is there nothing else that can be done?

Thank you all so much for your help though it is greatly appreciated.  As always I am amazed at how helpful this community is.

---

### Post by porchrat on 2008-09-25
> **tonybaqain said:**
> 
```

#!/bin/bash
######
# usage ./script [textfile] [stop word] [criteria]
######
$textfile=$1
$stopWord=$2
$criteria=$3

stopLine=`grep -m1 -n "$2" "$1" | awk -F: '{print $1}'`

head -${stopLine} "$1" | grep -A 1 $3

exit 0

```

OK with a little tweaking I've managed to get that initial grep to ouput what it is supposed to, all fields including the line numbers (as field $1).

However that doesn't solve the problem of getting it to write every instance of "pie" and its subsequent entries to a new file...is there any command (or series of commands) that could generate multiple different output files?

---

### Post by mbeach on 2008-09-25
just playing around a bit, came up with the following, but doesn't include the "pie" line - working on that.

breakfile.sh:
```

awk '/^'$2'/{d++;next}{print > d"extract.txt"}' $1
```
usage:
```
$ ./breakfile.sh testfile.txt pie
```

its not my handy work, grabbed it from 
[http://www.unix.com/shell-programming-scripting/29669-how-split-file-tags-inside-file.html](http://www.unix.com/shell-programming-scripting/29669-how-split-file-tags-inside-file.html)
[http://www.unix.com/shell-programming-scripting/14576-split-file-using-awk-2.html](http://www.unix.com/shell-programming-scripting/14576-split-file-using-awk-2.html)

---

### Post by mbeach on 2008-09-25
just eliminate the "next"

```
#!/bin/bash
awk '/^'$2'/{d++}{print > d"extract.txt"}' $1
```

so 
```
$ ./breakfile.sh testfile.in pie
``` 
should do the trick.

Good luck.
mb.

---

### Post by porchrat on 2008-09-25
> **mbeach said:**
> just eliminate the "next"

```
#!/bin/bash
awk '/^'$2'/{d++}{print > d"extract.txt"}' $1
```

so 
```
$ ./breakfile.sh testfile.in pie
``` 
should do the trick.

Good luck.
mb.

Thank you mbeach...it seems all is not lost for me after all.

Unfortunately it is the end of the day here for me so I'm not going to be able to look into this today, but things are starting to look up :)

I will of course pick it up again tomorrow.  Thank you all for your help so far!

---

### Post by porchrat on 2008-09-26
OK I tried a variety of scripts yesterday with limited success.

However this script is the closest (thank you to mbeach for finding this):

```
awk '/'$2'$/{d++}{print > d"extract.txt"}' $1
```

As you can see I've tweaked it slightly as the "pie" string actually occurs at the end of the line not the beginning (because there is another variable that under certain circumstances results in an unexpected "pie"), I then decided to move "pie" to the end of the line to avoid this confusion.

It works perfectly...with one problem...it gets about 25% of the way through and stops.

When I the script I end up with this:
> awk: cannot open "1020extract.txt" for output (Too many open files)


Seems like when awk tries to create all the "extract.txt" files it can't handle the scale?  (remember this is a text file with nearly a million lines)

Any suggestions?  Perhaps something similar to a xargs beforehand?

Forgot to add that it does get to "1019extract.txt" before quitting...so it is indeed falling over when it gets to 1020.  Haven't managed to find anything on google regarding this particular problem, but then again my search prowess is not exactly legendary.

Maybe a close?

---

### Post by mbeach on 2008-09-26
perhaps a more complex begin/end block which closes the previous file would do the trick.  I'll play around a little bit with this tonight - limited on 'testing' time right now.  Might also be time to look at another language, but I bet awk can do it.

Something like { close $d"extract.txt" } thown in there before the print might do the trick.  NB: I haven't tried it. 

Out of curiousity how long does the process take before it fails.  Seconds or minutes?

mb.

---

### Post by porchrat on 2008-09-26
> **mbeach said:**
> perhaps a more complex begin/end block which closes the previous file would do the trick.  I'll play around a little bit with this tonight - limited on 'testing' time right now.  Might also be time to look at another language, but I bet awk can do it.

Something like { close $d"extract.txt" } thown in there before the print might do the trick.  NB: I haven't tried it. 

Out of curiousity how long does the process take before it fails.  Seconds or minutes?

mb.

It takes about 15seconds or so (just a guess).

I'll try the close before the print...I tried putting it in at the end however then I just get the line before each occurrence of "pie" in each file (seems as though it closes the file before awk can add anything else to it).

It is sort of an awk problem coupled with the fact that most debian systems only keep 8096 files open at a time (bearing in mind that each read and write instance is a separate interrupt and therefore counts towards that total number).

Perhaps the answer is to just increase the number of files it can open at a time.  I have the memory to do so it's just I really would like this script to be portable and I don't want to have to up the file-max limit for every system I run this on.

I know at this point I should probably be moving it to another language, but I agree with you when you say awk is capable of it and now it has become a bit of an obsession for me to prove that.

---

### Post by koenn on 2008-09-26
when in doubt, use brute force
this bash script simply reads a file line by line, and writes those lines to a given filename.
part of that filename is a number; if the line contains the word "pie", the number increases, resulting in the creation of a new filename.

It's actually harder to explain than to code :

```

#!/bin/bash

## cut file to pieces before occurrance of a given word
#     origfile will be split in newfile.0 newfile.1  ... newfile.n


filecounter=0
stopword="pie"

cat origfile |while read line; do
	echo $line |grep $stopword && filecounter=$(( filecounter +1 ))
	echo $line >> newfile.$filecounter
done


```

---

### Post by mbeach on 2008-09-26
yes, something like the following appears it might work:
```
awk '/'$2'$/{close (d"extract.txt");d++}{print > d"extract.txt"}' $1

```

---

### Post by porchrat on 2008-09-26
> **koenn said:**
> when in doubt, use brute force
this bash script simply reads a file line by line, and writes those lines to a given filename.
part of that filename is a number; if the line contains the word "pie", the number increases, resulting in the creation of a new filename.

It's actually harder to explain than to code :

```

#!/bin/bash

## cut file to pieces before occurrance of a given word
#     origfile will be split in newfile.0 newfile.1  ... newfile.n


filecounter=0
stopword="pie"

cat origfile |while read line; do
	echo $line |grep $stopword && filecounter=$(( filecounter +1 ))
	echo $line >> newfile.$filecounter
done


```

Thats really clever.  I like the filecounter+1 idea.

I think it is time I think to stop this "pie" thing.  I started that because it was the first word that came to mind and we seem to have just rolled with it.  I'm actually attempting to split at the occurrence of "3".  Of course the problem with that is I also have other occurrences of "3" in the file, so I solved that by moving "3" to the end of the line and using "$" with an awk command.

However as the "3" has tab spaces next to it could grep possibly still differentiate it from other occurrences of "3", which don't?

If push comes to shove I'm going to have to break it into 4 files and run each one individually through the awk command or your script.

Although your script seems promising as well because when the filecounter grows it appends to a new file and then (hopefully) closes the old file, which would solve the problem.  (I hope that made sense to you guys).

By the way the "increasing file-max to allow Ubuntu to open more files at a time" did not work :(

Unfortunately once again we are out of time, but I will take a look at it again over the weekend and see what comes of these new ideas.  Thank you all once again and have a pleasant weekend.

Please feel free to answer those questions I've posed though as I will be checking in again over the weekend :)

---

### Post by koenn on 2008-09-26
you"d have to work on the grep statement then (or choose a more suitable delimiter if you can mofify that file)

grep can handle basic regular expressions, and extended regexp if you give the -e option. The hard part is knowing how to make a regular expression.

here are some basic examples
```

match '3' at the end of a line: grep 3$
match '3' at the start of a line: grep ^3
match '3' if it occurs after 2 or more spaces: grep "  3"
match '3' with space before and after :  grep " 3 "
match '3' at the beginning of a line if it's followed by a space: grep "^3 "

``` 
I don't have a real sollution for tabs. Sometimes tabs are written as 4 (or 5 or 8 ) spaces, so that is easy. there's also  [:space:] which should match whitespace, i.e 2 or more spaces and/or 1 or more tabs, but I haven't figured out how to use it.

You're right about output redirection ( > ) not having trouble with opening too many files. As I understand it, it just dumps the bits into the file without actually opening it in the usual sense of how a program would "open for writing" and write changes on closing

---

### Post by koenn on 2008-09-26
grep whitespace, eg match "3" preceded by any whitespace:
```
grep "[[:space:]][3]"  
```

---

### Post by stylishpants on 2008-09-26
One way to do it in ruby:

```

fhanson@fhanson:/tmp$ cat data.txt
a
b
c
pie 1234
d
e
f
g
pie
h
i
j
cherry pie 
k
l

fhanson@fhanson:/tmp$ rm extract*

fhanson@fhanson:/tmp$ ruby -e 'i=0; ARGF.read.scan(/^.*?pie.*?\n|.+/m).each {|s| File.open("extract#{i+=1}.txt","w") << s }' data.txt 

fhanson@fhanson:/tmp$ head extract*.txt
==> extract1.txt <==
a
b
c
pie 1234

==> extract2.txt <==
d
e
f
g
pie

==> extract3.txt <==
h
i
j
cherry pie 

==> extract4.txt <==
k
l
```

Note that this solution also prints out any text that occurs after the last separator.

---

### Post by mbeach on 2008-09-27
well, assuming it was 'pie' with a tab preceeding you could use:
awk '/\tpie$/{close (d"extract.txt");d++}{print > d"extract.txt"}' $1

if it was a trailing tab
awk '/pie\t$/{close (d"extract.txt");d++}{print > d"extract.txt"}' $1

the \t is tab.

---

### Post by porchrat on 2008-09-29
I think all of you deserve an update on this script.

I finally settled on this (A big thank you Koenn):

```
#!/bin/bash

#$1=source file
filecounter=0
stopword="3$"

cat $1 | while read line; do
	echo $line |grep $stopword && filecounter=$(( filecounter +1 ))
	echo $line >> newfile.$filecounter
done
```

It isn't nearly as fast as the awk solution was (close on 30 minutes and I didn't even let it run to completion), however at least it handles the scale, and I like the echo to the screen of the lines it greps as it runs...lets me watch the progress.

I am going to attempt this again at some point with the awk version when I have the time, as I really want this to run faster.

However it is running now and that is awesome.  I want to say thank you to all of you (mbeach, koenn, tonybaqain, TeXtonyx, stylishpants) for helping me out with this.  The scripts, documentation and advice are inventive and have been exceptionally helpful.

Thanks all and have a good week!

---

### Post by ghostdog74 on 2008-09-29
> **porchrat said:**
> I think all of you deserve an update on this script.

I finally settled on this (A big thank you Koenn):

```
#!/bin/bash

#$1=source file
filecounter=0
stopword="3$"

cat $1 | while read line; do
	echo $line |grep $stopword && filecounter=$(( filecounter +1 ))
	echo $line >> newfile.$filecounter
done
```

It isn't nearly as fast as the awk solution was (close on 30 minutes and I didn't even let it run to completion), 

lose the cat as its useless. The while read loop can take in input file. Also, using bash's while loop and then echoing each line to grep is certainly slow. As tools such as awk/grep/sed has already got an internal "looping" mechanism implemented in C, its definitely faster when used to parse files.

> 
I am going to attempt this again at some point with the awk version when I have the time, as I really want this to run faster.


the awk script by mbeach should work. you just need to close the files. here's little modified
```

awk '$NF~/pie/{close(d"extract.txt");d++}{print $0 > d"extract.txt"} ' file

```

it checks last field has the word "pie", instead of checking for tabs before pie.

---

### Post by mariuszkopec on 2008-09-29
Use:

csplit file.txt /pie/ {*}

You will get files xx00, xx01 - xx99. If you expect more than 100 files use option -n.

---

### Post by koenn on 2008-09-29
> **ghostdog74 said:**
> lose the cat as its useless. The while read loop can take in input file. Also, using bash's while loop and then echoing each line to grep is certainly slow. As tools such as awk/grep/sed has already got an internal "looping" mechanism implemented in C, its definitely faster when used to parse files.

well, awk is probably a better choice, but the original question was to do this in bash, which i found rather convenient : i can hardly read awk, let alone write it ; I wrote those 6 lines in bash in less than the time it'd take me to find an awk tut. :)

I'd love to see an example of a 'while read' loop that reads line by line so you can process individual lines. It's quite a common job, so if you know of a better way than piping cat, ...

---

### Post by ghostdog74 on 2008-09-29
> **koenn said:**
> well, awk is probably a better choice, but the original question was to do this in bash, 

you mean in pure bash with no external tools? then you shouldn't talk about using grep and cat as well. if you used grep, cut etc, then using awk is ok. awk is a programming language. it provides the functionality of common tools like grep/sed/cut/wc etc. 

> 
which i found rather convenient : i can hardly read awk, let alone write it ; I wrote those 6 lines in bash in less than the time it'd take me to find an awk tut. :)

see [here](http://www.unix.com.ua/orelly/unix/sedawk/index.htm) or [here](http://www.grymoire.com/Unix/Awk.html)

> 
I'd love to see an example of a 'while read' loop that reads line by line so you can process individual lines. It's quite a common job, so if you know of a better way than piping cat, ...
you should read the learn bash manual in my sig. it will show you various ways to use while loop
eg this is common way to read file in bash while read loop
```

IFS=
while read line
do
 echo $line
done < file

```
which is equivalent to awk '1' file

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by porchrat on 2008-09-30
```

awk '$NF~/pie/{close(d"extract.txt");d++}{print $0 > d"extract.txt"} ' file

```

it checks last field has the word "pie", instead of checking for tabs before pie.[/QUOTE]

Awesome!

Had to tweak it a little as the "$NF" wouldn't work (there is another instance in that last field that contains the string I was looking for...just not at the end of the line
i.e. the one I'm looking for is a b c pie
     the unwanted one is        a b c piedfg

Got around it by just doing this:
```
awk '/pie$/{close(d"extract.txt");d++}{print $0 > d"extract.txt"} ' $1
```
Where $1 is the original text file.  I like this...simple, fast and much easier to follow.  Takes about 3 seconds to run to completion on a text file containing around a million lines with 5 fields each.

I have another question though.  I've been trying to do this and haven't had much success.  Is it possible to make the name of the new file the fifth field from the first line of that file?  So like instead of using "d++" for an incremental increase put in a "print $5" as the file suffix?

Maybe with an "if then" statement?

Something like: ```
if awk '{print $NF} = "pie" then filesuffix=( awk '{print $5}' )
```

Even if it runs afterwards and reads incrementally changing each one as it goes. That would also be fine.

---

### Post by ghostdog74 on 2008-09-30
> **porchrat said:**
> ```



I have another question though.  I've been trying to do this and haven't had much success.  Is it possible to make the name of the new file the fifth field from the first line of that file?  So like instead of using "d++" for an incremental increase put in a "print $5" as the file suffix?

not tested
[code]
awk '/pie$/{close(five);five=$5}{print  > five".txt" } ' $1

```

---

### Post by porchrat on 2008-09-30
> **ghostdog74 said:**
> not tested
```

awk '/pie$/{close(five);five=$5}{print  > five".txt" } ' $1

```

Well done! =D>

Worked like a charm.

Although I was wrong when I said field 5 turns out it was actually field 4 (I really need to start checking these things more thoroughly).  Anyway just tweaked it to grab field 4 instead of field 5.

Thanks again guys

---

### Post by koenn on 2008-09-30
> **ghostdog74 said:**
> you mean in pure bash with no external tools? then you shouldn't talk about using grep and cat as well. if you used grep, cut etc, then using awk is ok. awk is a programming language. it provides the functionality of common tools like grep/sed/cut/wc etc. 

I wasn"t thinking about purity, nor am i interested in discussing it. 
awk is a programming language i hardly understand. Bash and common tools such as grep is something I can work with. So, I gave a sollution based on bash with grep. It works. I don't see the problem. 
You show a solution in awk, fine with me, so much the better. 


> **ghostdog74 said:**
> 
...
eg this is common way to read file in bash while read loop
```

IFS=
while read line
do
 echo $line
done < file

```

Thanks. Makes sense, although I can't remember having seen it before.

---

