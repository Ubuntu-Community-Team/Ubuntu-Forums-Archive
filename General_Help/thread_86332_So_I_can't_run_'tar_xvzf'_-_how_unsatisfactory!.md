---
title: "So I can't run 'tar xvzf' - how unsatisfactory!"
date: 2005-11-04
forum: General Help
---

### Post by monomaniacpat on 2005-11-04
When I run 'tar xvzf', I get the following response:

tar: ndiswrapper-1.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


It happens with any tarball - what can I do!?

Thanks in advance,

Mono.

---

### Post by SickTwist on 2005-11-04
if "tar xvzf" is all that you are typing you are missing the filename.
The f option should be followed by the file that you wish to extract (the action indicated by the x option).

For example:

tar -xvzf ies4linux-1.0.1.tar.gz

You will need to specify the path to the file if it is not in your current directory.

---

### Post by trilo on 2005-11-04
When you get into these sorts of problems, things don't seem to be working etc., it can be a lot faster than this forum to read the manual page for the command you're having difficulty with...

e.g.: typing "man tar" (without the quotes) in a terminal will bring up the manual page for the tar command. It will provide examples (usually) of how to use the command.

Another winning strategy is to search this forum for the command you're trying to use. A simple "tar" (again, no quotes) in the search box will bring up examples of how other people have used the command...

---

### Post by matthew on 2005-11-04
Also, unless it is in your home directory you will need to have root powers. 

This should work provided your original archive file is not corrupted:

```
sudo tar -xvzf filename.tar.gz
```

---

### Post by monomaniacpat on 2005-11-04
No, sorry - I should have been more specific - I AM adding the filename.

---

### Post by monomaniacpat on 2005-11-04
[QUOTE=matthew]Also, unless it is in your home directory you will need to have root powers. 

This should work provided your original archive file is not corrupted:

```
sudo tar -xvzf filename.tar.gz
```[/QUOTE]

Nope, no luck. My file is definately not corrupted - I've tried it on multiple files.

---

### Post by matthew on 2005-11-04
[quote=monomaniacpat]Nope, no luck. My file is definately not corrupted - I've tried it on multiple files.[/quote] But did you try it using sudo?

Also, did you cd into the directory where the tarball is?

i.e. if filename.tar.gz is in /usr/src then I need to
```
cd /usr/src
``` before I
```
sudo tar -xvzf filename.tar.gz
```

---

### Post by monomaniacpat on 2005-11-04
Yes and yes, I've done all the right things.

---

### Post by chrisgibbs on 2005-11-04
In gnome try and open it with archieve manager (which i think is install by default)

If that doesnt work as well it is probably screwed up...

```
tar -xvvzf filename.tar.gz
```

as said above should be fine....

Just a thought - do you have read access to the file?

---

### Post by monomaniacpat on 2005-11-04
I can open and extract it using archive manager... However, when I attempt to cd to the created file, it reads 'no such file or directory'.

How would I find out if I have read access?

---

### Post by aclaunch on 2005-11-05
You can check permissions with "ls -l" in the appropriate directory. You will see a set of symbols "rwx-rw-rw" for example; the first set is for the file "owner" (which shows up in the first column, followed by group), then "user", then "other". If this file is downloaded into one of your own directories (ie /home/your-username/somewhere) then the first set of permissions should be for you.

Alan

---

### Post by skylark on 2005-11-05
[QUOTE=monomaniacpat]Nope, no luck. My file is definately not corrupted - I've tried it on multiple files.[/QUOTE]
Does it just fail silently or does it give some sort of error message?

---

### Post by monomaniacpat on 2005-11-05
Yes, the error message reads:

tar: ndiswrapper-1.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by monomaniacpat on 2005-11-06
[/bump]!

---

### Post by skylark on 2005-11-06
tar -zxvf this_file_does_not_exist.tar.gz
tar: this_file_does_not_exist.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I think you need to double check that 
1. you are in the directory containing the file "ndiswrapper-1.5.tar.gz"
2. you typed in the name of the file correctly

---

### Post by veloct on 2005-11-06
[QUOTE=skylark]tar -zxvf this_file_does_not_exist.tar.gz
tar: this_file_does_not_exist.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I think you need to double check that 
1. you are in the directory containing the file "ndiswrapper-1.5.tar.gz"
2. you typed in the name of the file correctly[/QUOTE]

I agree with skylark, usually you get that error when you aren't in the directory where the file is located.

---

### Post by suRoot on 2005-11-06
1.  You shouldn't need root to extract a file (assuming you downloaded it with your own account & not root)

2.  What does ```
tar --version
``` return?

3.  What does ```
which tar
``` return?

4.  What does ```
ls -l filename.tar.gz
``` return?

---

### Post by monomaniacpat on 2005-11-06
[QUOTE=suRoot]1.  You shouldn't need root to extract a file (assuming you downloaded it with your own account & not root)[/quote]

OK.

> 2.  What does ```
tar --version
``` return?

monomaniacpat@ubuntu:/home$ tar --version
tar (GNU tar) 1.15.1


> 3.  What does ```
which tar
``` return?

monomaniacpat@ubuntu:/home$ which tar
/bin/tar


> 4.  What does ```
ls -l filename.tar.gz
``` return?

monomaniacpat@ubuntu:/home$ ls -l atmelwlandriver-3.4.1.0.tar.bz2
ls: atmelwlandriver-3.4.1.0.tar.bz2: No such file or directory
monomaniacpat@ubuntu:/home$ ls -l Gorillaz
ls: Gorillaz: No such file or directory
monomaniacpat@ubuntu:/home$ ls -l BrigadeDamaged-1600.jpg
ls: BrigadeDamaged-1600.jpg: No such file or directory
monomaniacpat@ubuntu:/home$

^There it is with several files which I can see exist from my GUI - why do I always get 'no such file or directory'?! I've double and triple checked that it is spelt correctly...

---

### Post by monomaniacpat on 2005-11-06
OK, I admit it, it was all my fault - I wasn't putting in the full pathnames!

Now it can't find the command 'INSTALL', however...

monomaniacpat@ubuntu:~/Desktop/rtl8180-0.21$ sudo ./INSTALL
Password:
sudo: ./INSTALL: command not found

???

---

### Post by Leif on 2005-11-06
do this :

./configure
make
sudo make-install

---

### Post by aclaunch on 2005-11-06
What do you get with "ls -l ~/Desktop/rtl8180-0.21 " or where ever rtl8180 is located?  The message is saying there is no executable named "INSTALL"; remember Linux/Unix is case sensitive so make sure the file is not "install" or "Install". Next, if that is OK, check that the file is actually executable. The permission bit "x" needs to be present for which ever user you are (ie if you are owner then you must have execute privileges, if you are a regular user and only the owner has execute privileges then you cannot execute) and if not you need to "chmod +x" to change execute permissions. Lastly, if the file is being installed in a system directory as opposed to your home directory you need to install as "sudo" since a regular user does not have write privileges into a systed directory like /usr/lib.

Alan

---

### Post by monomaniacpat on 2005-11-06
Thanks for the last two responses, but I'm not sure exactly what I should be doing to change the file to executable? The penultimate one just doesn't make any sense to me - could you clarify Leif?

---

### Post by Zwack on 2005-11-06
Greetings,
   Your first tar problem existed because you were in a different directory...  It cou;dn't find the file... Which is what it was telling you.
    The second problem is that INSTALL is not a program.  Usually it is a text file with installation instructions in it.
    To test this open a shell, and change into the directory with INSTALL in it.

do an ls -l INSTALL and see what it looks like...

```
user@host:~/example/linpal-0.5-binary$ ls -la ./INSTALL 
-rw-r--r--  1 user group 27 2005-11-06 09:34 ./INSTALL

```

If the first part said -rwxr--r-- or something similar then it is executable.   The ten characters are a flag, and three sets of three.  The first set is for the User, the second set is the Group and the third for Other.  reach set of three normally consists of r for read, w for write and x for executable.  The flag is - for a file, l for a symbolic link and d for a directory.  There are other letters you might see but these are the most common ones.  

To find out whether the non executable INSTALL file is text you could try viewing it, but a better way to test is to use the file command...
```
user@host:~/example/linpal-0.5-binary$ file ./INSTALL
./INSTALL: ASCII text

```

In this case it is plain text.  You can read it with more (or less)...

use space to move down a screenful at a time.

This file should tell you how to install whatever it is.

I hope that this helps,

Z.

---

### Post by monomaniacpat on 2005-11-06
Thanks for that. I've started following the instructions, but now I can't run one of the processes. When I try to run 

```
monomaniacpat@ubuntu:~/Desktop/rtl8180-0.21$ sudo ./module_load
insmod: error inserting 'ieee80211_crypt-r8180.ko': -1 **Invalid module format**
insmod: error inserting 'ieee80211_crypt_wep-r8180.ko': -1 **Invalid module format**
insmod: error inserting 'ieee80211-r8180.ko': -1 **Invalid module format**
insmod: error inserting 'r8180.ko': -1 **Invalid module format**
```

What can I do to make it a VALID module format?

---

### Post by skylark on 2005-11-06
I'm not sure what's going on with your modules there but it's worth taking a step back and telling us exactly what problem you are trying to solve (maybe in a new thread). If you are trying to get your "realtek 8180" wifi card working you might search the forums for rtl8180 and/or r8180 and also check out "apt-cache search ndis" (type it in a terminal) for packages that might help. I'm afraid I won't be much help since I don't have any experience with wifi though. 

If you are 100% sure that you need to compile and install your own modules to get everything working then post some background info to help us (maybe a copy and paste of your terminal output coveroing the steps you went through when following the INSTALL file). It is possible that the modules you are trying to load are already in the default kernel.

---

### Post by nolan43 on 2005-11-07
Yeah, I've got the same problem with installing Automatix, no joy here. The same
tar: automatix.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors 

Now what, everything else is working, (software) well not the printer, but I don't need it yet

---

### Post by Gustav on 2005-11-08
To install a tarballed program the usual procedure is:

```
tar xvfz "progname"
cd "progname"
./configure
make
sudo make install
```

And to make sure you're not making typos, use tab-completion

---

