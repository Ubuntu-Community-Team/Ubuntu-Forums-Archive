---
title: "apt-get install cups: Please Help with Crap-out!!"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by ktritty on 2009-05-10
For various reasons, I wanted to do a fresh install for my Ubuntu 9.04 server.  I forgot to choose the option to install print server during the initial setup.

I figured, no big deal, just run

[FONT=Courier New]$ sudo apt-get install cups

[FONT=Arial]and get on with it.  However, once the system was attempting to start cups, it hung (blinking cursor, no $ prompt, only ctrl-alt-del did anything other than display garble).

I attempted to run update command again to try to get back on track:

[FONT=Courier New]$ sudo apt-get update
"normal happy progress text here"
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

[FONT=Arial]So, I try to be a good listener for bash:[/FONT]

$ sudo dpkg --configure -a
Setting up cups (1.3.9-17ubuntu3)  ...  [OK ]
 * Reloading AppArmor profiles  ...  [ OK ]
 * Starting Common unix Printing System: cupsd  [ OK ]
_ "blinking cursor to nowhere"
"Same Crap-Out, need to press ctrl-alt-del"

[FONT=Arial]
***
SOLVED.

Restarted system, still had same problem, but let it hang for 30 minutes then problem went away for good.  Moderators: Feel free to remove this thread and inform me if there is a way I can remove my own dead threads to save space and time for all of us.  Thanks.
[/FONT][/FONT][/FONT][/FONT]

---

