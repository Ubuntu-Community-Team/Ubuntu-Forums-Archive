---
title: "Suspend fails so hard it breaks the system."
date: 2008-08-19
forum: General Help
---

### Post by sexyclient on 2008-08-19
I have a problem with Ubuntu 8.04.1 Hard Heron's "Suspend" function.  First here are the machine specs (as far as I know):  Sony vaio vgc rb-30 desktop, Intel pentium 4 3.0 ghz processor w/ 800 mhz bus, 512 mb of ram, dual-boot with windows xp, 4 total partitions (windows backup, windows, swap, and ubuntu).

As far as I can tell, it enters suspend mode without a hassle, but when I try to resume it appears to take all the necessary steps - the processor starts working (I can hear the fan), the lights light up, and the monitor receives an input signal and wakes up - but Ubuntu never comes back!  

But wait, there's more: A forced-shutdown (Holding down the power button and forcing the system to power down) also fails after this point as the system doesn't go through the regular processes of starting up.  After Ubuntu has done its work, even powering on from a suspend-induced forced-shutdown picks the system up right where it left off: the blank screen of death.

To regain the use of the system I have to do a hard-forced-shutdown (performing a forced-shutdown, then unplugging the power cable from the computer for about 5 minutes).  

Hibernate works quite perfectly ... well it's dirt slow - just about as much so as the regular startup which is already about 3x longer than windows xp. I use suspend mode A LOT, and for me the loss of this function is more than enough of a reason to switch back to windows.

Can anyone out there help me out?

**UPDATE:** It has come to my attention that I'm [not the only one]("http://brainstorm.ubuntu.com/most_popular_ever/") who has noticed Ubuntu's [Suspend/Hibernate]("http://brainstorm.ubuntu.com/idea/94/") and overall [power management]("http://brainstorm.ubuntu.com/idea/81/") shortcomings...  While even a timetable for a fix *still* hasn't so much as materialized, it appears power management is being worked on - apparently since march 18, go figure...  Here's looking at you Ibex!

---

### Post by hansdown on 2008-08-19
Hi sexyclient. Sorry I don't have the expertise to help, but these will hopefully be of use to you.  [http://www.google.ca/search?q=sony+vaio+suspend+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=sony+vaio+suspend+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by sexyclient on 2008-08-20
Despite your lack of expertise, I still appreciate your support!  I've scoured google already. As far as the search provider knows, nobody has ever had the same problem with *my* hardware - even though I found scores of others with problems with their Ubuntu hibernate (and/or) suspend function.  Google provided me with no help at all.

I'm pretty disheartened at this - and a bit surprised.  As far as I know, suspend/hibernate problems have dated back years, and it's a bit of a shock that with all the hype and publicity that Ubuntu is getting that this problem - a very integral part of fundamental modern computing - hasn't made much advance.

Before I switched to Ubuntu from windows, I didn't even spare a thought that the (apparently not so) simple, common aspect of a modern OS - power management - would be in such a deplorable state.  There isn't even an option to supplement hibernate or shutdown for the timed inactivity suspend function.

---

