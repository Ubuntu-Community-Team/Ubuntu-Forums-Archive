---
title: "Help convert a win shell script to linux"
date: 2008-07-10
forum: General Help
---

### Post by gdoutch on 2008-07-10
I was wondering if there's anyone out there who could help with this. The point of it is to be able to launch [Jython]("http://www.jython.org/Project/") on a USB stick (using standalone jython.jar, as a cross-platform [Portable Python]("http://www.portablepython.com/")) whether it's on windows or linux. I'm less familiar with linux so I'm wondering if anyone could help translate this windows script:

Part 1 read in arguments list
```

@echo off

set ARGS=
:loop
if [%1] == [] goto end
    set ARGS=%ARGS% %1
    shift
    goto loop
:end

```

Part 2 What DIR am I in?
```

rem get current dir
set CURDIR=%~dp0

```

Part 3
current DIR has my jython.jar and a subdirectory called 'jars' which are the files I want to include on my class path.
```

rem add jython to classpath
set MYCP="%CURDIR%jython.jar"
rem set jars dir
set JARS=%CURDIR%jars\

```

Part 4
Get a list of all of the jar files in the /jars direcory and add them to a parameter in the format "/path/to/jars/jar1.jar";"path/to/jars/jar2.jar"
```

rem add jars to the classpath
for /F %%a in ('dir %JARS% /a /b /-p /o') do set MYCP=%MYCP%;"%JARS%%%a"

```

Part 5 java launch command
```

rem java launch command
java -classpath %MYCP% org.python.util.jython %ARGS%

```

---

### Post by Pablo89 on 2008-07-10
Most parts of the script look completely unnecessary, but... what I've just wrote seems to be possibly most similar to your version (I don't use jython, so I'm not sure if it shall work... but it should :) ).

```
#!/bin/bash

#Part 1 read in arguments list
ARGS="$@"

#Part 2 What DIR am I in?
CURDIR="$PWD"

#Part 3 current DIR has my jython.jar and a subdirectory called 'jars' which are the files I want to include on my class path.
MYCP="$CURDIR/jython.jar"
JARS="$CURDIR/jars/"

#Part 4 Get a list of all of the jar files in the /jars direcory and add them to a parameter in the format "/path/to/jars/jar1.jar";"path/to/jars/jar2.jar"
for a in $(ls -A)
do
MYCP="$MYCP;$JARS$a"
done

#Part 5 java launch command
java -classpath "$MYCP" org.python.util.jython "$ARGS"
```

---

### Post by gdoutch on 2008-07-10
Many thanks, it mostly works, the only part is part 4, adding the list of files to the class path, it doesn't add any of the files from the sub directory to the list.

---

### Post by Pablo89 on 2008-07-11
Whoops! Of course, I'm listing a wrong directory (the current one instead of JARS)... Change that line (beginning of the loop):

```
for a in $(ls -A "$JARS")
```

---

### Post by ghostdog74 on 2008-07-11
> **Pablo89 said:**
> Whoops! Of course, I'm listing a wrong directory (the current one instead of JARS)... Change that line (beginning of the loop):

```
for a in $(ls -A "$JARS")
```

better to use a while and read loop in case of spaces in $JARS
```

ls -A | while read line
do
 .....
done

```

---

### Post by gdoutch on 2008-07-11
Thanks for the help guys.

I've still not quite got it sussed, but will post back the answers when I get back after a long weekend. I've had some help from a guy at work with using sed to do the job.

But first,

I never wanted $PWD, instead I required

```
CURDIR=$(dirname $0)
```

Gives the directory that the file is located in, as opposed to the working directory, which could be anywhere.

---

### Post by gdoutch on 2008-07-15
OK I have the answer. The main problem I was getting was that the java classpath was not converted. 

Linux uses : as a separator 
while win uses ;

(no wonder the script wouldn't work #-o )

Therefore the final working script was:

```

#!/bin/sh

# get the current directory:
CURDIR=$(dirname $0)

# set the jar lib directory
JARS=$CURDIR/jars/

# add all of the jars to the classpath, separated with a colon
MYCP=$(ls $JARS/ | sed "s#^#$JARS&#" | sed "s/$/:/" | xargs echo | sed 's/: */:/')

# add the jython.jar
MYCP="$MYCP$CURDIR/jython.jar"

# launch within rlwrap to help with L/R UP/DOWN chars and command recall
rlwrap -r java -classpath "$MYCP" org.python.util.jython "$@"
```

Anyway, thanks guys for your help.

---

