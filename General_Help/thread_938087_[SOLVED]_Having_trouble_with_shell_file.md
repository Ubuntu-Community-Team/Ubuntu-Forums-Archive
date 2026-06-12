---
title: "[SOLVED] Having trouble with shell file"
date: 2008-10-04
forum: General Help
---

### Post by ehellmer on 2008-10-04
I downloaded a shell file called: CSA.sh, it's saved to my desktop. I've tried several times to open it with no success, this is what i've tried:

erik@Automatron:~/Desktop$ cd ~/Desktop
erik@Automatron:~/Desktop$ chmod u+x CSA.sh
erik@Automatron:~/Desktop$ ./CSA.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
./CSA.sh: 12: function: not found
./CSA.sh: 18: mozilla: not found
./CSA.sh: 18: mozilla: not found
./CSA.sh: 19: function: not found
./CSA.sh: 25: netscape: not found
./CSA.sh: 25: netscape: not found
./CSA.sh: 26: function: not found
./CSA.sh: 30: function: not found
./CSA.sh: 33: epiphany: not found
./CSA.sh: 34: function: not found
./CSA.sh: 37: konqueror: not found
./CSA.sh: 38: function: not found
./CSA.sh: 46: seamonkey: not found
./CSA.sh: 46: seamonkey: not found
./CSA.sh: 47: function: not found
./CSA.sh: 50: opera: not found
Error running CSA.sh. Please call the helpdesk.
rm: cannot remove `tmp.csa': No such file or directory
erik@Automatron:~/Desktop$

it then opens up a firefox window telling me there is an error, also the file is removed from my desktop.

---

### Post by Calmatory on 2008-10-04
At least it seems you are missing the standard c++ libraries.

"sudo apt-get install build-essential" might help.

---

### Post by porchrat on 2008-10-04
could you post the contents of the shell file so that we know what it is doing, and therefore why it is failing?

You don't need to add u+x if all you want to do is "open" it.  All you need is u+r.

---

### Post by ehellmer on 2008-10-04
the contents of the file are:

#!/bin/sh
init_dir=`pwd`
mkdir .CSA.TEMP >/dev/null
\cd .CSA.TEMP
SKIP=`awk '/^__BEGIN_GZIP__/ { print NR +1; exit 0; }' $init_dir/$0`
tail -n +$SKIP $init_dir/$0 | gzip -dc | tar x
chmod +x ./engine

#LD_LIBRARY_PATH=.bncsa_deps:$LD_LIBRARY_PATH ./engine >/dev/null
#rm -r .bncsa_deps/
./engine >/dev/null
function doMoz
{
if mozilla -remote 'ping()';
then mozilla -remote "openFile(`pwd`/results.html)";
else mozilla file://`pwd`/results.html ;
fi;
}
function doNetscape
{
if netscape -remote 'ping()';
then netscape -remote "openFile(`pwd`/results.html)";
else netscape file://`pwd`/results.html;
fi;
}
function doFirefox
{
firefox file://`pwd`/results.html
}
function doEphy
{
epiphany file://`pwd`/results.html
}
function doKonq
{
    konqueror `pwd`/results.html
}
function doSeamonkey
{
    if seamonkey -remote 'ping()';
    then
        seamonkey -remote "openFile(`pwd`/results.html)";
    else
        seamonkey file://`pwd`/results.html;
    fi;
}
function doOpera
{
   opera -newwindow `pwd`/results.html  
}
if [ -e `pwd`/results.html ]
then
    doFirefox || doMoz || doNetscape || doOpera || doSeamonkey || doEphy || doKonq
else
    echo "Error running CSA.sh.  Please call the helpdesk."
fi
rm engine
rm agent.config
rm tmp.csa

\cd ..
rm $0
exit 0;

---

### Post by porchrat on 2008-10-04
Try getting the c++ libraries (as mentioned above)

You're going to need them for that.

---

### Post by Calmatory on 2008-10-04
After googling, this seems to be some university stuff. Does this happen to be a homework maybe? I hope not. However, if it is, you shouldn't be asking about it here. ;)

The file seems valid for as far as I can understand it, would need more info about the working directory, especially about "engine". I say the problem is the lack of standard C++ library files. Thus try: ```
sudo apt-get install g++
``` or ```
sudo apt-get install build-essential
```

Hope it helps. :)

---

### Post by ehellmer on 2008-10-04
I used both those codes, and tried it after installing each one. I still got the same response. It's not homework, it's a file to verify your operating system to give you access to the university network.

---

### Post by Calmatory on 2008-10-04
Ok, then try this:

```

sudo apt-get update
sudo apt-get install apt-get install libstdc++5
```

and run your script again.

---

### Post by ehellmer on 2008-10-04
That worked, i was able to execute the file. Thanks.

---

### Post by Calmatory on 2008-10-04
Could you add [SOLVED] to the topic title so others having similar problem will find here easier? :)

---

