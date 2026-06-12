---
title: "State of the suspend/hibernate bug?"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-03-26
The suspend/hibernate bug has been a big pain for me on my Ubuntu laptop. I am just curious if anyone has any idea if and when it will ever be fixed? Also, I am curious if there are currently any tweaks or hacks out there that can help with the issue and maybe make suspend and hibernate more likely to work?

Thanks.

---

### Post by Whiffle on 2008-03-26
Which hardware are you using?  Its not an overall bug, but hardware specific.

---

### Post by JaggedOne on 2008-03-26
Really? I thought all linux systems suffered from the bug. I am using a Dell XPS M1530 running Ubuntu 7.10.

---

### Post by Whiffle on 2008-03-26
My T43 thinkpad suspends perfectly.  It might hibernate too, I dunno, I've never actually tried to use it ... 

On the other hand, my desktop is completely worthless it seems as far as sleep and hibernate goes, even in windows.

---

### Post by JaggedOne on 2008-03-26
Then is there any way to fix it on my system?

---

### Post by luvit on 2008-03-27
I have a Compaq Presarion C700 ( C714NR ) with various sleep and hibernation problems.
If someone could give me direction on finding my laptop's "model" of sleep technology, I may be able to google the rest of the specific details.;)

---

### Post by TrevorBradley on 2008-03-27
I tried posting specific information 3 days ago in my own thread, but no replies.. so I'm hopping on the generic bandwagon.  I can't use hibernate or suspend on my Fujitsu P2120 without crashing or black screening.  I'm wondering if ubuntu 8 will be any better.

At this point I'm probably going to be sticking with XP for the machine if I can't get linux to work properly on it... :(

---

### Post by letitworknow on 2008-03-27
i have been having problems with my hibernate also. im using a intel based machine.  
     it was working fine for the first 3 or 4 months that it.  then i started to get a message that said HAL (Hardware Allocation Layer) error.  Now i don't even get that. my screen goes blank i get a flash of code to fast to read and then a log in screen.  

     Its my mission to find out what is going on tonight so ill keep you updated if i find anything out

---

### Post by Whiffle on 2008-03-27
> **luvit said:**
> I have a Compaq Presarion C700 ( C714NR ) with various sleep and hibernation problems.
If someone could give me direction on finding my laptop's "model" of sleep technology, I may be able to google the rest of the specific details.;)


That one is new enough that it should use ACPI.  What kind of problems are you having?

---

### Post by luvit on 2008-03-27
> **Whiffle said:**
> That one is new enough that it should use ACPI.  What kind of problems are you having?

If I manually suspend the laptop and put it in my laptop bag.
 I pull out the laptop - it is pretty warm and if it does wake up (battery is very low)

If computer goes to sleep automatically it won't wake up... or powers on like a fresh boot.

I've done very little hibernating, but I believe it too would conduct a fresh boot when I try to wake it up.

I use Gnome, and the power management preferences timers are setup for screen blanking and suspend.

---

### Post by JaggedOne on 2008-03-27
Does anyone have an answer for us?

---

### Post by NightwishFan on 2008-03-27
My desktop hibernates well as far as I have seen. It appears to suspend, but not wake up from it. I am not sure if the suspend works perfectly as my power button glows dull orange when it is in suspend mode but not so with Ubuntu. I am sure this is fixable but It is not a high priority for me.

---

### Post by jespdj on 2008-03-28
> **JaggedOne said:**
> Really? I thought all linux systems suffered from the bug. I am using a Dell XPS M1530 running Ubuntu 7.10.
No, not all Linux systems suffer from such a bug. In fact, my XPS M1330 suspends and resumes without any problem.

---

### Post by makeyre on 2008-03-28
My IBM Thinkpad T60 will die (screen is random characters when reopened) if I shut the lid.  I have set "When laptop lid is closed" to "Do nothing" under power management and the problem persists.  I have to CTRL-ALT-BKSP to restart X whenever this occurs.  So I can't pick my laptop up, close the lid, and move it anywhere unless I turn it off first, or I will lose all my work.

What information should I supply to help people triage this bug?

---

### Post by chronusdark on 2008-03-28
> **jespdj said:**
> No, not all Linux systems suffer from such a bug. In fact, my XPS M1330 suspends and resumes without any problem.

im using an m1210 which was succeeded by the 1330 did you do anything or did it work out of the box?

---

### Post by alliterationArtiste on 2008-03-30
> **letitworknow said:**
> i have been having problems with my hibernate also. im using a intel based machine.  
     it was working fine for the first 3 or 4 months that it.  then i started to get a message that said HAL (Hardware Allocation Layer) error.  Now i don't even get that. my screen goes blank i get a flash of code to fast to read and then a log in screen.  

     Its my mission to find out what is going on tonight so ill keep you updated if i find anything out

I have exactly the same issue and I'm also on the same mission! But my system is only three days old. I've been busy trying to break it on the theory that if it goes wrong now I lose that much less time and effort than months down the road when the system is bedded in with all sorts of critical stuff in it. I was poking and prodding it and can't remember exactly what I did which is rather annoying. What I did do was selectively follow a tuning guide. I'm compiling a kernel at the moment (why walk when you can run!!) and once It's over I'll try walking backwards over the changes as much as i can remember. Let me know if you find anything. Will do the same.

---

### Post by luvit on 2008-03-30
> **luvit said:**
> If I manually suspend the laptop and put it in my laptop bag.
 I pull out the laptop - it is pretty warm and if it does wake up (battery is very low)

If computer goes to sleep automatically it won't wake up... or powers on like a fresh boot.

I've done very little hibernating, but I believe it too would conduct a fresh boot when I try to wake it up.

I use Gnome, and the power management preferences timers are setup for screen blanking and suspend.
I started testing my sleep and hibernating problems and they seem to be error free for short periods (lab).
But just this morning I woke up my laptop just fine and I had a balloon stating there were errors... but I appeared to work fine. I'd like to get to the bottom of the error alerts.

I have taken no action to solve this for many weeks... could ubuntu's last couple rounds of updates have solved it?;)

*I have not yet tested my earlier experience of my sleeping laptop getting warm in my carrrying case*

---

### Post by luvit on 2008-03-30
Update. Since i've written the last post my[COLOR="Blue"] laptop has gone to sleep, but would not wake up. power light appears, wireless light enabled, but not connected (amber), keyboard is unresponsive (capslock, Ctl+Alt+ F8, F12, Backspace, etc).[/COLOR]

Seems no matter how many short tests I do it succeeds to wake up... but in the real world when the laptop self chooses to sleep/hibernate for various lengths, it refuses to wake up and usually has the problem I highlighted in blue text. ;)

---

### Post by alliterationArtiste on 2008-03-30
I've solved my problem by setting CONCURRENCY=none in /etc/init.d/rc file. This not only fixed by HAL issue but brought back my suspend and hibernate functionality. That'll teach me to blindly follow 'tuning' guides.

---

### Post by nfjd78 on 2008-03-30
Ok...
So i'm new to all this stuff - as in 2 weeks since the first install ever of any linux based OS.
and.. i guess i have this same problem... when order the machine to hibernate, it seems to reboot and "locks" in a screen where my password is asked... - to log on again...
I have an Intel based machine, if that helps...
Thanks...

---

### Post by Radon on 2008-03-30
I've got an Acer 5104 laptop with TurionX2 and integrated ATI graphics, both suspend and hibernate work without issue with the 2.6.24 and 2.6.25-rc7 kernel :)

nfjd78: I'd suggest you wait 24 days till the next Ubuntu is released, it should fix your issue.  In the meantime try the latest Ubuntu [8.04 beta]("http://www.ubuntu.com/testing/hardy/beta") LiveCD.

---

### Post by jespdj on 2008-03-31
> **chronusdark said:**
> im using an m1210 which was succeeded by the 1330 did you do anything or did it work out of the box?
Worked out of the box with Ubuntu 7.10.

---

### Post by Radon on 2008-03-31
> **jespdj said:**
> Worked out of the box with Ubuntu 7.10.
Good on Dell for working with Canonical to make the hardware as painless to setup as possible.  :)

---

### Post by plurt on 2008-03-31
I have noticed that every time after suspend or hibernate, it changes the attribute of my swap from
 
*/dev/sda7: TYPE="swap" UUID="4c11d204-1be0-488d-8c10-468938ab170f"*

to 

*/dev/sda7: TYPE="swsuspend" UUID="4c11d204-1be0-488d-8c10-468938ab170f"*

---

