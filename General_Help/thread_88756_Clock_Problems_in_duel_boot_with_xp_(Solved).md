---
title: "Clock Problems in duel boot with xp (Solved)"
date: 2005-11-11
forum: General Help
---

### Post by Drifter on 2005-11-11
I have a problem with my clock in xp since I started duel booting with ubuntu.  the clock in xp is way fast when I boot to xp.  Does anyone know how to fix this, thanks.

---

### Post by earobinson on 2005-11-11
I searched for "time windows" and i found this: [http://www.ubuntuforums.org/showthre...t=time+windows](http://www.ubuntuforums.org/showthre...t=time+windows)
[http://www.ubuntuforums.org/showthread.php?t=87649](http://www.ubuntuforums.org/showthread.php?t=87649)

---

### Post by Drifter on 2005-11-11
I set everything like the the guy said to do and my XP clock is still 7 hours fast, ubuntu's clock is ok.

---

### Post by earobinson on 2005-11-11
Did you look at both links, the second one figure something out i think

---

### Post by Drifter on 2005-11-11
I did and my clock preference is not set to utc and I changed the file to =no in the other and it still shows 7 hours fast.

---

### Post by Drifter on 2005-11-11
can anyone help me with this problem, my ubuntu clock is ok but when I go to xp it is 7 hours too fast.

---

### Post by jasay on 2005-11-11
Are you 7 hours from Greenwich Mean Time by chance?  Try right-clicking on the clock, set preferences and unclick "Use UTC."  If it's not checked maybe someone else has ideas?

---

### Post by Drifter on 2005-11-11
That is not checked in clock preferences, can anyone else help with this.

---

### Post by earobinson on 2005-11-11
I asked the person in this post [http://www.ubuntuforums.org/showthread.php?t=87649](http://www.ubuntuforums.org/showthread.php?t=87649) to post there file to try and maybe help you.

---

### Post by Drifter on 2005-11-11
I now have xp's clock running ok but ubuntu's is running 5 hours slow each time I boot to it from windows, I have two harddrives. This is what I did in the terminal to get to where I am now:  

sudo update-rc.d -f ntpdate remove

How to get both working ok anyone.

---

### Post by joris.brus on 2005-11-11
I think Linux sets your bios clock to GMT then subtracts or adds whatever your timezone is set to. Mine is GMT -5. 
Windows sets BIOS to it's local time. 
Set either linux or windows to GMT to trick the other, worked for me.

---

### Post by Drifter on 2005-11-11
[QUOTE=joris.brus]I think Linux sets your bios clock to GMT then subtracts or adds whatever your timezone is set to. Mine is GMT -5. 
Windows sets BIOS to it's local time. 
Set either linux or windows to GMT to trick the other, worked for me.[/QUOTE]
How do u do that, I am a new linux person, I like ubuntu very much however I don't know a whole lot about it yet.

---

### Post by Drifter on 2005-11-11
how do u do this, I am new to linux and I don't understand what u mean by this.  Could u explain it in more detail.

---

### Post by joris.brus on 2005-11-12
system -> Administration -> time and date
Or do it in windows

---

### Post by Drifter on 2005-11-12
I hope you don't get upset with me for asking stupid questions, but I still don't know what you are telling me to do.  I set the time and date in ubuntu just now and then went to windows and the time is now 6:00 PM, it should be 11:00 pm.  Please explain what you did so I can understand it as I said before I don't know that much about this.  Thanks

---

### Post by Drifter on 2005-11-12
I have the clock problem that happens in duel booting with xp and ubuntu. If I set the clock on one and boot to the other, that one that I boot to will be anywhere from 5 to 7 hours off.  I have tried a few things in some posts but nothing has helped.  Am I doomed to have to set the clocks evertime I boot from one to the other.

---

### Post by Drifter on 2005-11-12
I have xp on one harddrive and unbuntu on another one.  I have problems with the clock and time.  If I boot from one to the other the time is 5 to 7 hours different than it should be.  I have tried somethings from some posts but nothing has helped yet.  Can someone please help me get this fixed, or am I doomed to have to set each clock every time I boot.

---

### Post by aysiu on 2005-11-12
Please stop posting new threads on the same problem. If you've tried these two things already (see screenshots)--not using UTC and selecting the appropriate time zone, I don't know what else you can do. People have tried to help you--we're only human, we're only volunteers, and we're only fellow users. We don't know everything!

---

### Post by Drifter on 2005-11-12
Please don't get upset with me, I don't know that much about linux yet and I am sorry if I caused you any problems or stress.  I know you are vols and I appreaciate all of you that have tried to help.

---

### Post by aysiu on 2005-11-12
[QUOTE=Drifter]Please don't get upset with me, I don't know that much about linux yet and I am sorry if I caused you any problems or stress.  I know you are vols and I appreaciate all of you that have tried to help.[/QUOTE] I'm not upset. I'm just trying to get you to realize that there's only so much people can do. If you post your problem multiple times, it doesn't mean people will magically have a solution for you. I'm sorry you're encountering this problem, and I wish I could help you out.

---

### Post by manicka on 2005-11-12
[QUOTE=Drifter]I have xp on one harddrive and unbuntu on another one.  I have problems with the clock and time.  If I boot from one to the other the time is 5 to 7 hours different than it should be.  I have tried somethings from some posts but nothing has helped yet.  Can someone please help me get this fixed, or am I doomed to have to set each clock every time I boot.[/QUOTE]

The problem is that you have chosen to set your time by utc instead of local time during your ubuntu install. This is preferred for ubuntu systems but plays havoc with duel boot machines that also have windows.

I'm not sure how you change ubuntu to use local time instead of utc after install. I chose this type of setup when I installed breezy and got around the windows time problem by installing a freeware program in Windows that will log in to an internet time server and change the clock during startup. Unfortunately it's been that long since I logged into my windows partition that I can't remember the name of it.....sorry. I do however remember a google search giving me several freeware apps to choose from to do the job.

hth

---

### Post by Drifter on 2005-11-12
In my preferences on the clock I have this:  clock type 24 hour, I have show seconds and date, the utc is unchecked.

---

### Post by manicka on 2005-11-12
[QUOTE=Drifter]In my preferences on the clock I have this:  clock type 24 hour, I have show seconds and date, the utc is unchecked.[/QUOTE]

That won't help. Your problem lies in the install, not how the system is runing now.

---

### Post by Drifter on 2005-11-12
So do I re-install and If I do what is the question I need to answer when this comes up.

---

### Post by aysiu on 2005-11-12
Does [this](http://ubuntuforums.org/showthread.php?t=16872) help?

---

### Post by Drifter on 2005-11-12
Aysiu, I guess I am too new to understand enough, I looked at that post just now but I don't how to turn anything off in the boot menu.

---

### Post by aysiu on 2005-11-12
[QUOTE=Drifter]Aysiu, I guess I am too new to understand enough, I looked at that post just now but I don't how to turn anything off in the boot menu.[/QUOTE] I don't know how to change the boot menu, either. These commands are supposed to help you diagnose the problem, though. Just type them in the terminal and see what comes out. ```
date
``` ```
cat /proc/driver/rtc
```

---

### Post by Xian on 2005-11-12
[QUOTE=manicka]I'm not sure how you change ubuntu to use local time instead of utc after install.[/quote]

Three steps:

$ sudo gedit /etc/default/rcS

```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```

Reboot the system.

[QUOTE=manicka]I chose this type of setup when I installed breezy and got around the windows time problem by installing a freeware program in Windows that will log in to an internet time server and change the clock during startup.[/QUOTE]
Take this advice. Fix it from within windows if no further progress.
This is not a Ubuntu problem.

---

### Post by tb525 on 2005-11-12
Open a terminal and log in as root.

Type: **sudo gedit /etc/default/rcS** and hit [Enter]

Edit **UTC=yes** so it reads **UTC=no**

Save the edited file and close it.

Click  System -> Administration -> Time and Date

Set the correct time/date

In the terminal type: **sudo /etc/init.d/hwclock.sh restart** and hit [Enter]

Done...

---

### Post by manicka on 2005-11-12
[QUOTE=Xian]
$ sudo gedit /etc/default/rcS

```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```
[/QUOTE]
Thanks Xian, it's always bugged me not knowing how to do this :)

---

### Post by Drifter on 2005-11-12
Hey guys I just went ahead and fixed ubuntu like it should be and I went into windows and got a program to syn the time when windows boots and that takes care of it.  I would like to know how to do it without the program but as long as it works it will be ok.  I want to get away from windows someday but for now it is the only way I can use things like quicken and to burn backups of my dvd's.  I have been looking at posts for the dvd burning and I will eventually learn how in linux but for now that is why I still have xp.  The post above this, if you could explain what that does I would appreciate it.  Thanks

---

### Post by manicka on 2005-11-12
It changes the clock in ubuntu from using UTC to local time, which solves your original request to have ubuntu and windows clocks in sync.

---

### Post by manicka on 2005-11-12
Also, if you like windows programs for dvd backup have a look at this how-to to get dvd shrink working in Linux

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

---

### Post by Drifter on 2005-11-12
Now my ubuntu clock is running 7 hours fast and windows xp is keeping correct time.  How do I get unbuntu's clock to run correct time.

---

### Post by manicka on 2005-11-12
[QUOTE=Drifter]Now my ubuntu clock is running 7 hours fast and windows xp is keeping correct time.  How do I get unbuntu's clock to run correct time.[/QUOTE]
What have you done to make it like this? What settings have you changed? Which config files have you changed/comands have you run?

---

### Post by Qrk on 2005-11-12
Does your ubuntu clock sync with the server at boot up?

---

### Post by Drifter on 2005-11-13
My clock has the correct date and the time is listed as 18:35:27.  The time is 1:42 A.M. on the 12th of nov.  Is that time the same as 1:42 or is it different.

---

### Post by Xian on 2005-11-13
[QUOTE=Drifter]My clock has the correct date and the time is listed as 18:35:27.  The time is 1:42 A.M. on the 12th of nov.  Is that time the same as 1:42 or is it different.[/QUOTE]
Different. 18:35 is 6:35 pm.
What is the output when you walk through this command?:

```
$ sudo tzselect
```

---

### Post by Drifter on 2005-11-13
[QUOTE=Drifter]My clock has the correct date and the time is listed as 18:35:27.  The time is 1:42 A.M. on the 12th of nov.  Is that time the same as 1:42 or is it different.[/QUOTE]

excuse me the correct date is nov 13th now 1:53 am

---

### Post by Drifter on 2005-11-13
david@ubuntu5:~$ sudo tzselect
Please identify a location so that time zone rules can be set correctly.
Please select a continent or ocean.
 1) Africa
 2) Americas
 3) Antarctica
 4) Arctic Ocean
 5) Asia
 6) Atlantic Ocean
 7) Australia
 8) Europe
 9) Indian Ocean
10) Pacific Ocean
11) none - I want to specify the time zone using the Posix TZ format.

---

### Post by Drifter on 2005-11-13
I want to thank all of you that helped me.  I know I am slow when it comes to linux.  I think I have figured my problem out.  Both ubuntu and xp are now showing the correct time.  I hope that it stays this way, anyway this is the first time I have seen it happen and I believe it is corrected.  Here is what my problem was, I thought that I was editing the line that says utc=yes to =now but I didn't see the one on the next line.  When I figured this out and changed it to =no and set the time it fixed the problem.  Again forgive my stupidity and let me thank all of u again.  I am sure I will be needing other things fixed in the future.  But, I did learn a lot doing this even if I did it wrong for 2 days again thanks.

---

### Post by manicka on 2005-11-13
There's no such thing as a silly question. 

Keep asking. We were all newbies once :)

---

### Post by Xian on 2005-11-13
[QUOTE=Drifter]david@ubuntu5:~$ sudo tzselect
Please identify a location so that time zone rules can be set correctly.
Please select a continent or ocean.[/QUOTE]
I did mention that you should go ahead a walk through the command. :)
Finish out by selecting your timezone and subsequent prompts.

---

### Post by Drifter on 2005-11-13
[QUOTE=Xian]I did mention that you should go ahead a walk through the command. :)
Finish out by selecting your timezone and subsequent prompts.[/QUOTE]


Yes u did and I think u for your help both of u helped after I went through the posts again and tried that again and found that I had missed the correct utc=yes line.
Thanks and stay tuned I will need more help as I grow with ubuntu.

---

