---
title: "strange problem with amarok"
date: 2005-11-30
forum: General Help
---

### Post by skaboss on 2005-11-30
Hello,

I used to listen to radio streams with my favourite player : amarok.
It worked as hell until today : i still can listen normally to local mp3 or ogg files, but everytime i try to listen to a stream, amarok displays "connecting to stream source..." in the status bar, and then freezes. 
Even stranger : i can listen to these same streams with BeepMediaPlayer (but it's much less fun :D  ).
Strangest : if i switch to my wife's user acount, i can listen to streams with amarok !
I'm running amarok 1.3 with xine-engine (gstreamer doesn't seem to workon my system), on Kubuntu Breezy 5.10.

Does anyone got a clue ?

Thanks a lot.

---

### Post by da1 on 2005-12-01
AHoy, i'm having the same issue. can't get the audio streaming to work without it freezing up and also im looking for some better skins (any recommended?!) Sorted out my sony dig cam problem thanks everyone on this newbie forum and gonna post an applet prob quick. i'll look out for a reply on the audio streaming thang! Thanks

---

### Post by noigeaR on 2005-12-01
kubuntu released updated packeges for amarok 1.3.5. they're not in the repositories, but you can download them here and use dpkg to install them manually. maybe your problem is fixed in the newer version.
[http://www.kubuntu.org/announcements/amarok-1.3.5.php](http://www.kubuntu.org/announcements/amarok-1.3.5.php)

---

### Post by claydoh on 2005-12-01
If it is working on a different user account, you can try to delete (or rename - so you can restore it) your /home/<username>/.kde/share/config/amarokrc. Amarokrc contains all the configuration options and a new one with default settings will be recreated when you run amarok next.

---

### Post by skaboss on 2005-12-01
Thanks a lot for your help, guys.
I deleted amarokrc, with no success...
I'm gonna try to manually install the new version, and let you know if it solves my problem.

---

### Post by claydoh on 2005-12-01
Another thing to try is renaming/deleting your /home/<username>/.kde/share/apps/amarok, should have mentioned that as well. As your other user account has no problems, it is very likely a local problem and not a system one. Installing the newer version is fine (it for example has a much better volume slider), but you still may face the same issue. Just make sure you uninstall the previous amarok first, it seems to make a difference for some.

---

### Post by skaboss on 2005-12-02
Hello,

I removed amarok, deleted all config files and installed 1.3.5 from packages, and...
Still have the same problem : can't listen to streams ](*,) 
But thanks a lot for your advices, even if my problem isn't solved yet, it's great to find people concerned with my noobs' problems ;)

---

### Post by skaboss on 2005-12-07
Hello guys,

Thanks a lot for your suggestions. 
I finally found that my firewall was messing around, a "disable/enable" solved my problem   :oops:

---

### Post by McSnickered on 2005-12-13
So has anyone discovered a solution to this problem?  I'm almost ready to go back to Hoary because I've seen a lot of weird problems happening since switching to Breezy.

GStreamer does not work at all on my machine so I installed the amarok-xine.  It plays music files, but when I try streaming audio I can see that I'm downloading bits but there's no sound.  I tried the suggestion above about and installed the latest Amarok 1.3.5. with it's GSTreamer counterpart. That was a big mistake - now I'm back to no music and it's not compatible with xine.

So why was streaming audio no problem with Hoary but not in Breezy? 

Thanks,
Mac

---

### Post by skaboss on 2005-12-14
Some suggestions : 
for the stream problem :
- if you use a firewall, try disabling it before listening to streams.
for the "no sound problem" :
- in amarok preferences>engines, select xine, and try all the available modules (you will need to restart amarok after each change).
- if you use a motherboard chipset for the sound, try a real soundcard (a 15 bucks soundblaster is more than sufficient, and don't forget to disable your MB sound chipset in the bios).

Can your hear KDE system sounds ?
Can you play music on other programs (BMP, JUK...) ?

---

### Post by McSnickered on 2005-12-14
[QUOTE=skaboss]Some suggestions : 
for the stream problem :
- if you use a firewall, try disabling it before listening to streams.
for the "no sound problem" :
- in amarok preferences>engines, select xine, and try all the available modules (you will need to restart amarok after each change).
- if you use a motherboard chipset for the sound, try a real soundcard (a 15 bucks soundblaster is more than sufficient, and don't forget to disable your MB sound chipset in the bios).

Can your hear KDE system sounds ?
Can you play music on other programs (BMP, JUK...) ?[/QUOTE]

Ska - thanks for the suggestions.  I don't have a firewall other than my Router, but I can see the bits coming through so I don't think that's the problem.  I'll try the xine preferences - I didn't know I had to restart each time.  And yes, I am using the crappy motherboard chipset.  I'll have to look for a cheapo soundcard during vacation.

I can hear KDE sounds and play music files, just no sound when streaming audio.

Anyway, thanks again - I'll give these a try.

---

### Post by bettlebrox on 2005-12-19
Try the newer 1.3.7 version:

[http://kubuntu.org/announcements/amarok-1.3.7.php](http://kubuntu.org/announcements/amarok-1.3.7.php)

Follow the instructions on the above page, then:

sudo apt-get install amarok amarok-arts amarok-engines amarok-gstreamer amarok-xine

So far seems to work for me w/o crashing.

---

