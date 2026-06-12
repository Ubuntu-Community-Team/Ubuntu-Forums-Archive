---
title: "Upgrade kernel to 2.6.30-9, Waiting channel=poll_schedule_timeout"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by Temnyj on 2009-06-19
Hello!

Ubuntu 9.04.
I upgraded kernel to 2.6.30-9. And now system monitor indicates "poll_schedule_timeout" for the waiting channel (for most part of processes). 
In 2.6.28-11 and 2.6.28-13 system monitor indicated "do_poll".
What is mean?

Thank you!

P.S.: sorry for my english.

---

### Post by eyeJ on 2009-12-28
I have the same thing in my System Monitor. I didn't notice it before today when i accidentaly selected my home folder for monitoring in desktop drapes. Ubuntu laged like crazy. I then uninstalled the desktop drapes app but didn't manage to kill the process untill I restarted the pc. Well I'l just ignore "poll_schedule_timeout" for now hopefuly it will go away by itself after next kernel update XD

runing Ubuntu 9.10 2.6.31-16-generic here

---

### Post by Ralob on 2009-12-28
I have the same issue myself, and have found no information on what the heck it even is. I am going to just wait it out and see if someone else can chime in and enlighten us. :)

---

### Post by vfargenta on 2010-01-07
Me either! But using openSUSE 11.2 64-bit...

---

### Post by neurotopia on 2010-01-18
using karmic and kernel 2.6.31-17-generic i am seeing this on most of my processes in system monitor.  any word on what/why this is?

i don't recall experiencing this before, even just a few days ago?

---

### Post by chrisdude on 2010-01-18
My kernel version is 2.6.31-17-generic and I'm running Ubuntu 9.10. I've just noticed lots of my processes have the waiting channel status of poll_schedule_timeout in the System Monitor too. Does anyone know what poll_schedule_timeout means? I first noticed this when I realized the files on my Ubuntu One account weren't being updated. I don't think this is related to my problem though. The ubuntuone-syncdaemon is just one of many of my processes that have  poll_schedule_timeout as there status.

---

### Post by guvnr on 2010-01-20
bump ..

getting this for 2.6.31.17 and 2.6.31.18

in sys monitor .. affects all processes bar 2, (that I opened manually)

---

### Post by davewantsmoore on 2010-01-24
Same.
System very unresponsive.

---

### Post by guvnr on 2010-01-25
update:  still the same "poll_schedule_timeout" notifications but system is stable ..

wifi decided to pack up though, but i guess this could be unrelated.  (wifi says "connection established" but gives no connectivity .. ethernet fine, haven't changed interfaces file)

anyhow .. maybe someone has a clue about the "poll_schedule_timeouts"??

---

### Post by liorsolomon on 2010-01-28
Same for me, the computer tends to freeze for few seconds every few minutes the only thing I noticed is that all the processes are having the waiting channel set to poll_schedule_timeout

Using Linux 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

---

### Post by e_labranche on 2010-01-31
I'm also using kernel 2.6.31-17-generic, and I am experiencing really SLOW & lagging on my comptuter. I thought maybe it was my hardrive failing or something, but it doesn't seem to be the case at all after many tests.

In my case, I am using ubuntu 9.10. It's on a 1 terabyte sata western digital in dual boot with vista on 1 patition and linux on another.

I have tried with ubuntu 8.04 on another 500gig seagate, and all works good?

I am really tired of 9.10 beeing that slow, and it seems no one are posting any solutions or any recognition that this is ineed a problem for a lot of users. I keep getting pool_schedule_timeout and my cpu jumps to 100% and almost freezing my computer for a few minutes before returning to normal? 

Does ubuntu developers know about this?

tahnks for anyone for a possible solution!

---

### Post by win2456 on 2010-02-06
Does anyone have a solution for this?  I have the exact same issue and cannot figure out how to fix it.

---

### Post by loserock on 2010-02-10
Same problems here.

I'm using 2.6.31-19-generic kernel with ubuntu karmic x64, and some application (example: Pidgin, Skype, sometime the pulse-audio) use nearly 100% cpu suddenly. In system monitor i can see 'poll_schedule_timeout' in the column 'waiting channel'. If i close the applicatin, cpu fall back to normal performance, and i can restart the application, and it works fine, but sometimes after some minutes (hours) this 'bug' starting again!

I have detected this issue firs in the 2.6.31-16-generic kernel, but is could be an earlier issue.

(sorry for my english)

---

### Post by liorsolomon on 2010-02-14
One of the softwares that frequently freeze was evolution
I ran the software in debug mode and noticed an exception CRITICAL **: atk_object_set_name: assertion `name != NULL' failed 
This exception kept on showing every few seconds and from time to time the software freezes
After collecting the stack trace and posting it to the gnome bugzilla it seems that this problem was already fixed to gtk version 2.18.4

After compiling gtk from sources to the latest version the exception indeed stop appearing and more then that the side effect of that was that I stopped getting this freeze symptoms at all!
The computer runs much faster and it seems that much less resources are used.
I have no idea if this has something to do with it but I felt that I should share it with this post.

---

### Post by liorsolomon on 2010-02-15
Well I take my advise back it seems the freezing symptoms are back on evolution so that had nothing to do with the gtk critical warning...

---

### Post by jcoles on 2010-02-16
I downloaded your How-To. Do you really believe Karmic is 
"the ultimate installation of Ubuntu's superb new operating system"?

I have been using Ubuntu since 7.04. There are always a few things broken during upgrade, but 9.10 has got to be the worst Ubuntu ever! After a disastrous upgrade from 9.04, I tried a fresh install (/home is on a separate partition). The system is still buggy, new deficiencies coming to light each time I use it. 

Can you fix  wine app + firefox = 100% CPU? That's what I got tonight. Then, I closed both the application under Wine and firefox, and the CPU was still 100%! 

Thanks for putting together this How-To. Perhaps it will help me.

---

### Post by markdashabout on 2010-03-31
I am also experiencing this. 

ps -elf | grep poll_s| wc -l

gives numbers around 90. 

System seems slow. 

VB is not installed, wine is (and is running) 

uname -a gives 
Linux bigdaddy 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

Memory usage is between 1 and 2 G. Doesnt look like any listed processes are using this.

---

### Post by eyeJ on 2010-04-13
Weird... I have the same thing still in the system monitor and I have no other serious problems with my 9.10. My system seems to be running fine despite the weird waiting channel on almost all processes.
My CPU levels are normal as far as I can tell: around 0% with occasional spikes of 3% on all 4 cores at random times.
When running photoshop cs2 in wine with firefox and ktorrent processor usage and memory usage are normal. I am running wine1.2 version 1.1.31-0ubuntu3 that I installed from the synaptic.
uname -a:
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
I'l see and report back what happens when I install the latest ubuntu for testing on another partition ;)

Has no one still answered what does "poll_schedule_timeout" mean?
Maybe it's normal and the problems here are unrelated :lolflag:

---

### Post by kioan on 2010-06-08
Any update on that issue? My computer is behaving really slow from times to times and in the system monitor I see that the "waiting channel" for almost all proccesses is "poll_schedule_timeout"

I'm running 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

---

### Post by wijit on 2010-06-12
I've got the same problem. I use 3 computers, 1 at work and 2 at home. The laptop used at work is healthy, but has not been updated only to the recent one because I left it at my work place since last Friday. The PC used at home has this syndrome since the day I upgrade from Karmic to Lucid. Until now Firefox cannot run and always gets connection timeout. The laptop used at home works flawlessly until yesterday. To be more specific, it runs very slowly and has poll_schedule_timeout for Waiting channel field of System Monitor for most of the processes.
I notice a close relationship between running slowly and poll_schedule_timeout.
Looking forward to solution(s).:guitar:

---

### Post by wijit on 2010-06-14
To update to the previous post of mine, the laptop at work has got the same problem but not really shows slowly running. Different size of RAM may cause this effect. However, I found new common incidence: Update Manager refuses to work as usual. Normally, after entering a password the pop-up showing downloading progress should be shown. Here, nothing happened.:guitar:

---

### Post by mprofitt on 2010-07-08
poll_schedule_timeout here as well...

Linux mprofitt-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

Ubuntu 10.04 LTS

---

### Post by DragonDon on 2010-09-22
Still going on here:

Linux dragondon-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

---

### Post by elderbuy on 2010-10-31
Same story here. MUCH slower than usual, same "poll_schedule_timeout" on nearly every process.
When I retired several years ago, I decided to tinker with home automation, so I wanted a machine that would draw very little power (trying to be green).  The machine has a slow processor (Samuel 2, 5.33 MHz), Compact Flash for HD, and only 512MB RAM.

The home automation never materialized, but even though we have faster machines at home, this one ended up as our "production" machine.

Ubuntu 9.10, 2.6.31-22-generic.  Regularly install all updates.  Also, system monitor shows a BlueTooth process running, even though the machine does not have Bluetooth hardware.

---

### Post by Lucrus on 2010-12-16
Same problem here. The system is often unresponsive. I noticed that just after 10.10 upgrade from 10.04.

I have 2.6.36-rc6 vanilla (mainline).

---

### Post by JTML on 2011-04-06
The same problem appears to be discussed, without a solution, at Ubuntu Bug #488849.  I suggest that people check various logs at their Log File Viewers.  I am the newest beginner, but to me this seems to be a security problem.

---

### Post by JTML on 2011-04-14
I hope that Forum protocol permits me to post here what I just posted in the Bug #488849 discussion:                                            Let me be a bit more specific: from reading my log files and checking &quot;all processes&quot; through my system monitor, I have concluded that my computer has been turned into a zombie and probably added to a botnet.  I have learned about &quot;nice&quot; values (and it was &quot;pulse audio&quot; which had been set to a high value, one which is preceded by a negative symbol--&quot;-11&quot; in my case) and a variety of other things. I suggest that anyone who has been wondering about &quot;poll_schedule_timeout&quot;, &quot;futex_wait_queue_me&quot; and &quot;ep poll&quot;shown for their processes read some of the discussions under &quot;botnet&quot; in the security area of these forums.  I plan to arrange for a clean install of Ubuntu for my computer (in other words, to have everything wiped off my disk and Ubuntu re-installed) and to learn more about securing my system before re-connecting that computer to the Internet. I also will change my IP address and see if my ISP can give me anything other than a static IP address.  I would appreciate additional suggestions for continuing my computer education. I am surprised that no one seems to have connected the &quot;poll_schedule_timeout&quot; problem with unauthorized use of computers, specifically with botnets.

---

### Post by JTML on 2011-04-14
I hope that Forum protocol permits me to post here what I just posted in the Bug #488849 discussion:    Let me be a bit more specific: from reading my log files and checking "all processes" through my system monitor, I have concluded that my computer has been turned into a zombie and probably added to a botnet.  I have learned about "nice" values (and it was "pulse audio" which had been set to a high value, one which is preceded by a negative symbol--"-11" in my case) and a variety of other things. I suggest that anyone who has been wondering about "poll_schedule_timeout", "futex_wait_queue_me" and "ep poll"shown for their processes read some of the discussions under "botnet" in the security area of these forums.  I plan to arrange for a clean install of Ubuntu for my computer (in other words, to have everything wiped off my disk and Ubuntu re-installed) and to learn more about securing my system before re-connecting that computer to the Internet. I also will change my IP address and see if my ISP can give me anything other than a static IP address.  I would appreciate additional suggestions for continuing my computer education. I am surprised that no one seems to have connected the "poll_schedule_timeout" problem with unauthorized use of computers, specifically with botnets.

---

