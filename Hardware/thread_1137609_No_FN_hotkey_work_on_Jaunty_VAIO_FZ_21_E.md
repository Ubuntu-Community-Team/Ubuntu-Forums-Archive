---
title: "No FN hotkey work on Jaunty VAIO FZ 21 E"
date: 2009-04-25
forum: Hardware
---

### Post by doupi on 2009-04-25
Hi everybody, 

I've just installed Ubuntu 9.04, and my FN hotkeys don't work (except FN+F2 which put sound off). So I can't adjust brightness by FN+F5 or FN+F6, but I was able to do it with Ubuntu 8.10 with a script based upon NVClock ....

But now with Jaunty, I can only change brightness with a code by using the terminal, which is not very convenient ....

I hope that someone will be able to help me ! 

Thx !

---

### Post by doupi on 2009-04-26
I think that the problem comes from the keyboard which is not recognized ...
If someone has an answer ....

---

### Post by herculea8n1982 on 2009-04-26
I fixed this yesterday with the help of the awesome guys in this thread: [http://ubuntuforums.org/showthread.php?t=1004568&page=2](http://ubuntuforums.org/showthread.php?t=1004568&page=2)

---

### Post by doupi on 2009-04-26
Thx, but I've followed these instructions, but they don't work ....

In fact, if I change the brightness with a script console 

"nvclock -S 50 or nvclock -S +50", it's ok but not if I use fn+F5 or fn+F6

I think it's my keyboard which is not recognized ! 
And I don't know how to ...

---

### Post by herculea8n1982 on 2009-04-26
> **doupi said:**
> Thx, but I've followed these instructions, but they don't work ....

In fact, if I change the brightness with a script console 

"nvclock -S 50 or nvclock -S +50", it's ok but not if I use fn+F5 or fn+F6

I think it's my keyboard which is not recognized ! 
And I don't know how to ...

They've got the same laptop as you!! :confused: So you've created all of the scripts exactly as written made them executable and restarted acpid?

---

### Post by doupi on 2009-04-26
Yes of course ! 

That's why I think that the problem comes from my keyboard, but I don't know how to configure it, or what's the problem !

---

### Post by doupi on 2009-04-27
Problem solved ! 
It was a problem with chmod, I had to determine the path way to the file !

---

