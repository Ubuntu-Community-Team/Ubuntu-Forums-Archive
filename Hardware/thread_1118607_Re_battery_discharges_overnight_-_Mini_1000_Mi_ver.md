---
title: "Re: battery discharges overnight - Mini 1000 Mi versus Asus 901"
date: 2009-04-07
forum: Hardware
---

### Post by aspergerian on 2009-04-07
My HP Mini 1000 Mi has been losing from 7-9% of its charge overnight, when left with the battery in, the computer turned off, and current turned off. In the morning (when this effect is noticeable), the current has been restored, the computer booted immediately, the battery level read immediately. Other people have noticed similar discharging of their HP Mini 1000.  One other person has reported that when he removed the battery from his HP Mini 1000, a noticeable discharge did not occur overnight, even though his Mini discharges ~7% if the battery remains in his Mini overnight. Last night I compared discharge rates for my Asus 901 and for my Hp Mini 1000 Mi. 

The overnight test had the following results:

HP Mini 1000 Mi running actual Hardy Heron: 
    Fully charged all evening. Current disconnected & battery removed at 8:30pm. At 3:30 this morning, battery was reinstalled, current restored, then the machine was booted. Battery had not discharged overnight when removed from the HP Mini 1000 Mi.  

Asus 901 running actual Hardy Heron. 
    Fully charged all evening. Current was shut off at 8:30pm, battery was allowed to remain in the Asus 901 while it was off overnight. At 3:30 this morning, current was restored, 901 was immediately booted. Battery had not dischared overnight while remaining in the Asus 901. 

The problem of overnight battery discharge seems a talent of the HP Mini 1000 Mi. The Asus 901 did not discharge its battery overnight and never has since first purchased in July 2008. Both machines are running actual Hardy Heron, thus Ubuntu 8.04 does not seem to be the crucial factor causing the HP Mini 1000 battery to discharge overnight. The battery in my Mini and in one other person's Mini seems not to blame because when removed from the Mini, neither his nor my HP battery lost its charge overnight. 

My hunch is that owners of HP Mini 1000 computers may be wise to remove the battery if the computer is to be left unattended and not plugged in for more than several consecutive days.

---

### Post by aspergerian on 2009-04-08
Battery drain clue?  I've been keeping external speakers plugged into my HP Mini 1000 running Hardy Heron.  Last night the fully charged Mini was turned off (yep, "off"), the current source disconnected. In recent weeks that would generate ~7% battery discharge across 8-10 hours. This battery discharge may have occurred only when the external speaker cord remained connected. Last evening, I disconnected the external speaker cord. This morning, my HP Mini 1000 did not indicate that discharge had occurred. 

- - - - 

cat /proc/version
Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 21:47:28 UTC 2009

---

