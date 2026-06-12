---
title: "shutdown problem"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by rendon on 2008-01-15
Toshiba Satellite A30-714


Been all over google for ages now, you are my last hope before installing a different OS, please help, I really like Ubuntu.

Whether from the System->Quite or from command line "shutdown -h now" as root, shutdown is just always a surprise, maybe it'll work, maybe it'll just hang indefinitely.

when it doesn't work, it's apparent.  The screen will instantly go black and hang forever.  two hours, two days, just doesn't shutdown.

I disabled splash screen in a file called orgx or something.   added a line acpi=off or amp=off or something...

not to say that I configured these options incorrectly, just that I've tried so many things by now that I can't remember every exact character and don't see the meaning in reciting like as if I were supposed to be a genius.

bottom line is that I'm not shutting down properly, and I dont' know if there is any method to check the root of the error?

what log could I check?

do you have a similar problem?

I can see that I'm not alone on this issue, but is there a solution for it?

hair shy from cursing,
Brendon

---

### Post by rocko_mtv on 2008-01-15
my toshiba A105-S2716 does the same thing.  i will b watching this thread.

---

### Post by rendon on 2008-01-18
For some reason, I tried to shutdown networking before shutting down, and it seemed to work a couple of times, but then went back to usual, just getting a black screen.

I tried logging in with xfce desktop, thinking that a lighter interface might work better, but no, it still doesn't shutdown properly.

I seemed to have better success when trying to shutdown from command line, but I also have problems if I try to switch to a tty using Ctrl+Alt+F2/F3/...  this also can sometimes result in a black screen with no response and no return, at which point I have to hold the power button down and just kill it.

Am I posting this in a wrong location or is it just too busy here to get a reponse? 

Anybody know of other forums that could help in this matter?

any feedback appreciated..

---

### Post by ugm6hr on 2008-01-18
I think you have an Intel Video chipset.  If so, this might help:
[http://ubuntuforums.org/showthread.php?p=4122482#post4122482](http://ubuntuforums.org/showthread.php?p=4122482#post4122482)

Basically, I had the same problem which I fixed by using the i810 driver rather than the experimental Intel one.

---

### Post by rendon on 2008-01-19
ugm6hr, a million thanks for your response!  I'll give that a try asap!

---

### Post by rendon on 2008-01-22
OK!

it's been a few days now and I'm shutting down, restarting, logging in/out normally!

Hope people with similar problems find this thread and it works for them too.

thanks again!

---

