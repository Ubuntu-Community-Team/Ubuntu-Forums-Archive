---
title: "HP pavillion ze4400 - Some hotkeys sends no signal!"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-10-31
Hi There,

I have a HP Pavilion ze4400 (ze4453EA)

These multimedia-keys, doesn't send any signals: (according to xev and dmesg)

Mute (on the left vertical side of the laptop)
Multimedia-key 2 (With a tv symbol)
Multimedia-key 4 (With a lock symbol)
Multimedia-key 5 (With a questionmark symbol)

...There are 5 multimedia-keys above the keyboard (centered) - Counting from the left!

How do I fix this?

---

### Post by simohell on 2005-11-02
This applies to HP nx9005 as well... The 1st and 3rd in the top row work and the other 3 won't. Also the mute-button won't work (give any signal) although the volume up/down buttons work.(Muting works from fn+something, but not from the separate button.

I'd be happy to hear how to fix this.

They do work in Windows...

---

### Post by simohell on 2005-11-02
btw.

Does the ze4400 keyboard work after hibernation? With nx9005 that is another problem, exept if one uses external keyboard...

---

### Post by daller on 2005-11-02
[QUOTE=simohell]btw.

Does the ze4400 keyboard work after hibernation? With nx9005 that is another problem, exept if one uses external keyboard...[/QUOTE]

I'll check it tomorrow! (I'm not using hibernation - but for the sake of debuggin' - why not? :))

---

### Post by xxMEL0Nxx on 2005-11-02
Hi,

I have the same problem here, I have a ze4420us and those keys doesn't work, after hibernation the mouse and the touchpad got locked up, I'm going to try an external keyboard,  is there a way to fix the keyboard and mouse locking after hibernation?

---

### Post by teaker1s on 2005-11-04
[http://ubuntuforums.org/showthread.php?t=86163](http://ubuntuforums.org/showthread.php?t=86163)

---

### Post by simohell on 2005-11-24
I don't know if you managed to fix this already, but if not you might want to take a look at the following:

[http://sourceforge.net/projects/omke/]("http://sourceforge.net/projects/omke/")

You can find for instance a perl script (omke.pl) which made my mute button work.
The other three didn't work though.

I'm now going try to compile a kernel module from the same site. The kernel module also has a readme-file with different scan-or-someting codes for the one-touch keys on several different laptopmodels. (apparrently my laptop woudn't quite match yours in these codes)

---

### Post by simohell on 2005-11-24
[QUOTE=simohell]I don't know if you managed to fix this already, but if not you might want to take a look at the following:

[http://sourceforge.net/projects/omke/]("http://sourceforge.net/projects/omke/")

You can find for instance a perl script (omke.pl) which made my mute button work.
The other three didn't work though.
[/QUOTE]

Ok. Now I got it working. For me there is no need to install the kernel module. I just need to setup the keys as follows.

```
setkeycodes e070 123
setkeycodes e073 120
setkeycodes e071 116
```


Can't test this, but according to the documentation of the kernel module for your computer the following should be correct:

```

HP OmniBook xe4xxx and ze4xxx
-----------------------------

Mail button:                    e06c
Presentation button:            e073
WWW button:                     e032
Lock button:                    e071
Help button:                    e070

Volume down button:             e02e
Volume up button:               e030
Mute / Unmute button:           e020

```

---

### Post by ranf on 2005-11-24
[QUOTE=daller]
I have a HP Pavilion ze4400 (ze4453EA)

These multimedia-keys, doesn't send any signals: (according to xev and dmesg)

Mute (on the left vertical side of the laptop)
Multimedia-key 2 (With a tv symbol)
Multimedia-key 4 (With a lock symbol)
Multimedia-key 5 (With a questionmark symbol)

...There are 5 multimedia-keys above the keyboard (centered) - Counting from the left!

How do I fix this?[/QUOTE]
You could take a look if the ACPI daemon catches these keys:
```
sudo tail -f /var/log/acpid
```
Then press the buttons and see if you get some new output from tail.

---

### Post by daller on 2005-11-24
[QUOTE=ranf]You could take a look if the ACPI daemon catches these keys:
```
sudo tail -f /var/log/acpid
```
Then press the buttons and see if you get some new output from tail.[/QUOTE]

I don't get any output concerning the keys...

---

### Post by ranf on 2005-11-24
[QUOTE=daller]I don't get any output concerning the keys...[/QUOTE]
That was just an idea. Sorry that I couldn't help.

---

### Post by simohell on 2005-11-29
Did you try running the perl-script I mentioned earlier?
Your series (ze4xxx) was mentioned in the project.

A bit more description how it worked for me:

1. I run the script, and my mute button started working. At this stage my 3 out of 5 "one-touch" keys didn't give any signal.

2. I run the key-settings I mentioned according to the readme-onetouch in the kernel module. After this the keys started giving output and were configurable through "Keyboard Shortcuts".

No I've got a script running the commands during startup.

---

### Post by daller on 2005-11-29
[QUOTE=simohell]Did you try running the perl-script I mentioned earlier?
Your series (ze4xxx) was mentioned in the project.

A bit more description how it worked for me:

1. I run the script, and my mute button started working. At this stage my 3 out of 5 "one-touch" keys didn't give any signal.

2. I run the key-settings I mentioned according to the readme-onetouch in the kernel module. After this the keys started giving output and were configurable through "Keyboard Shortcuts".

No I've got a script running the commands during startup.[/QUOTE]

How do you run "./omke.pl" on startup? (and the setkeycodes)

...and is there a reason why such a simple script is not incorporated in the breezy release?

---

### Post by simohell on 2005-11-30
[QUOTE=daller]How do you run "./omke.pl" on startup? (and the setkeycodes)
[/QUOTE]

I put the following script as well as omke.pl to /etc/init.d and linked it with with appropriate runlevel-directories.

```

# Use omke script to enable one-touch keys
#!/bin/sh
#
# enable the multimedia keys on HP notebooks


# Carry out specific functions when asked to by the system
case "$1" in
  start)
echo "Enabling one-touch keys..."
/etc/init.d/omke.pl -k 1
setkeycodes e070 123
setkeycodes e073 120
setkeycodes e071 116
;;
  stop)
echo "Disabling one-touch keys..."
/etc/init.d/omke.pl -k 0
;;
 *)
echo "Usage: /etc/init.d/onetouch {start|stop}"
exit 1
;;
esac

exit 0

```

---

### Post by daller on 2005-11-30
[QUOTE=simohell]I put the following script as well as omke.pl to /etc/init.d and linked it with with appropriate runlevel-directories.

```

# Use omke script to enable one-touch keys
#!/bin/sh
#
# enable the multimedia keys on HP notebooks


# Carry out specific functions when asked to by the system
case "$1" in
  start)
echo "Enabling one-touch keys..."
/etc/init.d/omke.pl -k 1
setkeycodes e070 123
setkeycodes e073 120
setkeycodes e071 116
;;
  stop)
echo "Disabling one-touch keys..."
/etc/init.d/omke.pl -k 0
;;
 *)
echo "Usage: /etc/init.d/onetouch {start|stop}"
exit 1
;;
esac

exit 0

```[/QUOTE]

What is the appropriate runlevel? - Haven't played around with this before...

---

### Post by simohell on 2005-12-27
Sorry for not replying sooner. My laptop broke down and I've been away from the forum for some weeks now...

There is a very simple way to do this: update-rc.d

For good and simple instructions a quote from: [Ubuntu Blog]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

[INDENT]Write a script. put it in the /etc/init.d/ directory.
Lets say you called it FOO. You then run

% update-rc.d FOO defaults

You can check out
% man update-rc.d for more information. It is a Debian utility to install scripts. The option &#8220;defaults&#8221; puts a link to start FOO in run levels 2, 3, 4 and 5. (and puts a link to stop FOO into 0, 1 and 6.)[/INDENT]

---

