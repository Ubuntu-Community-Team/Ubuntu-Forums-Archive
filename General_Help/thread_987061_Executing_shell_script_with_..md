---
title: "Executing shell script with ./"
date: 2008-11-19
forum: General Help
---

### Post by gmh04 on 2008-11-19
Hi

I have just upgrade to ibex and I can't execute shell scripts using ./.  E.g

```

./my_script.sh

```

hangs and uses 100% CPU

whereas

```

sh my_script.sh

```

works

This happen whether the declaration of the script is #/bin/bash or #/bin/sh

Any thoughts?

Cheers

---

### Post by rampageoberon on 2008-11-19
Shoudln't the declaration be #!/bin/bash or #!/bin/sh

Or have you made a typo in the post?

---

### Post by hyper_ch on 2008-11-19
did you make the script executable?

---

### Post by ByteJuggler on 2008-11-19
To reiterate what others have posted:
1) The first line must start with #!  
(aka "Hash-bang")
2) The script must be marked executable to use ./script

If you're still having problems after checking these 2 things, can you try posting a small script that exhibits the behaviour and post it verbatim (as an attachment or quoted text) here.

---

### Post by gmh04 on 2008-11-19
Oh to my shame I missed out the !

The thing is these scripts have been around a bit, which means earlier version of bash were allowing me to get away with it.

Thanks to all,

---

### Post by chupachups on 2009-02-06
hi
this thread is similar to something I am encountering

whilst diagnosing a hanging script, I boiled it down to the script not containing a #! at the top

To reproduce the error, I have a simple script that contains just

echo "hallo"

The file has execute permission. If I run it as

./thingy

It hangs

But if I run it as

bash ./thingy

It works

My version of bash is 3.2.39

I have a separate linux machine not running ubuntu, and its bash (version 3.2.25), does not exhibit the hanging problem

Is this a bash improvement ? or have I messed up my ubuntu setup in some way ?

BTW the original script I had problems with is dbhome, an oracle corporation supplied script, which does not specify #!

---

### Post by lensman3 on 2009-02-06
Change the #!/bin/bash line to:

#!/bin/bash -x    (execute-dump lines as the shell executes them to stdout)

or

#!/bin/bash -v     (verbose-dump lines has the shell reads them to stdout)

or 

#!/bin/bash -vx  (or do both at the same time).


When the script hangs you should see which line.

Hope this helps.

---

### Post by chupachups on 2009-02-06
> **chupachups said:**
> hi
this thread is similar to something I am encountering

whilst diagnosing a hanging script, I boiled it down to the script not containing a #! at the top

To reproduce the error, I have a simple script that contains just

echo "hallo"

The file has execute permission. If I run it as

./thingy

It hangs

But if I run it as

bash ./thingy

It works

My version of bash is 3.2.39

I have a separate linux machine not running ubuntu, and its bash (version 3.2.25), does not exhibit the hanging problem

Is this a bash improvement ? or have I messed up my ubuntu setup in some way ?

BTW the original script I had problems with is dbhome, an oracle corporation supplied script, which does not specify #!

I've discovered that this seems to be a problem with my "putty" access from windows xp to ubuntu

Running the test script from an ubuntu terminal behaves correctly, but using the same user and a putty session from windows, just hangs

The ubuntu system is a clean install with all updates + openssh-server

Unless someone has a quick answer, I may post this question in a more appropriate place

---

### Post by ByteJuggler on 2009-02-07
> **chupachups said:**
> I've discovered that this seems to be a problem with my "putty" access from windows xp to ubuntu

Running the test script from an ubuntu terminal behaves correctly, but using the same user and a putty session from windows, just hangs

The ubuntu system is a clean install with all updates + openssh-server

Unless someone has a quick answer, I may post this question in a more appropriate place

I think to understand this you have to consider what actually happens in each case of execution.  When you execute a file with

```
./file
```

... the system initially doesn't know what type of file it is.  Now, it should be obvious that that the way you (or the system) load and execute a binary executable differently from, say a .Net compiler bytecode file, or a Java VMN compiled file, or a PERL script, or a Python script, or a BASH script.  

So what you must understand is this:  The system must first decide what to do, not knowing what file type it is up front, it has to effectively identify the type of file it's been asked to execute, in order to be able to do the right thing.  Now, Windows solves this problem through (kludgy) file extensions.   Unix by contrast places no limits on filenames/extensions, and instead uses "magic numbers" to help identify file types, and consequently what to do with them when executing them.  The primary magic number used here is the first 2 bytes of a file.  By convention, the bytes corresponding to "#!" is taken to mean "script", and further by convention, the bytes following the "#!" indicates the command or interpreter to use for the remainder of the file (which is usually a text file.)  

Now consider what will happen when you execute a shell script without the correct magic number.  The system will try to identify the file type based on magic number.  It should be obvious that in principle the result will be  unpredictable, because the magic bytes will effectively be arbitrary, based on the contents of the script.  The system may for example try to load the file as a conventional piece of machine code (for example) which obviously will fail horribly.  So, the #! is absolutely essential when you expect the system to automatically do the right thing for an executable script executed with "./script"

By contrast, running something as:

```
bash ./script 
```

or 

```
bash script
```

... you're effectively removing the need for the #!, because the system in that case runs your specified command "bash", which the system identifies as a compiled binary, loads and starts, and then gives a parameter "./script" or "script".  Since bash expects its input to be a valid bash script, things work as expected, and the script is run.  Aside, for scripts with "#!" on the first line, this still works as "#" lines are considered to be comments and are ignored by bash itself.  

So, bottom line, the behaviour is basically expected.  Just use the right invocation and if you want the script to be automatically executable then use the right header.

Aside: You can use the "file" command to see what Linux identifies a file as based on magic numbers, e.g.:

```

file afile

```
Try using the "file" command on a few of your scripts and other system commands and see what it outputs.  Also see the man pages on "magic" and "file".

---

### Post by chupachups on 2009-02-07
> **ByteJuggler said:**
> I think to understand this you have to consider what actually happens in each case of execution.  When you execute a file with

```
./file
```

... the system initially doesn't know what type of file it is.  Now, it should be obvious that that the way you (or the system) load and execute a binary executable differently from, say a .Net compiler bytecode file, or a Java VMN compiled file, or a PERL script, or a Python script, or a BASH script.  

So what you must understand is this:  The system must first decide what to do, not knowing what file type it is up front, it has to effectively identify the type of file it's been asked to execute, in order to be able to do the right thing.  Now, Windows solves this problem through (kludgy) file extensions.   Unix by contrast places no limits on filenames/extensions, and instead uses "magic numbers" to help identify file types, and consequently what to do with them when executing them.  The primary magic number used here is the first 2 bytes of a file.  By convention, the bytes corresponding to "#!" is taken to mean "script", and further by convention, the bytes following the "#!" indicates the command or interpreter to use for the remainder of the file (which is usually a text file.)  

Now consider what will happen when you execute a shell script without the correct magic number.  The system will try to identify the file type based on magic number.  It should be obvious that in principle the result will be  unpredictable, because the magic bytes will effectively be arbitrary, based on the contents of the script.  The system may for example try to load the file as a conventional piece of machine code (for example) which obviously will fail horribly.  So, the #! is absolutely essential when you expect the system to automatically do the right thing for an executable script executed with "./script"

By contrast, running something as:

```
bash ./script 
```

or 

```
bash script
```

... you're effectively removing the need for the #!, because the system in that case runs your specified command "bash", which the system identifies as a compiled binary, loads and starts, and then gives a parameter "./script" or "script".  Since bash expects its input to be a valid bash script, things work as expected, and the script is run.  Aside, for scripts with "#!" on the first line, this still works as "#" lines are considered to be comments and are ignored by bash itself.  

So, bottom line, the behaviour is basically expected.  Just use the right invocation and if you want the script to be automatically executable then use the right header.

Aside: You can use the "file" command to see what Linux identifies a file as based on magic numbers, e.g.:

```

file afile

```
Try using the "file" command on a few of your scripts and other system commands and see what it outputs.  Also see the man pages on "magic" and "file".

thanks for this, it was already in the back of my mind

BUT why does the system behave correctly when I invoke the shell script from terminal ?

BTW from both terminal and ssh, "file" correctly reports as ASCII text

---

### Post by ByteJuggler on 2009-02-08
> **chupachups said:**
> thanks for this, it was already in the back of my mind

BUT why does the system behave correctly when I invoke the shell script from terminal ?

BTW from both terminal and ssh, "file" correctly reports as ASCII text

Sorry if I'm asking for the obvious (or what what you've given already), but, invoke how exactly?  

It shouldn't matter whether you use "terminal" or "ssh" (or putty or...), except for each of these possibly running your shell in a different mode/configuration (e.g. interactive vs. non-interactive, interactive shells [edit: sorry, I should've said "login shells", not "interactive shells"] typically also have both .profile/.bash_profile and .bashrc run whereas non-login only has .bashrc run.  All of these things can contribute to different behaviour.)

The bottom line is that there are heuristics being applied to decide what to do in an underspecified situation (such as "./file" when file has no clear intrinsic filetype based on magic bytes), and so the behaviour may potentially vary and may end up wrong at apparently odd occassions.  The heuristics used by "file" is also probably not identical to that used by the the shell or system to decide what to do with a given executable file invocation.  You'd have to look into the source of particular versions of actual shell executables (and shell configuration e.g. .profile abd/or rc scripts being run or not run) and kernel being used, to understand why a particular route/method of invocation behaves the way it does.  As an aside, identifying a file as "ASCII text" does not help in a context where' you're expected to execute the file, since of course ASCII text by itself is not executable.

---

### Post by chupachups on 2009-02-08
> **ByteJuggler said:**
> Sorry if I'm asking for the obvious (or what what you've given already), but, invoke how exactly?  

It shouldn't matter whether you use "terminal" or "ssh" (or putty or...), except for each of these possibly running your shell in a different mode/configuration (e.g. interactive vs. non-interactive, interactive shells typically also have both .profile/.bash_profile and .bashrc run whereas non-interactive only has .bashrc run.  All of these things can contribute to different behaviour.)

The bottom line is that there are heuristics being applied to decide what to do in an underspecified situation (such as "./file" when file has no clear intrinsic filetype based on magic bytes), and so the behaviour may potentially vary and may end up wrong at apparently odd occassions.  The heuristics used by "file" is also probably not identical to that used by the the shell or system to decide what to do with a given executable file invocation.  You'd have to look into the source of particular versions of actual shell executables (and shell configuration e.g. .profile abd/or rc scripts being run or not run) and kernel being used, to understand why a particular route/method of invocation behaves the way it does.  As an aside, identifying a file as "ASCII text" does not help in a context where' you're expected to execute the file, since of course ASCII text by itself is not executable.

to reproduce, try the following

ssh localhost
echo echo hello! > hello
chmod +x hello
./hello

then run the same command from terminal only without using ssh

---

### Post by ByteJuggler on 2009-02-08
> **chupachups said:**
> to reproduce, try the following

ssh localhost
echo echo hello! > hello
chmod +x hello
./hello

then run the same command from terminal only without using ssh

On my one system, both methods does the same (and happens to work.)

---

### Post by chupachups on 2009-02-08
> **ByteJuggler said:**
> On my one system, both methods does the same (and happens to work.)

think this has been identified as a bug occuring only in intrepid ibex are you only using hardy ?

---

### Post by XanTrax on 2009-02-08
> **chupachups said:**
> to reproduce, try the following

ssh localhost
echo echo hello! > hello
chmod +x hello
./hello

then run the same command from terminal only without using ssh

You see here?

```

echo echo hello! > hello
...
./hello

```

You're using ./ to execute it without identifying it is a bash script. 

Either way, you're missing the #!/bin/bash in your example.  ByteJuggler just got done explaining in whole why your script is probably hanging.  The example you just gave us to "reproduce" shows us that you're not specifying anything like bash or sh.

---

### Post by ByteJuggler on 2009-02-08
> **chupachups said:**
> think this has been identified as a bug occuring only in intrepid ibex are you only using hardy ?

The test was on Hardy yes.  On Intrepid I can reproduce your problem.  

However I've found it's got nothing to do with ssh as such, but rather with whether or not the shell (bash) was started as a login shell or not (which is actually somewhat what I've suggested might be the case in a previous post.)  

To see this, try:
```

bash -i
./hello
```

..., non-login (although interactive) shell, which works.
```

bash -l
./hello
```

..., login (also interactive) shell, which doesn't work.  

So clearly, bash's heuristics for deciding how to start a program differs slightly in the version used in Intrepid based on whether it's a login or non-login shell, which smells buggy (even though in principle it would not be incorrect if it consistently crashed/refused to run in all cases for scripts such as the above -- the fact that bash makes a guess when not told what type of file it's faced with is really a courtesy, but yes, given that it worked before, one might validly expect it to continue working, and particularly given that it does work if the shell is started as a non-login shell.)

...

For what it's worth I've just downloaded and compiled the latest bash 4.0 source from GNU's website and it appears to not have this behaviour (e.g. both "bash -i" and "bash -l" manages to correctly identify and run the test script, so it would appear the bug's been fixed again somewhere along the line.  [Edit: Perhaps I'll check the latest 3.x version of bash as well.]  

Notwithstading all the above, I suggest it's better to simply properly identify your scripts as bash scripts with the proper #! header, which avoids the problem in all cases.

[Edit2: The lastest 3.x version bash, 3.2.48, from GNU's website, still has the hanging behaviour on Intrepid, as I've just verified after compiling from scratch.]

[Edit3: OK this is strange.  I've just checked, the version of bash on Intrepid and Hardy is the same.  3.2.39(1).  Which means the difference in behaviour is not due to bash itself, at least not between Intrepid and Hardy default shells, and must be due to some circumstantial thing that affects bash's behaviour.  And yet, bash 4.x on Intrepid works fine.  So, hence I'm currently at a bit of a loss as to where this issue is coming from.]

---

### Post by XanTrax on 2009-02-08
Interesting...I tried this too:

```

[17:16:23][kozler@kozler-ubuntu:~]$ ssh localhost -l kozler
kozler@localhost's password: 
Linux kozler-ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sun Feb  8 17:15:28 2009 from localhost
[17:16:41][kozler@kozler-ubuntu:~]$ echo "hello world" > hello 
[17:16:48][kozler@kozler-ubuntu:~]$ ./hello 
^C^C^C^C^C^C^C^C^C^C^CKilled
[17:17:29][kozler@kozler-ubuntu:~]$ 

```

The ^C is where I was trying ctrl+c and then it finally got killed when I killed the sshd process that my ssh connection was using.

maybe a bug report is in order since a lot of people are using the standard bash installation?

---

### Post by ByteJuggler on 2009-02-08
> **XanTrax said:**
> Interesting...I tried this too:

```

[17:16:23][kozler@kozler-ubuntu:~]$ ssh localhost -l kozler
kozler@localhost's password: 
Linux kozler-ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sun Feb  8 17:15:28 2009 from localhost
[17:16:41][kozler@kozler-ubuntu:~]$ echo "hello world" > hello 
[17:16:48][kozler@kozler-ubuntu:~]$ ./hello 
^C^C^C^C^C^C^C^C^C^C^CKilled
[17:17:29][kozler@kozler-ubuntu:~]$ 

```

The ^C is where I was trying ctrl+c and then it finally got killed when I killed the sshd process that my ssh connection was using.

maybe a bug report is in order since a lot of people are using the standard bash installation?

Bug report -- yes, perhaps, although it's not really clear who's problem it is, given that Intrepid and Hardy uses the same version of bash but behaves differently, but bash 4.0 works for me on Intrepid.   Aside: Above, instead of killing the sshd, you can do a "pstree -p" and only kill the instantiated hanging bash if you want, without killing off your actual interactive shell.  Here I've opened a terminal, and then entered "bash -l".  Then I tried to run the "hello".   You'll see a pstree line that says something like 

```
gnome-terminal(7254)&#9472;&#9516;&#9472;bash(7257)&#9472;&#9472;&#9472;bash(7275)&#9472;&#9472;&#9472;bash(7297)
```

The final bash on that branch is the hanging one, instantiated to run the "hello" script.  It's parent is the "bash -l" I ran.  Its parent is the shell started by the gnome-terminal.

---

### Post by chupachups on 2009-02-08
The plot thickens, doesn't it ?

FYI, the script in question that doesn't have #! isn't one of mine, its an oracle corporation script as part of oracle 11g (oraenv/dbhome).

If is was just one of mine, I would change it and stand corrected (in fact I will just clone the script and fix it on my system), but as oraenv runs successfully on AIX and a multitude of other UNIX systems, and indeed this works on hardy too, I'd like to try at least understand why intrepid is behaving like this, all part of the learning experience

---

### Post by chupachups on 2009-02-08
thanks guys for bearing with me

---

### Post by capscrew on 2009-02-08
I'm curious, maybe the shell is not reacting the way you think it is or is not really bash.  Using Solaris I got in the habit of using this:```
#! /bin/bash
```

Note the space between the shebang and the path.

This convention works on my bash scripts created in my current Ubuntu installation.

---

### Post by ByteJuggler on 2009-02-09
> **chupachups said:**
> The plot thickens, doesn't it ?

FYI, the script in question that doesn't have #! isn't one of mine, its an oracle corporation script as part of oracle 11g (oraenv/dbhome).

If is was just one of mine, I would change it and stand corrected (in fact I will just clone the script and fix it on my system), but as oraenv runs successfully on AIX and a multitude of other UNIX systems, and indeed this works on hardy too, I'd like to try at least understand why intrepid is behaving like this, all part of the learning experience

No problem and I agree, however I would nevertheless be of the opinion Oracle should ideally also fix their script (i.e. they're arguably wrong not having a header in it, as far as I'm concerned, if their intent is for you to be able to run it without specifying the interpreter explicitly), as the fact remains, a script without a header should be run explicitly as "sh script" or "bash script" or "tsch script", since otherwise the system has to guess/assume.  

Many years ago I had to help troubleshoot some scripts written by some company (IIRC) in the context of Physics research.  This was as I recall also on a Sun Solaris box.  It was most perplexing as things sometimes seemed to work and sometimes not, depending on how it was run.  We eventually traced it as I remember to the script invocation headers.  The scripts were in fact written in "tcsh" but in some scripts specified simply "/bin/sh" in the headers or somesuch.  This caused scripts to be sometimes run with the wrong interpreter and consequently caused breakage on occassions.  Eventually I/we fixed it by correcting the script headers. 

So anyway, notwithstanding Intrepid's behaviour (which should be looked into I agree) I would suggest this should probably also be reported to Oracle as a bug/omission in their scripts.

---

### Post by mixmaster on 2009-02-09
If the script is intended to be run via a specified interpreter then it should not be flagged as executable.  That way things can't go wrong.

I've also seen some shops where script.sh was used to designate a (sub-) script intended to be invoked with an explicit interpreter from a top-level executable without an extension.  Maybe oracle are doing something like that.

Is the script one explicitly intended for user invocation or is it something you have pulled out of a working oracle setup because it seems to do what you want?  I'm not criticizing you for doing that, if it is what happened, 'cause I do it myself but you can occasionally come unstuck.

---

### Post by ByteJuggler on 2009-02-09
> **mixmaster said:**
> If the script is intended to be run via a specified interpreter then it should not be flagged as executable.  That way things can't go wrong.

Sorry but no. What's the point of having the "#!/bin/interpreter" convention then?  That's precisely the point of that convention -- to make it possible to write executable files as scripts (or have scripts operate like binary executables), without having to rely on users telling the system what interpreter to use.

---

### Post by chupachups on 2009-02-09
> **mixmaster said:**
> If the script is intended to be run via a specified interpreter then it should not be flagged as executable.  That way things can't go wrong.

I've also seen some shops where script.sh was used to designate a (sub-) script intended to be invoked with an explicit interpreter from a top-level executable without an extension.  Maybe oracle are doing something like that.

Is the script one explicitly intended for user invocation or is it something you have pulled out of a working oracle setup because it seems to do what you want?  I'm not criticizing you for doing that, if it is what happened, 'cause I do it myself but you can occasionally come unstuck.

the original problem was a user invoked script (oraenv) which calls a secondary script (dbhome), its the secondary script that doesn't have the #!, but causes any oraenv invocation to hang on my intrepid system, which is a bummer considering oraenv is supposed to be placed in .profile or .bashrc

---

### Post by chupachups on 2009-02-09
> **mixmaster said:**
> Maybe oracle are doing something like that.

ubuntu is not an oracle supported env, I suspect there are two hopes for getting oracle to fix this a) bob hope b) no hope

BTW bob hope is dead

---

### Post by mb_webguy on 2009-02-09
> **chupachups said:**
> ubuntu is not an oracle supported env, I suspect there are two hopes for getting oracle to fix this a) bob hope b) no hope

BTW bob hope is dead

Ubuntu is Linux.  Oracle supports Linux.  What therefore makes you think that Ubuntu isn't supported by Oracle?

---

