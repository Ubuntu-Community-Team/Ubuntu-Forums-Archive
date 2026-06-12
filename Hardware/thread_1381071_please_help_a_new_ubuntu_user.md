---
title: "please help a new ubuntu user"
date: 2010-01-14
forum: Hardware
---

### Post by nubunto on 2010-01-14
I have been trying for days to install the omnibook kernel module into ubunto 9.10 karmic with out sucsess.
My problem is I have no idea how to do this.
I have downloaded the file from sourceforge and the package was instaled but what do I do now?
I have found some examples of others compiling and installing and have tried to type exactly what they have in the terminal but it returns multiple errors,invalid files,no such files,no such directory etc.
This is my first try at an operating system other than windows and Ubuntu works great on my daughters HP omnibook Xe3 laptop but the machine will frequently freeze up requiring a hard shutdown. I beleive this is because the fan is not running and it is getting hot.
Having the one touch keys working would also be a plus.
Can some kind soul point me in the right direction or coach me in trying to install this so I can make a 9 yr.old happy
 
Thank You so much for any all help.
 
nubunto

---

### Post by nubunto on 2010-01-14
By the way,
I was able to install and figure out ndiswrapper to get the Netgear WG511v2 wireless pcmciaa card to work on the first try which impressed me but this omnibook kernel module has got me stumped.
 
Thanks again
nubunto

---

### Post by phillw on 2010-01-14
Hello & welcome to the forums,

I've had dig round for you and found a decent set of instructions. Don't be worried about it being for Jaunty, nor being about bluetooth. I cannot see from the threads if it still fails with all 9.10 installations, but for the fan issue, the install and work-around of 

> 
no the fan doesn’t work at all without the omnibook module. There is a workaround that consists in suspending to ram the pc then wakeing it up again…doing that the fan starts working.
It seems to have various mileage - some report back that the module + work around is okay, others report back that it is not.  Only one way for you to find out !!

/edit - oops - the  link --> [http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html](http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html)

Hope it all goes well.


Regards,


Phill.

---

### Post by nubunto on 2010-01-14
Thanks Phill.
I'll give it a shot tomorrow. I work nights and it's time for sleep.
By the way, I assume I type in the terminal exactly what is in bold face on that page?
I really like Ubuntu and am excited about learning something new.
 
Thanks again and I'll post back with my results.
 
nubuntu

---

### Post by phillw on 2010-01-14
> **nubunto said:**
> Thanks Phill.
I'll give it a shot tomorrow. I work nights and it's time for sleep.
By the way, I assume I type in the terminal exactly what is in bold face on that page?
I really like Ubuntu and am excited about learning something new.
 
Thanks again and I'll post back with my results.
 
nubuntu

Not quite ...

```
gksudo gedit /etc/apt/sources.lst
```Then add the lines
```

deb http://packages.kirya.net/debian/ sid main contrib non-free
deb-src http://packages.kirya.net/debian/ sid main contrib non-free 
```to the bottom of the file, then save & exit

Next,
```
sudo apt-get update
sudo apt-get install omnibook-source
sudo m-a a-i omnibook-source

```Now unless you have bluetooth on the laptop, i'd give the bit about ectype a miss and just

```
gksudo gedit /etc/modules
```and add ```
omnibook
```to the bottom of the file, then save & exit.

Reboot. If the fan still does not come on after a couple of minutes, then try putting it into suspend
then waking it backup, as per the work-around.

I'm not sure how you'll get on, but it's about all I can find .

Regards,

Phill.

---

### Post by nubunto on 2010-01-15
Thank You Phill
 
With nyour expert guidance, I was finally able to install the omnibook kernel module and now all of the extra keys work on my daughters laptop.
Sadly though, the fan still does not start up.
A few posts after mine, someone reported they solved their fan problem by disabling AHCI in the bios so I will see if that option is available to me.
 
Thanks again Phill 
 
nubunto

---

### Post by nubunto on 2010-01-15
Unfortunately, AHCI is not an option in my bios.
I sure do wish there was a way to manually turn on the fan to make sure it works.
It looks like my best option at this point is to buy a laptop cooler and see if that prevents the freeze ups.
 Thanks again Phill for all of your help.
 
nubunto

---

