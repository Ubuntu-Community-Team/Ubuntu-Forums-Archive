---
title: "ANSI control in console terminal question"
date: 2008-11-14
forum: General Help
---

### Post by Krupski on 2008-11-14
Hi all,

I have written a small BASH script to run a microcontroller assembler program and display "success" or "failure" based on the exit code of the assembler. Works fine, no problem.

However, in playing with the script, I discovered that certain ANSI sequences don't seem to do anything. In particular, "Italic", "Blink" and "Fastblink" seem to do nothing.

I tried different fonts in console (i.e. Truetype fonts that HAVE italic versions), I tried setting the TERM variable to "ansi", "vt100" and "xterm" and nothing made a difference (although the NANO editor worked differently when TERM was set to "ansi" - but that's irrelevant).

Any ideas why all the other codes work, but "Italic", "Blink" and "Fastblink" do not?

By the way, here's the script I am referring to... it may be useful as a "skeleton" for other projects... feel free to use it.

```

#!/bin/bash

#####################################################
# script to run the mgtek 68hc11 assembler
# url: http://www.mgtek.com/miniide/
# NOTE: escape is in OCTAL! (\033 = 27 = 0x1b)
#####################################################

# ANSI control code functions

################################
# control codes
################################

function RESET     { /bin/echo -en "\033[0m"; }
function BOLD      { /bin/echo -en "\033[1m"; }
function FAINT     { /bin/echo -en "\033[2m"; }
[color=red]function ITALIC    { /bin/echo -en "\033[3m"; } # <- doesn't work[/color]
function UNDERLINE { /bin/echo -en "\033[4m"; }
[color=red]function BLINK     { /bin/echo -en "\033[5m"; } # <- doesn't work[/color]
[color=red]function FASTBLINK { /bin/echo -en "\033[6m"; } # <- doesn't work[/color]
function REVERSE   { /bin/echo -en "\033[7m"; }
function CONCEALED { /bin/echo -en "\033[8m"; }
function STRIKEOUT { /bin/echo -en "\033[9m"; }


################################
# background color codes
################################

function BLACKFG   { /bin/echo -en "\033[30m"; }
function REDFG     { /bin/echo -en "\033[31m"; }
function GREENFG   { /bin/echo -en "\033[32m"; }
function YELLOWFG  { /bin/echo -en "\033[33m"; }
function BLUEFG    { /bin/echo -en "\033[34m"; }
function MAGENTAFG { /bin/echo -en "\033[35m"; }
function CYANFG    { /bin/echo -en "\033[36m"; }
function WHITEFG   { /bin/echo -en "\033[37m"; }



################################
# foreground color codes
################################

function BLACKBG   { /bin/echo -en "\033[40m"; }
function REDBG     { /bin/echo -en "\033[41m"; }
function GREENBG   { /bin/echo -en "\033[42m"; }
function YELLOWBG  { /bin/echo -en "\033[43m"; }
function BLUEBG    { /bin/echo -en "\033[44m"; }
function MAGENTABG { /bin/echo -en "\033[45m"; }
function CYANBG    { /bin/echo -en "\033[46m"; }
function WHITEBG   { /bin/echo -en "\033[47m"; }



#############################################
# bash functions
#############################################

# green for success
function green { BOLD; WHITEFG; GREENBG; }      

# red for failure
function red { BOLD; WHITEFG; REDBG; }      

# reset
function reset { RESET; }

# success sound
function success
{
  /usr/bin/beep -f 880 -l 100;
  /usr/bin/beep -f 770 -l 100;
  /usr/bin/beep -f 660 -l 100;
  /usr/bin/beep -f 550 -l 100;
  /usr/bin/beep -f 440 -l 100;
  /usr/bin/beep -f 330 -l 100;
  /usr/bin/beep -f 220 -l 100;
}

# failure sound
function fail
{
  /usr/bin/beep -f 440 -l 500;
  /usr/bin/beep -f 220 -l 500;
}


###############################
# assemble the source code
###############################

/bin/asm11 -lc -ls -stat -W4 "$@"

if [ "${?}" -eq "0" ]; then
{
    success /* success sound */

  /bin/echo

    green
  /bin/echo -n "+---------------------+"
    reset

  /bin/echo

    green
  /bin/echo -n "| Assembly succeeded! |"
    reset

  /bin/echo

    green
  /bin/echo -n "+---------------------+"
    reset

  /bin/echo
  /bin/echo
}

else
{
    fail /* fail sound */

  /bin/echo

    red
  /bin/echo -n "+---------------------+"
    reset

  /bin/echo

    red
  /bin/echo -n "| Assembly FAILED!!!! |"
    reset

  /bin/echo

    red
  /bin/echo -n "+---------------------+"
    reset

  /bin/echo
  /bin/echo
}

fi

```

Anyone know why those 3 ANSI codes don't work?

Thanks!

-- Roger

---

### Post by spibou on 2008-11-14
When you say console do you mean Linux console or some terminal emulator? In order to find out what a terminal (emulator) can or cannot do you need to read the terminfo database. Do **man 5 terminfo** and also check out the man pages mentioned at the end. There's no reason to assume that a terminal (emulator)  supports italics, and if it does that you activate them through the sequences you gave. By the way, modifying the TERM variable will not have any effect on how the terminal (emulator) behaves; it doesn't even know the change since children cannot modify the environment of their parents. The purpose of TERM is to inform the programmes running *on top* of the terminal about the type of terminal so that they can query terminfo and find out the capabilities of the terminal. Try the following:
```

tput sitm
if [ $? -eq 0 ] ; then
    echo Supports italics
else
    echo Does not support italics
fi

```
Of course for this to produce correct results, TERM must have the value it had before you started doing your experiments.

---

### Post by Krupski on 2008-11-14
> **spibou said:**
> When you say console do you mean Linux console or some terminal emulator? In order to find out what a terminal (emulator) can or cannot do you need to read the terminfo database. Do **man 5 terminfo** and also check out the man pages mentioned at the end. There's no reason to assume that a terminal (emulator)  supports italics, and if it does that you activate them through the sequences you gave. By the way, modifying the TERM variable will not have any effect on how the terminal (emulator) behaves; it doesn't even know the change since children cannot modify the environment of their parents. The purpose of TERM is to inform the programmes running *on top* of the terminal about the type of terminal so that they can query terminfo and find out the capabilities of the terminal. Try the following:
```

tput sitm
if [ $? -eq 0 ] ; then
    echo Supports italics
else
    echo Does not support italics
fi

```
Of course for this to produce correct results, TERM must have the value it had before you started doing your experiments.

Thanks for the reply!

I ran your script and it returns "Does not support italics". My "terminal" is "GNOME Terminal 2.24.1.1" running under Ubuntu 8.10 (32 bit version).

My term type is set to "xterm" and the shell is "/bin/bash".

My script does not modify the "TERM" variable, nor do I modify it elsewhere (except I did t once for testing purposes - but it's back to normal now).

By the way, what does the "sitm" parameter mean in the "tput sitm" line? I did "man tput" and "tput --help" and found no references to those options. What do they do?

(edit nevermind - just found out what "sitm" does in "terminfo") :)

Thanks!

-- Roger

---

### Post by geirha on 2008-11-14
It uses the first type of invocation, where sitm is the capname
```

       tput [-Ttype] capname [parms ... ]

```

Anyway, try [apt://rxvt-unicode](apt://rxvt-unicode), run it with urxvt and try your script there. It handles italics and blinking.

---

### Post by Krupski on 2008-11-14
> **geirha said:**
> It uses the first type of invocation, where sitm is the capname
```

       tput [-Ttype] capname [parms ... ]

```

Anyway, try [apt://rxvt-unicode](apt://rxvt-unicode), run it with urxvt and try your script there. It handles italics and blinking.

Hey! I like that terminal! Thanks!!! [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]


-- Roger

---

