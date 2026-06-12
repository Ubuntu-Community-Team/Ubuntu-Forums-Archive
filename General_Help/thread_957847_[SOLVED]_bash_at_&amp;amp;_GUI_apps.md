---
title: "[SOLVED] bash: at &amp;amp; GUI apps"
date: 2008-10-24
forum: General Help
---

### Post by bryonak on 2008-10-24
I'm quite puzzled by **at**.
Apart from it's really strange usage (either echoing the command into a pipe or having to add an ampersand in many cases in 'interactive mode'), why can't that darned thing just start any GUI application (gedit, gcalc, whatever)?

Cron is not what I'm looking for, because you have to use an editor and I don't need the repetitiveness.

Ideally, it should be something I can simply and quickly write in a terminal, without having to use other tools... an **at** like this:
at 12:45 firefox slashdot.org thedailywtf.org xkcd.org
(that would be some entertainment after lunch)

or:
at now + 15min xterm -e echo pizza should be ready by now & sleep 10

Any suggestions?

---

### Post by lovinglinux on 2008-10-24
I know you are looking for a command-line solution, but you could give [[COLOR="Red"]**Alarm Clock**[/COLOR]]("http://www.getdeb.net/app/Alarm+Clock") a try. It is very simple to configure several types of alarms, including launching scripts and programs.

---

### Post by bryonak on 2008-10-24
Thanks, Alarm Clock works nicely.

Yep, I'd rather have the command line, especially since it takes something around 8-10 clicks plus typing to launch my first example from above... that makes cron look quite friendly ;)

But I'll keep it anyway, the counter function is nice and I can't find a better alternative.
kalarm might be worth a try, but I'm not going to install kdelibs on a laptop just because of it. Can anyone **really** recommend kalarm?

---

### Post by lovinglinux on 2008-10-24
If you want simple reminders you can use Tomboy reminder plugin. Once installed all you have to do is create a note with the "remind" word in the body like this:

```
remind today @ 20:00
```

or something like

```
remind next monday @ 17:00
```

or

```
remind october 25 @ 13:00
```

Unfortunately, you can't launch programs automatically, but you could add links to scripts, applications or web sites.

---

### Post by lswb on 2008-10-24
The reason at won't run a gui program is because the daemon process (atd) that actually runs the jobs specified by at isn't running on any kind of display or tty that firefox or other X programs can use. You can specify a display like this

at [your time here]
firefox --display=:0
^D

---

### Post by sdennie on 2008-10-24
You can also make relative reminders with the sleep command.  For example:

```

sleep 30m && gcalctool &
disown

```

That will wait 30 minutes and then start the gnome calculator.  The "disown" is only needed if you close the terminal window you start the command in.  See the sleep man page for more information on what times can be specificied with the command.

---

### Post by bryonak on 2008-10-25
@lovinglinux:
I wasn't comfortable with running an additional application which I didn't need at all, so I actually searched aptitude for 'remind', which gave me a very sophisticated calendar/scheduling command line tool. This isn't what you meant, but thanks anyway ;)
It will take some time to learn the syntax and get used to it, and maybe it's a bit too heavyweight for my needs, but I like it. There's a ncurses interface (wyrd) and two GUIs (tkremind is built-in, wxRemind is a bit prettier, but needs additional Python libs) for those who need to set up complex reminders without learning the script language.

@lswb:
Typing '--display=:0' every time can't be automated (at least to my knowledge) in **at**'s "interactive mode", so I wrote a little function to do the piping.
Just paste into your .bashrc and use it the same way as the idealized **at** in my initial posting.
```
gat () { echo "$2 --display=:0" | at "$1"; }
```
Remember to put both the time and the program+options in quotes if it contains whitespaces.

@vor:
Very good idea there!
Interestingly (and this makes it very useful to me) it even survives suspends.

How come that without 'disown' the calculator dies if I close the terminal **after** it has started, but works happily on closing the terminal before the sleep has finished? Is it because the "parentship" gets passed up to somewhere else if the invoking shell doesn't exist anymore?
Anyway, I'm quite content with using 'sleep && ' with both alt+f2 and 'disown' for my count-down needs.

---

### Post by sdennie on 2008-10-25
> **bryonak said:**
> 
@vor:
Very good idea there!
Interestingly (and this makes it very useful to me) it even survives suspends.

How come that without 'disown' the calculator dies if I close the terminal **after** it has started, but works happily on closing the terminal before the sleep has finished? Is it because the "parentship" gets passed up to somewhere else if the invoking shell doesn't exist anymore?
Anyway, I'm quite content with using 'sleep && ' with both alt+f2 and 'disown' for my count-down needs.

I really don't know why that's the behavior.  I would think that without the disown, closing the terminal would kill the sleep and other command.

Regardless, if you are using this method for reminders, you may want to look at zenity too.  You can write a simple script to have zenity popup dialogs using this method.  Maybe something like:

```

#!/bin/bash

sleep $1 && zenity --info --text="$2"

```

Then:

```

name_of_script 45m "Go to bed!"

```

---

### Post by bryonak on 2008-10-25
> **vor said:**
> I would think that without the disown, closing the terminal would kill the sleep and other command.

It doesn't, at least on my system. Nevermind.

I prefer bash functions over script files, at least for such short things, so here's what I find a useful snippet:
```

tat () { echo "$2 " | at "$1"; }
gat () { echo "$2 --display=:0" | at "$1"; }
rem () { sleep "$1" && zenity --info --text="$2" & disown; }
```

'tat' is for shell commands (which don't play well with --display) and can be used if you really want to force yourself to stop something:
```
tat 23:59 "killall firefox" & gat 23:59 "rem 0 'time to sleep, seriously'"
```
That's what I think 'at' should do by default... even better would be merging the functionalities of 'tat' and 'gat'

'rem' is my favourite count-down alert for now :)

---

