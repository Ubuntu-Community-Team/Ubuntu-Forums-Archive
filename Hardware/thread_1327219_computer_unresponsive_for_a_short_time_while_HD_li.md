---
title: "computer unresponsive for a short time while HD light is on"
date: 2009-11-15
forum: Hardware
---

### Post by jjatria on 2009-11-15
i don't know if this belongs here, but i have the intuition it might be a hardware problem, so i'm posting this here just in case someone finds it. i've tried finding info on this problem, but apparently, i'm the only one who has come across it (or, much more likely, i haven't been able to find where all those other people are asking questions).

the problem i have is this: sometimes, for no particular reason, the computer will temporarily stop responding. all the programs keep running, the mouse keeps moving, the music (if there is music) keeps playing (for some time)... but there is no possible input on the screen, nor changing windows, nor focus. flash videos will stop playing, but audio will go on. while the computer is in this state, the HD light will be on even if there is no (obvious) hard drive activity (there is no sound coming from the hard drive either). after a while, the light will go off, the computer will catch up with all the desperate attempts at doing things i've made during the unresponsive time, and everything will go back to normal... until it happens again.

it's driving me crazy.

it has happened before, but it stopped for the longest time until it started again recently. sometimes i can go a full day without seeing it once, other times it renders the computer unusable. sometimes (like now) it happens often enough that i can't use the computer... as long as i'm using a particular program (in this case kiten, a japanese dictionary).

i have a dell inspiron e1505 running 32 bit kubuntu karmic. my system runs scim (which has been responsible for other problems in the past) and turning it off is not an option. i also use compositing on, in case any of that might prove handy. i'm not using nepomuk, but i did install gnome desktop search. maybe it has to do with that? database indexing renders the pc unusable? i seem to recall trying that in the past to no avail... any ideas?

thank you.

---

### Post by dumblebee100 on 2009-11-15
I feel that data is not supplied to your cpu at right time ..

this can be happened at certain cases 
1) you may request a large data chunk
2) your hdd is pretty old and have a lot of wear and tear ..I mean the motor inside may not catch upto the data request 
3) may be programs are in a deadlock situation ( it never happens ) but if it doesnt get the data needed from hdd it waits till it gets the whole data needed ..so till then almost all the works get stopped temporarily ( you feel like that ) but the data in RAM is used so thats why you get sound ...but after certain time even the data in buffer gets empty then the sound too gets stopped 
4) Once check your HDD for bad sectors and do a complete fsck 
5) keep your hdd healthy by giving less load to it ( I mean less IO operations ) because if the HDD is "ON" all the time and rotating the life will be decreased 
6) if you are really not satisfied with the suggestions then check the logs for the programs ...may be u can catch a bug

---

### Post by sparklingspecks on 2009-11-15
You can also try Palimpsest (aka Disk Utility) to do a SMART scan, if you want to see if the drive recorded failures before, install smartmontools (if you're comfortable with the command line) or Gsmartcontrol (UI on top of smartmontools). I had a somewhat similar problem and have since had to replace the disk.

---

