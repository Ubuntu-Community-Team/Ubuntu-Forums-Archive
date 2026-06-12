---
title: "[SOLVED] Efficiently orgnazing files via Command Line"
date: 2008-11-18
forum: General Help
---

### Post by bonfire89 on 2008-11-18
Hey there,


I was wondering, is there a way to efficiently organize files using the command line?


Using a GUI it's nice because you can ctrl select, shift select or even draw that box around groups of files and click and drag them to other folders etc.

Is there away to do the same thing with similar efficiency from the command line?

Perhaps, one route might be to make a script... but that still seems a bit cumbersome.

---

### Post by sdennie on 2008-11-18
The command line has many ways of organizing files.  Information about commands like, "cp", "mv", "rm", "tar", etc. can be found by looking at their man page.  For example:

```

man cp

```

Also, wildcards are a way to match multiple files and you'll want to know how to use them.  This tutorial looks good: [http://www.helpdesk.umd.edu/systems/wam/general/1098/](http://www.helpdesk.umd.edu/systems/wam/general/1098/)

---

### Post by bonfire89 on 2008-11-18
aha yes, I know about those, but I did humour it incase I was missing something. It states 

"Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

specifically SOURCE(s) so, I can at specify a few files at a time. 

I think this is one play where a GUI may definitely win.

At least in my case, If I want to sort my thousands upon thousands of mp3s it would be annoying to do so via CLI, even with people able to have multiple sources, and with TAB completion.

Being able to manipulate the files without having to type their file names (even fractionally) would be good.

Be able to go through a list, and select them for moving some how.

Maybe the day I start developing... ;)

But Thanks :)

---

### Post by olejorgen on 2008-11-18
It's absolutely cases where a gui file manager is faster than a shell. No shame in using one.

> 
At least in my case, If I want to sort my thousands upon thousands of mp3s it would be annoying to do so via CLI, even with people able to have multiple sources, and with TAB completion.
Depending on how you're sorting them, this sounds like the job of a script. (unless they have no tags and is named badly)

If you want a "gui filemanager" running in the shell, I've heard good things about midnight commander

---

### Post by deadowl on 2008-11-18
Learning about piping and grep will be your best bet to do this most efficiently.

What you probably want, especially since it's music files:

```

#find files:
ls -1 | grep 'filename_pattern'

#move files:
mv `ls -1 | grep 'source_file_pattern'` destination_folder

#move files and have it output what's being moved where:
mv -v `ls -1 | grep 'source_file_pattern'` destination_folder

#move files and have it output to a file what's being moved where:
mv -v `ls -1 | grep 'source_file_pattern'` destination_folder > output.txt

```

Other than running that, you just have to mkdir for every new folder you add.

For instance, let's say I have (ls -1):

meow1.txt
meow2.txt
meow3.doc
woof1.doc
woof2.doc
woof3.txt

I'd type:

mkdir meow
mv `ls -1 | grep 'meow'` meow
mkdir woof
mv `ls -1 | grep 'woof'` woof

Alternatively, I could do:
mkdir txt
mv `ls -1 | grep '.txt'` txt
mkdir doc
mv `ls -1 | grep '.doc'` doc

So yea, just copy and Ctrl+Shift+V into your terminal, replace the text you need to, and have fun making moving files around easier.

---

### Post by lotharz0r on 2008-11-18
The CLI is very powerful, and if you learn some of the commands and get into piping you will probably prefer to do stuff like this in the terminal.
I have made several aliases in my /etc/bash.bashrc which does sorting of folders and similar.

Here is an example of an alias I use which sorts directories.
alias mp3sort='for dir in *; do y=`echo $dir | sed -e 's/_-_/-/g'`; x=`echo $y | cut -f1 -d-`; mkdir /path/to/musicdir/$x; mv -v $dir /path/to/musicdir/$x/; done'

what this command does is basicly:
## to loop through all dirs in the current dir, 
for dir in *; do
## if the directories is named Artist_-_Album i want to make a temporary variable without the underscores to easier determine the artist name. So I use sed to replace _-_ with just -
y=`echo $dir | sed -e 's/_-_/-/g'`;
## Now I make one variable with the artist name.
## I use cut to cut the variable on each occurence of -
## I know that the artist and album name is seperated by -
x=`echo $y | cut -f1 -d-`;
## Now that x=the artist name I want to make a dir for that artist.
## if the dir allready exists it will still move on in the script
mkdir /path/to/musicdir/$x;
## Now that we are sure that the artist dir exists we want to move the directory
mv -v $dir /path/to/musicdir/$x/; 
## end of script
done

When you run this command it will run the series of commands from do; to done on each directory in the current dir, you will end up with a nicely sorted music directory like this:
Artist1/Arist-album
Arist2/Arist-album
When you had this before:
Artist1-album
artist2-album
artist3-album
and so on.

the "find" command is also very powerful.
It can do recursive searches and perform commands on each of the results it gathers.

For example if I open an terminal and go to /media/movies/ and want to run a command on all directories in this folder that contains a specific filename I can use this alias:
alias unrar-recursive='find -name *.??? -execdir /path/to/command -prefix '{}' \;'

(Replace *.??? with your file)

---

### Post by deadowl on 2008-11-18
Aliases are nice, but not a great thing to use unless you absolutely know what you're doing.

---

### Post by lotharz0r on 2008-11-19
Of course.
The comands in my post dont need to be used in an alias, you can also use them as regular commands, I have just made aliased for them to make it easier for myself.

---

### Post by KeyserSoze93 on 2008-11-19
You can use midnight command, and use Insert to tag a set of files to move / copy.

---

### Post by bonfire89 on 2008-11-29
awesome! midnight command will definitely work really well especially in the mean time, and for a bunch of the mp3s as they are terribly named

but, in the future, I would like to be using the alternative methods shown/mentioned. 

Certainly a big help in terms of general command usage.

thanks!

---

