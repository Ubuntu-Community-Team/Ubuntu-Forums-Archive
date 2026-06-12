---
title: "[SOLVED] Unix &amp;quot;at&amp;quot; command usage"
date: 2008-08-06
forum: General Help
---

### Post by GammaPoint on 2008-08-06
I was hoping to use the 'at' command to play music at a certain time. This won't be a regular thing so I don't want to use cron. But I'm not sure how to do it. This is what I tried...

```
mplayer [song] | at 07:20 PM
```

but that just played the song immediately (and it wasn't 7:20). I couldn't find many examples online. Anyone know the correct syntax to do this simple thing that I want?

---

### Post by estyles on 2008-08-06
I've never used the command, so I don't know.  But have you tried:```
man at
```

---

### Post by iaculallad on 2008-08-06
> **GammaPoint said:**
> I was hoping to use the 'at' command to play music at a certain time. This won't be a regular thing so I don't want to use cron. But I'm not sure how to do it. This is what I tried...

```
mplayer [song] | at 07:20 PM
```

but that just played the song immediately (and it wasn't 7:20). I couldn't find many examples online. Anyone know the correct syntax to do this simple thing that I want?

Instead of using 07:20 PM, try:

```
mplayer [song] | at 17:20
```

> 17:20 = 7:20 PM

---

### Post by GammaPoint on 2008-08-06
> **estyles said:**
> I've never used the command, so I don't know.  But have you tried:```
man at
```

Yes, I looked there. But I didn't see anything that was similar to what I was trying to do. They don't have any examples and trying various things wasn't working for me. 

Using 19:20 (not 17:20 ;) ) doesn't work either. 'at' is supposed to be able to recognize AM and PM also.

---

### Post by estyles on 2008-08-06
> **GammaPoint said:**
> Yes, I looked there.

Yeah, you got me there.  Man pages tend to never have examples, which I think is a definite failing with how people write man pages.  One line of example is worth a hundred lines of explanation.

---

### Post by mikjp on 2008-08-06
At reads by default standard input, so try this:

```
at 17:20
warning: commands will be executed using /bin/sh
at> mplayer [song]
CTRL+D
```


Also this should work:

```
echo "mplayer [song]" | at 17:20
```

Greetings,

Mikko

---

### Post by mb_webguy on 2008-08-07
I've been playing around with the "at" command for the last few minutes, and I'm having the same problem as GammaPoint, I think.

The following command will work just fine, deleting the file "cmd.txt" one minute (technically when the next minute ticks over, between 1 and 60 seconds) after I enter the command.```
matt@the-tardis:~$ at now + 1 minute
warning: commands will be executed using /bin/sh
at> rm cmd.txt
at> <EOT>
job 12 at Wed Aug  6 23:13:00 2008
```
The following command, however, will do nothing.```
matt@the-tardis:~$ at now + 1 minute
warning: commands will be executed using /bin/sh
at> mplayer ~/Music/Who\ -\ Baba\ O\'Reilley.mp3
at> <EOT>
job 13 at Wed Aug  6 23:15:00 2008
```
And yes, I did make sure that the command "mplayer ~/Music/Who\ -\ Baba\ O\'Reilley.mp3" executes successfully on its own.

It seems that the "at" command will only execute shell commands, but not run programs, which seems somewhat limiting...

---

### Post by GammaPoint on 2008-08-07
Actually mb_webguy, I tried something similar to what you described and mplayer DID work for me. This is what I tried:

```

bmalone@papabear:~/media/music/artists/Owen/At Home With$ at now +1 minute
warning: commands will be executed using /bin/sh
at> mplayer * 
at> <EOT>
job 8 at Wed Aug  6 22:20:00 2008
```

This worked appropriately. I also tried it with an individual song and it also worked. 

This is what I wanted to know. Thanks to everyone who helped out!

---

### Post by mb_webguy on 2008-08-07
"mplayer *" worked for me as well, but I can't play a specific file.  Furthermore, it seems that you can't open any kind of GUI application using the "at" command.  If I substitute "gmplayer *" in your example instead of "mplayer *", it begins playing music, but doesn't open the MPlayer GUI.  Substituting "vlc *" does nothing at all, even though inputing the command directly in the terminal opens VLC and begins playing the music in the directory.

I can think of quite a few uses for the "at" command if I could open any application at any time, but not if I can only run command-line apps, and even then in only a limited fashion...  *sigh*

---

