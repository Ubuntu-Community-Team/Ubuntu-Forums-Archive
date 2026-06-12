---
title: "Strange RAM problems"
date: 2014-02-21
forum: Hardware
---

### Post by honza-hejzl on 2014-02-21
I have Acer XC600 which has 2GB RAM only. Well, I had decided to increase that and bought a new module.

This is the basic module to which I wanted to add the new one:

Handle 0x0024, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0007
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix/Hyundai
    Serial Number: 2D541117
    Asset Tag:                       
    Part Number: HMT425U6AFR6C-PB      
    Rank: 1
    Configured Clock Speed: 1333 MHz

And so I have bought this one:

[http://www.evolveo.eu/cz/zeppelin-ddr3-4gb-1333mhz-cl9](http://www.evolveo.eu/cz/zeppelin-ddr3-4gb-1333mhz-cl9)

After the install, the systems worked well, all sensors showed the new amount, 6144 MB. But these problems had started:

- Chromium as well as Firefox were constantly crashing, usually after a few seconds;
- the system immediately wanted to update both of them;
- the update failed because of strange broking of packages.

I supposed this could be the problem of unpacking and loading files to the new added RAM. And so I tried memtest86&#8212;**without errors!** After that I tried liveCD, Firefox was stable (at least during few minutes of browsing). I was desperate and decided to try fresh install. Everything worked well, new clean install with updates was done. And then those strange problems with browsers **emerged again**. With that it again had problems with updates.

I simply can't imagine where could be the problem. It does not seem to be the one of really broken RAM module. The only one I could suppose is Ubuntu has problems with two different RAM sizes. However, I have positive experiences with that from my old laptop, where I had 1+2GB modules (for years without any problems).

Neither me nor my hardware-skilled colleague know what could be going about here.

Any help appreciated. :-|

---

### Post by deadflowr on 2014-02-21
Was that 4GB added RAM one stick?
Might be the problem is the system has a max limit, which the stick goes over.
Just a guess though.

---

### Post by varunendra on 2014-02-21
How long did you run memtest+ ? How many Passes it passed?

I recently experienced exactly same problems as you, and much more than that (because I use a lot of memory hogging programs simultaneously on Unity desktop).

When I bought my laptop two years ago, it came with 2GB onboard DDR3 - 1333MHz (Hynix). I immediately upgraded to 4 GB with a Transcend 2GB DDR3-1333MHz. It ran fantastic until I got greedy and decided to replace the 2GB module with a 4 GB one.

Local market was facing some weird shortage problems and I couldn't find any Transcend or Kingston or any decent brand. Ended up with a 4GB DDR3-1333MHz "**Irvine**" module *(remember this name - **Irvine**, and also remember that you should avoid it at all costs)*. Even the first glance at its packing cried out loud to me that this was a crap module. But... having no other options available at that time I replaced the Transcend with it anyway, and ran memtest+ successfully for about 6 hours.

Then.. I had to leave the city, packed the laptop and left. Within a week, when I got the first opportunity to use the lappy intensively, it crashed my running session - had tens of chromium tabs open. Since then it crashed not less than 4-6 times daily (I hardly shut down my laptop - it keeps running 24x7 if possible). It continued for about one and a half month when I finally ran out of patience.

Now, that additional 4GB module is resting in peace in my bag (no, it didn't die, I just said a "thank you very much, goodbye sir" to it). I'm back to 2 GB and am waiting to meet my beloved 2GB Transcend again, which is waiting for me in the other city at my brother's home where I left it.

My Laptop supports upto 6GB RAM, officially. (chip wise 16 GB, but I'm not thinking about that).

**Morale of my comic/tragic/to-be-comic-again story :** Don't trust memtest results blindly, especially if you have run it less than 24 hours. 4-6 passes mean nothing. Oh, and certainly don't trust cheap brands, even if they are giving it for free, it may be better to stay away from them. Not sure if your model falls in that category.

---

### Post by honza-hejzl on 2014-02-21
Thanks,

Honestly, I did the test just few times (2–3×)…

The exact phrase from the spec document: Maximum memory: 8 GB (using two 4 GB modules)

I guess this could be really the problem, they probably should be equal in size. I will try to put there just the new as recommended and will see, hope I won't broke something there :)

I will let you know, thanks!

---

### Post by varunendra on 2014-02-21
> **honza-hejzl said:**
> The exact phrase from the spec document: Maximum memory: 8 GB (using two 4 GB modules)

I guess this could be really the problem, they probably **should be equal in size**.

I don't think that could be the cause, as long as the voltage and frequency ratings are matched with the specified rating (and they do for DDR3 modules). Even ancient DDR1 based systems have been able to handle different sizes nicely (including one small and one largest possible size), and the technology is getting better at handling this.

Also, have you tried using up the memory with activities other than anything related with browsing? Like opening many programs and files, many different tabs in your File manager (which is Nautilus in default Ubuntu) with hundreds of files listed in each of them, then frequently switching between programs and tabs etc. (so that memory swapping starts happening vastly and frequently).

If the crashes are limited to only browser or update related activities, it may not be hardware at all!

But if it does crash in anything that makes the memory usage/swapping frequent, then it may be hardware, most probably, but not necessarily memory.

For example, I have also seen similar things happening when using "Unlocked" cores of AMD phenom/sempron cores. These cores are disabled by default because they *may be* faulty, but certain motherboards allow to 'Unlock' them to try your luck and see if they are usable (thus almost doubling the processor's power). The reason of crash in such 'Unlocked' cores are usually that either they are indeed defective, or because their requirement of 'additional' voltage/power was not sufficed (a mistake by user, or incapability of the SMPS).

Besides these two, I'd imagine (theoretically), that if any component that is involved in the whole data I/O process gets defective or starts malfunctioning for ANY reason, you'd experience the same problem.

In my real world experience so far, the following have been the cause of such issues, with their frequencies given roughly (and vaguely) on a scale of 100 times of occurrence of such issues :

[table="width: 80%"]
[tr]
	[td][COLOR="#800000"]**Memory :**[/COLOR][/td]
	[td] [COLOR="#800000"]only about 15 times of such case[/COLOR]s[/td]
[/tr]
[tr]
	[td]**Loose cards/cables :**[/td]
	[td]about 40 times[/td]
[/tr]
[tr]
	[td]**Corrupt partition/OS :**[/td]
	[td]about 25 times[/td]
[/tr]
[tr]
	[td]**Weared out/malfunctioning power controlling components :**[/td]
	[td]about 12 times[/td]
[/tr]
[tr]
	[td]**A misbehaving program/process :**[/td]
	[td]6 times[/td]
[/tr]
[tr]
	[td][B]Other, usually non-natural reasons
(like 'Unlocked' CPU cores) :[/B][/td]
	[td]2 times (not counting 'Overclocking', that would make this figure about 12 times out of 100).[/td]
[/tr]
[/table]
I have excluded some other known causes that exist in the world of computers, I just haven't experienced them myself yet (like a healthy CPU starting malfunctioning over time).

Anyway, I didn't mean to confuse you with possibilities, just sharing my experience here :P

About YOUR problem, given the information we have so far, I seriously suspect it to be the memory or memory controller. I'd be curious to know how your new combination works. :)

---

### Post by honza-hejzl on 2014-02-22
Thank you a lot for the vast information!

(Just a notice, yes and no, I have not tried those tests with other apps as you mentioned I could but using the desktop in a common sense was OK.)

However, I have tried to add another one module of 2GB AND different frequency, it worked well, without any problem. Than I tried to let there just the new 4GB module and those strange problems emerged again. For sure I did 4 passes of memtest, without errors (longer testing probably has no logic because problems are evident immediately after the using of the memory by browsers). It seems to be a sort of magic here! I will try to return the memory back to the seller and will change it for another one module of 2GB. I think it could work and be enough for intensive browsing of my tons-of-tabs loving wife.

I will let you know the result, thanks again!

P. S. The manual for my PC mentions in compatible RAMs table they should be ECC! Don't know it that could count, the tested 2GB was not ECC (afaik).

---

### Post by tgalati4 on 2014-02-23
I would stick to quality RAM sticks with matched sizes.  So either go to 4GB or 8GB and run memtest for 30 full cycles to validate.  And don't change RAM before a business trip.

---

### Post by honza-hejzl on 2014-02-23
> **tgalati4 said:**
> And don't change RAM before a business trip.

:) definitely!

---

