---
title: "[SOLVED] doubts over &amp;quot;/dev/pts&amp;quot;"
date: 2008-07-11
forum: General Help
---

### Post by dexter.deepak on 2008-07-11
it was only today that i came to know that pts refers to the terminal i use on my ubuntu system.
i have now 2 doubts:
1. why is the terminal a part of the /dev , when it doesnt refer to any device ? if it so because it gives us a visual console, then "every" visual program should be there in /dev...
2. how are these files dynamically generated ? how is a new file created every time i open a terminal...although i dont have "write" permission in /dev ?
3. since the no. of 'tty's are limited, is there a chance that no. of pts are also limited ?

---

### Post by Vivaldi Gloria on 2008-07-11
> 
why is the terminal a part of the /dev , when it doesnt refer to any device ? if it so because it gives us a visual console, then "every" visual program should be there in /dev...

Sometimes we say "terminal" when we actually mean "terminal emulator" because it's shorter to say.

Consider a university mainframe. When I sit in a computer lab and connect to my account in that mainframe using one of the lab computers I can run commands on that mainframe. I can say to that mainframe "compute this and report back". In this example the lab computer is a terminal, it does nothing other than connecting to the mainframe. It's dumb in the sense than all it does is to send commands to the mainframe and display the result.

Back in the time, there were a lot of terminals such as VT100, VT220, VT320, IBM 3270/8/9/E, IBM 5250/3179, Data General D211, Hewlett Packard HP700/92, Sperry/Unisys 2000-series UTS60, QNX, etc. etc. etc. These were dumb terminals.

So a terminal is a device you use to connect to a unix (linux) machine. A lot of people can connect at the same time using different terminals. 

When you start gnome-terminal (for example) in your desktop computer then you are emulating a terminal. You can do with it the same things you can do with a dumb terminal connected remotely. Actually, you can specify the type of terminal you want to emulate. For example

```
export TERM=vt100
```

So it's clear by now that a terminal is a device and a program like gnome-terminal emulates it. Nice thing with the terminal emulators is that you can have as many virtual terminals as you want on the same hardware.

Now when you login you can use "who" to find out about terminal you are logged into.

```
vivaldi@narval:~$ who
vivaldi tty7         2008-07-11 12:08 (:0)
vivaldi pts/0        2008-07-11 13:06 (:0.0)
```

As you can see from the output i am using tty7 and pts/0. There are other possible terminal devices as well. Here tty7 is the terminal we are logged in to (which runs gnome) and pts/0 is the gnome-terminal emulator window.

If I press Ctrl+Alt+F3 and also log in there then this what I get:

```
vivaldi@narval:~$ who
vivaldi tty3         2008-07-11 23:42
vivaldi tty7         2008-07-11 12:08 (:0)
vivaldi pts/0        2008-07-11 13:06 (:0.0)
```


> how are these files dynamically generated ? how is a new file created every time i open a terminal...although i dont have "write" permission in /dev ?

The terminals are already generated in /dev during boot. The command agetty (getty) opens tty1-tty6. See "man getty" for more info. During boot upstart init uses the tty1-tty6 files in the /etc/event.d folder. When you do ctrl+alt+F<number> you just connect to one of them. Since you don't start them your write permissions in /dev is a non-issue.


> since the no. of 'tty's are limited

The number of open tty terminals is only limited in the start of the system by convention. You can change it to whatever you want. If you want start a million.


> is there a chance that no. of pts are also limited ?

No. I started 12 gnome-terminals (without closing any of them) and this is what I get:

```
vivaldi@narval:~$ who
vivaldi tty3         2008-07-11 23:42
vivaldi tty7         2008-07-11 12:08 (:0)
vivaldi pts/0        2008-07-11 13:06 (:0.0)
vivaldi pts/1        2008-07-12 01:18 (:0.0)
vivaldi pts/2        2008-07-12 01:18 (:0.0)
vivaldi pts/3        2008-07-12 01:18 (:0.0)
vivaldi pts/4        2008-07-12 01:18 (:0.0)
vivaldi pts/5        2008-07-12 01:18 (:0.0)
vivaldi pts/6        2008-07-12 01:18 (:0.0)
vivaldi pts/7        2008-07-12 01:18 (:0.0)
vivaldi pts/8        2008-07-12 01:18 (:0.0)
vivaldi pts/9        2008-07-12 01:18 (:0.0)
vivaldi pts/10       2008-07-12 01:18 (:0.0)
vivaldi pts/11       2008-07-12 01:18 (:0.0)
```

---

### Post by dexter.deepak on 2008-07-12
thanks a lot !!:KS
yet your explanation has invoked some new doubts.. 
1. i have a doubt over difference b/w dumb terminal and terminal emulator.
with reference to the mainframe example you gave,tell me if i am right:
the lab computers are all dumb , and its only the gnome-terminal i am opening is an emulator. the default tty1-7 are "real" terminals.

2.> Here tty7 is terminal typewriter (keyboard) and pts/0 is window device (screen). 

why do you say tty to be just keyboard ? it also gives visual interface (screen) by echoing what we type..like that of pts.

---

### Post by Vivaldi Gloria on 2008-07-12
> **dexter.deepak said:**
> 1. i have a doubt over difference b/w dumb terminal and terminal emulator. with reference to the mainframe example you gave,tell me if i am right: the lab computers are all dumb , and its only the gnome-terminal i am opening is an emulator. the default tty1-7 are "real" terminals.

If I use a computer to connect to a mainfame then is the computer dumb? Not really. You can compute on that computer as well. So I wouldn't call that computer a dumb terminal. But it's a terminal device of the mainframe anyway. On the other hand, if that computer did nothing other than connecting and running code on the mainframe then I can say that it behaves like a dumb terminal. To be honest, this "dumb" usage is a bit unclear and I'd rather not used it at all.

About terminal emulators. Here's a defn from wikipedia:

> A terminal emulator is a program that emulates a "dumb" video terminal within some other display architecture. A terminal emulator inside a graphical user interface is often called a terminal window. 

The first definition pretty much says that everything we use nowadays is actually a terminal emulator. Let me quote from Text-Terminal-HOWTO (links are at the end):

> Today, real terminals are becoming rarities and most people that use terminals use a personal computer to emulate a terminal. Almost everyone who uses Linux uses terminal emulation. When you are not using an X Window GUI at a Linux PC, you are likely using a text interface (virtual terminal). It's also called a command line interface. In X Window one can also get a command line interface using one or more terminal windows by using an x-terminal-emulator with names such as xterm, gnome-terminal, or konsole (KDE). All these use software to emulate a real terminal.

A real text-terminal is different from a monitor or x-terminal-emulator because the simple character images that get displayed on the text-terminal are stored right inside the terminal in it's memory. For a monitor or x-terminal-emulator, the images are stored in the video card of the PC and/or in the PC's memory itself. The text-terminal's keyboard plugs into the the terminal and is part of the terminal while a PC's keyboard plugs into the computer.

For a monitor, the video images are sent by a short cable running from the video card to the monitor while for a text-terminal there is a bi-directional flow of character bytes in a long cable between the computer's serial port and the PC it's connected to. Most text terminals do not have mice.


Now let us look at how terminal devices are named. TTY is short for Teletype(writer). I guess those were the things unix was first run from. Today TTY refers to the screen (or window, in the case of an emulator), keyboard and some other human interaction devices. There are different types of TTY devices: tty, pts, ptyp, ttyp etc. It depends on how you are connected to the mainframe and which system the mainframe runs. I don't know the differences between them exactly. Most of these are archaic names and sometimes things which you don't expext to be a terminal device turns out to be one. For example, a serial port is a terminal device! Let me quote from Text-Terminal-HOWTO again:

> The computer considers each serial port to be a "device". It's sometimes called a terminal device since at one time terminals were the most common use for a serial port. For each such serial port there is a special file in the /dev (device) directory. /dev/ttyS0) is the special file for the serial port known as COM1 in the DOS/Windows world. 

So don't bother understanding what and why of these terminal device names. They are just old conventions still living on. Also different systems disagree on names. What linux calls pts is pty in BSD if I remember correctly. But, as an experiment, when you login to a different system (locally or remotely, say by ssh or rdp) check out what names you get with "who".

Now let's also look at /dev/tty. I opened a gnome-terminal and I also logged in from ctrl+alt+F3:


```
vivaldi@narval:~$ who
vivaldi tty3         2008-07-11 23:42
vivaldi tty7         2008-07-11 12:08 (:0)
vivaldi pts/0        2008-07-11 13:06 (:0.0)
```

The gnome session I'm logged in is via the terminal device /dev/tty7. The gnome-terminal is using the terminal device /dev/pts/0 and the login in ctrl+alt+F3 uses /dev/tty3.

What are the differences between the following commands?

```
echo "Hello" > /dev/tty3
echo "Hello" > /dev/pts/0
echo "Hello" > /dev/tty
```

For the first two commands, it doesn't make any difference whether I use them in gnome-terminal or in ctrl+alt+F3 terminal.

The first one will write hello to only the ctrl+alt+F3 terminal. Since the name of the window of the gnome-terminal is pts/0 the second command will only write hello to the gnome-terminal.

Now /dev/tty is just a pseudonym for "the terminal device the user is working on". This is one of those smart unix things. Instead of knowing the exact name of the terminal you can just echo to /dev/tty and the good old unix will find the right place to write hello. This is very useful, especially in scripts

Thus if I execute the 3rd command in ctrl+alt+F3 terminal then I see hello there. If I execute the 3rd command in the gnome-terminal then I see the result there.

To sup up, there are hundreds of terminal devices in /dev. Not all are open though. As I said in the last post the files in /etc/events.d starts some tty's using (a)getty. From man agetty:

> agetty  opens  a  tty  port,  prompts  for  a login name and invokes the /bin/login command. 


> 2. why do you say tty to be just keyboard ? it also gives visual interface (screen) by echoing what we type..like that of pts.

You are right. I didn't mean to say that. tty7 is the terminal we are logged in to (which runs gnome) and pts/0 is the gnome-terminal emulator window on the screen. I'll correct this in the above post.


Finally, here are tldp and the Text-Terminal-HOWTO links:

[http://tldp.org/](http://tldp.org/)

[http://tldp.org/HOWTO/Text-Terminal-HOWTO.html](http://tldp.org/HOWTO/Text-Terminal-HOWTO.html)

Also available as pdf:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Text-Terminal-HOWTO.pdf](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Text-Terminal-HOWTO.pdf)

---

### Post by dexter.deepak on 2008-07-12
again a lot of thanks + some more queries..actually i you have made this topic pretty interesting to me .:) . i am just about to go through the links you provided.

 here's my part of the experiment you did above:
```
dpak@dpak-server:~$ who
dpak     tty7         2008-07-12 13:25 (:0)
dpak     pts/0        2008-07-12 20:51 (:0.0)
dpak@dpak-server:~$ echo "hi" > /dev/pts/0
hi
dpak@dpak-server:~$ echo "hi" > /dev/tty7
bash: /dev/tty7: Permission denied
dpak@dpak-server:~$ sudo bash
root@dpak-server:~# echo "hi" > /dev/tty7
root@dpak-server:~# echo "hi" > /dev/tty
hi

```

and here are my queries:
1. why do i get a permission denied message for tty7, when I am actually working on it !!
2. after being root, i am able to write to tty7 , but where does the o/p go ?
3. since i can echo text to other terminals, i feel i can also log on to other terminals while residing on my tty7 ....but i am unable to do it. 
4. i think i got some point...isnt this the same mechanism (what i am trying in point 3) used for remote logins ?

---

### Post by Vivaldi Gloria on 2008-07-12
> 
since i can echo text to other terminals, i feel i can also log on to other terminals while residing on my tty7 ....but i am unable to do it.

The key combinations from ctrl+alt+F1 to ctrl+alt+F6 are shortcuts for tty1 upto tty6. For example, press ctrl+alt+F4 to login to tty4. To return to gnome press ctrl+alt+F7. 


> why do i get a permission denied message for tty7, when I am actually working on it !!

Actually you were not working on it. You were typing in the gnome-terminal (or whichever terminal window you are using) which was pts/0. You are trying to echo from pts/0 to tty7. Now tty7 is running X (and gnome) and I guess it is not listening in its default configuration. I have no idea as to how you can log echos that tty7 receives.

To test echoing to other terminals I suggest you do the following experiment:

1. Open a gnome-terminal (pts/0)
2. Open another gnome-terminal (pts/1) side by side to the first.
3. Press ctrl+alt+F4 and login with you username (tty4). Return to gnome by pressing ctrl+alt+F7.
4. Then try the following commands from gnome-terminal pts/0 and then from gnome-terminal pts/1 and then from ctrl+alt+F4:

```
who
echo "hello_to_pts_0" > /dev/pts/0
echo "hello_to_pts_1" > /dev/pts/1
echo "hello_to_tty_4" > /dev/tty4
echo "hello_to_here" > /dev/tty
```

After the fourth command check tty4 by pressing ctrl+alt+F4 and then return back using ctrl+alt+F7.


> after being root, i am able to write to tty7 , but where does the o/p go ?


I don't understand your question. What is o/p? Can you clarify? Don't forget that tty7 is the one gnome runs in. When you write in the gnome-terminal that is pts/0. When you open another gnome-terminal then that is pts/1.


> i think i got some point...isnt this the same mechanism (what i am trying in point 3) used for remote logins ?

Yes. I can connect remotely to my university using ssh. Now when in the ssh session I can run "who" to find out about users and which terminal devices they are connected to. Actually you can use the command "tty" to find out which terminal you are using. I tried it:

```
vivaldi@external>ssh beluga
vivaldi@beluga's password: 

Last login: Sat Jul 12 2008 09:39:32 from blue.cc.metu.edu.tr

*******************************************************************************
*  Welcome to AIX Version 5.2!                                                *
*                                                                             *
*  Please see the README file in /usr/lpp/bos for information pertinent to    *
*  this release of the AIX Operating System.                                  *
*******************************************************************************
 
You have mail.
[YOU HAVE NEW MAIL]

TERM = (vt100) 

$ who
e1cnab1     pts/0       Jul 10 07:27     (blue.cc.metu.edu.tr)
e1cfa82     pts/2       Jul 12 19:43     (blue.cc.metu.edu.tr)
root        pts/5       Jul 11 16:57     (abacus.cc.metu.edu.tr)
vivaldi     pts/6       Jul 12 19:44     (blue.cc.metu.edu.tr)
akta5       pts/23      Jul 11 12:00     (aktann.dopf.metu.edu.tr)
$   
$ tty
/dev/pts/6
$ 
$ exit
Connection to beluga closed.
```

---

### Post by dexter.deepak on 2008-07-13
well, you misunderstood me...i know how to switch between tty1-7 , i was asking about, how can i log on to tty4 without "actually" going to tty4..that is ,i want to issue some commands from a gnome-terminal on tty7 , and that command should help me log on to tty4. here's what i tried :
```
sudo bash
echo "dpak" > /dev/tty4

```
this way i can see the following screen on tty4:
```

dpak-server login:dpak

```
since i had to issue a line change (or press return) i started afresh,
```

echo "dpak\n" > /dev/tty4

```
but unluckily this is what i see on tty4:
```
dpak-server login:dpak\n
```

i hope i am clear enough...in short, i want to "run" commands on another terminal while residing on my terminal...and since i can echo my stuff on other terminal, i think i "should" be able to execute the too !!

---

### Post by Vivaldi Gloria on 2008-07-13
OK. Now I understand your questions better. 

**1)** About echo. Things like \n, \t, etc. only work with the option -e.

```
echo -e "hello\t mate.\nHow are you?"
```

**2)** When I try something like

```
echo "test 1-2-3" > /dev/tty3
```

then I cannot get a new prompt line automatically in tty3. I have to press return to get one. I don't know a way around this.

**3)** I don't know how you can login to tty3 (say) from gnome-terminal. On the other hand I know a way to start the computer with you already logged in to tty3. You can do it with modifiying /etc/events.d/tty3 file. I can look into it if you want.

**4)** But once you login to tty3 you can send any command's output to tty3 with

```
command > /dev/tty3
```

For example

```
date > /dev/tty3
factor 333864 > /dev/tty3
cal -3 > /dev/tty3

```

What ">" does is to direct the standard output to a file. For example to save a list of all packages installed in your computer you can do this:

```
dpkg --get-selections > packages.txt
```

The nice thing with linux is that every device is represented as a file in /dev. So to send the standard output to tty3 just use "> /dev/tty3" after the command.

---

### Post by dexter.deepak on 2008-07-13
thanks for reminding about the option -e for echo.
i totally understand the redirection you are doing here...but what i want here is not to direct the "output of a command" on other terminal; what i want is "execution of a command" on the other terminal.
eg.
date > /dev/tty4 , calculates date on tty7 and then sends the output to tty4 , but i want to have date calculated on tty4.

seems its not possible:( 
i thought all this "imagining" the remote logins where we can login from other terminals too...so i thought it is also possible to log on the other terminal on the same system.

...and i just had a look in the /etc/event.d folder ...its really interesting :) ; i will try the step3 of your above post, if i fail i would take your help then.

---

### Post by Vivaldi Gloria on 2008-07-13
If you want to be automatically logged in (say) tty3 rather than entering your username & password after ctrl+alt+F3 follow the following steps:


**1)** Edit the file 

```
/etc/login.defs
```

and change the line

```
# NO_PASSWORD_CONSOLE
```

to

```
NO_PASSWORD_CONSOLE tty1:tty2:tty3:tty4:tty5:tty6
```


**2)** Create a file 

```
/usr/sbin/autologin 
```

which is as follows:

```
#! /bin/bash
exec login <your_username>
```

Replace <your_username> with the name of the user you want to login automatically. Then make that file executable via

```
sudo chmod a+x /usr/sbin/autologin
```


**3)** Edit the file 

```
/etc/event.d/tty3 
```

and change the line

```
exec /sbin/getty 38400 tty3
```

to

```
exec /sbin/getty -l /usr/sbin/autologin -n 38400 tty3
```


That's it. Next time you start your computer everthing should look exactly the same except fot he fact that when you press ctrl+alt+F3 you'll see that you're already logged in there.

The only problem is that I haven't tried this yet!! My computer has to stay on for the time being so I cannot restart it.

---

### Post by Vivaldi Gloria on 2008-07-13
> **dexter.deepak said:**
> what i want here is not to direct the "output of a command" on other terminal; what i want is "execution of a command" on the other terminal. .... i thought all this "imagining" the remote logins where we can login from other terminals too...so i thought it is also possible to log on the other terminal on the same system.

I don't know how to this. I'll try to find out about it. You may not be able to start commands in an already open tty but may be it's possible to open a new tty with a command of choice running in it. 

But I don't even know how one can start a new tty from gnome-terminal. Try this in a gnome-terminal:

```
getty 38400 /dev/tty9
```

Now press ctrl+alt+F9. You'll see that tty9 is opened but login does not work. It seems that getty (more precisely the login command) works when called during boot but you run into the problem above when you try to open a new tty in gnome-terminal.

---

