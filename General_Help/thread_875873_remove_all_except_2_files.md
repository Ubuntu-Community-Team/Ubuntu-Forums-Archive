---
title: "remove all except 2 files"
date: 2008-07-31
forum: General Help
---

### Post by ra2008 on 2008-07-31
Hi,
asumme i have the files: a,b,c,d
i want to delte them all except a,b
what is the command line?
thanks

---

### Post by sanocli on 2008-07-31
Hi,

I think that the most simple is to copy a and b to another directory, remove all in you directory and paste a,b. 

This is the command lines :
```

cp /your_directory/a /your_save_directory
cp /your_directory/b /your_save_directory
rm -rf /your_directory/* 
cp /your_save_directory/a /your_directory
cp /your_save_directory/b /your_directory

```


Maybe you have to do a sudo before if root is the owner of the directory

---

### Post by ra2008 on 2008-07-31
well this is a simple example of two files.
what if there are many files...??

---

### Post by justleen on 2008-07-31
```
 find . ! -name file1 ! -name file2 -maxdepth 1 -exec rm {} \;
 
```

find all files in current dir that do NOT (the !)  match filename1 or filename 2
the maxdepth 1 ensures it doenst descend into other sub dirs (leave it out of thats is what you want)
-exec rm {} \;   removes and found files.

run  WITHOUT  the -exec bit first, and check if its finds what you want to be deleted

---

### Post by ghostdog74 on 2008-07-31
> **ra2008 said:**
> Hi,
asumme i have the files: a,b,c,d
i want to delte them all except a,b
what is the command line?
thanks

just use range negation
```

ls -l [^ab]
rm [^ab]

```

---

### Post by justleen on 2008-07-31
> **ghostdog74 said:**
> just use range negation
```

ls -l [^ab]
rm [^ab]

```

that would only work if the files are actually called (or start with) a and b
so if you have a file ax and ay, and ay should remain, it wouldnt work?

ps: isnt the syntax ```
 ls -l [^ab]* 
```

---

### Post by ra2008 on 2008-07-31
> **justleen said:**
> ```
 find . ! -name file1 ! -name file2 -maxdepth 1 -exec rm {} \;
 
```

hi,
thanks, actually this worked.
but i get this after applying the above command;
```
rm: cannot remove directory `.'
raed@raed-laptop:~/r$ find . ! -name b ! -name a -maxdepth 1 -exec rm {} \;
find: warning: you have specified the -maxdepth option after a non-option argument !, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it). Please specify options before other arguments.

```

onemore
> ls -l [^ab]*
what does this do "^" ??

---

### Post by justleen on 2008-07-31
the "^" stand for "start of line", like "$" is the end of line

the find is complaining about presedence.. try 
find . -maxdepth 1 ! -name b ! -name a -exec rm {} \;

its complaining it cant delete the "." directory (the current dir).. which is only logical..

---

### Post by ghostdog74 on 2008-07-31
> **justleen said:**
> that would only work if the files are actually called (or start with) a and b
so if you have a file ax and ay, and ay should remain, it wouldnt work?

ps: isnt the syntax ```
 ls -l [^ab]* 
```

well, OP did give examples of file names that are called a , b, c and d right?:) If ax and ay, and ay should remain, a different arrangement is needed
```

# touch ay ax
# ls -1
ax
ay
# rm a[^y]
# ls -1
ay

```

---

### Post by john test on 2008-07-31
> **justleen said:**
> the "^" stand for "start of line", like "$" is the end of line

the find is complaining about presedence.. try 
find . -maxdepth 1 ! -name b ! -name a -exec rm {} \;

its complaining it cant delete the "." directory (the current dir).. which is only logical..

1.  Can I replace the "." with "pwd" and accheive the same result?
2.  Do I need the -maxdepth if I don't specify recursive with rm -RF?

---

### Post by mannheim on 2008-07-31
Another option for those of us who can never remember the syntax of "find" or shell patterns is something like (untested):

```

ls --hide=file1 --hide=file2  [COLOR="Blue"]# And if that seemd to work, then ...[/COLOR]
rm `ls --hide=file1 --hide=file2`

```

---

### Post by justleen on 2008-08-01
> **john test said:**
> 1.  Can I replace the "." with "pwd" and accheive the same result?
2.  Do I need the -maxdepth if I don't specify recursive with rm -RF?

1. yes, but you need to include pwd as a command ```

find `pwd` -name whatever

2. yes, you need the -maxdepth option, even if you dont do a rm -rf.
Find is always recursive. the -exec option executes a command on all found files. so if you have a tree of files and dirs, and execute
[code]find . -exec rm {} \; 
``` it will delete all files, and try to delete all directories as well - but rm will complain that found dir is not a regular file.

@Ghostdog: Never underestimate the power of regexes! I never thought of using  regex ranges in that way, on "ordinary" commands.. Thanks for the lesson!

---

### Post by ghostdog74 on 2008-08-01
> **justleen said:**
> 

@Ghostdog: Never underestimate the power of regexes! I never thought of using  regex ranges in that way, on "ordinary" commands.. Thanks for the lesson!
if you are interested , you can take a look at the bash man page. If you turn on extglob
```

# shopt -s extglob
# ls -ltr !(*.txt)

```
the above list files not ending with .txt.

---

### Post by justleen on 2008-08-01
what kinda baffles me, is that by default it seems to include the NOT option..
```
 ls -l [^a]
```
I'd expect to show files starting with "a" not exclude them..

And yes, im intrested! cant get enough of bash... ls with pattern matching and echo to string replace seem to be this weeks lessons :)

---

### Post by ghostdog74 on 2008-08-01
> **justleen said:**
> what kinda baffles me, is that by default it seems to include the NOT option..
```
 ls -l [^a]
```
I'd expect to show files starting with "a" not exclude them..

And yes, im intrested! cant get enough of bash... ls with pattern matching and echo to string replace seem to be this weeks lessons :)

the ^ inside a square bracket implies NOT, "not starting of a string". If you look at the man page of bash under Pathname expansion: 
> 
  [...]  Matches  any  one of the enclosed characters.  A pair of characters separated by a hyphen denotes a range expression; any
              character that sorts between those two characters, inclusive, using the current locale's collating sequence and character
              set,  is matched.  If the first character following the [ is a !  or a ^ then any character not enclosed is matched. 

the link to the bash manual in my sig shows you lots of examples with bash string matching/substitution/expansion and such. you might want to have a look

---

### Post by justleen on 2008-08-01
I realize that now.. but its still "weird" since that syntax goes against the normal sed/vi/find+regex syntax.. 

And its bash-only, sh/ksh dont understand this kind of handiness..

Still, thanks for the explanation. And TLDP is already in my Favs :)

---

### Post by ghostdog74 on 2008-08-01
its not weird actually. Older Bash does not recognize standard RE. It  does basic wildcard expansion and globbing. From version 3 onwards, Bash has so called "regexp" using =~ eg ```
if [[ $1 =~ $regex ]];
```

---

### Post by justleen on 2008-08-01
> **ghostdog74 said:**
> its not weird actually. Older Bash does not recognize standard RE. It  does basic wildcard expansion and globbing. From version 3 onwards, Bash has so called "regexp" using =~ eg ```
if [[ $1 =~ $regex ]];
```

Can we meet up for coffee and BASH talk? :)

---

### Post by Cypher2 on 2010-12-06
I have a similiar issue as to remove files and folders recursively through a bash script except for the .png file type.

when i run cd /DIRECTORY followed by rm -rf !(*.png) it works... but whenever its within a bash script, the terminal returns the following error:

syntax error near unexpected token `('

how do I make the command run as absolute then?

Thanks for any help

---

### Post by sisco311 on 2010-12-06
> **Cypher2 said:**
> I have a similiar issue as to remove files and folders recursively through a bash script except for the .png file type.

when i run cd /DIRECTORY followed by rm -rf !(*.png) it works... but whenever its within a bash script, the terminal returns the following error:

syntax error near unexpected token `('

how do I make the command run as absolute then?

Thanks for any help

You have to enable extglob:
```
#!/bin/bash

shopt -s extglob
echo !(*.png)

```

---

### Post by Cypher2 on 2010-12-06
Thank you very much!

I'm not that much a genius in programming or scripting.. but i get around in making it work.. thanks to you guys :)

So I guess shopt is a script option enabler?

---

### Post by sisco311 on 2010-12-06
> **Cypher2 said:**
> 
So I guess shopt is a script option enabler?


Yes, it's a bash builtin which allows you enable/disable options.

See:
```
man bash | less +/"shopt \[-pqsu\]"
```

---

### Post by Cypher2 on 2010-12-06
Would you mind pointing out whats wrong with this?



read -p "Would you like to upgrade? (y/n)"
if [ "$REPLY" == "y" ] || sudo apt-get -y dist-upgrade
elseif read -p "Would you like to reboot? (y/n)"
then [ "$REPLY" == "y" ] || sudo reboot
else
exit
fi



It seems to execute even when I say no..

how can I include multiple reply formats? (yes y YES Yes / no n NO No) ?

---

### Post by sisco311 on 2010-12-06
> **Cypher2 said:**
> Would you mind pointing out whats wrong with this?



read -p "Would you like to upgrade? (y/n)"
if [ "$REPLY" == "y" ] || sudo apt-get -y dist-upgrade
elseif read -p "Would you like to reboot? (y/n)"
then [ "$REPLY" == "y" ] || sudo reboot
else
exit
fi





Check out this guide: 
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)


```

read -p "Would you like to upgrade? (y/n)"
if [ "$REPLY" == "y" ]; then
  sudo apt-get -y dist-upgrade
elseif 
  read -p "Would you like to reboot? (y/n)"
  if [ "$REPLY" == "y" ]; then
    sudo reboot
  fi
fi

exit
fi

```


> **Cypher2 said:**
> 
how can I include multiple reply formats? (yes y YES Yes / no n NO No) ?

Try something like:
```

if [[ $REPLY = [yY] || $REPLY = [yY][eE][sS] ]]; then
  echo yes
else
  echo no
fi

```

---

### Post by Cypher2 on 2010-12-06
Thank you so much for your help.. I'll read up some more on scripting

Thanks again! :)

---

### Post by billibrwer on 2010-12-07
this source is very helpful :p

---

### Post by HiImTye on 2010-12-07
you can do this
```
nautilus /path/to/files
```
select the first file
shift and select the last file
ctrl and deselect the files you want to keep

wasn't that easier?
not everything has to be done the hard way lol

---

### Post by Cypher2 on 2010-12-11
^ the point my friend is that i would like to get rid of some bloating files installed by default with a fresh ubuntu install.. thus, I would like to minimize manual input to a maximum :)


Is anyone here able to help me figure this out:

How does the ubuntu installer figure out if the system is a laptop or a desktop?

You know.. when you type your full name and then the hostanme underneath magically starts  filling in with something like:

"full name"-"laptop/desktop"-"machine oem id"-blabla...

---

