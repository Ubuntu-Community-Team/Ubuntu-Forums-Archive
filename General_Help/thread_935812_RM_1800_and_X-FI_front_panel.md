---
title: "RM 1800 and X-FI front panel"
date: 2008-10-02
forum: General Help
---

### Post by spartan777 on 2008-10-02
I have the X-fi elite, platinum, gamer, fatal1ty, pro, etc etc- The one with the front panel and the RM-1800 remote control. Is there any way to set this up with LIRC so that I can eventually control Elise, Banshee or Rhythmbox with it? Do I need to wait for X-fi drivers to come out (my guess since the front panel attaches to the card itself)?

I've tried to use gnome-lirc-properties, but it says that it detects no compatible receivers.

---

### Post by pogush on 2009-07-08
same question here.

I've installed the drivers and the card is working fine, but still i can't use the front panel and the RM-1800 remote..
Any suggestion?

---

### Post by pogush on 2009-07-12
bump

---

### Post by Benchamoneh on 2009-11-19
Sorry but AFAIK Creative have not released a driver that supports the front panel yet. It's pretty shocking really. Your front panel is completely useless (as is mine) until they do and I can't see it being anytime soon :(

---

### Post by GalloGlas on 2010-01-04
You got that right.   I doubt we will ever see it.  Creative has already shunned its customers with it's unwillingness to release a good set of drivers for even Windows users.  Their solutions involve:

1. removing any RAM over 3gs 
2. Changing from 64 bit to 32 
3. Removing motherboard drivers and using generic ones
4. Switching PCI slots.  

Windows 7 doesn't have remote functionality for the X-fi either.  So I guess Linux users shouldn't feel so bad.  

Section 5 of their warranty pretty much sums it up.  
[http://support.creative.com/warranty/welcome.aspx?pid=14064&cid=1&h=15](http://support.creative.com/warranty/welcome.aspx?pid=14064&cid=1&h=15)


> Creative does not warrant uninterrupted or error-free operation of the Product. Creative is not under any obligation to support the Product for all operating environments, including but not limited to, interoperability with either or both current and future versions of software or hardware.

Paraphrased: If it works, you're lucky, because we won't help you.  

It's too bad really, Creative has great hardware but their support and software sux.   I guess that means my next sound card I'll be moving on.   Sad really, I'm not sure what is out there that has the functionality of the X-Fi Elite Pro.  

With 9.10 supporting "5.1" (actually it sounds like stereo piped through 4 speakers) I doubt we'll see much of anyone dabbling with the driver like we saw in previous releases.

---

### Post by josh_o on 2010-02-22
I am using the digital out on the x-fi (platinum) front panel with no problems on Karmic.  Although I was sad when I realized I couldn't use the IR receiver.

---

### Post by Perturbed Penguin on 2010-06-12
I just happened upon this post while searching for Windows drivers for my rm-1800 since I now have it working in Linux using LIRC. So if I remember correctly I was having the same issue you are all having and I think the problem was that when I installed LIRC it installed the gnome-lirc-properties which is basically its GUI but it did not install the actual LIRC program. I am in Windows right now so I can't look it up but use synaptic to search for 'lirc' and try to find another lirc-related package that is not the 'gnome-lirc-properties' package.

Installing the other package should fix your problems if I remember right. Once you've done this there is still some program-specific setup that needs to be done and I can help out with that if needed - it took me a few days of googling to fully understand how everything works. I currently have Rhythmbox and Moovida set up to use my rm-1800 remote. If you have any questions just post back here and I'll try to keep a watch on this thread for a while. Cheers! ;)

---

### Post by yongleflibbit on 2010-10-01
@Peturbed Penguin: Please share file version numbers and repository keys that you can recall, I have no other leads on how to get my RM-1800 working on any Linux breed.

If there is any way to get some kind of feedback from the remote or front panel, that would be enough.

From there we can knock up some scripts to share: I'm a pretty awful programmer but mapping simple key commands to the remote would be enough for me, probably for most people on these forums.

Thanks in advance.

---

### Post by PRGUY85 on 2011-05-18
> **josh_o said:**
> I am using the digital out on the x-fi (platinum) front panel with no problems on Karmic.  Although I was sad when I realized I couldn't use the IR receiver.

Can you get Digital Input working? And how?

---

