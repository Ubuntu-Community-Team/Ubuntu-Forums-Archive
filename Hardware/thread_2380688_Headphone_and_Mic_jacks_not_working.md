---
title: "Headphone and Mic jacks not working"
date: 2017-12-20
forum: Hardware
---

### Post by jjbby on 2017-12-20
I have tried a number of different work arounds searching the web for  help on this issue and none of them work so I am asking here. (Not as worried about the mic jack but use headphones to work late at night)


  The speakers work and keep playing after the headphones are plugged  in. There are no headphone options in settings. Alsa tools also dont  look like they show a headphone connected? Do I need to just update  drivers from the manufacturer?


  I have an Asus ROG G751 JL running 17.10


  This is alsa link that might be helpful? [URL="http://www.alsa-project.org/db/?f=86bf1ba1f6e3d841d4ac713059a3e39f0b2bf39e"]http://www.alsa-project.org/db/?f=86bf1ba1f6e3d841d4ac713059a3e39f0b2bf39e

[/URL]

  No idea where to go from here as going to other help answers and just  trying all the commands in the terminal hasnt helped and I dont know  what they do.  Any help is appreciated!

---

### Post by #&amp;thj^% on 2017-12-20
This has been a problem with these machines. (Dual Booting Windows with Linux)
I quote one user I know>
> had something to do with Windows 8.1 not shutting down properly when I reboot so I have to shut down Windows and then boot Linux to have any sound at all instead of simply restarting into the other OS. If you're in a dual boot configuration, this might be the solution for you as well. It's kind of annoying to shut down and then restart but with the notebook's fast boot I really don't mind that much.
**_Another issue I had was with the headphones - in Linux they wouldn't be recognized at all. Strangely I found a solution - plugged them into the third audio jack which was advertised as line-in but is apparently line-out. _**That worked like a charm. 
Link Source: [https://rog.asus.com/forum/showthread.php?59557-Asus-G751JY-No-sound-on-Linux-Mint-17-1-Cinnamon](https://rog.asus.com/forum/showthread.php?59557-Asus-G751JY-No-sound-on-Linux-Mint-17-1-Cinnamon)
There is a fix of sorts if I can find it. Will post it when i find it.

---

### Post by jjbby on 2017-12-20
Hmm that is interesting. What does it mean by plugging it into the "Line-in"? Does that mean using a different jack?

---

### Post by #&amp;thj^% on 2017-12-20
Yes. It was named  "line-in"
Let us know if it works for you.

---

### Post by Yellow Pasque on 2017-12-20
[https://ubuntuforums.org/showthread.php?t=2261149](https://ubuntuforums.org/showthread.php?t=2261149)

---

### Post by jjbby on 2017-12-20
Thanks [**[COLOR=#000000]Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")! Ill check through that and see what I can find and if it works/helps

I am thinking that as a work around I can use bluetooth headphones...not sure yet. 

Also there is no line-in that I saw that was changeable to correct the issue!

---

