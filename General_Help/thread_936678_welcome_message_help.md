---
title: "welcome message help"
date: 2008-10-03
forum: General Help
---

### Post by linkxs on 2008-10-03
hey tehre

i´ve been poking around with bash scripts for a bit but i only know a little, anwyays, i was wondering fi it was possible to output the output of a program (fortune) as a welcome emssage, rihgt after a line of just stuff?

what i want it to look like is:

blarg

[fortune output]

who doesnt love fortune.. best thing ever created..

Thank a lot!

---

### Post by ajmorris on 2008-10-03
hi there,
Which welcome message are you referring to? your GDM welcome message, or you bash welcome message to your CLI?

AJ

---

### Post by linkxs on 2008-10-03
the welcome message thatyou get when you log into the system in terminal.

---

### Post by ajmorris on 2008-10-03
> **linkxs said:**
> the welcome message thatyou get when you log into the system in terminal.

yes, it is very achievable, you just need to add it to ~/.bashrc :)

it just requires a simple echo in ~/.bashrc
```

clear
cal -3
echo
date
echo
echo -ne "${CYAN}";uptime
echo
echo -ne "${LIGHTGREEN}";fortune
echo

echo -ne "${LIGHTBLUE}""Hello $USER, have a nice day"
echo
echo

```that is the lines i am currently running to have the date, calendar, fortune etc, you may like to have a fiddle around with those :)

AJ

---

### Post by linkxs on 2008-10-04
.bashrc?

i tghought welcome message is in /etc/motd and /etc/motd.tail

---

### Post by ajmorris on 2008-10-04
> **linkxs said:**
> .bashrc?

i tghought welcome message is in /etc/motd and /etc/motd.tail

.bashrc is what your terminal displays when you start a bash session, /etc/motd does have the message of the day as well, yes... if you were to put "echo blah" in ~/.bashrc and have blah in /etc/motd, you would see blah twice. Not sure if you can put commands into your motd file...

AJ

---

### Post by linkxs on 2008-10-04
> **ajmorris said:**
> .bashrc is what your terminal displays when you start a bash session, /etc/motd does have the message of the day as well, yes... if you were to put "echo blah" in ~/.bashrc and have blah in /etc/motd, you would see blah twice. Not sure if you can put commands into your motd file...

AJ

ah, well originally my question was meant to be about the motd.. but if i just put that into .bashrc it should work.. well, thanks a lot!

---

### Post by taladan on 2008-10-04
to clarify the difference, motd is more for systemwide announcements that you want every user to see, ferex:

> IT is taking the print server Alice down today for routine maintenance at 4pm EST.  We will be dragging it out into a field and going Office Space on it.  Thanks for working at Innetech

Whereas the .bashrc (and /etc/bashrc) are to run special startup scripts, programs, etc.  /etc/bashrc makes it global for all users.  ~/.bashrc makes it local for one user.

Tal

---

### Post by linkxs on 2008-10-04
ah, well thanks a lot!

is motd global for all users?

---

### Post by ajmorris on 2008-10-04
> **linkxs said:**
> ah, well thanks a lot!

is motd global for all users?
yes motd is global for all users, and displays whenever any user starts up the CLI, counting if someone SSHs into your machine ;)

---

### Post by linkxs on 2008-10-04
the part where you do

echo -ne "$(CYAN)";

is no worky, as i understand you set the colors of the following command output, but it doesnt work. it just says that command isn't found.

EDIT:

sorry i was doing it on a very odl alptop and i ahd to type it up again didnt see those were {} not (). but, now that i fixed it, it just doesn't do anything different, i mean it doesnt give me errors but none of the text is different color.

---

### Post by ajmorris on 2008-10-05
> **linkxs said:**
> the part where you do

echo -ne "$(CYAN)";

is no worky, as i understand you set the colors of the following command output, but it doesnt work. it just says that command isn't found.

EDIT:

sorry i was doing it on a very odl alptop and i ahd to type it up again didnt see those were {} not (). but, now that i fixed it, it just doesn't do anything different, i mean it doesnt give me errors but none of the text is different color.


oh, sorry, those are colours i defined specifically, add this towards the top of ~/.bashrc:
```
 
# Color Definitions
 BLACK='\e[0;30m'
 BLUE='\e[0;34m'
 GREEN='\e[0;32m'
 CYAN='\e[0;36m'
 RED='\e[0;31m'
 PURPLE='\e[0;35m'
 BROWN='\e[0;33m'
 LIGHTGRAY='\e[0;37m'
 DARKGRAY='\e[1;30m'
 LIGHTBLUE='\e[1;34m'
 LIGHTGREEN='\e[1;32m'
 LIGHTCYAN='\e[1;36m'
 LIGHTRED='\e[1;31m'
 LIGHTPURPLE='\e[1;35m'
 YELLOW='\e[1;33m'
 WHITE='\e[1;37m'

```that'll enable the colours in the echos, and a few more incase you wanna fiddle ;)

---

### Post by linkxs on 2008-10-05
wow. great! thanks again!

---

