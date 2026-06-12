---
title: "Acer Aspire 5542 issues"
date: 2010-03-06
forum: Hardware
---

### Post by Godspell on 2010-03-06
Hi there,

I'm using Karmic 32bit on Aspire 5542 and having some issues. I searched for solutions before but couldn't find any (maybe I didn't look for it hard enough) and also, I wanna put all the issues I encounter in one place. Anyone who uses the same (or similar) laptop, please feel free to join.

**First of all, the wireless.**

AR928X Wireless Network Adapter (PCI-Express)
Atheros Communications Inc.

It works alright but gets disconnected quite often, like once every hour or so, and the signal isn't that great either. This one was running on Windows 7 before and signal back then was pretty good (in the same hotspot of course).
The most annoying thing is when it gets disconnected, it doesn't reconnect. I have to reboot every time this happens.
Any bright idea on this?? I'm pretty much of a newbie on Linux so detailed explanations are greatly appreciated.

**Another problem is with touchpad.** It's got a lock button and really useful when writing essays cause I can temporarily disable the touchpad. It doesn't work properly.
Once it's switched off, it can't be switched back on. Any idea on how to sort it out???

**I can't get the mic working either.** I've installed Skype and the app works just fine but the mic doesn't.
My audio device is SBx00 Azalia (Intel HDA), ATI. As far as I'm concerned, device is recognised because I've been watching films, listening to music etc. I just can't speak.

**Also, how do I find my web cam?** In Windows, it can be found under My Computer but how do I look for it in Ubuntu? I'm presuming it's been recognised cause it works on Skype. 

**My last question is there a way to turn off Ubuntu startup sound?** No the sound it makes when you login (that's been switched off) but the one when you see the login screen.
I've selected "NO SOUND" and MUTE the ALERT VOLUME but that sound doesn't go away.

Many thanks for reading, guys. Sorry if I sound a bit cheeky posting all the issues in once place. Just thought it would be more efficient than making loads of threads. Hope y'all can get back to me.

Thank you very much and regards.
GS

---

### Post by gordintoronto on 2010-03-06
1. I have no suggestion about your wireless.

2. According to this site:
[http://www.linlap.com/wiki/acer+aspire+5542](http://www.linlap.com/wiki/acer+aspire+5542) 
there is no solution for the touchpad issue.

3. Check your volume controls. By default, the mic is muted.

4. Run Administration/Synaptic, and install Cheese. It should appear under Sound and Video, and let you record pictures and videos.

5. I have no suggestion about the login sound.

By the way, I Googled:
acer 5542 linux
and got lots of results, a couple of them are even useful.

---

### Post by Godspell on 2010-03-06
Hey thanks for the reply. I've got 3 of my issues sorted; touchpad, mic and webcam.
Funnily enough, I found a very simple yet godlike accurate solution from THE web link you gave me.

You were right about the mic, it was muted. I guess I was naive for not checking it :)

Cheese is really great, man. I totally love the app. Wouldn't have heard of it if it wasn't for you.

Thanks for your suggestions, mate. I really do appreciate it.
Hope somebody will come up with some answers for the rest.

Now, following is the solution to Acer touchpad on/off button problem POSTED by a fella named Juan Peròn on [http://www.linlap.com/wiki/acer+aspire+5542](http://www.linlap.com/wiki/acer+aspire+5542)
FULL CREDITS TO ORIGINAL UPLOADER.

 {[SIZE=2][I]You can make work the Acer 5542 touchpad in Ubuntu Karmic following this instructions: 
   Open a terminal and type:
sudo gedit /etc/default/grub 
   The gedit text editor will open. You should search this line:
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
   and replace it adding i8042.nomux variable as follows:
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash i8042.nomux” 
   Save the file. 
   Now in the console type  
   sudo update-grub 
   When completed, restart your computer.[/I][/SIZE]}

Regards,
GS

---

### Post by Godspell on 2010-03-06
Just looking around and found this thread
[http://ubuntuforums.org/showthread.php?t=1309605](http://ubuntuforums.org/showthread.php?t=1309605)

It sorted out all of my wireless problems right away :D No more weak signal and dropping off randomly. 
Hopefully, this is helpful for others like me.
Thanks.

Regards,
GS

---

### Post by ptrinder64 on 2010-06-13
I'm looking at buying one of these laptops and was wondering how your experience with it has been? I see you're now running Lucid - any problems with it?

How would you rate the laptop overall? Do the graphics work ok?

Sorry for sounding like the Spanish Inquisition and thanks in advance!

---

### Post by Godspell on 2011-12-20
> **ptrinder64 said:**
> I'm looking at buying one of these laptops and was wondering how your experience with it has been? I see you're now running Lucid - any problems with it?

How would you rate the laptop overall? Do the graphics work ok?

Sorry for sounding like the Spanish Inquisition and thanks in advance!

Was just looking through my old threads and saw your questions.
You've probably already bought a laptop and are using it already but I'll reply anyway. Wouldn't be a bad idea to keep record of Acer-Ubuntu experience, would it? heh

I've used Ubuntu on Dell Vostros 1700 laptop before and really didn't like it. Even on Lucid (which is my favourite), it was giving me troubles with graphics, networking and other annoying little issues.

But with Acer 5542,...man it works pretty much out of the box. Especially with Lucid. The experience is beautiful. I've had sooo much fun with Ubuntu as much as I did with the laptop itself. Ubuntu 10.04 (and I quote 10.04 cause I don't like the later ones so far) is, imo, rock solid OS. On the other hand, Acer also has pretty durable hardware,...I've dropped it several times; formatted and re-installed OS many times and so forth but still no problems whatsoever.
Combining these two, the user experience is amazing. Gives me a real sense of freedom. Even the infamous ath9k wireless drivers don't give any trouble. I rarely have freeze/hang problems.

To conclude, I would recommend Acer Aspire to anybody. I've seen my friends used different models of Aspire with Ubuntu as well. They don't seem to have any problems either.

Anyway,...just my 5p worth of experience :)

---

