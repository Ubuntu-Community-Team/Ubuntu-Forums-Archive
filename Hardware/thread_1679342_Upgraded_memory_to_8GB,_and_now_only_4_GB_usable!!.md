---
title: "Upgraded memory to 8GB, and now only 4 GB usable!!"
date: 2011-01-31
forum: Hardware
---

### Post by freesparks on 2011-01-31
Hello all,

   I upgraded my Dell Latitude E6510/ Intel(R) Core (TM) i3 CPU M380@2.53 GHZ to
8GB ram and now I'm getting confirmation that only (3.43 GB) is usable?  Is a Ubuntu 10.10 64bit even worth it?  If it is what are some of the downfalls that I will encounter.  Will most of my software no longer work?  Will they upgrade accordingly.  And as far as swap goes, I have it configured to 8GB is this suitable, or overkill.  I read somewhere that swap should typically be double the size of the physical memory that is installed on the system, if so, is it necessary to even worry about it considering I am running Ubuntu 32bit??  Any insight on this would be more than appreciated.

Best Regards,

freesparks

---

### Post by fabricator4 on 2011-01-31
> **freesparks said:**
> Hello all,

   I upgraded my Dell Latitude E6510/ Intel(R) Core (TM) i3 CPU M380@2.53 GHZ to
8GB ram and now I'm getting confirmation that only (3.43 GB) is usable?  Is a Ubuntu 10.10 64bit even worth it?

You need to be running a 64 bit OS to access more than 4 GB of memory, so if your machine will run it, that's what you need to use.

>   If it is what are some of the downfalls that I will encounter.  Will most of my software no longer work? 

As far as I know, all the programs will work. 64 bit applications will handling the paging more appropriately, in cases where the file sizes you are working require more memory than 4 GB. My understanding is that the testing and development for the 64 bit versions is not as mature as the 32 bit.  Your mileage may vary.


> 
 Will they upgrade accordingly.  And as far as swap goes, I have it configured to 8GB is this suitable, or overkill.  I read somewhere that swap should typically be double the size of the physical memory that is installed on the system, if so, is it necessary to even worry about it considering I am running Ubuntu 32bit??  Any insight on this would be more than appreciated.


When running a 32 bit OS, there's not much point having the swap more than twice the size of the addressable memory. Many people say the minimum size should be the same as the addressable memory size but even that is not written in stone.  It depends on your computer and how you use it.

Chris

---

### Post by cascade9 on 2011-02-01
> **freesparks said:**
>  And as far as swap goes, I have it configured to 8GB is this suitable, or overkill.  I read somewhere that swap should typically be double the size of the physical memory that is installed on the system, if so, is it necessary to even worry about it considering I am running Ubuntu 32bit??  Any insight on this would be more than appreciated.

Like fabricator4 said, swap isnt written in stone. 

If you want to use hibernate swap must be bigger than your RAM size, but if you dont want to use that feature then it wont matter much if your swap size is smaller than RAM. 

> **fabricator4 said:**
> You need to be running a 64 bit OS to access more than 4 GB of memory, so if your machine will run it, that's what you need to use.

Nope, you dont have to use 64bit to see 4GB+ of RAM. PAE- 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Getting the PAE kernel should let you see all 8GB. Its a bit of a hack though, and is limited to 3/4GB per process. 

I'd go for 64bit. Aside from a few odd programs (very uncommon) or some rare drivers for peripherals everything should work.

---

### Post by fabricator4 on 2011-02-01
> **cascade9 said:**
> Nope, you dont have to use 64bit to see 4GB+ of RAM. PAE-

I stand (sit) corrected.

I'd try the PAE kernal, it sounds interesting, except I like my machines to be rock solid and more importantly: I don't have the RAM  :-)

> 
If you want to use hibernate swap must be bigger than your RAM size, but if 

Even this is not a "must" situation.  The swap file on the 8 GB SSD in my Eee PC is much less than the 1 GB RAM size for obvious reasons.  I've never had a problem coming out of hibernation but I do keep an eye on how much RAM I'm using.  Maybe one day I'll shoot myself in the foot with it, but I'm finding 10.04 so efficient with memory it takes a real effort to use a significant part of it, at least with the types of things I use a tiny netbook for. (Current usage, 224 Mb ;-))

Chris

---

### Post by cascade9 on 2011-02-01
> **fabricator4 said:**
> Even this is not a "must" situation.  The swap file on the 8 GB SSD in my Eee PC is much less than the 1 GB RAM size for obvious reasons.  I've never had a problem coming out of hibernation but I do keep an eye on how much RAM I'm using.

I stand...sit...actually, with the weather here tonight, I sweat corrected is probaby the most accurate. :lolflag:

Thanks for that information, I thought that was the case (that as long as swap is bigger than RAM is use hibernation would work). But I'd never got confirmation before.

---

### Post by freesparks on 2011-02-01
Guys thanks so much for all your expertise, I can't thank you enough.  I suppose I can play on my other laptop, that's what I bought it for, in case I break something.  Now, if I can just find the steps in upgrading.  Is it better to burn 10.10 64 bit to CD, or can I upgrade from the Upgrade manager?    I'm guessing you're sweating from the heat from your heater.  How cold is it up there, be it northeast, or midwest??  

Thanks so much guys,

Nevins Duret

---

### Post by fabricator4 on 2011-02-01
> **freesparks said:**
> Guys thanks so much for all your expertise, I can't thank you enough.  I suppose I can play on my other laptop, that's what I bought it for, in case I break something.  Now, if I can just find the steps in upgrading.  Is it better to burn 10.10 64 bit to CD, or can I upgrade from the Upgrade manager?    I'm guessing you're sweating from the heat from your heater.  How cold is it up there, be it northeast, or midwest??  

Thanks so much guys,

Nevins Duret

I'd have to recommend installing from the CD over an upgrade. Upgrades are more reliable than they were, but there's still a good chance of it going awry.  It's outside my experience but that may go double for the 64 bit version.  I wouldn't even consider upgrading from 32bit to 64bit, even if it is possible.

We're both in Brisbane ("Brisb'n") Australia.  I think you're thinking of BrisBANE, Canada.  Check the news, Cyclone Yasi, North Queensland Australia.  We're not north, but the weather is hairy and scary, and set to get worse.

Chris.

---

### Post by freesparks on 2011-02-01
Godspeed Fabricator4,

   I'll be praying for you, midwestern N America and the Northeast is supposedly going to get blasted with heavy snow.  I'll let you know how I fair out when I have some time.  For now, it's Python, Web Development, and animation on my agenda.

Best Regards,

freesparks

---

### Post by timsdeepsky on 2011-02-01
I run 10.10 Maverick 64 bit on my system with 8 gigs of ram and quad 3.5 processors....It sees all the ram and i found that i fared better when installing from the iso,,instead of the upgrade....I have to say,,once i got it tweaked,,i noticed a considerable difference when i run cinelerra....Cinelerra seems to runs much better with the 64 bit and bigger ram,,especially when rendering hd video....Rock on 64 bit!!

---

### Post by timsdeepsky on 2011-02-01
By the way......I live in Iowa and we are in a blizzard right now....Can not see 2 feet away outside....Good luck to you in the land down under,,,,i see you have been getting hammered with the weather for a while now....

---

### Post by Khakilang on 2011-02-01
It seem that the topic has change. It is because the Cafe has been disable? Anyway nothing but rain here for the past 2 days. Back to the topic. Has the the OP solve the problem?

---

### Post by cascade9 on 2011-02-02
> **fabricator4 said:**
> We're both in Brisbane ("Brisb'n") Australia.  I think you're thinking of BrisBANE, Canada.  Check the news, Cyclone Yasi, North Queensland Australia.  We're not north, but the weather is hairy and scary, and set to get worse.

Brisbane, or bris-bin, or bris-veags (obsolete, but those days of illegal casinos and dodgy brothels are coming back) or brisneyland (the new, child-safe version of brisvegas) :lolflag: 

I didnt know there was a Brisbane in Canada, but there is another one in California- 

[http://en.wikipedia.org/wiki/Brisbane,_California](http://en.wikipedia.org/wiki/Brisbane,_California)

> **freesparks said:**
> Guys thanks so much for all your expertise, I can't thank you enough. I suppose I can play on my other laptop, that's what I bought it for, in case I break something. Now, if I can just find the steps in upgrading. Is it better to burn 10.10 64 bit to CD, or can I upgrade from the Upgrade manager? 

You'll have to do a fresh install to change from 32bit to 64bit.

---

