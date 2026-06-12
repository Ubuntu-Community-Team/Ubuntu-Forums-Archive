---
title: "Spontaneous rebooting and syslog not updating"
date: 2019-11-18
forum: Hardware
---

### Post by Clueless Wonder on 2019-11-18
I have a Dell XPS Studio 7100 on which I just installed Lubuntu 18.04.  It has begun doing a spontaneous reboot every so often.  One thing that seems to trigger it is when I am reviewing the syslog file, scrolling through it....but it doesn't do it every time then, either.  I have a 430 watt power supply, one HD, 2 DVD drives, and a Radeon 300se graphics card. I switched out the CMOS, in case that was the problem, and it didn't seem to change anything.

Also, the syslog hasn't updated since 9:18a this morning, and I had the PC on for 3 hours after that (spontaneously rebooting every 20 - 30 minutes).  

Not sure if these two issues are connected, but wanted to share them both in case it helps point out the issue.

I am planning to run a Mem28 test tonight and wanted to check here to see if anyone has any other ideas.

Thanks!

---

### Post by Autodave on 2019-11-19
That sounds like a RAM problem to me.  Possible power supply, but more likely RAM.  Run the RAM test and see what that gives you.

---

### Post by Clueless Wonder on 2019-11-19
Hi Autodave -

Thanks for the reply!

It was rebooting every couple of minutes when I first turned it on this morning.  I decided to remove the dedicated GPU before running the memtest to see what that did.  It has been running now for 1.5 hours without a reboot.   So....would you think that would mean that there is a driver (or otherwise) conflict with the card (although it seemed to be working great otherwise) or that the card required too much of a drain on the PSU and that a 500w might improve things (over the 430w I currently am using)?  

I just finished the memory scan and it passed with no errors.

Also...syslog is now updating correctly.  So, it seems that the PC is working fine without the card.  Just trying to figure out why the card is causing a problem.

Interested in any thoughts with this additional info.  Thanks!

---

### Post by jetsam on 2019-11-19
>  or that the card required too much of a drain on the PSU and that a 500w might improve things (over the 430w I currently am using)?

...even not knowing all that much about pc hardware in detail, what you're suggesting is entirely plausible here.  It's very common for systems to shut down in whole or in part in the case of too much power or voltage or current.  They often cycle, because the safety system also detects nothing is wrong after the shut down, it soon turns things on again.  It's a sort of logical power oscillation, and it can be damaging in that computers weren't designed to cycle so often...  Not badly damaging, but it's something you want to stop and get to the bottom of.

---

### Post by Autodave on 2019-11-19
Sounds like you need a new power supply.  Just for a little more info, what was the GPU that you removed?

---

### Post by Clueless Wonder on 2019-11-19
Hi Autodave - it was a Radeon x300se.  

Are you thinking that the PSU is bad, or just not powerful enough to handle the GPU?  I ask because a) I had used the card in a PC with a less PSU without a problem, and b) this PC runs fine without the card.

Edit...

I just put the Radeon card in a Optiplex 790, which has the same OS and 500 watt PSU.  It is freezing when I try to scan the syslog file.  The other PC was rebooting when doing the same thing.

---

### Post by Autodave on 2019-11-20
You could possibly have a bad / shorted GPU.  That is rare, but possible.  That card doesn't use much power: only about 30 watts.  So, I kinda doubt that that would kill 2 power supplies.

---

### Post by Clueless Wonder on 2019-11-24
I am thinking you are right...it seems to be a bad GPU.  Others are working fine.  I will close this as solved.

Thanks!

---

