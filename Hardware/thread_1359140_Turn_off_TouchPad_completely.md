---
title: "Turn off TouchPad completely"
date: 2009-12-19
forum: Hardware
---

### Post by stoopid_noob on 2009-12-19
Hello all, 

I recently purchased a dm3 from HP, which I love, however I am not able to turn off the touchpad while in Ubuntu 9.10, which I can in Windows using the button right about the touchpad.

This is driving me nuts! Just typing this message out the cursor jumped around three times and I have to go back and correct for it. I usually use a wireless mouse, and I want to turn off the touchpad completely. 

It is not a Synaptics unit, it is an ALPS unit. 

I have seen a few guides on how to do this, none of which have worked thus far. 

Any help would be greatly appreciated.

---

### Post by wangsuda on 2009-12-19
I have two suggestions for you:

1. Go to System>Preferences>Mouse and go to the "touchpad" area. you can disable the touchpad while typing and disable scrolling. If that doesn't help, then

2. Go to the top panel and right click. Left click on "Add to Panel" and select the "Pointer Capture" item. you can then lock the cursor into the top or bottom panel - no more jumping cursor! To unlock the cursor, simply left click the mouse!

Hope this helps!

---

### Post by stoopid_noob on 2009-12-19
> **wangsuda said:**
> I have two suggestions for you:

1. Go to System>Preferences>Mouse and go to the "touchpad" area. you can disable the touchpad while typing and disable scrolling. If that doesn't help, then

2. Go to the top panel and right click. Left click on "Add to Panel" and select the "Pointer Capture" item. you can then lock the cursor into the top or bottom panel - no more jumping cursor! To unlock the cursor, simply left click the mouse!

Hope this helps!

Hello, thank you for your input. 

The second technically works, but is not a solution, because if while typing you tap the pad with your palm it unlocks it again. :(

The first solution I have tried, but my issue lays with the fact that I do not have a Touchpad section. There are only mouse options, and nothing relating to touchpad. 

I am trying to install "gpointing-device-settings" and I have the files downloaded but I have no idea how to initiate the installation process. Any help there?

---

### Post by wangsuda on 2009-12-19
> **stoopid_noob said:**
> 
I am trying to install "gpointing-device-settings" and I have the files downloaded but I have no idea how to initiate the installation process. Any help there?
Let's see, all depends on what format you dowloaded it in. If it's deb, then use the GDebi Package installer. If it's tar, then I am no help. Documentation on your packages, as well as people to contact for help can be found at [http://packages.ubuntu.com/karmic/gpointing-device-settings](http://packages.ubuntu.com/karmic/gpointing-device-settings) and [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

EDIT: You can download and install your package through Synaptic! That would be the easiest way. Visiting the live gnome URL will give you screen shots of the program you want.

---

### Post by stoopid_noob on 2009-12-19
Ok, thanks a lot for that. Installed. 

Now, under my System > Preferences > I have something called "TouchPad" there but once I click it to initiate it gives me an error message that states the following:

[B]GSynaptics could not initialize. 

You have to set "SHMConfig" to "True" in xorg.conf or XF86CONFIG to use Synaptics. [/B]

I looked for this file on my system to set to true, but I am not able to find either.

EDIT: OK I have located the xorg.conf file on my system and opened it up. What do I need to add to the file in order to set the "SHMConfig" to "True"? 

Thanks for your help.

---

### Post by moddie666 on 2009-12-19
hi.

try to google the error message or parts of it, chances are youre not the first to encounter this.

greetings
/moddie

example:
[http://www.google.at/#hl=de&source=hp&q=shmconfig+true&meta=&aq=1&oq=SHMConfig&fp=1&cad=b](http://www.google.at/#hl=de&source=hp&q=shmconfig+true&meta=&aq=1&oq=SHMConfig&fp=1&cad=b)

---

### Post by turvyc on 2009-12-19
Hi there,
I'm not sure if my solution works with anything other than a Synaptics touchpad, but here goes ...
It's a simple terminal command:
```
synclient TouchpadOff=1
```
Of course, if you want it back on, the value should be 0.
Now, this command is pretty clunky, so what I then did is put it into my bash_aliases file (okay, maybe this is a little off-topic but I still think it's so cool!): 

First, open up bashrc:
```
sudo gedit ~/.bashrc
```
This file is actually really interesting and well-commented. Scroll down to the "Alias Definitions" section, and make sure the if/fi bit is uncommented.

Then create your bash-aliases file, if it's not there already:
```
sudo gedit ~/.bash-aliases
```
Aliases are just a custom, usually very simple "alias" for a more complex command. Here's my bash-aliases file, for example:
```
alias ged='sudo gedit'
alias ls='ls -F --color=always'
alias la='ls -aF --color=always'
alias ..='cd ..'
alias grep='grep --color=auto'
alias writer='openoffice.org3 -writer'
alias touchpad-on='synclient TouchpadOff=0'
alias touchpad-off='synclient TouchpadOff=1'
alias volume='gnome-volume-control &'
alias rm='rm -i'
```
Cool, eh? Now all I have to do is open up a terminal (always keyed to F12 ... I love Guake!), and enter touchpad-off to turn my pad off!

Anyways, I hope I didn't hijack this thread with my sojourn into the joys of bash-aliases, and if I did I am very sorry, but this is the very first time I think I might be able to help somebody out on these forums, and my enthusiasm for Linux certainly tends to run over ...

---

### Post by wrsh1983 on 2009-12-19
I use hp dm3 1030us, and I have the same problem with you (the button on the top of touchpad does not work). However, you can disable touchpad by using command: 

  sudo rmmod psmouse

and enable it with

  sudo modprobe psmouse

---

### Post by wizzeerd on 2009-12-31
I love my dm3 also.  (Intel model.)

I've got the button above the trackpad working to toggle whether the touchpad works or not.  (Light is always on though.)

Step 1 - create a script to toggle the touchpad.

Create a script in /usr/local/bin named mousetoggle.sh (don't forget to make it executable)
```
#!/bin/bash

if [ -e /tmp/mouse-disabled ]; then
  rm -f /tmp/mouse-disabled
  xinput set-int-prop 'ImPS/2 Generic Wheel Mouse' 'Device Enabled' 8 1
else
  touch /tmp/mouse-disabled
  xinput set-int-prop 'ImPS/2 Generic Wheel Mouse' 'Device Enabled' 8 0
fi;
```Step 2 - create a keyboard shortcut to execute this script when the key above the touchpad is pressed.

* Go to System > Preferences > Keyboard Shortcuts
* Click on Add to add a new shortcut
* * name = Toggle Touchpad
* * command = /usr/local/bin/mousetoggle.sh
* click the word 'disabled' next to the new shortcut and press the key above the touchpad
* close the keyboard shortcuts menu

Hope that works for you.

---

### Post by zeezam on 2010-01-08
> **turvyc said:**
> Hi there,
I'm not sure if my solution works with anything other than a Synaptics touchpad, but here goes ...
It's a simple terminal command:
```
synclient TouchpadOff=1
```
Of course, if you want it back on, the value should be 0.
Now, this command is pretty clunky, so what I then did is put it into my bash_aliases file (okay, maybe this is a little off-topic but I still think it's so cool!): 

First, open up bashrc:
```
sudo gedit ~/.bashrc
```
This file is actually really interesting and well-commented. Scroll down to the "Alias Definitions" section, and make sure the if/fi bit is uncommented.

Then create your bash-aliases file, if it's not there already:
```
sudo gedit ~/.bash-aliases
```
Aliases are just a custom, usually very simple "alias" for a more complex command. Here's my bash-aliases file, for example:
```
alias ged='sudo gedit'
alias ls='ls -F --color=always'
alias la='ls -aF --color=always'
alias ..='cd ..'
alias grep='grep --color=auto'
alias writer='openoffice.org3 -writer'
alias touchpad-on='synclient TouchpadOff=0'
alias touchpad-off='synclient TouchpadOff=1'
alias volume='gnome-volume-control &'
alias rm='rm -i'
```
Cool, eh? Now all I have to do is open up a terminal (always keyed to F12 ... I love Guake!), and enter touchpad-off to turn my pad off!

Anyways, I hope I didn't hijack this thread with my sojourn into the joys of bash-aliases, and if I did I am very sorry, but this is the very first time I think I might be able to help somebody out on these forums, and my enthusiasm for Linux certainly tends to run over ...

Alias doesn't work for me!
I have created a file .bash_aliases in ~/ with the alias you suggested. I have checked in ~/.bashrc that the if/fi lines isn't uncomment.

When I typ "alias" in terminal the alias in .bash_aliases isn't listed. Another thing, you wrote ".bash-aliases", it should be ".bash_aliases" (that is what .basrc says).

---

### Post by turvyc on 2010-01-08
Hi Zeezam,

That's really weird! As for bash-aliases vs. bash_aliases, I think it's just a suggested name ... you can name the file whatever you want as long as it matches up to the if/fi statments in .bashrc. Here's mine:

```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#
if [ -f ~/.bash-aliases ]; then
    . ~/.bash-aliases
fi

```

It's strange how it doesn't work, though. One thing I thought of is maybe the aliases in the .bashrc are uncommented. Right under the above bit of code there are several alias commands in an if/fi statement, then a couple more by themselves. In my .bashrc they are all commented ... is this the case with you, too?

Can you create on-the-fly aliases? For example can you use the alias command in a terminal prompt? That is, can you enter one of the alias commands into the terminal and have it work for that session?

I'm afraid I am no Linux guru (obviously :P ), and this is the limit of my ability to help you ... hope it works, and if not, I hope someone with a greater geekitude than will descend upon this thread!

---

### Post by zeezam on 2010-01-09
> **turvyc said:**
> Hi Zeezam,

That's really weird! As for bash-aliases vs. bash_aliases, I think it's just a suggested name ... you can name the file whatever you want as long as it matches up to the if/fi statments in .bashrc. Here's mine:

```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#
if [ -f ~/.bash-aliases ]; then
    . ~/.bash-aliases
fi

```

It's strange how it doesn't work, though. One thing I thought of is maybe the aliases in the .bashrc are uncommented. Right under the above bit of code there are several alias commands in an if/fi statement, then a couple more by themselves. In my .bashrc they are all commented ... is this the case with you, too?

Can you create on-the-fly aliases? For example can you use the alias command in a terminal prompt? That is, can you enter one of the alias commands into the terminal and have it work for that session?

I'm afraid I am no Linux guru (obviously :P ), and this is the limit of my ability to help you ... hope it works, and if not, I hope someone with a greater geekitude than will descend upon this thread!

I created the aliases in .bashrc instead.
After I ran source .bashrc and it worked. Maybe it works with .bash-aliases if I run source .bashrc before a try to run the alias...

---

### Post by bluefoxox on 2010-01-22
I have a similar problem.  The "Touchpad" tab is not present on my machine which is a dm3-1039wm and has an ALPS unlike the original poster, I want to use my touchpad but get frustrated by how as I type the cusor jumps, and I have to start all over again.  Any suggestions as to how to get this tab to show up?

---

### Post by turvyc on 2010-01-23
Hello Bluefoxox,

I just did a quick search, and [this post]("http://ubuntuforums.org/archive/index.php/t-477323.html") had an idea that worked for another guy.

Essentially, edit your xorg.conf, using these commands:

```
# First back up the original:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.my.backup
# Now open it for editing:
sudo gedit /etc/X11/xorg.conf
```

Now add the line <Option "SHMConfig" "on">, so it looks like this:

```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "on"
EndSection
```

Now, I realize that this example says it's for a Synaptics pad, but the original poster had an alps touchpad, and he claimed this method worked.

Anyways, with this option enabled, you can install syndaemon if it's not on your computer already. This disables your touchpad only when you're typing. For the full list you can just type <syndaemon -h>. Myself, I have it in my startup applications, with these args:

```
syndaemon -S -t -d -i 1
```

-S forces it to Synclient (lets it run), -t disables only tapping and scrolling (not movement), -d starts it as a daemon, -i is the length of time disabled in seconds.

Hope this works for you!

---

### Post by meesekiller on 2010-02-02
> **wrsh1983 said:**
> I use hp dm3 1030us, and I have the same problem with you (the button on the top of touchpad does not work). However, you can disable touchpad by using command: 

  sudo rmmod psmouse

and enable it with

  sudo modprobe psmouse

You my friend...are my new most favorite person in the world (for a few minutes). That was bugging the hell out of me.

Thank you much.

Edit:

A quick note. This route only allows for it to be turned off from the terminal...meaning every time you reboot you have to do it again.

If you want a permanent way to turn off the touchpad you can use the black list feature.

[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

so type:
sudo su
echo blacklist psmouse >> /etc/modprobe.d/blacklist-custom.conf

This creates a custom blacklist file that runs on boot and shots off the internal mouse (or the touchpad in this case).
Worked for me.

---

### Post by cmcanulty on 2012-01-07
just install g pointing devices settings in synaptic then tweak it as you like under applications-other-pointing devices the jumping around cursor was driving me nuts

---

