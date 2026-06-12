---
title: "[SOLVED] Turning off Compiz for Games Script"
date: 2008-07-28
forum: General Help
---

### Post by anotherdisciple on 2008-07-28
I'm looking to write a simple script for my friend. I want to have a shortcut open that script in the terminal and ask him... "What game would you like to play?". The script would then replace Compiz with Metacity.... run that game command... and then, once the game is closed... it will restart compiz and exit the terminal.

Here is what I have written...

```
#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
$GAME
compiz --replace
exit


```

I'm not at a linux computer... so I don't know if it will work. Does this seem right, or should something be changed?


PS- I'm brand new to BASH scripting

---

### Post by dexter.deepak on 2008-07-28
probably you would also like to run compiz in the background :
```
compiz --replace &
```

---

### Post by sdennie on 2008-07-28
You may also need to disown the compiz process from the parent shell:

```

compiz --replace &
disown

```

---

### Post by bthoward on 2008-07-28
There is another option... Give compiz-icon or compiztray a look.  You can either look for them in google or synaptic.  

They give you a quick simple icon in your tray that allows you to quickly switch between compiz and metacity.

---

### Post by anotherdisciple on 2008-07-28
I already installed fusion-icon for him... I'm just trying to take a click or two away from the process, but thanks for the suggestion.

I understand putting "&" after compiz --replace... so that it can actually exit after that command is run, but why might I need to disown? Just curious... I've never used that command.

---

### Post by sdennie on 2008-07-28
> **anotherdisciple said:**
> 
I understand putting "&" after compiz --replace... so that it can actually exit after that command is run, but why might I need to disown? Just curious... I've never used that command.

The best way to describe it is by example.  Start a terminal and type:

```

gcalctool &
exit

```

Notice the gnome calculator dies when the shell dies.  Now try:

```

gcalctool &
disown
exit

```

The gnome calculator stays even after the terminal is closed.  You can check the man page for bash to find out more information about disown.

---

### Post by anotherdisciple on 2008-07-28
hmmm that's strange... disown didn't work..

```
gcalctool &
disown
exit
```
just exited the terminal and closed the calculator... is there something not typed correctly?

---

### Post by sdennie on 2008-07-28
That's odd.  Are you using bash as your shell?  If I start a new terminal and type the two sets of statements above, it works as I'd expect.

---

### Post by anotherdisciple on 2008-07-28
Yes, I'm using BASH.... weird!? The second command keeps the terminal open just like before... it's like it ignores the exit command.

It all works as I suspected... asks "What game do you want to play?" switches to metacity, opens the program.... switches back to compiz once the game is closed... if I close the terminal it doesn't change the compiz command since I put & after compiz, but it doesn't close the terminal for me... how can I do this?

---

### Post by anotherdisciple on 2008-07-29
So... does anyone know how to make a BASH script close the terminal after it is finished? If I can figure that out I'll mark this thread as solved.

So far I have had no luck. If you type exit in the terminal... it will close the terminal.... if it's in that bash script... it doesn't seem to do anything.... I tried killall gnome-terminal... that didn't work either.... back to the drawing board...

---

### Post by anotherdisciple on 2008-07-29
Idea... yet again... I'm not at a linux computer, so I'll let you know if it works. Maybe I can make a shortcut to that file and put this for the command:

/home/path/to/file exit

I have no clue if you can do that... never tried it... but I'll let you know.

---

### Post by anotherdisciple on 2008-07-30
Nope, it immediately closes the terminal before the script has a chance to do anything.

---

### Post by dexter.deepak on 2008-07-30
this thread is a bit confusing for me.
i made a script1 :
```
#!/bin/bash
gcalctool &
disown
exit
```
on running it, i get a calculator and as soon as i close the terminal, it is also vanished.

script2 :
```
#!/bin/bash
gcalctool &
exit
```
 on run, when i close the terminal, the calculator keeps on running, as if it is simply independent of the parent program (the terminal which invoked it)

this is somewhat contradictory over what vor said, i guess.
and this is what anotherdisciple wants ?? (the script2)...isnt it ??

---

### Post by anotherdisciple on 2008-07-30
> **dexter.deepak said:**
> this thread is a bit confusing for me.
i made a script1 :
```
#!/bin/bash
gcalctool &
disown
exit
```
on running it, i get a calculator and as soon as i close the terminal, it is also vanished.

script2 :
```
#!/bin/bash
gcalctool &
exit
```
 on run, when i close the terminal, the calculator keeps on running, as if it is simply independent of the parent program (the terminal which invoked it)

this is somewhat contradictory over what vor said, i guess.
and this is what anotherdisciple wants ?? (the script2)...isnt it ??

Ummm... not exactly. I know that this is stupid, but I want the terminal to close itself after it switches back to compiz. Can that even be done? I know that it is REALLY REALLY simple to just have it start compiz and then I could close the terminal, but I'm just experimenting. It works fine without it closing itself... I just wanted to try to automate it just a little bit more.

On a side note... ever since I ran nexuiz with this script... some of the players are invisible! Just a bunch of guns floating around shooting me! haha! The script seems like it wouldn't do anything to effect that. I just deleted the old .nexuiz folder and it worked just fine... then I ran the game with that script again.... and now they are invisible again! haha... how weird?

---

### Post by overdrank on 2008-07-30
moved :)

---

### Post by soxs on 2008-07-30
> **anotherdisciple said:**
> Ummm... not exactly. I know that this is stupid, but I want the terminal to close itself after it switches back to compiz. Can that even be done? I know that it is REALLY REALLY simple to just have it start compiz and then I could close the terminal, but I'm just experimenting. It works fine without it closing itself... I just wanted to try to automate it just a little bit more.
simply use ```
exit
```

> **anotherdisciple said:**
> 
On a side note... ever since I ran nexuiz with this script... some of the players are invisible! Just a bunch of guns floating around shooting me! haha! The script seems like it wouldn't do anything to effect that. I just deleted the old .nexuiz folder and it worked just fine... then I ran the game with that script again.... and now they are invisible again! haha... how weird?
You may have to wait till metacity got started, so you will have to create a, I would say, at least 3s sleep:
use: ```
sleep 3
```

---

### Post by anotherdisciple on 2008-07-30
The sleep thing is a good idea... I'll do that... I think it may just be a nexuiz bug though... not sure yet. So here is what I have so far....

```
#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
sleep 3
$GAME
compiz --replace &
exit
```


Notice... the last command is exit... yet it doesn't close the terminal.... can someone try this script for me and see if you get the same results? I even tried writing a script that just says...

```
#!/bin/bash
exit
```

...it did nothing!

---

### Post by dexter.deepak on 2008-07-30
got your problem dude..you need to get the ppid of the terminal, and then kill it.

```

#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
sleep 3
$GAME
compiz --replace &
exit
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
kill $a

```
i havent tested it yet, please report back if it doesnt work

---

### Post by anotherdisciple on 2008-07-30
So, I tried...
```
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
kill $a
```
and it didn't work... I even ran it in a script by itself... and I tried killall instead of kill. But that was pretty clever... I wouldn't have thought about the id.

However I tried running a script that just slept for 3 second and did a killall gnome-terminal... it worked. Here is the final script if anyone wants to use it...

```
#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
sleep 3
$GAME
compiz --replace &
sleep 3
killall gnome-terminal
```

---

### Post by soxs on 2008-07-31
this worked pasting in terminal and running it as a script(commented parts out, to speed up testing):
```

#!/bin/bash

#read -p "What game would you like to play?" GAME
#metacity --replace &
#sleep 3
#$GAME
#compiz --replace &
sleep 3
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
#echo $a
kill -9 $a
```

---

### Post by dexter.deepak on 2008-07-31
> **anotherdisciple said:**
> So, I tried...
```
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
kill $a
```
and it didn't work... I even ran it in a script by itself... and I tried killall instead of kill. But that was pretty clever... I wouldn't have thought about the id.

However I tried running a script that just slept for 3 second and did a killall gnome-terminal... it worked. Here is the final script if anyone wants to use it...

```
#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
sleep 3
$GAME
compiz --replace &
sleep 3
killall gnome-terminal
```


your "solution" script has a BIG flaw, when you issue :
```
killall gnome-terminal
```
it will kill ALL the gnome-terminals you are currently running...and i dont think you would want this.
thats why i used ppid, so that only the present terminal is closed.
to make things more complex, i have to use the pppid now, ie, the pid of the command's (to find the pid) parent 's (this shell script) parent (the terminal).
so here is the final code :
```
#!/bin/bash
read -p "What game would you like to play?" GAME
metacity --replace &
$GAME
compiz --replace &
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
b=`ps -fp $a | tail -1| awk '{print $3}'`
kill $b
exit

```

one more thing about your script...the exit status of your script is 1 - and this technically means that your script isnt yet perfect.
i am also keen to know what purpose does 'sleep' solve for you ??

---

### Post by soxs on 2008-07-31
> **dexter.deepak said:**
> 

one more thing about your script...the exit status of your script is 1 - and this technically means that your script isnt yet perfect.
i am also keen to know what purpose does 'sleep' solve for you ??

who cares? as long this script will stay a single peace of "art", it doesn't matter at all. (At least I think so)
Edit: I have RadeonHD 3870 factory OC

---

### Post by dexter.deepak on 2008-07-31
> **soxs said:**
> who cares? as long this script will stay a single peace of "art", it doesn't matter at all. (At least I think so)


it was a mere suggestion, if he wants to reuse this script in a bigger application someday ;)

---

### Post by soxs on 2008-07-31
> **dexter.deepak said:**
> it was a mere suggestion, if he wants to reuse this script in a bigger application someday ;)

well, in that case, I suggest him to use python or C/C++, whereas he could implement the functions in the peding language and not nasty shellscript^^

---

### Post by anotherdisciple on 2008-07-31
That's my next goal... learn python.... I'll try out that last code tonight.

---

### Post by anotherdisciple on 2008-07-31
> **dexter.deepak said:**
> your "solution" script has a BIG flaw, when you issue :
```
killall gnome-terminal
```
it will kill ALL the gnome-terminals you are currently running...and i dont think you would want this.
thats why i used ppid, so that only the present terminal is closed.
to make things more complex, i have to use the pppid now, ie, the pid of the command's (to find the pid) parent 's (this shell script) parent (the terminal).
so here is the final code :
```
#!/bin/bash
read -p "What game would you like to play?" GAME
metacity --replace &
$GAME
compiz --replace &
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
b=`ps -fp $a | tail -1| awk '{print $3}'`
kill $b
exit

```

one more thing about your script...the exit status of your script is 1 - and this technically means that your script isnt yet perfect.
i am also keen to know what purpose does 'sleep' solve for you ??

Well.. I'm not sure that killing all of the gnome-terminals would be a problem in this case... I never have more than one terminal open anyways.... plus this script is being used when I am running a game... so I wouldn't be doing anything in the terminal anyways.

But for the sake of learning... I am going to try it some other ways. Can you explain to me what $a and $b do exactly? I know it has something to do with finding the pppid... that's about all I know.

What does an exit status of 1 mean?... and how do you know that it has that?

---

### Post by dexter.deepak on 2008-07-31
> **anotherdisciple said:**
> Well.. I'm not sure that killing all of the gnome-terminals would be a problem in this case... I never have more than one terminal open anyways.... plus this script is being used when I am running a game... so I wouldn't be doing anything in the terminal anyways.

..and i thought you were doing this all for your friend :p
> **anotherdisciple said:**
> What does an exit status of 1 mean?
i am sorry for this..i actually tested your script in geany, and since there was no gnome-terminal there, i got an  exit 1 status.
> **anotherdisciple said:**
> Can you explain to me what $a and $b do exactly?
$a gets the ppid of the command to calculate the ppid ...in our case the parent of the command (ps -fp...) is the shell-script itself.
$b gets the parent of the shell-script..that is the terminal which invoked it.

---

### Post by anotherdisciple on 2008-07-31
HAHA! Actually, I'm not much of a gamer... and my friend is not much of a terminal user... so it works both ways... I will probably use it since I spent all this time trying to figure it out, but it's mostly to make it easier on him... since he isn't very familiar with the command line.'

About the $a and $b stuff... wow... I'm going to whip out my "Linux in a nutshell" and try to see how you came to that command... haha... it's a long and complicated one... I just want to know what it is doing to find that number... awk sounds familiar... not sure where I've used it before... hmmm... I'll get back to you about all this...

---

### Post by anotherdisciple on 2008-07-31
ps= Report on active processes
-fr= Forest, Running Processes
$$= I have no clue (print all of the information?)
tail -1= print only the last line
awk = text based data
print $3- print the third section of this data

So, it says:

Give me a full listing of all the running processes, filter it to only display the last line of those processes, and print only the data in the third section... which represents the id... but this is a bash script... and we want to close the terminal running that bash script... so we do it all over again... but sorting out what id is the parent of that particular bash script.

Am I close?

---

### Post by anotherdisciple on 2008-07-31
I tried this:

```
#!/bin/bash
read -p "What game would you like to play?" GAME
metacity --replace &
sleep 3
$GAME
compiz --replace &
sleep 3
a=`ps -fp $$ |tail -1 | awk '{print $3}'`
b=`ps -fp $a | tail -1| awk '{print $3}'`
kill $b

```

... and yes, the sleep 3 after compiz --replace & is necessary. Without it... the terminal closes before it gets a chance to switch to compiz.... weird eh?

The good news is that your script works... the bad news.... well.. it does the same thing as killall gnome-terminal! I opened a few gnome-terminals just to test it.... it killed all of them... not just the one I ran the script in. Any more ideas on how to sort it even further?

---

### Post by dexter.deepak on 2008-08-01
> **anotherdisciple said:**
> 
... and yes, the sleep 3 after compiz --replace & is necessary. Without it... the terminal closes before it gets a chance to switch to compiz.... weird eh?

in my system, i am not facing this problem ; maybe mine is a bit faster.

> **anotherdisciple said:**
> 
The good news is that your script works... the bad news.... well.. it does the same thing as killall gnome-terminal! I opened a few gnome-terminals just to test it.... it killed all of them... not just the one I ran the script in. Any more ideas on how to sort it even further?

i already tested this script before testing, and i retested now..it works man ; only the parent terminal is closed, not the others...theres no logic for closing others.

and yes, $$ means the pid of the current process.

---

### Post by anotherdisciple on 2008-08-01
hmmm... you opened more than one terminal? Maybe it has something to do with how the gnome-terminal works. When I open two gnome-terminals and check my processes.... it has created 2 new bash processes and 1 terminal process.... so when we are filtering out the terminal... it closes all of them... because they both run under the same id. Even if I close only one terminal id... it closes all gnome-terminals.

---

### Post by soxs on 2008-08-02
> **anotherdisciple said:**
> hmmm... you opened more than one terminal? Maybe it has something to do with how the gnome-terminal works. When I open two gnome-terminals and check my processes.... it has created 2 new bash processes and 1 terminal process.... so when we are filtering out the terminal... it closes all of them... because they both run under the same id. Even if I close only one terminal id... it closes all gnome-terminals.

Did anybody try to kill one bash process?

---

### Post by senectus on 2008-09-04
Why does this have [SOLVED] on it.. I can't see a completd solution here yet.. ?


It's a great idea... I'd love to try it out...

---

### Post by anotherdisciple on 2008-09-04
Well, It was solved in my mind. I was fine with it closing all of the gnome-terminals that were open.

Here is the final script that closes all the terminals...

```
#!/bin/bash

read -p "What game would you like to play?" GAME
metacity --replace &
sleep 1
$GAME
compiz --replace &
sleep 2
killall gnome-terminal
```

If you don't want to run a terminal and just want to have a GUI change it to use zenity for the gui...

```
#!/bin/bash
GAME=$(zenity --entry --title "Game Runner" --text "What game would you like to play?)
metacity --replace &
sleep 1
$GAME
compiz --replace &
sleep 2
exit 1
```

Let me know if any of that doesn't work for you.

---

### Post by esteel on 2008-09-10
I do not use compiz, just normal metacity but i use this script for playing games (just named it 'game' :) )

```
#! /bin/sh

[ -x "`which aoss`" ] && aoss=aoss
if [ -x "`which gnome-screensaver-command`" ]; then
	gnome-screensaver-command -i &
	inhibit=$?
fi

loadkeys -c -u -s us
setxkbmap -symbols "pc(pc105)+us"
synclient touchpadoff=1

$aoss "$@"

xgamma -gamma 1
synclient touchpadoff=0
setxkbmap -symbols "pc(pc105)+us(intl)+group(alts_toggle)"
loadkeys -c -u -s us-intl.iso15

[ -n "$inhibit" ] && kill $inhibit
```
Seems some games have problems with non-us keyboard layouts or deadkeys.

---

### Post by kommizzarr on 2009-03-17
Nobody figured this out ?

---

