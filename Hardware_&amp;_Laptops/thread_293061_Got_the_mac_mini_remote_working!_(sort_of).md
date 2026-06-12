---
title: "Got the mac mini remote working! (sort of)"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by almahtar on 2006-11-04
I'm running Edgy on an Intel Mac Mini.  I wanted to be able to control amarok with my apple remote, so I started tinkering around.  I hacked together a ruby script that works great, but I'm trying to figure out how to get it to start up when I log in.  I've attached my script (remote.tar.gz) - give it a whirl and let me know what you think if you have a mac remote.  You'll need Amarok installed to work it.  Hit the "menu" button on your remote to start Amarok up.

I've been running it with:
sudo cat /dev/hiddev0 | ruby /sbin/remote.rb

The problem is that I need sudo to have read permission on /dev/hiddev0, so I can't just stick it in my session.  Anyone have any ideas?

Also, if anyone wants to add to the script (give it the choice of controlling xmms, rhythmbox, etc) let me know the commands to control those programs and I'll throw them in the script and add a .conf file to the archive so you can choose (or a command line option).  This is just a quick and dirty script - it should be extended so when you press a key like "play" and amarok hasn't been started it detects that and starts Amarok up automatically.  I'll try to do that when I get time. *edit - I got bored and implemented this.  When you hit "play" it'll figure out if amarok is running and start it if it isn't.*

Has anyone else gotten their remote working in a more conventional fashion?  I mean, my way only lets it control one program, rather than whatever multimedia app is currently in focus.  Is there some kind of generic "mediakey_next" kind of command I can have the script run that will fire off a keypress event in X?

*edit: I updated it with a slightly more refined version.  It now turns your screen saver on/off with the "menu" button, and does a better job of waiting for Amarok to start up before sending it the "play" event if you hit "play" when Amarok isn't running.*

---

### Post by xfile087 on 2006-11-10
Love the script, works perfect! :D

---

### Post by almahtar on 2006-11-10
Sweet! Thanks for letting me know.  I didn't know if anyone even read this post :-)

I'm trying to figure out how to post on the mactel-linux wiki about it, but I'm not very wicki-savvy. :-\

---

### Post by almahtar on 2006-11-10
I just uploaded a smoother-working version with a few minor improvements.  I figured I'd take advantage of that to post, in hopes a quick bump will provide more feedback.

---

### Post by xfile087 on 2006-11-11
Nice improvements, I love the screensaver option!

---

### Post by waterj2 on 2006-11-11
There's a kernel patch on [this page](http://www.madingley.org/macmini/) to get the remote working. I don't know how to apply their generic solution to your script, but maybe it's of some use.

---

### Post by waterj2 on 2006-11-11
I just got your script working. Apparently, my remote is different than yours. The values I had to use for theByte were:
volume down = 13
volume up = 11
play/pause = 4
previous = 8
next = 7
menu = 2

---

### Post by almahtar on 2006-11-11
Interesting.  What model do you have?

---

### Post by almahtar on 2006-11-12
> **waterj2 said:**
> There's a kernel patch on [this page](http://www.madingley.org/macmini/) to get the remote working. I don't know how to apply their generic solution to your script, but maybe it's of some use.

Yeah, I am trying to get something going that doesn't require kernel patching.  Pretty much anyone can copy and paste the command to run a ruby script to their command prompt, but patching the kernel is pretty intimidating :\

Thanks though!

---

### Post by megs on 2006-11-14
almahtar,
Nice work - I too had to change the values that water2j posted, but after that it seems happy enough.  I have the version of the mac mini with a faster processor (1.83 GHz?)
Cheers,
Megs

---

### Post by almahtar on 2006-11-14
Ok.  I should post both versions so people won't have to actually edit the script.  I also tweaked it lately so it opens /dev/hiddev0 itsself, so you can just type "sudo ruby remote.rb" to run it. Thanks for the feedback, Megs.

Also, I've been thinking of other uses for the menu button.  It could toggle shuffle on and off, perhaps.  Would anyone prefer that to the screensaver?

---

### Post by whyameye on 2006-12-09
I wrote a similar program which I called remote.sh and which runs in bash:

```
#!/bin/bash
while [ 1 ]; do
  DecKey=0
  while [ $DecKey -eq 0 ] || [ $DecKey -eq 255 ] || [ $DecKey -eq 135 ] || \
        [ $DecKey -eq 238 ] || [ $DecKey -eq 122 ] || [ $DecKey -eq 156 ] ; do
    key=$(dd bs=1 count=1 2> /dev/null)
    DecKey=$(( $((`printf "%u" "'$key"`)) & 255))
  done
    echo $DecKey
done
```

if you run it with:
```
cat /dev/hiddev0 | ./remote.sh
```

it will show you the codes your remote is sending. This is on a MacBook with the standard Apple remote which comes w/ it.

---

### Post by zpon on 2006-12-10
I took the liberty to edit your script a little so it works with mpd and mpc
```
#!/usr/bin/ruby

#
#  Remote.rb - Jonathan Woffenden - October 2006
#  Contact:  woff9769@uidaho.edu - user "Almahtar" on the Ubuntu Forums
#
#  Description:
#  This is, essentially, a hacked together specific-purpose script
#  that allows you to control Amarok with your apple remote.
#  It's been tested only on my 1.66 Ghtz Intel Mac Mini running
#  Ubuntu 6.10.  Drop me a line if you get it working on other
#  configurations, or if you have questions/improvements.
#
#  Instructions:
#  Pipe /dev/hiddev0 into this script and you should be good.
#  You have do it with "sudo" to get read access to /dev/hiddev0.
#
# edited by zpon

$stdin.each_byte { |theByte|

        if (theByte == 3)
            puts "Menu."
            system("mpc pause")
        end
        if (theByte == 12)
            puts "Volume down."
            system("mpc volume -10")
        end
        if (theByte == 10)
            puts "Volume up."
            system("mpc volume +10")
        end
        if (theByte == 5)
            puts "Play"
            system("mpc play")
        end
        if (theByte == 9)
            puts "Previous."
            system("mpc prev")
        end
        if (theByte == 6)
            puts "Next."
            system("mpc next")
        end
}

```
The menu button is used for pause, I haven't really been using ruby before, so you will probably find a lot of bad coding in the example above

---

### Post by almahtar on 2006-12-10
> **whyameye said:**
> I wrote a similar program which I called remote.sh and which runs in bash:
it will show you the codes your remote is sending. This is on a MacBook with the standard Apple remote which comes w/ it.

Nice!  Doing it in a shell script is a much more useful form: anyone can run it that way.  Great idea.  When I get time (a month or so from now) I think I'll re-write mine as a shell script (using your example), or more likely C, add a config file, and maybe even package it in a deb if I'm feeling ambitious. 

> **zpon said:**
> I took the liberty to edit your script a little so it works with mpd and mpc

The menu button is used for pause, I haven't really been using ruby before, so you will probably find a lot of bad coding in the example above

Thats great, the more things it works with the better (and your coding is fine).  I recently learned from someone on these forums how to turn the Gnome system volume down from the command line, which would be more useful than for a specific player.

I've been thinking it'd be pretty easy to write a C program that'd do all this, and read from a config file so if people need to program different buttons in or use MPD and MPC Vs. Amarok or the like, they could.  Once I'm done with my compilers course (finishes on the 23rd of December... bah... ) I'll start working on it, and if anyone would like to help, that'd be sweet.

When I'm not feeling lazy, Zpon, I'll write a little function in the ruby file that will ask you, the first time it runs, what music player you want to use and then parses itsself, commenting out the right line so it won't ask again.

---

### Post by zpon on 2006-12-12
> **almahtar said:**
> Nice!  Doing it in a shell script is a much more useful form: anyone can run it that way.  Great idea.  When I get time (a month or so from now) I think I'll re-write mine as a shell script (using your example), or more likely C, add a config file, and maybe even package it in a deb if I'm feeling ambitious. 



Thats great, the more things it works with the better (and your coding is fine).  I recently learned from someone on these forums how to turn the Gnome system volume down from the command line, which would be more useful than for a specific player.

I've been thinking it'd be pretty easy to write a C program that'd do all this, and read from a config file so if people need to program different buttons in or use MPD and MPC Vs. Amarok or the like, they could.  Once I'm done with my compilers course (finishes on the 23rd of December... bah... ) I'll start working on it, and if anyone would like to help, that'd be sweet.

When I'm not feeling lazy, Zpon, I'll write a little function in the ruby file that will ask you, the first time it runs, what music player you want to use and then parses itsself, commenting out the right line so it won't ask again.

I would like to help you, if I can (if nothing else, I can always beta test ;)), I have done a bit work in C/C++ and GTK if that can be used. I think it is a great idea to use gnomes volume controller instead

---

### Post by almahtar on 2006-12-12
Haha... that's funny, because most of my experience has been C++ in Qt. :-p  I wonder if there's a way to tell if you're in Gnome or KDE and branch accordingly...

---

### Post by russellc on 2006-12-15
i managed to get to controling the beryl cube (and pretty much any action you can bind a key to) by changing around zpon's ruby script.

---

### Post by almahtar on 2006-12-15
> **russellc said:**
> i managed to get to controling the beryl cube (and pretty much any action you can bind a key to) by changing around zpon's ruby script.

Would you mind posting it? I'm interested in seeing what you did!

---

### Post by russellc on 2006-12-15
all i did was compile this tiny bit of source i found on google: [http://www.ltn.lv/~aivils/?proj_id=xsendkey](http://www.ltn.lv/~aivils/?proj_id=xsendkey)

allows you to send keys from a command. so essentially, anything you can bind a key to is possible.

and the commands i used (the edited code):
```

#!/usr/bin/ruby

#
#  Remote.rb - Jonathan Woffenden - October 2006
#  Contact:  woff9769@uidaho.edu - user "Almahtar" on the Ubuntu Forums
#
#  Description:
#  This is, essentially, a hacked together specific-purpose script
#  that allows you to control Amarok with your apple remote.
#  It's been tested only on my 1.66 Ghtz Intel Mac Mini running
#  Ubuntu 6.10.  Drop me a line if you get it working on other
#  configurations, or if you have questions/improvements.
#
#  Instructions:
#  Pipe /dev/hiddev0 into this script and you should be good.
#  You have do it with "sudo" to get read access to /dev/hiddev0.
#
# edited by zpon

$stdin.each_byte { |theByte|

        if (theByte == 2)
            puts "Menu."
            system("xsendkey 37 1; xsendkey 73 1; xsendkey 37 0; xsendkey 73 0")
        end
        if (theByte == 13)
            puts "Volume down."
            system("xsendkey 37 1; xsendkey 72 1; xsendkey 37 0; xsendkey 72 0")
        end
        if (theByte == 11)
            puts "Volume up."
            system("xsendkey 37 1; xsendkey 71 1; xsendkey 37 0; xsendkey 71 0")
        end
        if (theByte == 4)
            puts "Play"
            system("quodlibet --play-pause")
        end
        if (theByte == 8)
            puts "Previous."
            system("xsendkey 37 1; xsendkey 69 1; xsendkey 37 0; xsendkey 69 0")
        end
        if (theByte == 7)
            puts "Next."
            system("xsendkey 37 1; xsendkey 70 1; xsendkey 37 0; xsendkey 70 0")
        end
}
```

yeah, there is some left over code from the audio control (because i use quod libet)

i simply binded some keys that i would never press. it took a little time to find all the keys' numbers, but all that was easy. all the keys above are just a combination of: Control + "Some F Key"

it would be cool if it were possible to have all this work the way some os x apps work (a la remote buddy).

i was also wondering if it would be possible to check for the focused process, and then in turn have a set of rules for that specific application (this is how remote buddy works, to a lesser degree of course)

---

### Post by zpon on 2006-12-16
> **russellc said:**
> all i did was compile this tiny bit of source i found on google: [http://www.ltn.lv/~aivils/?proj_id=xsendkey](http://www.ltn.lv/~aivils/?proj_id=xsendkey)

allows you to send keys from a command. so essentially, anything you can bind a key to is possible.

and the commands i used (the edited code):
```

#!/usr/bin/ruby

#
#  Remote.rb - Jonathan Woffenden - October 2006
#  Contact:  woff9769@uidaho.edu - user "Almahtar" on the Ubuntu Forums
#
#  Description:
#  This is, essentially, a hacked together specific-purpose script
#  that allows you to control Amarok with your apple remote.
#  It's been tested only on my 1.66 Ghtz Intel Mac Mini running
#  Ubuntu 6.10.  Drop me a line if you get it working on other
#  configurations, or if you have questions/improvements.
#
#  Instructions:
#  Pipe /dev/hiddev0 into this script and you should be good.
#  You have do it with "sudo" to get read access to /dev/hiddev0.
#
# edited by zpon

$stdin.each_byte { |theByte|

        if (theByte == 2)
            puts "Menu."
            system("xsendkey 37 1; xsendkey 73 1; xsendkey 37 0; xsendkey 73 0")
        end
        if (theByte == 13)
            puts "Volume down."
            system("xsendkey 37 1; xsendkey 72 1; xsendkey 37 0; xsendkey 72 0")
        end
        if (theByte == 11)
            puts "Volume up."
            system("xsendkey 37 1; xsendkey 71 1; xsendkey 37 0; xsendkey 71 0")
        end
        if (theByte == 4)
            puts "Play"
            system("quodlibet --play-pause")
        end
        if (theByte == 8)
            puts "Previous."
            system("xsendkey 37 1; xsendkey 69 1; xsendkey 37 0; xsendkey 69 0")
        end
        if (theByte == 7)
            puts "Next."
            system("xsendkey 37 1; xsendkey 70 1; xsendkey 37 0; xsendkey 70 0")
        end
}
```

yeah, there is some left over code from the audio control (because i use quod libet)

i simply binded some keys that i would never press. it took a little time to find all the keys' numbers, but all that was easy. all the keys above are just a combination of: Control + "Some F Key"

it would be cool if it were possible to have all this work the way some os x apps work (a la remote buddy).

i was also wondering if it would be possible to check for the focused process, and then in turn have a set of rules for that specific application (this is how remote buddy works, to a lesser degree of course)

remote buddy looks cool, could be interesting to make something like it

---

### Post by zpon on 2006-12-16
I made a little mockup in glade, of how I imagine a application to choose between the different scripts, could look like.

[IMG]http://static.flickr.com/129/324334928_3aeaa6275d.jpg?v=0[/IMG]

What do you think? Feedback please :)
By the way, "annullér" means cancel and "anvend" means apply, in Danish.

---

### Post by vh1 on 2006-12-21
are there any programs for X like [joytokey for windows](http://www.electracode.com/4/joy2key/JoyToKey%20English%20Version.htm). this always kind of hit me as a shocker, considering how useful joytokey can be. and how useful it would be if there were a program to convert any input to any output. i.e: macbook right-apple key to mouse2, joystick axis to mouse, apple remote play to XF86AudioPlay

I know that I can use xmodmap for the right-apple key trick, but that doesn't seem to actually be working for me, and doesn't seem as tangible as something that actually translates between the two

---

### Post by vh1 on 2006-12-31
I made a few modifications to the shell script so it uses xsendkey to send the best suited XF86Audio* keycodes

my remote keycodes were different than the original ruby script so I decided to make them variables. and the XF86Audio keycodes I got from `xmodmap -pke | grep XF86Audio`. not sure if they differ on other systems

```
#!/bin/bash

MENU=2
UP=11
DOWN=13
RIGHT=7
LEFT=8
PLAY=4

while [ 1 ]; do
  DecKey=0
  while [ $DecKey -eq 0 ] || [ $DecKey -eq 255 ] || [ $DecKey -eq 135 ] || \
        [ $DecKey -eq 238 ] || [ $DecKey -eq 122 ] || [ $DecKey -eq 156 ] ; do
    key=$(dd bs=1 count=1 2> /dev/null)
    DecKey=$(( $((`printf "%u" "'$key"`)) & 255))
  done
    if [ $DecKey -eq $DOWN ]; then
       xsendkey 174 1
       xsendkey 174 0
    fi
    if [ $DecKey -eq $UP ]; then
       xsendkey 176 1
       xsendkey 176 0
    fi

    if [ $DecKey -eq $LEFT ]; then
       xsendkey 144 1
       xsendkey 144 0
    fi
    if [ $DecKey -eq $RIGHT ]; then
       xsendkey 153 1
       xsendkey 153 0
    fi

    if [ $DecKey -eq $PLAY ]; then
       xsendkey 162 1
       xsendkey 162 0
    fi
done

```

---

### Post by almahtar on 2006-12-31
YES.  That's perfect.  That's by far the best thing it should be doing.  Thanks a ton, VH1.  Anyone here know how to make a .deb?  It'd be cool to actually make a package out of this and see if it can't sneak it's way into the feisty repos.

---

### Post by vh1 on 2007-01-01
it doesn't use the media key though. but I noticed that there was a symbol called XF86AudioMedia, which should be fine until (or if) a better fit is found

alas, I don't know how to make a .deb outside of checkinstall. but there are plenty of tutorials floating around

I'm working on an init.d script now. should just be some cutting and pasting in the skeleton file

---

### Post by almahtar on 2007-05-16
Any luck on this so far?

---

### Post by russo.mic on 2007-05-31
Hey!

Love the work,  I'd love to use my remote to control Amarok.  

But for some reason my remote isn't at /dev/hiddev0.  I can't find it anywhere.  Any ideas?  I'm using the MacBook Pro C2D 2.33.

Thanks!

Russo

---

### Post by almahtar on 2007-06-01
Have you tried to see if maybe it's called /dev/hiddev1 or the like?  Like, have you tried "ls /dev/hid*"?

Let me know what you have tried and I'll try to figure out what you might not have :-)  Feel free to get into detail.

---

### Post by megs on 2007-06-03
Seems to me that the remote is now supported under feisty, as it attempts to control the volume without any kind of scripts running on my part.  Am searching for information on how to get it working properly and interacting with kaffeine/myth/amarok.  Anyone else seen this?
Megs

---

### Post by almahtar on 2007-06-03
Nice! Then people won't have to use my hastily hacked together script :-)

---

### Post by russo.mic on 2007-06-04
Yep,  it's definately not there.  

There is nothing in /dev that even starts with hid or whatever.

I also checked in /dev/input and still nothing.  

Hmm.....

Thanks for any assistance!

Russo

---

### Post by russo.mic on 2007-06-04
So, 

I've found my remote.  It was at /dev/input/event7, I found it using the Hardware Manager.  
My problem now is that not only are the theByte values incorrect, but each time I hit a button on the remote, it seems to select a button at random.  plus, instead of just one button push, about 10 or so fly across the screen.  

I think the 

if (theByte != 0 && theByte != 255 && theByte != 135 && theByte != 238 && theByte != 122)	

line sets a value of ranges maybe?  I'm currently trying to learn ruby.  Is this my problem?

Macbook Pro C2D
Feisty Fawn 7.04

I know the remote is supported, because by default it controls the system volume, and it will control rythembox fine.  I'm just trying to learn ruby.  

Anybody else have a amarok / kaffine / remote solution they feel like sharing?

Russo

---

