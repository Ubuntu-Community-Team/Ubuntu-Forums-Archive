---
title: "Boot Starts Ok, then screen goes BLANK"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by rchrd on 2006-01-26
{This is my first time with Ubuntu}

Installing on an Acer Ferrari 4005 (AMD64).
Partitioning (Win/XP on first partition, installing Ubuntu on second) goes ok, and Ubuntu seems to be properly installed. GRUB looks ok and I can install either W/XP or Ubuntu default or Ubuntu recovery.

But when booting (default), the initial flash screen comes up and it starts booting... all looks ok, but then the screen goes completely dark. Black. 3 seconds later an alarm sounds, African drum. Nothing I can think of will revive it. Rebooting to W/XP is ok.

During install I set the screen resolution to a max of 1280x1024, and all smaller sizes. No idea if that has any significance.

Any hints? Is there something I can do in single-user mode?

I am downloading the x86 32-bit version and will try installing it instead.

---

### Post by adwait on 2006-01-26
If you can hear the drum beats, that means Ubuntu is installed fine and starting, just that your display drivers are not configured properly and hence there is no display. Try pressing Shit+Ctrl+F1 at the blank screen after you hear the drum beats. That should get you into  a console. Try logging in there and running
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rchrd on 2006-01-26
Ok. I'll try it. Thanks for the suggestion.

---

### Post by rchrd on 2006-01-26
Well, the key-command turns out to be Alt+Ctl+F1. I found it by chance because Shift+Ctl+F1 did nothing. 

So then I was led thru the setting of the XServer options. I did the best I could, but rebooting got me to the same place. Entering terminal mode again the screen was really messed up. So obviously I didn't set the options correctly.

I'll try again tomorrow. It's late here.

---

### Post by kaamos on 2006-01-26
You could try choosing the "vesa" driver. That could help.

---

### Post by rchrd on 2006-01-26
Hey. That worked!  Wow. 
THANKS!

Thanks to both Kaamos and Adwait!  Just think, I got help from India and Finland!
Super!

---

### Post by adwait on 2006-01-26
You should be used to getting tech support from India by now ;)

Sorry about the key combination.......I forgot :p

---

### Post by nielseno on 2006-12-24
I got the black screen too but it was because I forgot about the 192MB minimum requirement.  Added more memory and all is well.

---

### Post by Kyouto on 2007-10-28
I have the same problem, except this isn't a first time install.... I've had Gutsy installed for a few weeks and it's worked fine, other than I had trouble installing my PCI card (I finally just uninstalled it and had no trouble with the onboard video.) Finally I decided to try it out again, I booted into Ubuntu with my PCI card installed and I got the prompt saying I was in low graphics mode... I had options to change the drivers for my PCI card, so I tried selecting the fglrx drivers (note that I made no changes to the onboard drivers) then restarted... when I did, I was getting the same screen as the OP, but by the sounds I could tell Ubuntu itself was running fine. I've tried the suggestions in this thread, alt+ctrl+F1 does nothing for me. I booted back into XP and I was having troubles there, so I uninstalled/reinstalled the drivers and was able to get everything working fine in XP... however, I still have the same problem with Ubuntu.  I'm wondering if there's a way I can roll back the drivers, or something like that. Any suggestions?

---

### Post by lex` on 2008-02-26
Hi !  

I have the same problem and yea im kinda noob in linux but my problem seems little different.

after a fresh installl of ubuntu 7.10  i got black screen ( no sounds of drums etc.) 

i went in recovery mode and well i could actually go in the graphic mode but with some problems.. i dont see wifi i cant access to several appl etc. (i guess is normal in this mode)  ; after this i restarted and... well 
acutally i was able to access normally... with all the features... wifi... graphics... (compiz already installed and working..) 

But this morning i restarted the system and well... Black screen again :( !!! i really dunno... what to do. i mean last n8 i was playing with my cuBe :> and today im starring at the black screen :(

---

### Post by prabackar on 2008-03-10
I got very good review from my friend about Ubuntu. I downloaded the iso yesterday and tried installing it today.....
I am having the same problem. "screen goes BLANK"

My configuration
---------------------------
Asus Motherboard - M2NE
Processor - AMD X2 4200+ 
Graphic Card (PCX) - 8500GT BIG
**_I don't have a on-board VGA supoort on my motherboard_**

Ubuntu installs and goes blank before I hear the music. 
I tried pressing CRTL+ALT+F1. Nothing happens. 

Kindly help. What is this vesa drivers? How can I use it to solve my problem?

---

### Post by MachineHead on 2008-04-16
Hi all,

I have the same problem at the moment.
I'm no expert at all, just a noob tying loose ends together.
For Graphics I have 2 XFX Geforce 8600 GTS cards.
New hardware (wich requires new drivers) seems to be the challange.
Together with the configuration of the xorg.conf file.

Join us here, I'm looking for the solution and I will find it.
[http://ubuntuforums.org/showthread.php?t=756708](http://ubuntuforums.org/showthread.php?t=756708)

-MachineHead

---

