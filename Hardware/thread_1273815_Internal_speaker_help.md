---
title: "Internal speaker help"
date: 2009-09-23
forum: Hardware
---

### Post by vivaldibabe on 2009-09-23
I newly installed Ubuntu 9.04 (jaunty) on my Acer laptop- and my internal speakers (and external) don't work.  I can't find any solutions to the problem, and I'm hesitant to try my noob ubuntu skills on this. Any suggestions?

(who am I kidding? Of course you guys have suggestions..:P)

---

### Post by chris1950 on 2009-09-23
> **vivaldibabe said:**
> I newly installed Ubuntu 9.04 (jaunty) on my Acer laptop- and my internal speakers (and external) don't work.  I can't find any solutions to the problem, and I'm hesitant to try my noob ubuntu skills on this. Any suggestions?

(who am I kidding? Of course you guys have suggestions..:P)

Try this it may help. But first check to make sure the sound is not muted:).

	 	 		 			 				 					Originally Posted by **Broder** 					[[IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/buttons/viewpost.gif[/IMG]]("http://www.linuxquestions.org/questions/showthread.php?p=3399629#post3399629") 				
 				[I]**Fix:** The sound on Front was disabled as opposed to muted.  A friend of mine found a solution by adding the following line of code:

options snd-hda-intel model=laptop enable=1 index=0

to /etc/modprobe.d/options file which forces enabling the speakers on start up. 

Thanks for the advice, hope the solution can be of help to others.[/I]
 			 		 	 	 
worked for  me to on Hp 6930P, thanks

ps
editing alsa-base.conf just open terminal and
sudo -s
sudo mousepad /etc/modprobe.d/alsa-base.conf

---

### Post by vivaldibabe on 2009-09-24
Well thank you, but its a no-go.

I can't even find /etc/modprobe.d/options...
/etc/modprobe.d/, yes, but no further.

Noob advise?

---

### Post by HammoD on 2009-10-03
> **vivaldibabe said:**
> Well thank you, but its a no-go.

I can't even find /etc/modprobe.d/options...
/etc/modprobe.d/, yes, but no further.

Noob advise?


Hi, try the following:

1) Sudo -s

"then enter root password"

2) cd /etc/modprobe.d/

3) pico alsa-base.conf

 "PICO" is text editor which is very simple to use.  Hope you already have it.if not then follow these steps:

from desktop main menu:

System -> Administration -> Synaptic Package Manager

Then from quick search type the word "nano". You should select the result and install it.

You can also replace the word pico by the word nano in step#3.

Hope this work:)

---

### Post by vivaldibabe on 2009-10-05
I could not get nano to install, *however* when I rebooted this last time my internal sound came through. :P
I have no idea what I did. =x
As happy as I am with sound again, my headphone jack still won't work.
I'll look around the forums and see what I can scare up.

---

