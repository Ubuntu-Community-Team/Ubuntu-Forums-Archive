---
title: "Thinkpad volume and brightness buttons not connected to software"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by trevorv on 2007-06-10
In an attempt to make the "Access IBM" button on my ThinkPad run a program, I installed a little app called ``tpb''. I failed to get it working (which, to be honest, I'm not too fussed about). I have now uninstalled the app, but the volume and brightness buttons, whilst they do work, are not connected to software as they were before. This means, for example, I can have full volume in Totem, but no sound as I have turned down the volume using the hardware. Previously the two were one and the same.

If anyone could help in reconnecting the two I would be grateful, it's a much neater way of doing things.

Thank you.

---

### Post by DagMan on 2007-06-11
try reinstalling acpi-support 
I found once that reinstalling it didn't necisarily reinstall all the scripts and had to open up the deb, unpack it, unpack the archive inside called data, then copy everything to /etc/acpi

If that doesn't work, you might be able to tie those events to an action yourself doing 
tail -f /var/log/acpid | grep "received event" 
in  a terminal and then seeing if the key combos make something that can be tied to... any terminal output would be a good thing.
There's a good gentoo guide out there on acpi events if you want to google, I don't have the time myself at the moment.

---

### Post by trevorv on 2007-06-11
I've had a look around for how to solve this without very much luck, I've tried what you suggest and can't see anything too helpful online at the moment, although I'll keep looking.

The output of tail -f /var/log/acpid | grep "received event" is

```
[Mon Jun 11 13:04:34 2007] received event "ibm/hotkey HKEY 00000080 00001010"
[Mon Jun 11 13:04:56 2007] received event "ibm/hotkey HKEY 00000080 00001008"

```

Any suggestions what to do with that?

Thanks!

---

### Post by DagMan on 2007-06-11
in /etc/acpi/events there are a bunch of files and have a look at the ibm and lenevo ones. 
Ubuntu's aren't incredibly straightforward because they work with a number of other scripts for a bit of logic in working on more systems and not specific laptops.  You'de want to know how to control your volume and brightness at the command line and once you have that you can make a text file in /etc/acpi/events and where it says action= 
you send it to a shell script that does the action like you would at the command line.  The script typically are kept in /etc/acpi which is why I suggested downloading the .deb file and opening it and copying everything into /etc/acpi including subdirectories.  I'd still give that a shot if you haven't already.  You can open a .deb file with file-roller at the command line or archive manager from the menu.

Here's an example of a file on my drive from the acpi-support package, in /etc/acpi/events
```
# /etc/acpi/events/ibmsleepbtn
# Called when the user presses the sleep button

event=ibm/hotkey HKEY 00000080 00001004
action=/etc/acpi/sleepbtn.sh

```
The first two lines are comments.
The events line is similar to the output you got when you looked at it through the terminal.
The action is what is specified to happen when that occurs, when the sleep button is pressed, which is to run the script /etc/acpi/sleepbtn.sh

You need to put the event in there and associate it with a script that does something.
The script /etc/acpi/sleepbtn.sh does a lot and checks for lots of common laptops so it probably involves calling other scripts which in turn call other scripts as they are needed but for a specific laptop you would just need to have a very simple script for /etc/acpi/sleepbtn.sh that tells the computer to suspend.  In my case I had to edit this particular script to get it to work and as a result it is just one single line.

Things like brightness are modified at the command line by using the echo command to change a value in files located in or in subdirectories of /proc/acpi and sometimes the /sys filesytem.  I don't know where volume is typically done but looking at the related file in /etc/acpi might help you out.

I'm sorry I can't make it simpler.  I know that all sounds very complex and technical but unless I actually have your laptop I can't simplify it and have to be extremely general.  Hopefully someone who does have your laptop and knows how to configure it will find the thread.

I just now noticed something while in my package manager though... try reinstalling hotkey-setup it was marked for removal when I looked at what selecting tpb did.

Hopefully it's as simple as this
```
sudo apt-get install hotkey-setup
sudo apt-get install --reinstall acpi-support
```

---

### Post by trevorv on 2007-06-11
Thank you! Reinstalling hotkey-setup did the trick, and now everything's fine again :-)

Cheers for all your help!

---

