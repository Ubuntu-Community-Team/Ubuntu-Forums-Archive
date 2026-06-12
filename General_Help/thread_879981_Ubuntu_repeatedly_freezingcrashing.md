---
title: "Ubuntu repeatedly freezing/crashing"
date: 2008-08-04
forum: General Help
---

### Post by sag969 on 2008-08-04
I'm completely new to ubuntu (and linux in general) but consider myself to still be pretty knowledgeable when it comes to computers. However, the problem I'm having now with Ubuntu is throwing me for a loop.

I used Wubi to install Ubuntu Hardy 8.04 on my Windows Vista desktop computer, and everything works fine for the most part. I have two problems, one of them being pretty big and the other not so much.

1) My big problem: Ubuntu freezes. It might be after 10 minutes of usage, or 2 hours...but the whole OS will freeze. I can still move the mouse around, but all the windows go gray, and clicking does nothing. Ctrl+alt+delete does nothing. I printed out a list that showed about a half dozen keypad combination to force your computer to do a restart without actually holding down the power button (which I heard was very bad for linux computers especially). Out of those half dozen, only one works - the one where you press about 8 keys! Something like ctrl+alt+sysRq+r+b+ who knows what else - I assume you know what I'm talking about. Anyways, thats the only one that works. 

So, does anybody have any idea what is happening? There is no apparent rhyme or reason to when it happens. It might happen when firefox is open, it might happen when i'm only using pidgin, it might happen when i'm installing something...its completely random and the only possible solution is to reboot. I did some googling for it, but couldn't find anything to useful.

2) My other somewhat less important problem is wireless. I use a netgear wireless usb card, and on Vista I get a decent signal from my router (usually 60-70%) and the speed is pretty fast. However, in linux the range cuts down to maybe 10-20%, and half of the time it will just die out. Also, the speed gets pretty low sometimes, almost to 2 mbs. Downloading is incredibly slow. Half of the time it will lose the signal after a few minutes and have to reconnect. Any ideas on what I can do to fix this? If you want more specifics let me know.

It has occurred to me that the two incidents may be somehow related - but I have so little knowledge of ubuntu that I'm not sure if that's possible or how to check/retrieve logs to verify that.

Any help would be greatly appreciated.

---

### Post by ago on 2008-08-04
You should be able to press ctrl + alt + f2 to get to a terminal and look at the logs to find the reason. Logs are in /var/log/. You might want to check the output of "top", "free" and "df" as well

---

### Post by K2712 on 2008-08-04
Also, have you checked synaptic to see if there are any broken packages?

---

### Post by SlimDan22 on 2008-08-04
I wonder if it could be a disk problem on the windows end

wouldnt hurt to run chkdsk to check for bad sectors and etc..

but what do i know im just an ubuntu noobb :)

---

### Post by sag969 on 2008-08-05
> **ago said:**
> You should be able to press ctrl + alt + f2 to get to a terminal and look at the logs to find the reason. Logs are in /var/log/. You might want to check the output of "top", "free" and "df" as well

Pushing ctrl + alt + f2 doesn't do anything. I still have to hit alt+r+s+u+b+sysrq if I want to get a soft restart.

---

