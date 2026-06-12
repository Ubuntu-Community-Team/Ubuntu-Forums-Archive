---
title: "No Sound in UT2004&quot;open /dev/[sound/]dsp: Device or resource busy&quot;"
date: 2008-08-13
forum: General Help
---

### Post by equity on 2008-08-13
I searched the whole internet for a solution. I do not get sound to work in UT2004. I use Gnome so "killall artsd" does not work for me (since artsd is a KDE program). "killall esd" gives me "esd: no process killed". When I start UT2004 from the command line "open /dev/[sound/]dsp: Device or resource busy" is the only output.

Any suggestions?

---

### Post by Drezliok on 2009-10-31
Same here.

---

### Post by Demonizer on 2009-11-21
I fixed it.
I don't know what exactly solved the problem but what I did was running Nautilus as root and changing /usr/local/games/ut2004/ut2004 permissions
to my userName and rebooted my machine. now when I run it not in terminal(desktop icon) it is running great.

wait... no i didnt.. >:( looks like every it decides when to give me sound.

---

### Post by hibob on 2010-08-04
Are you running Amarok or some other music player in the background?
I had sound until I started using it. Now I'm not sure what's going on but I have the same problem.

---

### Post by kgolick on 2010-10-27
Hi, for me it worked with: 
padsp /home/myhomefolder/ut2004/ut2004

I'm running Ubuntu 10.10

Hope it will help other old games fans

---

### Post by WaroDaBeast on 2010-10-27
Dude, you're my savior! :D

Did

```
padsp /usr/local/games/ut2004/ut2004
```

and guess what? I gots sound now! Thanks a thousand times! :D

---

### Post by gerowen on 2010-12-12
Tried this on mine and I get:
```

exec: 88: /home/marcus/Downloads/ut2k4: Permission denied

```
Running the command as root doesn't make a difference.

---

### Post by gerowen on 2010-12-12
This fixed my sound:
```

ln -sfn /usr/lib/libopenal.so /home/marcus/Downloads/ut2k4/System/openal.so

```

---

### Post by Nospoonzz on 2011-04-14
Old game but still TONS OF FUN !!!!!!!!!!  Thanks a billion times !!!!!!!! this fixed my no sound issues on 10.10 64bit Ubuntu. Now I am 100% FREE FROM WINDOWS !!!!!!!!!!!!!!!!!!!:popcorn::):):)






> **WaroDaBeast said:**
> Dude, you're my savior! :D

Did

```
padsp /usr/local/games/ut2004/ut2004
```and guess what? I gots sound now! Thanks a thousand times! :D

---

### Post by travlemon on 2011-09-30
> **kgolick said:**
> Hi, for me it worked with: 
padsp /home/myhomefolder/ut2004/ut2004

I'm running Ubuntu 10.10

Hope it will help other old games fans


Thanks so much!  This worked for me too, on Kubuntu 11.04.  I saw this command mentioned on another thread, but they didn't mention the syntax, and I was unsure of how it was supposed to work. I installed the game as root, and installed it to the default directory, so my command looks like this:

```
padsp /usr/local/games/ut2004/ut2004
```

Now I just have to change the shortcut to reflect this command, thanks again!

---

### Post by not12listen on 2011-11-15
i got the exact same error...  going to test the above steps...  i'll repost if it works or not.

----

well, i've tried both steps listed.  here is the result:

open /dev/[sound/]dsp: No such file or directory


i also tried copying the 'libopenal.so.1' files from my /usr/lib folder into the System folder within my ut2004 folder.

at this point, i am basically throwing spaghetti against the wall.  the audio does work everywhere else within Kubuntu 11.10 (64bit).  so, i'm very puzzled why it is not working in UT2004. :/

any help would be greatly appreciated.

---

### Post by not12listen on 2011-11-20
i did get sound working.

from console:
padsp ./ut2004-bin-linux-amd64


the problem is, after you exit the game, if you go back into the game without using padsp, there will be no sound.  so, you have to 'padsp' each time.

i did some other steps as well, so i'm going to remove UT2004 from my system and try this again from scratch.  i want to see if just installing UT2004 and doing the 'padsp' works or not.

---

### Post by blablubb1234 on 2012-07-13
gerowen's answer does the trick:

Find your existing libopenal.so by:

```
locate libopenal.so

``` which should give You something similar to:
```

/usr/lib/i386-linux-gnu/libopenal.so.1
/usr/lib/i386-linux-gnu/libopenal.so.1.13.0
/usr/lib/x86_64-linux-gnu/libopenal.so
/usr/lib/x86_64-linux-gnu/libopenal.so.1
/usr/lib/x86_64-linux-gnu/libopenal.so.1.13.0
```Find the openal.so UT tries to open by:
```
locate openal.so
```which again gives You something similar to:
```
/usr/lib/i386-linux-gnu/libopenal.so.1
/usr/lib/i386-linux-gnu/libopenal.so.1.13.0
/usr/lib/x86_64-linux-gnu/libopenal.so
/usr/lib/x86_64-linux-gnu/libopenal.so.1
/usr/lib/x86_64-linux-gnu/libopenal.so.1.13.0
/usr/local/games/ut2004/System/openal.so
```In the last line You see the file you have to backup:
```
sudo mv /usr/local/games/ut2004/System/openal.so openal.so.bak
```Now link Your libopenal.so to openal.so in Your UT's System-Folder (may vary due to different paths, but that should be easy to find out):
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libopenal.so /usr/local/games/ut2004/System/openal.so
```Have LOUD fun with this awesome oldschool game! :)

---

