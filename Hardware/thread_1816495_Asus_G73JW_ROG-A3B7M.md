---
title: "Asus G73JW ROG-A3B7M"
date: 2011-08-02
forum: Hardware
---

### Post by Cardale on 2011-08-02
I'm using the Asus G73JW ROG-A3B7M laptop which has an i7, 16gigs of ram, and a Gefore GTX 460M graphics card.

I'm diggin the new Ubuntu style. At first I was apprehensive, but after a little break(system break down and classes requiring Windows) I am back.

Any way.  Switching between Ubuntu or Ubuntu Classic with or without affects has no effect :D

When I grab a window and move it around the screen it stutters like it is lagging.

I have manually installed the latest proprietary drivers from Nvidia and also tried using the compiz tool to disable and change settings to no avail.  

Do I need to fix the settings in the Nvidia control panel some how?

What am I doing wrong? Is my hardware just to new?

Using Ubuntu 11.04 btw completely updated.

---

### Post by vlbaindoor on 2011-08-02
> **Cardale said:**
> I'm using the Asus G73JW ROG-A3B7M laptop which has an i7, 16gigs of ram, and a Gefore GTX 460M graphics card.
I'm diggin the new Ubuntu style. At first I was apprehensive, but after a little break(system break down and classes requiring Windows) I am back.
Any way.  Switching between Ubuntu or Ubuntu Classic with or without affects has no effect :D
When I grab a window and move it around the screen it stutters like it is lagging.
I have manually installed the latest proprietary drivers from Nvidia and also tried using the compiz tool to disable and change settings to no avail.  
Do I need to fix the settings in the Nvidia control panel some how?
What am I doing wrong? Is my hardware just to new?
Using Ubuntu 11.04 btw completely updated.

Two questions:
1. Are you sure your laptop is actually using the drivers you installed?
Try the 'System -> Administration -> Additional Drivers' - what does it say?
2. You are saying you have 16gigs of RAM - are you using 32bit or 64bit version of Ubuntu?

My experience so far:

My desktop PC uses a Asus P5Q motherboard and a Nvidia graphics card and after lots of trouble with the setup I changed to Ubuntu Studio 64bit and now everything seems to work correctly.  I re-installed UbuntuStudio 64bit by formating the root partition - I have a dual boot system and I also run Windows 7 64bit. With standard Kubuntu 64bit I had lots of problems but touch wood, I am happy with Ubuntu Studio 64bit (11.04)

---

### Post by Cardale on 2011-08-02
I am sure it is activated.  When I go to the place you suggest there is a green dot in its place so I am guessing this means it is activated.  Is there a command line method of checking?  I will post the output.

My Ubuntu version can be verified with this output I believe.
```
uname -a
Linux goddard-G73Jw 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Let me know what else you need to help.

---

### Post by Cardale on 2011-08-03
glxinfo | grep -i direct output

[http://pastebin.com/hu3qSXGr](http://pastebin.com/hu3qSXGr)

---

### Post by Cardale on 2011-08-03
New Nvidia drivers just came out and same issue.

---

### Post by Cardale on 2011-08-04
bump

---

### Post by Cardale on 2011-08-06
bump

---

### Post by Cardale on 2011-08-07
bump

---

### Post by Cardale on 2011-12-11
I retried Ubuntu again 11.10 and the issue still isn't fixed.  The black flashing isn't there, but the windows are extremely laggy.

Any help please advise.

---

### Post by Cardale on 2011-12-14
I asked at the ubuntu ask since the forums are dead just for any random googler I guess.

[http://askubuntu.com/questions/87070/nvidia-gtx-460m-laggy-display](http://askubuntu.com/questions/87070/nvidia-gtx-460m-laggy-display)

---

