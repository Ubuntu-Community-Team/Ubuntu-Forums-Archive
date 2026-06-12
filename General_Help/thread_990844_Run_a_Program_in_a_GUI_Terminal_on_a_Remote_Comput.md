---
title: "Run a Program in a GUI Terminal on a Remote Computer?"
date: 2008-11-23
forum: General Help
---

### Post by Jose Catre-Vandis on 2008-11-23
Not sure if this can be done, but let me explain;

I have a home server running Hardy with full desktop.

I access the server using VNC with resumable sessions, usually leaving the session on. As the server is on all the time, I use Aria as a download manager during the night.

Now while it is not too much hassle to connect via VNC and then run a script on the server which then opens up a terminal on the server desktop showing aria's progress, I would like to run a command from my main PC, probably via ssh, that does the same thing. So end result would be, run a command on this PC that runs aria on the existing login on the server, so if I then check via VNC I can see the terminal window and aria's progress. The command should also log off from any ssh connection. Make sense? Can it be done? Also hoping to fill a few gaps in my knowledge along the way (hence the "stages" approach to this)

Progress so far:

a) I can ssh to the server and have passwordless sshing set up
```
 ssh user@server 
```
b) I know how to send info from one tty to another, e.g.
```
ls -l > /dev/pts/0 
```
c) I already use a command to start a VM on a remote server thatv does the logging on and off without intervention, but I don't understand how!
```
ssh 10.20.30.14 'VBoxVRDP -startvm "XP" >/media/Machines/"XP"/Logs/VBoxVRDP.log 2>&1 &'
```

Things I think I need to know:

1. How to get receiving tty to return to a command prompt after sending info?

2. How to send a command to another tty, as opposed to the output of a command run on the sending tty?

3. How to find the right tty to send information/commands to?

4. How to send a command via ssh to a remote PC both logging on and off automatically and without intervention?

5. How to open up a program running on an open GUI session from outside that session?

(found some useful info here to try out: [http://ubuntuforums.org/showthread.php?t=514054](http://ubuntuforums.org/showthread.php?t=514054))

I guess if not all can be achieved I can at least learn how to do this in a tty / screen.

I'll convert this to a howto once we are done!

---

### Post by Jose Catre-Vandis on 2008-12-22
Progress Report:

1. How to get receiving tty to return to a command prompt after sending info?

[COLOR="Sienna"]Not been able to figure this one out[/COLOR]

2. How to send a command to another tty, as opposed to the output of a command run on the sending tty?

[COLOR="Sienna"]This is about having a script or program that can be called from the receiving tty, rather than running a script on the sending tty[/COLOR]

3. How to find the right tty to send information/commands to?

[COLOR="Sienna"]Probably can be done with some clever scripting (I am not clever)[/COLOR]

4. How to send a command via ssh to a remote PC both logging on and off automatically and without intervention?

[COLOR="Sienna"]This is fairly straight forward using ssh, but you need to have passwordless access setup to smooth things along[/COLOR]
```
ssh user@targetpc /path/to/script/on/targetpc &
```

5. How to open up a program running on an open GUI session from outside that session?

[COLOR="Sienna"]This is all about knowing the location of the tty for the running x session. In my case its pts/1. You need to issue a command in your script on your target pc:[/COLOR]
```
export DISPLAY=localhost:1.0
```
[COLOR="Sienna"]for pts/0 the syntax would be[/COLOR]
```
export DISPLAY-localhost:0.0
```

[COLOR="Sienna"]Now I wanted to run aria2c which under normally circumstances opens up a terminal when you run it. But when trying to do this via ssh / separate tty it doesn't work so you have to issue the terminal -x command as well. Normal gui programs are OK with this. For example:
To run aria2c the command needs to be:[/COLOR]
```
gnome-terminal -x aria2c
```
[COLOR="Sienna"]while to run gedit:[/COLOR]
```
gedit
```


[COLOR="Sienna"]So if we put it all together now

Create a script on your host pc that opens up the ssh channel and demands a script to be run on the target pc[/COLOR]
```
#!/bin/bash
ssh user@targetpc /path/to/script_or_program/on/targetpc &
```
[COLOR="Sienna"]Create a script to run the program in your x session on a different tty:[/COLOR]
```
#!/bin/bash
export DISPLAY=localhost:1.0
gnome-terminal -x aria2c -i urls -j 1 -s 1 -d /home/joe &
```

[COLOR="Sienna"]To close down aria2c, you need a similar setup but the script on the targetpc looks something like this:[/COLOR]
```
#!/bin/bash
export DISPLAY=localhost:1.0
killall aria2c

```

[COLOR="Sienna"]This works but it is not very intuitive, and requires some prior knowledge about ttys on the target machine. Also there is no feedback, so you do not know if the command worked (unless you vnc to the target pc to see, but then that kind of defeats the object).[/COLOR]

---

