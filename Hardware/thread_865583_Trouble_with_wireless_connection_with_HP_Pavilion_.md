---
title: "Trouble with wireless connection with HP Pavilion dv9036nr"
date: 2008-07-20
forum: Hardware
---

### Post by Sebastian12 on 2008-07-20
Hey,

I just installed Ubuntu on my separate HD and everything's well, but now I need to get the internet working before I can start customizing and experimenting with everything else.  I was able to get it to *show* that it was connected and say "90%" next to the SSID (I assume that means it's getting a signal) but then when I opened Firefox it flat out didn't connect to any web sites.

Help, please?

Oh, and the light on the laptop that shows if the connection is working is orange when it should be blue, meaning that it's not being used.  Don't know if that helps.

UPDATE: Solved.  I figured it out for myself.  I have a feeling I'll have to do this more often now.

---

### Post by Sebastian12 on 2008-07-20
Bump

Please, someone?

---

### Post by Dark_Stang on 2008-07-20
Do you mean a dv9035nr? There is no dv9036nr to my knowledge...

Edit: Regardless. Post the output of "lspci" for us.

---

### Post by Tigin on 2008-07-20
what is your wireless card model? and tell us please if your system is 32 bit or 64....

---

### Post by Sebastian12 on 2008-07-20
Oh, sorry, yes.  It's dv3035nr (If you looked at the sticker on the bottom it looks like a 6).

*My system is 32 bit.

*How do I find out the wireless card model?

*I tried putting in that command and it said it wasn't a recognized command.

---

### Post by Dark_Stang on 2008-07-20
You entered "lspci" in a terminal window (without quotes) and it said it isn't recognized?...

---

### Post by Sebastian12 on 2008-07-20
Oh sorry, you meant in Ubuntu?  I'll have to reboot into it and then out, so it'll take 3 minutes... (I thought you meant the Command Prompt in Windows)

---

### Post by Sebastian12 on 2008-07-20
OK, I got it... but I printed it out since there was no way to keep it in a text file and it's a lot.  Is there any specific information you need so I can just post that instead of the whole thing?

---

### Post by Sebastian12 on 2008-07-20
UPDATE: Of the two things that seem obviously needed, here they are.

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

---

### Post by Dark_Stang on 2008-07-20
Okay, check out this thread.
[http://ubuntuforums.org/showthread.php?t=823366&highlight=intel+3945](http://ubuntuforums.org/showthread.php?t=823366&highlight=intel+3945)

---

### Post by Sebastian12 on 2008-07-21
Tried everything in the thread and even the links within it and nothing worked...

---

### Post by Sebastian12 on 2008-07-21
I hate to bump a topic twice but I'm afraid I'm going to have to.

---

### Post by Dark_Stang on 2008-07-21
I don't have an intel machine to test this on otherwise I'd keep going. I'd make a new thread with a title like "Intel Wireless 3945ABG Help" as people tend not to look at threads with this many replies.

---

### Post by Daelyn on 2008-07-23
> **Sebastian12 said:**
> Hey,

I just installed Ubuntu on my separate HD and everything's well, but now I need to get the internet working before I can start customizing and experimenting with everything else.  I was able to get it to *show* that it was connected and say "90%" next to the SSID (I assume that means it's getting a signal) but then when I opened Firefox it flat out didn't connect to any web sites.

Help, please?

Oh, and the light on the laptop that shows if the connection is working is orange when it should be blue, meaning that it's not being used.  Don't know if that helps.

UPDATE: Solved.  I figured it out for myself.  I have a feeling I'll have to do this more often now.

Might be useful. I can't connect without doing this myself.
[http://ubuntuforums.org/showthread.php?t=764886](http://ubuntuforums.org/showthread.php?t=764886)

---

