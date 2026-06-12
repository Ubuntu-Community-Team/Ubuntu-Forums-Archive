---
title: "[SOLVED] mkdir and wildcards query"
date: 2008-10-30
forum: General Help
---

### Post by Krydahl on 2008-10-30
I have a set of directories where all the sub-directories have a similar structure. I find I now want to add a new sub-directory to this structure.

I thought I'd be able to do:

mdkir toplevel/*/oldfolder/newfolder

so that all directories under toplevel that have the directory oldfolder in them get this newfolder. It doesn't seem to work. It says, "mkdir cannot create directory: No such file or directory."

I can't see an option in mkdir's man to help. Anyone any ideas how I do this?

---

### Post by anotherdisciple on 2008-10-30
I'm not at a linux computer, but I don't think there is a "toplevel folder" that I recall. If there was, you left something off.. the first "/"...

mdkir [COLOR="Red"]/[/COLOR]toplevel/*/oldfolder/newfolder

or you need to make it relative to your working directory

---

### Post by Krydahl on 2008-10-30
Yes, there isn't a directory called toplevel - it was a made up name in an attempt to illustrate what I was talking about. And, yes, I'd need to be in whatever directory contained toplevel for that command to work.

My query is, can I use a wildcard like this? If so, how?

---

### Post by Portmanteaufu on 2008-10-30
As I understand things, when you use a wildcard operator the '*' itself is replaced by all file names that could match your query all in a single string. (That is, it does not execute the same command once using each match.)

For example, 
```
ls *.jpg
```
when run in a directory containing:

text1.txt  img.jpg  img2.jpg  resume.pdf

would *really*be running

```
ls img.jpg img2.jpg
```

This works out well for a lot of programs like ls and cp, which can take a variable number of arguments. In your case, I suspect that the mkdir command actually comes out looking something like this: 

```

mdkir toplevel/dir1 dir2 dir3 dir4 dir5/oldfolder/newfolder

```

I could be wrong about this, I'm just speaking from my own experience.

---

### Post by Krydahl on 2008-10-30
Sounds plausible - disappointing.

I suppose I can write a bash script that cds down the directory structure and creates the new directory in a loop.

Thanks for the reply.

---

### Post by Portmanteaufu on 2008-10-30
Yeah, sorry. It seems like wildcards only match in the current directory as well.

Here's a script to take a new directory to make and a variable number of directory arguments and run mkdir in each of them: 

```

#!/bin/bash
TOMAKE="$1"
shift
for i in $*
do
        #Append file to make to the end of each parameter
        echo $i$TOMAKE
        mkdir $i$TOMAKE
done

```

Then run the script (here called "mkdir_wrapper") like so: 

```

./mkdir_wrapper [new Directory Name] */

```

The */ will match all directories in the current directory. You could use a similar script to cd into each argument and run mkdir_wrapper to create the new path structure.

Hope that helps!

---

### Post by Krydahl on 2008-10-30
Cheers, that'll save me some. Thanks.

---

