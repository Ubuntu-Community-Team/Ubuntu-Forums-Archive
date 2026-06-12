---
title: "Laptop just shutsdown"
date: 2008-08-08
forum: Hardware
---

### Post by DocMSK on 2008-08-08
Hi,

Have 8.04 installed via an upgrade of the previous version of Ubuntu on my laptop (Acer).

Ever since the upgrade if I leave my laptop unattended Ubuntu just shuts down. Have tweaked all the settings (Never shutdown etc etc) and it still does. This is a dual boot WinXp/Ubuntu machine. WinXP does not exhibit this problem. Previous versions of Ubuntu did not either.

As a relative Newbee not sure where to start looking to solve this problem. Therefore, any help appreciated.

Thanks.

---

### Post by DocMSK on 2008-08-09
*Bump*

Any help appreciated. A gold star to the first person that solves this one :)

When running on AC Power I have the option in System-Preferences-Power Management "Put computer to sleep when inactive for: Never" However, when left unattended still shuts down.

Thanks in advance!

---

### Post by starcannon on 2008-08-09
DocMSK,

I'm not sure if I can help you or not, but to help others help you better (lol don't laugh at me) please post the output of:
```
sudo lshw
```

for starters

---

### Post by DocMSK on 2008-08-09
Thanks Starcannon,

Before I post the output as you suggest, I think it may be an issue of my laptop overheating. I don't use Ubuntu for many CPU intensive applications. 

What I have noticed is that when my normal screensaver (MatrixView) is running the fan is whirring away quite quickly. The CPU temp also goes up. Then the laptop turns off. So what I tried was switching my screensaver to Blank (blank black screen), and the laptop never shutsdown. The temp also hovers around 47-50C with a blank screensaver.

This laptop had 7.10 installed and I never had this problem. I then upgraded to 8.04 using the built in upgrade feature (not a clean install), then this problem started.

So, how can i determine if over heating is a problem, and if it is, how do I fix it (laptop is an Acer TM8106WLMi)

many thanks

---

### Post by starcannon on 2008-08-09
You could try installing lm-sensors from synaptic package manager and watching your cpu temperatures.

If you use Nvidia graphics you could try nvidia-settings and look at the gpu temperatures and see if they are abnormally high.

If the CPU temp is high, be sure to get some compressed air and blow the debris out of the heat sinks, often accomplished by forcing air through the intake and exhaust vents on the laptop casing (I actually take mine apart and void the warranty to do this task).

Oh and before I forget, be sure to look in bios, just do a fast reboot, and jump right into bios, and take a look at your system temps in there; most bios that I have seen have system temps available.

GL let us know what you find.

---

### Post by DocMSK on 2008-08-09
Hi,

Thanks for the suggestions.

BIOS does not display system temps on this laptop.
Using ATI graphics not Nvidia

I installed a temp monitoring utility. Ran the MatrixView screensaver and laptop shut down. Examined logs, and last temp recorded was 63C. Normal temperature right now with only a web browser running is 52C.

Any other ideas where I can look to see why this is happening? 63C doesn't seem to high, or is it?

Also noticed that if I force the cpu to run at the lowest speed then temp stays low. I wonder if its a fan issue, or I need to change the trip points?

As I mentioned before only started happening when I upgraded to 8.04 from 7.10.

Thanks

---

### Post by phidia on 2008-08-09
63C is pretty warm but from what I could find probably within the cpu temperature range. 
I think you want to know _why_ the computer is shutting down. 

Are there any messages in /var/log try the most recent messages, xorg.0.log, syslog
Something in /var/log should be leaving a clue as to why this is happening.

It would also be interesting if you could install Gutsy to a small partition or even external drive and compare.

---

### Post by DocMSK on 2008-08-10
Thanks for your reply and suggestions.

Looking at syslog I see when the systems shutsdown it does so by reporting "exiting on signal 15". I could not find anything in the syslog about "critical temperature", so may be it is not an over heating problem. The CPU temp goes up with the use of glxgears or MatrixView (as examples). Yesterday the temp went to 93C then the machine just shut down.

mmm... any other ideas? What is Signal 15?

Thanks

---

### Post by starcannon on 2008-08-10
signal 15 is sigterm you can read all about it here:
[http://www.linuxjournal.com/article/6483](http://www.linuxjournal.com/article/6483)

93c is nearly 200f, no doubt about it that it shut down to save itself on that one. Even 63c is danged hot at 145f, I'm guessing overheating is the problem. The trick now is "whats causing it". As a previous poster mentioned try running 7.10 on a small partition, see what happens. My suspicion though is that you have a coincidence going on, the cooling unit may have gotten weak at around the same time you installed 8.04. A little trial and error at this point should get you pointed towards a solution though.

By the way are the fans going gang busters when that thing is crankin out 200f of heat? If not they should be.

---

### Post by DocMSK on 2008-08-10
Thanks for all the replies.

I got myself a compressed air can today and blasted the fan opening. OMG, the amount of dust was unbelievable. I sneezed as it blew around. Now running MatrixView screensaver and logging the temp shows that the temp stays at 80C (176F) and the machine stays on. Further testing needed. The only other thing that changed this morning was reinstalling the ATI card drivers.

I am guessing the dust had something to do with the overheating.

Will continue to investigate.

Thanks

---

### Post by DocMSK on 2008-08-10
ok, reinstated the ATI hardware drivers via Envy and get same prob of over heating. Not sure if coincidence.

Will use my workaround of using "Blank" as screen saver at least machine stays on when unattended.

Not sure what else to try.

Thanks

---

