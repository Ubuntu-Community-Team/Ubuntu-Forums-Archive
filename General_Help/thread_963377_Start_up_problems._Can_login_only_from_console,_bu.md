---
title: "Start up problems. Can login only from console, but then?"
date: 2008-10-30
forum: General Help
---

### Post by federicodemaria on 2008-10-30
I can't login from the graphic page, but i can from the Console. 
But then i don't know what to do 

username@systemaname:~$ 

what should i do? Is there any command that would allow me, once i have logged in, to pass from Console to my computer?

thanx 
f

What is the problem?
Can't start. Keeps asking me password in loop
I have Kubuntu.

1. It boots properly

2. Comes the graphics that asks me password.

3. I enter the correct password

4. Black screen comes

5. Asking me the password again.

It goes in loop from 2. to 5.
Entering in recovering mode, i tried to add a user (adduser). Apparently nothing has changed. Still asking the password of the previous user. Don't know what to do and nobody answered me in the forums. i found another similar post of 6 months ago, and nobody answered.

---

### Post by small_sammy on 2008-10-30
Well hi, 

I dunno if this will solve your problem...
Once logged in from the console, the command to go into graphic mode is: startx

But before running the command you must be sure that the X server is not running or else it will complain about already running and wont start. Try booting to a different runlevel, or kill the X server.. :)

---

### Post by rakris on 2008-10-30
ctrl+alt+F7 to go back to Graphic ( if it works)

---

### Post by federicodemaria on 2008-10-30
with Ctrl Alt F7 it does not work, while with startx comand it gives me this

(**)RADEON(0): RADEONRestoreMode()
...
(**)RADEON(0): RADEONRIC loseScreen
FreeFontPath: FPE"/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

username@systemname:~$

Help! :->

thanx, 
fede

---

### Post by small_sammy on 2008-10-30
Look here

[http://www.linuxquestions.org/questions/ubuntu-63/cant-startx-freefontpath-fpe-log-message-629072/](http://www.linuxquestions.org/questions/ubuntu-63/cant-startx-freefontpath-fpe-log-message-629072/)

---

### Post by federicodemaria on 2008-10-30
i tried, but...


$ sudo mkdir /etc/dbus-1/ session.d 

mkdir: no se puede crear el directorio 'etc/dbus-1/' : el fichero ya existe

username@systemname:~$


(((in english:
mkdir: impossible to create directory 'etc/dbus-1/': the file already exists)))

And now?

thanx
f

ohi ohi ohi...

The sentence in spanish means: "impossible to create temporal file for this document. there is no free space in the device" 


username@systemname:~$ startx
hostname: unknown host
/usr/bin/startx: line 132: no se puede crear archivo temporal para este documento: no hay espacio libre en el dispositivo 
/usr/bin/startx: line 150: no se puede crear archivo temporal para este documento: no hay espacio libre en el dispositivo 
/usr/bin/startx: line 150: no se puede crear archivo temporal para este documento: no hay espacio libre en el dispositivo 


Fatal server error:
Server is already active for display 0
         If this server is no longer running, remove /tmp/.X0-lock
and start again 

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error. 
username@systemname:~$



Could have been this caused by the fact that there is no free space on my hard disk. it could be that is full.
What can i do? 

I removed /tmp/.X0-lock 
following 

[www.linuxforums.org/forum/suse-linux-help/9043-user-lost-x-window-priviledge-why.html+remove+/tmp/.X0-lock&hl=ca&ct=clnk&cd=1&gl=es&client=firefox-a](www.linuxforums.org/forum/suse-linux-help/9043-user-lost-x-window-priviledge-why.html+remove+/tmp/.X0-lock&hl=ca&ct=clnk&cd=1&gl=es&client=firefox-a)

getting the same result


Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.



thanx
fede

NB On my laptop i have Kubuntu and Windows. I'm trying to pass form W to L, definitively. Just having few problems

---

### Post by platypuss72 on 2008-11-04
hi there 

i have the same problems .... just loop loop 

so have looked through lots off help and done wot said in this posting ... an still problems ..

so i had enough .. after 5 hrs trying to fix i reinstalled ...

all good and working .. then i reinstalled my backed up home folder ... NOW back to start ... :-( 

I removed /tmp/.X0-lock and this got me past the login loop BUT now i just get a terminal window with prompt ..

if i startx 

"x: user not authorized to run the x server, aborting,
could not get a file desciptor referring to the console"

and back to prompt .... :-( 

please help 

cheers luke

---

### Post by aethernaut on 2008-11-30
::bump::

Same issue here!

You can work around the problem (kinda sorta) by selecting 'console login' from the drop down menu at the login screen.  Enter username and password and then type 'sudo startx' at the command prompt and you should have a desktop environment again.

you can check the amount of disk usage by running:

df -h

which should show you how much space you have left and where the largest files are.

In my case this all seems to have started when I deleted the contents of my /tmp/ directory after getting a warning from KDE that I was low on disk space (I'm actually running off of a USB stick so I only have 4 gigs total).  /tmp/ had eaten up an absurd amount of space and I went from 95% to 68% full just by cleaning it out and running apt-get autoclean.

Everything seemed to be fine when I did so; but the very next day (today!) I'm stuck in the same login-loop as everyone else in this thread o_O

df -h still shows that I have over 30% of the space left on the USB stick and there haven't been any more warnings ... but a full or near-full disk seems to be what most of us have in common?

---

### Post by schnook9 on 2009-02-04
same problem here.  I mysteriously ran out of room on my drive (fine one day, full the next) and could not find the offending files.  I managed to get it to  boot and started removing programs until I had enuf space.  Then of course no kde starting anymore.

I tried uninstalling and re-installing kde, I tried re-configure, and finally I tried upgrading to kde 4.2  that actually managed to get me to the login screen, but once I login, it just brings up a blank screen with the background image loaded.  

startx from the console does even less with just a grey screen loaded.  I am fresh out of ideas.  Oh, and today my network settings decided to undefine themselves.  I had define a static IP, dns, and a gateway route, but packets are being dropped like crazy and I can't keep a connection going.

quite the craziness!  ](*,)

hopefully this added something to troubleshooting and we can figure this one out
thanks!

---

