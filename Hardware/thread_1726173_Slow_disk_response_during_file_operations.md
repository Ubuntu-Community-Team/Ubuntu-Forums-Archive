---
title: "Slow disk response during file operations"
date: 2011-04-10
forum: Hardware
---

### Post by orethrius on 2011-04-10
Marking thread SOLVED as my method seems to work, though I'd still like an explanation if anyone's offering one. :)

UPDATE 1: Using htop to set the **nice** value of **ext4-dio-unwrit** to **-20** seems to have worked wonders in my case, though I have absolutely no idea *why*.  
Cue my entire Linux history of doing things without fully understanding the ramifications first. :lolflag:
UPDATE 2: From what I can tell, I actually achieved the direct opposite of my goal, prioritizing file moves *over* everything else; still, the end result seems the same, with other processes taking only a slight backseat to the file operations, and everything co-existing peacefully.  Perhaps having everything running at the same level of niceness isn't always a good idea?
__________________

Per: [http://ubuntuforums.org/showthread.php?t=399316](http://ubuntuforums.org/showthread.php?t=399316)
Per: [http://ubuntuforums.org/showthread.php?t=86418](http://ubuntuforums.org/showthread.php?t=86418)

I'm rather curious, as I've seen this mentioned a bit, but haven't noticed a direct solution (please point it out if it's been posted, as a cursory search didn't turn up much).

I don't know that this actually *is* a problem, so much as it is a rather simplistic focus on prioritizing file transfers over any other operation.  Isn't there some background-intelligent (forgive the MS allusion) way to re-nice mv operations, for example if I wish to browse the Internet with any kind of responsiveness?  I don't have a problem with file transfers taking a backseat to foreground operations, even if it means they may not finish *precisely* on schedule.  Besides, doing this neatly could be another "killer app" functionality to add to Ubuntu's already impressive list of features. :)

EDIT: This may be more appropriate to "Development & Programming"; if so, feel free to move it there. ;)

---

### Post by SeijiSensei on 2011-04-10
> **orethrius said:**
>  Isn't there some background-intelligent (forgive the MS allusion) way to re-nice mv operations, for example if I wish to browse the Internet with any kind of responsiveness?

Sure. You said it yourself. Use nice to run the copy from the command prompt:

```
nice -n 10 'cp -a /path/to/source /path/to/target &'
```

or perhaps

```
nice -n 10 'rsync -av /path/to/source /path/to/target &'
```

if you just want to synchronize two directories.

---

### Post by orethrius on 2011-04-10
I suppose I should clarify, being new to Kubuntu and all.  I'm using the "standard" file-copy method to transfer files between drives, and responsiveness while doing this seems to be quite sluggish.  Natch, I remember being able to make my system quite a bit snappier while using mv and cp, due to niceness; I suppose I figured Kubuntu uses mv and cp in the same manner.  From what I can tell, it doesn't; sudo'ing and setting a different nice value for ext4-dio-unwrit seems to be the key / equivalent here.  I have absolutely no idea why this is the case, but it seems to work. :)

---

