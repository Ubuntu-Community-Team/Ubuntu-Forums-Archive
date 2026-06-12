---
title: "[SOLVED] Script to search through .zip .tar and .tar.gz archives"
date: 2008-10-13
forum: General Help
---

### Post by porchrat on 2008-10-13
Hi all I'm posting here again as my first thread was about trying to find a **program** that could search through compressed archives to find a filename (I needed something with the functionality of grep or find, but that could search within archive files such as .zip, .tar and .tar.gz).

Anyway I've sort of given up on finding something like that (rather difficult to google for) and have decided to create a script that does it instead.  I found this online:

```
grab () {
find /directory_path -iname "*.tar.gz" -exec tar tz -f '{}' \; | grep $1
find /directory_path -iname "*.tar" -exec tar t '{}' \; | grep $1
find /directory_path -iname "*.zip" -exec unzip -l '{}' \; | grep $1
}
grab *foo*.bar

```

But it doesn't want to work.  It doesn't ouput an error or access the HDD, so I don't think it's actually doing anything.  Basically I'm looking for anything of filetype ".bar" with "foo" as part of the filename (e.g. *foo*.bar).  Also I would assume I put "*foo*.bar" in as argument 1 ($1) but I would like some clarification on it.

I also need it to search through the legitimate directories and subdirectories as well, so I would probably just add a standard "find" or "grep" funtion to the start of it as well.  Any advice?

---

### Post by justleen on 2008-10-13
First of, the $1 your inputting is the actually grep. So your now grepping for *foo*.bar in the found file list.

Second, the scriot below searches one dir for any archives. Then it lists the files in it, and greps for a string in those files names.

Thirdly, find by default searches through all sub directories. SO no need to add anything

So, in this function, your searching for *foo*.bar  in the file lists of the archives, found in this dir + any subdirs.. 
Which is what you want right?
Im not sure what you need really..

---

### Post by geirha on 2008-10-13
*foo*.bar is a pattern, not a regular expression. grep uses regular expressions, so try with ".*foo.*\.bar" (including the quotes. The quotes are important to avoid possible pathname expansion)

Also quote the $1
```
find /directory_path -iname "*.tar*" -exec tar tf {} \; | grep "$1"
```

The tar command in ubuntu will automatically detect if it's compressed with gzip or bzip2, so you can do "tar tf something.tar.bz2". This won't necessarily be the case on other systems though.

---

### Post by porchrat on 2008-10-13
Looking at this script you would think it would just run right?  However when I run it it doesn't seem to do anything.  I was really asking if anyone could see anything wrong with it.  It doesn't really throw an error, but it also doesn't seem to actually look through anything as there is no HDD activity at all.

I realise that "find" is recursive, but what I am saying is that some of the files in amongst these compressed archives are uncompressed, so I will need to add another "find" to the front or the end of the script as well, possibly with a "grep -v" piped onto it as I have noticed that "find" tends to pull out red-herrings when it comes to compressed archives.

---

### Post by justleen on 2008-10-13
this works for me:
```
#!/bin/bash

grab () {
find /home -name "*.tar.gz" -exec tar tvf  {}  \; | grep $1
find /home -name "*.tar" -exec tar tvf {} \; | grep $1
find /home -name "*.zip" -exec unzip -l {} \; | grep $1
}
grab $1

```
mind: the $1 is what you type after the command. so if you save this as "search_archives" you will excute it with
```

./search_archive *foo*.bar 
```

---

### Post by porchrat on 2008-10-13
Thought that maybe my problem was that I had hard-coded *foo*.bar at the end instead of leaving it as $1, however I'm running it right now and it doesn't seem to be doing anything.  No HDD activity and no response from the script.  I mean grep should be outputting a list of filenames as it runs, but I get nothing.

---

### Post by justleen on 2008-10-13
hm.. works just fine for me.. on a tar.gz anyway...
```

leen@leen-laptop:~$ find . -name "*.tar.gz"
./images/slax_usb_backup.tar.gz
./Desktop/groupoffice-com-2.18-stable-21.tar.gz
./Desktop/cellauto.tar.gz
./xx.tar.gz
./vpnclient-linux-4.8.00.0490-k9.tar.gz
**./php_writeexcel-0.3.0.tar.gz**

``````

leen@leen-laptop:~$ tar -tvf ./php_writeexcel-0.3.0.tar.gz
..<snip> ..
-rw-r--r-- root/root     11085 2005-11-01 15:27 php_writeexcel-0.3.0/class.writeexcel_olewriter.inc.php
-rw-r--r-- root/root        56 2005-11-01 15:46 php_writeexcel-0.3.0/CONTACT
-rw-r--r-- root/root      2068 2005-11-01 15:27 **php_writeexcel-0.3.0/example-textwrap.php**
..<snip> ..

```
```
leen@leen-laptop:~$ ./search_archive te*wrap
-rw-r--r-- root/root      2068 2005-11-01 15:27 php_writeexcel-0.3.0/example-textwrap.php

```


to make grep always return the file name use the -H flag.

---

### Post by porchrat on 2008-10-13
> **geirha said:**
> *foo*.bar is a pattern, not a regular expression. grep uses regular expressions, so try with ".*foo.*\.bar" (including the quotes. The quotes are important to avoid possible pathname expansion)

Also quote the $1
```
find /directory_path -iname "*.tar*" -exec tar tf {} \; | grep "$1"
```

The tar command in ubuntu will automatically detect if it's compressed with gzip or bzip2, so you can do "tar tf something.tar.bz2". This won't necessarily be the case on other systems though.

what will ".*foo.*\.bar" do?  What I really want is to pick up any file with a filename containing foo (thought that *foo* would do that) and with the extension ".bar".

Also good idea on the ".tar*" thing, I hadn't thought of that.  I don't really need to look through a .tar.bz2 at the moment, but for future applications it might be nice to add that functionality.  Thanks

---

### Post by justleen on 2008-10-13
*foo*.bar will not search for a litteral . 
thus, to make grep do search for a litteral ., you need to escape it with a \

(a . is a wildcard for a single char for grep)

---

### Post by porchrat on 2008-10-13
> **justleen said:**
> *foo*.bar will not search for a litteral . 
thus, to make grep do search for a litteral ., you need to escape it with a \

(a . is a wildcard for a single char for grep)

Well do I really want literal?  I mean I actually have no idea how many characters there are before and after "foo" in the filename (I'm looking through someone else's old archives here and he can't remember what he called the darned thing), so what I was trying to do was just get the grep to pick up on any file that had "foo" in the filename, regardless of how many characters there were before and after the "foo".

Will *foo*.bar not do that?...do I need to use the one mentioned above?

Also I've tried it out now and I see that the script works with .tar.gz (and I'm assuming it will work with a .tar as it is basically the same command), but for some reason it doesn't run on a .zip (which is actually the most important one as these are mainly windows backups...so plenty of ,zips).

---

### Post by justleen on 2008-10-13
in your case, your matching a .bar extension, so yes, you want a litteral.
*foo*.bar  -> searches for <anything>foo<anything><one char>bar
*foo*\.bar ->  searches for <anything>foo<anything>.bar

ill try with some zip files, see what happens (dont have these normally :)

create a zipfile of the file nohup.out, then "search_archive nohup" : finds the zip file..

---

### Post by geirha on 2008-10-13
> **justleen said:**
> 
*foo*\.bar ->  searches for <anything>foo<anything>.bar


No, it will match <0 or more of nothing>fo<0 or more o's>.bar

---

### Post by justleen on 2008-10-13
> **geirha said:**
> No, it will match <0 or more of nothing>fo<0 or more o's>.bar

Your absolutly right, I stand corrected!

---

### Post by porchrat on 2008-10-13
> **justleen said:**
> 
create a zipfile of the file nohup.out, then "search_archive nohup" : finds the zip file..

Are you saying you tried that...or I should try that?...currently I have about 3 or 4 zip files in the directory I'm trying to search and whenever I run the script against the directory searching for files that I know are contained in at least one of the .zip's it returns nothing. :(

OK so I understand what you guys are saying now...that the "." in the *foo*.bar will create some problems with grep misinterpreting it.  So then if I use this:

".*foo.*\.bar" as geirha suggested, would grep then interpret it as: <0 or more of anything>foo<0 or more of anything>.bar?

---

### Post by justleen on 2008-10-13
I just tried that, create a zip, then search for the file i zipped, that works
cah you run the script with "sh -x" and then post the output? 

Yes, use the regex Geisha  suggested.
a . stand for any char.
a * stands for 0 to more of the prefixed char
so, .* searches for anychar, matched 0 or more times..

(just saying this outloud to remember this myself :)

---

### Post by porchrat on 2008-10-13
> **justleen said:**
> I just tried that, create a zip, then search for the file i zipped, that works
cah you run the script with "sh -x" and then post the output? 

Yes, use the regex Geisha  suggested.
a . stand for any char.
a * stands for 0 to more of the prefixed char
so, .* searches for anychar, matched 0 or more times..

(just saying this outloud to remember this myself :)

Came back with this (has been edited to eliminate my particulars regarding usernames etc. (sorry I'm paranoid)

```
+ grab .*17Apr.*\.log
+ find directory_path -iname *.tar.gz -exec tar tz -f {} ;
+ grep -H .*17Apr.*\.log
+ find directory_path -iname *.tar -exec tar t {} ;
+ grep -H .*17Apr.*\.log

```

So there you go...I know for a fact that there is a file inside one of the zip archives that contains 17Apr and has a .log extension.

As of now the script is still sitting there in the terminal, yet to end whatever the heck it thinks it is doing...blissfully unaware of how annoying it is being!

---

### Post by justleen on 2008-10-13
try this, in the dir where the zip file is, please:```

find . -name "*.zip" -exec unzip -l {} \; | grep -H log 
```

---

### Post by porchrat on 2008-10-13
there is a syntax error there.

Ouputs this:

 ```
find . -name "*.zip" -exec -l {}; | grep -H log
bash: syntax error near unexpected token `|'
```

---

### Post by justleen on 2008-10-13
ohw darn, my bad again...
syntax error ;)
```
find . -name "*.zip" -exec unzip -l {} \; | grep -H log 
```

on another note: the -H flags doenst do anything in this case. SInce your grepping on standard out, the -H flag will return "Standard Out"
	
so, it should be:
```
find . -name "*.zip" -print  -exec unzip -l {} \; | grep log 
```

---

### Post by -Zeus- on 2008-10-13
so, this might be late, but the program zgrep does what you want... installed by default.  Remove the ; before the |, btw

---

### Post by porchrat on 2008-10-13
> **justleen said:**
> ohw darn, my bad again...
syntax error ;)
```
find . -name "*.zip" -exec unzip -l {} \; | grep -H log 
```

on another note: the -H flags doenst do anything in this case. SInce your grepping on standard out, the -H flag will return "Standard Out"
	
so, it should be:
```
find . -name "*.zip" -print  -exec unzip -l {} \; | grep log 
```

OK strangely enough that worked...what does that mean?

I like the avatar by the way..."Vell, Zaphod's just zis guy, you know?"

---

### Post by justleen on 2008-10-13
that means something in the script is not doing what its supposed to ;)

copy that working line, and adjust it for the script (which means: change the grep log to grep $1 )
see if that works..



And thnx ... I think Zaphod is the best char... "any person capable of running the universe shouldnt by no means be allowed to do the job" and then they found Zahpod :)

---

### Post by porchrat on 2008-10-13
> **-Zeus- said:**
> so, this might be late, but the program zgrep does what you want... installed by default.  Remove the ; before the |, btw

Looked it up...can't believe it!

This sucker handles .zip as well.  However it uses grep in text, I really only need the equivalent of a "find" function...for filenames.  Is there a flag to use with grep to restrict it to filenames as opposed to running in text.  (unfortunately there is no zfind otherwise that would've been perfect!).

This however is an AWESOME command that I will be making use of in the future.

---

### Post by porchrat on 2008-10-13
> **justleen said:**
> that means something in the script is not doing what its supposed to ;)

copy that working line, and adjust it for the script (which means: change the grep log to grep $1 )
see if that works..

Tried it and it still just sits there, no HDD activity, no end to the script, just looks as though it would hang forever.  It sort of looks like what happens when you use a "grep" with a string but with no target file.  I hope you know what I mean it just sort of hangs there not really executing, but not really finishing.

By the way sorry it takes me so long to respond sometimes I'm trying to do more than one thing at a time here, but I do really appreciate the help.

---

### Post by porchrat on 2008-10-13
Even if we don't get this script running it is quite acceptable to just run that command straight from the command line when in the directory in question, however I will get it to output the list to a text file just to make it easier to sift through the returned filenames.

You guys certainly have made my life a lot easier :)

Thanks..but by all means keep the advice coming as I would like to get this script working, both for ease of use and of course for the challenge.

---

### Post by geirha on 2008-10-13
I found it. It's not grep that is waiting for input, it's tar.

```
find /directory_path -iname "*.tar" -exec tar t '{}' \; | grep $1
```

You've forgotten the f.

```
find /directory_path -iname "*.tar" -exec tar t[COLOR="Red"]f[/COLOR] {} \; | grep [COLOR="Red"]"[/COLOR]$1[COLOR="Red"]"[/COLOR]
```

---

### Post by porchrat on 2008-10-13
> **geirha said:**
> I found it. It's not grep that is waiting for input, it's tar.

```
find /directory_path -iname "*.tar" -exec tar t '{}' \; | grep $1
```

You've forgotten the f.

```
find /directory_path -iname "*.tar" -exec tar t[COLOR="Red"]f[/COLOR] {} \; | grep [COLOR="Red"]"[/COLOR]$1[COLOR="Red"]"[/COLOR]
```

A round of applause for geirha!! =D>

I can't believe that was all that was missing!

Runs like an Zimbabwean MDC supporter being chased by Zanu-PF secret police now.

Well thanks guys for all your time and effort.  Once again I've come away with more knowledge than I had before.  I now know a lot more about how grep reads arguments and I've been introduced to zgrep.

Thank you all and remember "I can't do this without my third arm!" -Zaphod

---

### Post by porchrat on 2008-10-14
OK got another problem now...seems that the script doesnt print out the full path of the file it finds.  Sure it tells me which subdirectories within the archive contain the files I need, but it doesn't output which compressed archive it is contained in.

For example:

when searching for foo.bar:

it ouputs directory/subdirectory/foo.bar

instead of archive.zip/directory/subdirectory/foo.bar

is there a way to get it to print this information out?...like get it to maybe echo what it is searching through as it goes?

---

### Post by justleen on 2008-10-14
include the -print for the find command, that prints the file its has found, thus the archive.

I noticed that yesterday.. I tried an echo {} in between, but that results in stdout as well.. so I think the only way to get the filenames, is to let find spit it out..


> Runs like an Zimbabwean MDC supporter being chased by Zanu-PF secret police now. 
LOL

---

### Post by geirha on 2008-10-14
To get that format, you'll either have to split it up a bit by saving the output of find to a variable or file, then loop over it, or you can add the grep inside the -exec, giving grep access to the filename.

```

find /directory_path -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;

```

---

### Post by porchrat on 2008-10-14
Thanks you guys will give them both a go as soon as possible.  Don't know if I will be able to get around to it today though, as I am extremely busy at the moment.

Although I see you are keeping an eye on this thread which is great!

---

### Post by porchrat on 2008-10-14
> **geirha said:**
> To get that format, you'll either have to split it up a bit by saving the output of find to a variable or file, then loop over it, or you can add the grep inside the -exec, giving grep access to the filename.

```

find /directory_path -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;

```

Tried the -print flag and it didn't work unfortunately.

Have looked at geirha's suggestion, and while some of it makes sense I am still wondering about this part:

```
bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

Does that mean that the entire string after "bash" is passed in one go?  if so why can't I use something like "&&" instead?

---

### Post by justleen on 2008-10-14
the find -exec only accepts one argument/command. So to work around that, you  enter one command, bash in this case, with options - which happens to be other commands.. This is "just" a work around to execute more then one command with find -exec 

you cant use &&, that would launch seperate command. What he is doing here is passing the output of tar tf through a pipe to grep..

---

### Post by porchrat on 2008-10-14
> **justleen said:**
> the find -exec only accepts one argument/command. So to work around that, you  enter one command, bash in this case, with options - which happens to be other commands.. This is "just" a work around to execute more then one command with find -exec 

you cant use &&, that would launch seperate command. What he is doing here is passing the output of tar tf through a pipe to grep..

OK before you posted that I tried playing around with "&&" seeing as I thought I was soo clever.  Needless to say nothing came of it.  That rather large set of commands that geirha posted doesn't seem to do anything.  It just sort of hangs there.  Perhaps there is some sort of syntax error?...although I can't see anything wrong with that script.

---

### Post by porchrat on 2008-10-14
Also is there any particular reason why I can't use this:

```
find ~/Desktop/interesting -name "*.tar.*" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

as opposed to this:

```
find ~/Desktop/interesting -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

---

### Post by geirha on 2008-10-14
> **porchrat said:**
> Tried the -print flag and it didn't work unfortunately.

Have looked at geirha's suggestion, and while some of it makes sense I am still wondering about this part:

```
bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

Does that mean that the entire string after "bash" is passed in one go?  if so why can't I use something like "&&" instead?

bash -c "bash code here" will spawn a new shell and execute the bash code. We have to use that because -exec will only accept one process, while tar | grep is two. You can use && and || in there too if you like, but I don't see why you would want to do that in this case.

As an example, if we did: 
```
find ... -exec tar tf {} | grep -H --label={} --color=auto "$1" \;
```
It would try to run «find ... -exec tar tf {} » and pipe the output to «grep -H --label={} --color=auto "$1"» 

And if we quote the commands behind -exec
```
find ... -exec "tar tf {} | grep -H --label={} --color=auto \"$1\"" \;
``` It would still not work, because the command behind -exec isn't executed in a shell, and the | is the shells job to interpret. Thus, | would be taken as an argument to tar.

That's why we must specifically tell -exec to run the commands in a shell. Hope that made sense :)

---

### Post by geirha on 2008-10-14
> **porchrat said:**
> Also is there any particular reason why I can't use this:

```
find ~/Desktop/interesting -name "*.tar.*" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

as opposed to this:

```
find ~/Desktop/interesting -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" -exec bash -c "tar tf {} | grep -H --label={} --color=auto \'$1\'" \;
```

That's fine, though use the pattern "*.tar*" instead, because "*.tar.*" would not match *.tar files. Of course there is the possibility that a file could be called something like .target or whatever, and that would then match too. I doubt that would be a problem though.

---

### Post by geirha on 2008-10-14
> **porchrat said:**
> OK before you posted that I tried playing around with "&&" seeing as I thought I was soo clever.  Needless to say nothing came of it.  That rather large set of commands that geirha posted doesn't seem to do anything.  It just sort of hangs there.  Perhaps there is some sort of syntax error?...although I can't see anything wrong with that script.

I see I did a mistake in my example, by escaping the quotes for the parameter to grep, and also, the -o (ors) need to be grouped with \( \).
```

find ~/Desktop/ \( -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" \) -exec bash -c "tar tf {} | grep -H --label={} --color=auto '$1'" \;

find ~/Desktop/ -name "*.tar*" -exec bash -c "tar tf {} | grep -H --label={} --color=auto '$1'" \;

```

Sorry!

---

### Post by porchrat on 2008-10-14
> **geirha said:**
> bash -c "bash code here" will spawn a new shell and execute the bash code. We have to use that because -exec will only accept one process, while tar | grep is two. You can use && and || in there too if you like, but I don't see why you would want to do that in this case.

As an example, if we did: 
```
find ... -exec tar tf {} | grep -H --label={} --color=auto "$1" \;
```
It would try to run «find ... -exec tar tf {} » and pipe the output to «grep -H --label={} --color=auto "$1"» 

And if we quote the commands behind -exec
```
find ... -exec "tar tf {} | grep -H --label={} --color=auto \"$1\"" \;
``` It would still not work, because the command behind -exec isn't executed in a shell, and the | is the shells job to interpret. Thus, | would be taken as an argument to tar.

That's why we must specifically tell -exec to run the commands in a shell. Hope that made sense :)

It did indeed make sense.  I also just found out why the script you posted wasn't running...yay!

It was because the section "bash -c" passes the next argument as a literal string to a new shell, and therefore you don't need the backslashes with \'$1\' all you need is $1.

It seems to work now...this is what I ended up with:

```
find directory_path -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" -exec bash -c "tar tf {} | grep -H --label={} --color=auto $1" \;
```

Now I merely need to follow that up with another similar line, except it will read something like this:

```
find directory_path -name "*.zip" -exec bash -c "unzip -l {} | grep -H --label={} --color=auto $1" \;
```

Let me know what you think. :)

---

### Post by porchrat on 2008-10-14
> **geirha said:**
> I see I did a mistake in my example, by escaping the quotes for the parameter to grep, and also, the -o (ors) need to be grouped with \( \).
```

find ~/Desktop/ \( -name "*.tar" -o -name "*.tar.gz" -o -name "*.tar.bz2" \) -exec bash -c "tar tf {} | grep -H --label={} --color=auto '$1'" \;

find ~/Desktop/ -name "*.tar*" -exec bash -c "tar tf {} | grep -H --label={} --color=auto '$1'" \;

```

Sorry!

It is OK it seems like I pretty much discovered the same thing at the same time.  Hopefully that means I'm learning :)

EDIT: Strange though that while this process runs the HDD light doesn't illuminate at all, despite all the activity...strange.

---

### Post by geirha on 2008-10-14
> **porchrat said:**
> It is OK it seems like I pretty much discovered the same thing at the same time.  Hopefully that means I'm learning :)

Excellent! Do put quotes around $1 still though, '$1' will work and \"$1\" will work, but not \'$1\'.

The reason why you want quotes around that, is if you want to search for something with spaces in. e.g.

```
./yourscript 'Program Files'
```

If you don't quote, you'd be running "... | grep Program Files" which would grep for "Program" in a file called Files

---

### Post by porchrat on 2008-10-14
Is there anything wrong with this set of commands?

```
find /directory_path -iname "*.zip" -exec bash -c "unzip -l {} | grep -H --label={} --color=auto $1" \;
```

It seems to be finding files that end in .zip that don't actually exist.  Like it will say something like:

```
unzip:  cannot find or open /directory_path/directory/subdirectory, /directory_path/directory/subdirectory/randomfile.zip or /directory_path/directory/subdirectory/randomfile.ZIP.
grep: README.txt: No such file or directory

```

I was testing it by searching for README.txt which as you can imagine is rather abundant.  I get that message nearly constantly and only ever concerned with .zip files which leads me to believe it has something to do with the line I have shown above.

---

### Post by geirha on 2008-10-14
Ah, right, we're still lacking some quoting it seems. It has probably found a zip-file with spaces, or a zip file inside a dir with spaces.

```
find /directory_path -iname "*.zip" -exec bash -c "unzip -l '{}' | grep -H --label='{}' --color=auto '$1'" \;
```

We didn't need to quote the {} before, because find was executing them, but since we now are using bash, they need to be quoted so the spaces are treated as part of pathnames.

---

### Post by Slim Odds on 2008-10-14
> **porchrat said:**
> EDIT: Strange though that while this process runs the HDD light doesn't illuminate at all, despite all the activity...strange.

If you have a descent amount of memory and you're already run the script once, all of the data is in the disk cache. Hence, no need to go do disk again.

---

### Post by porchrat on 2008-10-14
> **geirha said:**
> Ah, right, we're still lacking some quoting it seems. It has probably found a zip-file with spaces, or a zip file inside a dir with spaces.

```
find /directory_path -iname "*.zip" -exec bash -c "unzip -l '{}' | grep -H --label='{}' --color=auto '$1'" \;
```

We didn't need to quote the {} before, because find was executing them, but since we now are using bash, they need to be quoted so the spaces are treated as part of pathnames.

That fixed it, but I don't really understand why it did fix it.  Is it possible for you to explain in a little more detail (sorry I obviously catch on slowly)

This script now does everything I need it to do...awesome!

---

### Post by geirha on 2008-10-14
```
find /directory_path -iname "*.zip" -exec bash -c "unzip -l '{}' | grep -H --label='{}' --color=auto '$1'" \;
```

Right, starting with this line, bash goes over it replacing all variables ($1 in this case) and processing the quotes. Let's assume $1 is README

find is then executed, and it's got 8 arguments (excluding the zeroth)
```
$0=find 
$1=/directory_path 
$2=-iname 
$3=*.zip
$4=-exec
$5=bash 
$6=-c
$7=unzip -l '{}' | grep -H --label='{}' --color=auto 'README'
$8=;

```
Notice that the seventh contain a lot of spaces, that's because we had quotes ("") around it. Making it treated as one argument instead of many, since bash treats space as a delimiter of arguments.

find parses each argument, then starts searching for files matching *.zip. Ones it finds a hit, it executes all arguments between "-exec" and ";", but first replacing all occurances of {} with the path of the file it found. Let's say it found "/tmp/foo bar.zip": It then executes this:

```
$0=bash
$1=-c
$2=unzip -l '/tmp/foo bar.zip' | grep -H --label='/tmp/foo bar.zip' --color=auto 'README'

```

Notice the space between foo and bar is now inside quotes. Otherwise bash would now have run unzip -l /tmp/foo bar.zip which will surely fail.

bash starts, and reads it's two arguments. -c tells it that the next argument contains a list of commands to run. So it does that. And ends up running two processes simultaneously, with the output of the first process connected as the input of the second:

```
$0=unzip
$1=-l
$2=/tmp/foo bar.zip

```
```
$0=grep
$1=-H
$2=--label=/tmp/foo bar.zip
$3=--color=auto
$4=README

```

Did this make sence?

---

### Post by porchrat on 2008-10-14
> **geirha said:**
> ```
find /directory_path -iname "*.zip" -exec bash -c "unzip -l '{}' | grep -H --label='{}' --color=auto '$1'" \;
```

Right, starting with this line, bash goes over it replacing all variables ($1 in this case) and processing the quotes. Let's assume $1 is README

find is then executed, and it's got 8 arguments (excluding the zeroth)
```
$0=find 
$1=/directory_path 
$2=-iname 
$3=*.zip
$4=-exec
$5=bash 
$6=-c
$7=unzip -l '{}' | grep -H --label='{}' --color=auto 'README'
$8=;

```
Notice that the seventh contain a lot of spaces, that's because we had quotes ("") around it. Making it treated as one argument instead of many, since bash treats space as a delimiter of arguments.

find parses each argument, then starts searching for files matching *.zip. Ones it finds a hit, it executes all arguments between "-exec" and ";", but first replacing all occurances of {} with the path of the file it found. Let's say it found "/tmp/foo bar.zip": It then executes this:

```
$0=bash
$1=-c
$2=unzip -l '/tmp/foo bar.zip' | grep -H --label='/tmp/foo bar.zip' --color=auto 'README'

```

Notice the space between foo and bar is now inside quotes. Otherwise bash would now have run unzip -l /tmp/foo bar.zip which will surely fail.

bash starts, and reads it's two arguments. -c tells it that the next argument contains a list of commands to run. So it does that. And ends up running two processes simultaneously, with the output of the first process connected as the input of the second:

```
$0=unzip
$1=-l
$2=/tmp/foo bar.zip

```
```
$0=grep
$1=-H
$2=--label=/tmp/foo bar.zip
$3=--color=auto
$4=README

```

Did this make sence?

Perfect sense.  I understand now that it was attempting to run "unzip -l" using the first half of a filename with spaces as the entire filename and of course that failed as this file did not really exist.  It therefore only handled .zip files in which there were no spaces.  Thank you for explaining it to me :)

Well thank you all of you it has been yet another incredible learning experience and I hope to continue to grow and learn new things about scripting and how Linux operates in general.

---

