---
title: "UT2004 (Error: Audio initialization failed)"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by The-Don on 2009-06-23
Howdy,
I've scanned all of the Internets but I cannot find a solution that works for me. In the logfile at the end I'm getting:

_***Error: Audio initialization failed***_


[LIST]
[*]Latest UT version of course (megapack).
[*]Latest 9.04 Jaunty of course.
[*]OpenAL is the only option in UT2004.
[*]I can listen to mp3's, dvd's, YouTube...just not UT2004.
[*]It was working last night :\
[/LIST]
Thanks in advance guys.

P.S.
A lot of symlink talking...assume I don't know how to do that :\

---

### Post by izizzle on 2009-06-23
Do you have OpenAL installed? 

```
sudo apt-get install libopenal1
```

---

### Post by The-Don on 2009-06-23
```
<username>@Computer:~$ sudo apt-get install libopenal1
[sudo] password for <username>: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=DarkOrchid]libopenal1 is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
<username>@Computer:~$ 
```

:(

---

### Post by The-Don on 2009-06-24
_**FIXED**_
 :popcorn:

```
sudo nautilis
```
Copy libopenal.so.1.4.272 from /usr/lib to /usr/local/games/ut2004/System
Rename libopenal.so.1.4.272 to openal.so

Sorted :D

---

### Post by sam99969 on 2011-03-25
> **The-Don said:**
> _**FIXED**_
 :popcorn:

```
sudo nautilis
```Copy libopenal.so.1.4.272 from /usr/lib to /usr/local/games/ut2004/System
Rename libopenal.so.1.4.272 to openal.so

Sorted :D

Now the final numbers are other but it works!! Thank you

---

### Post by mgmiller on 2012-05-06
In 64 bit Precise (12.04)  the files have moved around and changed their versions.

In 64 bit Precise (12.04) You need to fix the openal.so symlink in ~/ut2004/System
you need to _**link to the 32 bit version**_ which is now in: /usr/lib/i386-linux-gnu/libopenal.so.1.1.13.0
So:
```
gksudo nautilus
```
to get a root browser and navigate to: /usr/lib/i386-linux-gnu/libopenal.so.1.1.13.0 
Right click it and Make Link.  
Move the link to ~/ut2004/System
Rename the link openal.so

To finish getting the sound working, edit ~/.UT2004/system/UT2004.ini

Go to the area:
[ALAudio.ALAudioSubsystem]

and change this:
UseEAX=False
Use3DSound=False
UseDefaultDriver=True
CompatibilityMode=False

To this:
UseEAX=True
Use3DSound=False
UseDefaultDriver=False
CompatibilityMode=False


Also (to fix scratchy sound) change:
 channels=32

to:
channels=72

save the file and sound should now be good.

:guitar:

---

