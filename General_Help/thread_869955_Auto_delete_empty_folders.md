---
title: "Auto delete empty folders?"
date: 2008-07-25
forum: General Help
---

### Post by cmatte on 2008-07-25
I need a way to delete empty folders remained after Amarok's reorganization of my media library.
I had just found a thread which seemed very useful to me to delete empty folders, it's here in the archive [http://ubuntuforums.org/showpost.php?p=2251050&postcount=17]("http://ubuntuforums.org/showpost.php?p=2251050&postcount=17"). It also provides deleting a max number of jpegs in every folder (like album arts etc) and then deletes the folder if empty.
All seemed great, but I'm having problems with it!
Of course I gave an eye to it before running and it seemed good, but I'm not that great at bash coding, also half a newbie with Ubuntu :(
The matters are(translated from italian):
A lot of:
> ls: can't access /home/matte/Musica/Example Directory/Example Directory: No file or directory

Seems like a little part of the name has gone, almost every time!
And at the end:
```
rmdir: missing operand
Use "rmdir --help" for further information.

```
Can someone help me to figure this out?

---

### Post by drs305 on 2008-07-25
Would you post the script or command you ended up running? There are several suggestions in the referenced post.

A way to reference a post is to put the post number at the end of the link (example: **#2**). For instance, if you wanted to reference this post, the link would be:
[http://ubuntuforums.org/showthread.php?p=5456064#post5456064**#2**]("http://ubuntuforums.org/showthread.php?p=5456064#post5456064#2")

---

### Post by cmatte on 2008-07-25
No misread, I actually have spaces in many directories!
Anyway the script seemed not to work because I gave it a "linked" start directory, now something works.Also, I've added quotes almost everywhere, here it is the result:
```
#!/bin/bash
##----------------
##Script Name: 
##Description of Script:
##Date:
#-----------------

## USER-SET VARIABLES -----------

# ****** startdir - Set Starting Directory

startdir="/media/DATA 320/Musica"

# ****** maxjpgs - Set Maximum Number of JPGs to Delete - USER NEEDS TO SET THIS VARIABLE
# This allows for deletion of more than one JPG (front cover, back cover, liner notes, etc.)
# while maintaining a margin of safety (i.e., the script can't accidentally delete hundreds of image files
# in a single folder at a time). If you know you only will have one JPG file in a directory, set value to 1. 
# For testing , this was set to 2 to test that the dummy folder with three JPGs + no music files would not be targeted.

maxjpgs=3

## END USER_SET VARIABLES -------


cd "$startdir"

find -type d | while read dir; do
	dircut=$(echo $dir | cut -c3-)
	fulldir="$startdir"/"$dircut"
	numfiles=$(ls -l "$fulldir" | grep "^-" | wc -l)
	jpgfiles=$(ls -l "$fulldir" | grep ".jpg$" | wc -l)

	if [ "$numfiles" = "$jpgfiles" ] && [ "$jpgfiles" != "0" ] && [ "$jpgfiles" -le "$maxjpgs" ] ; then
		filemask=*.jpg
echo *** THIS CODE DELETES THE STRAY JPG FILES
		find "$fulldir" -maxdepth 1 -type f -print0 | xargs -0 rm -f $filemask
	fi
done

echo *** ORIGINAL CODE THAT DELETES EMPTY DIRECTORIES 
find "$startdir" -type d -print0 | xargs -0 rmdir --ignore-fail-on-non-empty --parents

#---
exit
```
I added echos to understand where the script was and I run it as ./delempmusand3jpg >output.txt, shouldn't this print to file the same things I can't see entirely from the console? I simply find there a list of files :confused:
Anyway, now it works! It simply doesn't access a few directories with strange characters in the name, like "Definitivt BEAT, Nummer  6&#8226;96", or with two consecutive spaces, like "Remixland 2006, Volume 5 (disc 2)".
Removed the few spaces and changed the strange directory character, it worked on those directories too.
Thanks for your help drs305!

---

### Post by drs305 on 2008-07-25
I edited my original response about spaces since I thought I misread the post. If you didn't see it all before I edited the post, here is how to handle spaces in the names of folders/filenames:

1. Enclose the entire entry in quotes:  ls "/my directory".
2. Use the escape symbol ( \ ): ls my\ directory

---

### Post by drs305 on 2008-07-25
1. Note: I am not the best source of information on bash scripts. You've been warned. However...

2. Here is a find command, combined with SED pipes, which adds comment symbols at the beginning and end of each result (to account for spaces). The first SED adds the beginning quote symbol, the second adds the trailing quote. (You could combine both SED commands into one if desired.) I've also changed the 'print0' command to 'print' so each line is output on a separate line.

You may be able to incorporate this command into your script to prevent errors due to spaces within the find results.

```

find $startdir -type f -print | sed 's/[^ ][^ ]*/"&/' | sed 's/$/"/g'

```

3. Return to reread #1 ;-)

---

### Post by cmatte on 2008-07-25
Seems like it had done its duty, anyway, you mean to substitute 
```
# *** THIS CODE DELETES THE STRAY JPG FILES
		find "$fulldir" -maxdepth 1 -type f -print | xargs -0 rm -f $filemask
```
with:
> **drs305 said:**
> 
```

find $fulldir -type f -print | sed 's/[^ ][^ ]*/"&/' | sed 's/$/"/g' rm -f $filemask

```
I know, very *newbie* question, but that's what I'm right now:) I understood? Or do I need an extra | like ```

find $fulldir -type f -print | sed 's/[^ ][^ ]*/"&/' | sed 's/$/"/g' | rm -f $filemask

``` ... I am a bit confused about "|" ! Is it a "simple" && ?
You are substituting [ ^][ ^]* with "&\ and $ with "/g ? Could you explain :???: ?
Oh, by the way, just read xargs man and here's the intersting part ```
 Because  Unix  filenames  can contain blanks and newlines, this default
       behaviour is often problematic; filenames containing blanks and/or new&#8208;
       lines  are  incorrectly  processed by xargs.  In these situations it is
       better to use the ‘-0’ option, which  prevents  such  problems.    When
       using  this  option you will need to ensure that the program which pro&#8208;
       duces the input for xargs also uses a null character  as  a  separator.
       If that program is GNU find for example, the ‘-print0’ option does this
       for you.

```
Doesn't it say it should already work as is? I'd like to understand, thanks for your help mate!

---

### Post by drs305 on 2008-07-25
> **cmatte said:**
>  ... I am a bit confused about "|" ! Is it a "simple" && ?
You are substituting [ ^][ ^]* with "&\ and $ with "/g ? Could you explicate :s ?

The " | " symbol is used to 'pipe' output from one command into another (like running it through a pipe I guess). It takes the results of the preceding command and directs it into the following command. The second part of the quoted line is using the SED command, which in this case modifies lines of text piped to it. The code looks at the beginning of the line and adds a quotation symbol and then looks at the end of the string and adds another quotation symbol. I readily admit SED commands can be very hard to look at!

I have learned not to get too deep into areas I can't confidently write about, so as to your other questions -  my intent was to substitute the line into your script, not add another one. I was not trying to run your script - I just experimented in command line. That is why I changed the print0 to print - so each result would display on a separate line. When I ran it with print0 all the results ran together and the quotes weren't inserted.

So if you just want to play with your script while you are waiting for some expert advise, try substituting it and see if it works. 

I only replied to this post because I could answer the pipe part of your question (and it will bump your post to the top again). ;-)

---

