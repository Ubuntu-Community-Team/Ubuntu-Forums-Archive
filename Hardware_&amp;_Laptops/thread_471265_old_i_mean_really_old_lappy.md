---
title: "old i mean really old lappy"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by mrreality13 on 2007-06-11
Hi all,
I found an OLD lappy i want to play with its:p hehe a
    pent.166 mhz /16 megs ram/2.1 gig hd 
should i try puppy,or feather  or dsl,on it? or can any one recomend a distro that will run with only 16megs ram OH and it does have a blazing fast 8x cd drive--lol

---

### Post by equant on 2007-06-11
I would try Slackware (using the lowmem kernel) or Deli Linux.  DSL and Puppy are meant for machines with more memory, and I never had as much luck with them as Slackware.  If you can, upgrade the memory on that machine.

I have slack running nicely on a 100MHz Toshiba laptop with 40 MB of memory, and a 50MHz 486 fujitsu tablet with 8 MB of memory.

A few random tips...  Limit the number of virtual consoles you run.  If you're going to use X, use a wm like ctwm, fvwm, twm, etc.  Even xfce and icewm have trouble at these levels.  Use sh instead of bash.  aterm is a light version of xterm.  Eliminate daemons you don't need (cups, sshd, etc).  It's been a while since I've looked, but dillo is an ok graphical web browser for slow/old machines, but elinks is a goo alternative too.  Use lsmod to make sure you're not running modules you don't need.

Most likely the PCMCIA slot is 16bit.  You can get a wireless card, but make sure it's 16bit, and not a 32 bit PC card.  The orinoco golds are well supported pcmcia wireless cards.  I think some might have been 32 bit, but I have several that are 16 bit.

Sorry if this is all obvious or not what you wanted to know, I just get excited about old hardware getting a new lease.

Good luck, and take pride in using old hardware.

Nathan
[http://retards.org/](http://retards.org/)

---

### Post by mrreality13 on 2007-06-11
Thanx it helps:popcorn:
,i dont have much $$ so i like to play with old hardware as to adding ram I may be able to IF a coworker remembers to dig up a old lappy he has.

Right now im having a heck of a time geting my old cd burner to burn slow enough for the old drive in the lappy and floppys arent an option as i have none.

 i pulled the cd drive from lappy and its a 12x ,I had a old cd burner in a box and im trying to get kb3 to see it , 
its top burn speed is 24x so i should be able to set it to 12x or a bit slower

---

### Post by MaximusTG on 2007-06-12
Do you mean that you want to burn at 12 speed, because you think that the old cd drive in that laptop wont be able to read cd's burnt at a higher speed? Because that doesn't matter at all... the max speed of the cd drive simply indicates how fast it can read data of a cd.

---

