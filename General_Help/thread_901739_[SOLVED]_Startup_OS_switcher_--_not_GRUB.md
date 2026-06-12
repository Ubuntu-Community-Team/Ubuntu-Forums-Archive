---
title: "[SOLVED] Startup OS switcher -- not GRUB?"
date: 2008-08-26
forum: General Help
---

### Post by itsjareds on 2008-08-26
I slowly figured out that GRUB is not the only operating switcher - there's another one that I use when my computer restarts. It says "Please select the operating system you wish to use: Microsoft Windows XP Professional
Ubuntu"

If I select Ubuntu, then it will start up Ubuntu and then I can get to the GRUB boot menu.

How/where do I edit this file, I need it to hide automatically unless I press ESC in the timeout period.

I don't think it's a Windows thing, but something already installed on my computer? It's the same thing on two computers, so I know it's not something unique.

---

### Post by srt4play on 2008-08-26
Sounds like the Windows bootloader which was probably set up automatically by Wubi.

---

### Post by itsjareds on 2008-08-26
That's what I figured, but how can I change it?

Briefly looked through the ubuntu install folder but didn't find anything.

---

### Post by srt4play on 2008-08-26
It's a file in the root directory of your windows C: drive if I remember correctly, called boot.ini.  Here's the microsoft support article on the boot.ini file:

[http://support.microsoft.com/kb/314081](http://support.microsoft.com/kb/314081)

---

### Post by Hyper Tails on 2008-08-26
do you have ubuntu selected as your default operating system?

---

### Post by itsjareds on 2008-08-27
No, I want it to run Windows XP by default, which it does, but is it possible to hide the menu and only show it when I press ESC?

---

### Post by Hyper Tails on 2008-09-06
if you used wubi it'll go to the windows boot loader.
but is you partitioned you hardrive and install Linux Last it should go to the grub loader

try it (i did)

---

### Post by itsjareds on 2008-09-07
Thanks, srt4play gave me the right answer.

Marking this thread solved.. thanks everyone for the help.

---

### Post by Kumagoro on 2008-09-09
> **srt4play said:**
> It's a file in the root directory of your windows C: drive if I remember correctly, called boot.ini.  Here's the microsoft support article on the boot.ini file:

[http://support.microsoft.com/kb/314081](http://support.microsoft.com/kb/314081)

So if i type 0 in the timeout, will it be endless or hidden unless i do something? Or should i type 2?

I want to hide the loader, my bro hates linux with a passion, he wouldn't like to see it on his/mine PC...

---

### Post by itsjareds on 2008-09-09
To truly make it completely hidden you have to put in 0 for it to not show up, but what I did was just turn it 0 before school, then come back and if I want to use Ubuntu, I just went back in and changed the timeout back to 30.

Probably can write a script to do this faster, if I wanted..

---

### Post by Kumagoro on 2008-09-10
Hmm, how about creating a boot cd? Is it possible?

---

### Post by itsjareds on 2008-09-10
I think so, I had this exact same question about 3 days ago. Someone else told me to try installing remastersys.

```
sudo apt-get install remastersys
```

The only problem I had with it was that I don't have much memory space and I tried to write it on the hard drive without thinking, and I left it running overnight. In the morning the terminal was stuck with remastersys at 99% complete, but my computer was out of memory. Had to delete all that work.. :(

---

### Post by Virtua-Touch on 2008-09-10
You could also click on My Computer in XP, type "C:\boot.ini" (without quotes) and a text file will open in notepad with a bunch of words. This is the boot menu. You should see c:\wubildr.mbr="Ubuntu" Delete that, and save it. If you get an error saving it, go [here.]("http://users.bigpond.net.au/hermanzone/p9.html") Just open up CMD and type what's in the black boxes. You should be able to save it, and the boot.ini file will show up in C:\ without typing it in the address bar. Reboot, and it should automatically boot into XP, without showing the boot menu. Then, just add that back in when you want to boot into Ubuntu. This is how I do it without my dad knowing.

---

### Post by itsjareds on 2008-09-10
Genius :)

I might actually do that instead.

---

### Post by itsjareds on 2008-09-10
edit: oops double post.. can't find a delete post feature.

---

### Post by Virtua-Touch on 2008-09-10
Haha, all thanks to [caljohnsmith]("http://ubuntuforums.org/member.php?u=530779"). Original Thread: [Here]("http://ubuntuforums.org/showthread.php?t=912403")

---

### Post by itsjareds on 2008-09-10
I actually tried to edit boot.ini a while ago, but when it blocked me from saving I didn't feel like looking further into it.

---

### Post by Virtua-Touch on 2008-09-11
Yeah, the "boot.ini" isn't readable/writable even with show hidden folders tacked. That's why you have to set an attribute for read/write access.

---

