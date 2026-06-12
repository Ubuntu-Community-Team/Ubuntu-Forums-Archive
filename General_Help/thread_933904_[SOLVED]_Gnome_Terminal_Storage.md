---
title: "[SOLVED] Gnome Terminal Storage"
date: 2008-09-29
forum: General Help
---

### Post by elkade on 2008-09-29
I have learned by using, that the Gnome Terminal backs up or saves all command entries.  When opening up a terminal and then hitting the up arrow, the last entry is shown.

My question is:  How long or how many of these previous entries are saved?  And if there is capacity in the terminal, can that be changed.

I like the the fact that entries are saved as I needed to help a friend install an app., but didn't write down the commands.  By using the up arrow approach, I was able to help him.

Thanks all for your help in advance

Larry

---

### Post by niteshifter on 2008-09-29
Hi,

It's called history. Rarely do I say RTFM, but this is one case (as what one can do with the history database is quite a lot) ... so:

```
man history
```

will show all there is on the subject. To make up for being brief: the command 'history' and 'grep' are arguably the most useful pairing of commands ever invented: Pretend for a moment, that you dimly remember using some command to do a fix, but can't quite recall the exact spelling of that command, just a few letters come to mind. Here's a nifty trick:
```
history | grep abcd
```
That will print to the terminal just those command lines in the history database that contain that sequence of letters "abcd".

Another: I use ffmpeg to convert video files. Sometimes I can't recall the long, complex command line used on that odd file I got last week, so:
```
history | grep ffmp
```
gives me all the ffmpeg commands I've used recently.

Enjoy!

---

### Post by elkade on 2008-10-08
I would also like to know if I can view this history from a folder or file.  If so where would it be located?

Thanks,

Larry

---

### Post by Archmage on 2008-10-08
Unfortunatly you can only see the history of your whole commands.

---

