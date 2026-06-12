---
title: "Turn off screen?"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by dave9191 on 2005-05-08
Hey guys, 

Ive installed ubuntu as a server on my antique 333mhz laptop. Its doing a great job and setting it up was too easy. But now I would like to turn the laptops screen off. Blank it and turn the backlight off. Its going to be in my room and Id like to sleep in there, so i dont want the blazing light and even tho its an old laptop thats not useful for anything else, id like to save the screen from burning out :) 

I know of xset dpms off, but xset isnt install. No X things are (just a server instal). Ive tried to apt-get xset but that came up with nothing. And i dont really want to install X onto it. 

Anyone got any ideas?

Dave

---

### Post by Arthemys on 2005-05-08
Does the laptop have an FN key and a "Change output display" key? If so, try cycling the LCD into CRT mode, that may blank out the screen.

---

### Post by Sam on 2005-05-08
Create a new file on ~/bin called suspend_monitor and put these lines:
```
#! /bin/sh

if [ ! -z $1 ] ; then
  if [ -z "$(echo $1 | awk '/^[0-9]+$/')" ] ; then
    echo Usage: suspend_monitor [DELAY]
    echo Suspend the monitor. If DELAY is set, it waits DELAY seconds before.
    exit
  fi
  sleep $1
fi

xset dpms force standby
```
Then allow execution:
```
$ chmod +x ~/bin/suspend_monitor
```
Create a new launcher and add this:
[list][*]Name: Suspend monitor
[*]Command: /home/<your username>/bin/suspend_monitor 1
[*]Icon: gnome-term-night.png[/list]

When you click on it the screen will turn off after one second (the time to release the mouse).

---

### Post by RastaMahata on 2005-05-08
> **Sam]Create a new file on ~/bin called suspend_monitor and put these lines:
```
#! /bin/sh

if [ ! -z $1 ]  said:**
> +$/')" ] ; then
    echo Usage: suspend_monitor [DELAY]
    echo Suspend the monitor. If DELAY is set, it waits DELAY seconds before.
    exit
  fi
  sleep $1
fi

xset dpms force standby
```
Then allow execution:
```
$ chmod +x ~/bin/suspend_monitor
```
Create a new launcher and add this:
[list][*]Name: Suspend monitor
[*]Command: /home/<your username>/bin/suspend_monitor 1
[*]Icon: gnome-term-night.png[/list]

When you click on it the screen will turn off after one second (the time to release the mouse).
 but he doesnt have xorg/xfree86 installed, so there's no xset for him :(

---

### Post by Sam on 2005-05-08
[QUOTE=RastaMahata]but he doesnt have xorg/xfree86 installed, so there's no xset for him :([/QUOTE]
Good catch...
:?

---

### Post by dave9191 on 2005-05-08
Arthemys, i tired that, but it just blanks for a sec and comes back to lcd as there is no other monitor connected. 

I also messed around with the bios settings to see if the power managment stuff there would work, but its like linux overrides those. 

And thx for the attemp Sam, but you can see where my problem lies :)

---

### Post by RastaMahata on 2005-05-08
[QUOTE=dave9191]Arthemys, i tired that, but it just blanks for a sec and comes back to lcd as there is no other monitor connected. 

I also messed around with the bios settings to see if the power managment stuff there would work, but its like linux overrides those. 

And thx for the attemp Sam, but you can see where my problem lies :)[/QUOTE]
 just a guess here, but what about installing the xserver-xorg package? I dont know, it would allow you to use xset, right? /me is confused

---

### Post by spartas on 2005-05-08
Does the screen go off if the lid is closed?  If so, you should be able to execute lid.sh and blank the screen.  (You'll have to execute it again, but blindly, to bring it back up though).  I don't know if that'll work, because I don't know if it will check the lid switch when you run lid.sh.

---

### Post by dave9191 on 2005-05-09
it doesnt blank when you close the lid (which is what its set to do in bios). But the lid.sh script is stored in /etc/acpi and acpi doesnt seem to intsalled. im going to install xserver-xorg now and see if i can use xset. its only 18mb according to apt-get. 

And it just finished insalling that and no xset :(

Dave

---

### Post by stevetone on 2005-05-09
To get the lid switch to shut off the screen I think you need to tell ACPI to execute lid.sh when the lid is closed. Google "lid ACPI".

---

### Post by dave9191 on 2005-05-09
[QUOTE=stevetone]To get the lid switch to shut off the screen I think you need to tell ACPI to execute lid.sh when the lid is closed. Google "lid ACPI".[/QUOTE]

Which brings me back to the point that acpi is not installed as its a server base install. And the acpi lid switch calls xset to turn the screen off. 

Anyone know what package i need for that to work .

Dave

---

### Post by willis on 2005-05-09
If you need to find components of packages, or just what package something might be in don't forget about [http://packages.ubuntu.com](http://packages.ubuntu.com) .  It lets you search for keywords in package contents etc... 

[all packages with a file matching "bin/xset" in them](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=bin%2Fxset&searchmode=searchword&case=insensitive&version=hoary&arch=i386)

---

### Post by dave9191 on 2005-05-09
Thanks for that link. 

Ive installed xset, but now when i do 

xset dpms force standby

I get 

xset: uable to open display ""


Any ideas ?

---

### Post by dave9191 on 2005-05-09
Ok, i also installed more packages to startx and loaded that up and i can properly blank the screen now :) 

But if anyone has any ideas how i can do that without the need to startx or even install it, then id  be greatful. 

Dave

---

### Post by mird on 2005-05-09
I've not used it personally, but does
```
man setterm
```
look promising?

---

### Post by dave9191 on 2005-05-09
Looks promissing, but i cant seem to get it to do anything. It either accepts commands and does nothing or says that it cant (un)set the termainal. 

Dave

---

