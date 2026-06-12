---
title: "Dual Core Processor Troubles"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Tumpster on 2007-07-06
This is going to sound like a copy of my last posting but read through please. :) I purchased a new Optern 164 AMD Dual Core Processor (Socket 939), I had previously been running a AMD Athlon 3000+ 64 bit chip w/ dapper drake. I just put in the new processor and hooked up the heatsink and sat everything as was in the case and cleaned it up a little bit. Everything runs fine, except now I'm getting random lock ups in ubuntu, I was playing UT2004 and in mid shot it froze, or when booting up it will freeze, or loading up a video it will freeze. What can I do to fix this or what may be causing my ubuntu/comp to do this?  My specs are as follows

AMD Opteron 165 Dual Core
3 sticks of 512mb pc3200 ram
80gb hard drive
250 gb hard drive
DVD Burner
DVD Rom
MSI K8NEO PLatinum Mobo
TV Tuner Card
ATI X700 Pro
Netgear Wireless card
Sound Blaster live 5.1 card

Any help is appreciated! Thanks@!

---

### Post by scxtt on 2007-07-06
overheating?  does your bios (or lm_sensors) tell you the CPU temp?

---

### Post by fredj on 2007-07-07
Does it freeze forever or if you leave it does it recover?

---

### Post by Tumpster on 2007-07-07
It's freezes forever like i have to reboot the machine entirely. What could this be? I have the heatsink sitting properly and it's on great fans!! :(

---

### Post by scxtt on 2007-07-07
yeah, but what kinda temps is it running @?

---

### Post by Tumpster on 2007-07-07
I'll have to get home shortly and post up what it is.....

---

### Post by Tumpster on 2007-07-07
Ok so I've looked, when I booteed it said it was sitting at 93 degrees, after it locked and I looked at a reboot it said it was sitting at 109 degrees. What is ok or acceptabale and what should I do now to keep it from locking up?

---

### Post by scxtt on 2007-07-07
is that Celsius or Fahrenheit?

---

### Post by Tumpster on 2007-07-07
Fahrenheit, sorry... :)

I'm using the heatsink that the core came with, otherwise I have this one I can throw on. 
[http://www.keenzo.com/showproduct.asp?ID=921660&ref=FRG0](http://www.keenzo.com/showproduct.asp?ID=921660&ref=FRG0)

---

### Post by scxtt on 2007-07-07
those temps are just fine ... my AMD X2 3600+ runs b/t 86-100 and my intel P4 2.4Ghz runs b/t 105-120 -- no freezes - so at least that should be able to be ruled out ...

can you boot from a LiveCD and use it for a good amount of time w/o freezes?

---

### Post by Tumpster on 2007-07-07
it's really varying on what times things freeze, i mean now I've got my  box fan over my case and i've been running for some time now, same with the last time, I removed the box fan and shortly afterwards it locked up. Theres no real frequency on when  it does it of course.....I'm awaiting to see if it freezes at all when I have the box fan there.

---

### Post by Tumpster on 2007-07-07
So after running it with the fan, it DID freeze but took a while until it did. W/O The fan it freezes after a few minutes so the fan IS helping. Should I put my other heatsink in?? However I'm ready to just yank this dual core right out and send it back to newegg.  I'm so frustrated, I want to put my old core back in. I suppose if it ain't broke don't fix it applies here. ANy ideas what could be causing this? I have since put the 686 kernel to use and all so what else could it be?

---

### Post by scxtt on 2007-07-07
i don't think it's a temperature issue ... could be something w/ your kernel ... that's why i suggested using a LiveCD - it would be a new environment, not sure it you're having this problem cause of recycling your "old" install ... could be a module problem ...

---

### Post by fredj on 2007-07-07
If I changed a cpu from single to dual core I would tend to think that I might have to reinstall the OS.
However your experiments with the fan seem to show that it is heat related.

---

### Post by scxtt on 2007-07-07
those temps aren't bad @ all - and blowing a fan ON the CPU (or into the case) doesn't help ...

---

### Post by Tumpster on 2007-07-08
So, should I reinstall it all?

Also, should I instally Fiesty or should I use a fresh install of dapper?

---

### Post by scxtt on 2007-07-08
why use dapper?  unless you have a good reason not to use feisty, i'd use the most recent one ... the more recent your kernel (generally) the better ... i'm using feisty w/ an AMD X2 3600+ Dual Core - works well ...

i'd try a LiveCD of feisty and see how it goes ...

---

### Post by Tumpster on 2007-07-08
So I'm putzing around to make sure everything is ok with the Fiesty live cd and it locked up!!! What could be causing this?

---

### Post by Tumpster on 2007-07-08
Bump!

---

### Post by fredj on 2007-07-08
Well your earlier posts about the lockup being delayed when you were blowing an extra fan on it seemed
to indicate that it was heat related. However if it was a retail package then I would expect that the included
heatsink would be good enough. Are there any bios upgrades for your motherboard.
I would still be tempted to try reinstalling ubuntu.
However before doing that run System - Administration - System monitor and just do nothing else and see
if the system locks up. Also see if System monitor indicate a dual core cpu.

---

### Post by sam0t on 2007-07-09
Being a long time Windows man, I too would suggest reinstalling the OS or atleast try it with livecd. I have read about issues when upgrading from single core to dual core and the OS has not just understood it very well, something to do with the ACPI, or atleast so in Windows.

The heatsinks coming with the cpu retail package are generally ok, but the 3rd party heatsinks are way better. Heres what I would do, take the side off of your computer and run the livecd, that pretty much eliminates the heat issue and OS. If still freezes occur, it needs some more troubleshooting.

ps. The bios upgrade is a good recomendation, just remember to load up "setup defaults" in the bios afterwards. Been running Ubuntu with dual core (AMD) for ages without any problems, so something is definetly up here.

---

### Post by Tumpster on 2007-07-09
When I tried a fiesty live cd it still locked up on me....

---

### Post by stchman on 2007-07-09
It might be bad RAM.  I have seen RAM do this to a system.

---

### Post by scxtt on 2007-07-09
i don't see how it's bad RAM, w/ the other processor - he has no troubles ...
i don't see how it's temp related, since the temps he posted are good temps ...
since it locks up on a LiveCD session too, it can't be his current install ...

all that's really left is the new core itself, or his motherboard (bios upgrade, if possible, may be the best route - esp. if the board was purchased when socket 939 was relatively new) ...

---

### Post by sam0t on 2007-07-09
If it crashes with livecd it points to a hardware problems, lucky for the OP livecd has the memtest program on it. Let the memtest run for 200-400% and  if no errors, its pretty safe to say its not the ram.

---

### Post by scxtt on 2007-07-09
i'm certainly not saying that's a bad idea, just pointing out that i highly doubt the memory coincidentally went bad around the same time the CPU was swapped out ...

---

### Post by stchman on 2007-07-09
> **scxtt said:**
> i don't see how it's bad RAM, w/ the other processor - he has no troubles ...
i don't see how it's temp related, since the temps he posted are good temps ...
since it locks up on a LiveCD session too, it can't be his current install ...

all that's really left is the new core itself, or his motherboard (bios upgrade, if possible, may be the best route - esp. if the board was purchased when socket 939 was relatively new) ...

There are many things that can go wrong with a ssytem when you tinker with it.  I was claening my PC one time (dust and stuff) and I accidentally loosened a jumper.  It took sometime to find that problem.  He could havealso unseated a card slightly.

---

### Post by scxtt on 2007-07-09
a valid possibility - and we can only assume the OP knows what he/she is doing (seems to be the case) ... but your opening post doesn't hold water based off the info the OP provided ...

---

### Post by Tumpster on 2007-07-09
This is true, I do know what I'm doing as I' built this machine. But now that we do bring up gram I wonder, it registers 2 or the 3 sticks with this core in. Then when I put in the new core it saw 3 out of 3.....I DID add a stick a bit before switching CPU's BUT my board runs in dual channel. I had 4 sticks total and it saw all four w/ my origional core but that stick went bad and I removed it so I'm down to 3 now. I've sent the core back to newegg for a new one. Should I install my third party heatsink instead of the one that comes with it? The one I got from AMD was slight copper with bulk being aluminum. My 3rd party is of all copper with a fan in the middle, allways kept my current one cool. My next step, when I get a new core is to try and see about a bios update because I have not since getting the new core and switching to linux. Any other ideaS?

---

### Post by bsmith1051 on 2007-07-09
Here's some voodoo troubleshooting for you, based on various other trouble reports people are now having because of a hard-drive bug in all the recent kernels:

1. leave the new Opteron installed but disable dual-core.  (Sorry not sure how to do this exactly but I believe it involves adding a command in the lilo start-up file.)

2. leave discs in both your optical drives (some reports say that the problem is time-out as the IDE driver searches for a non-existent disc volume)

---

### Post by sam0t on 2007-07-10
> **Tumpster said:**
> This is true, I do know what I'm doing as I' built this machine. But now that we do bring up gram I wonder, it registers 2 or the 3 sticks with this core in. Then when I put in the new core it saw 3 out of 3.....I DID add a stick a bit before switching CPU's BUT my board runs in dual channel. I had 4 sticks total and it saw all four w/ my origional core but that stick went bad and I removed it so I'm down to 3 now. I've sent the core back to newegg for a new one. Should I install my third party heatsink instead of the one that comes with it? The one I got from AMD was slight copper with bulk being aluminum. My 3rd party is of all copper with a fan in the middle, allways kept my current one cool. My next step, when I get a new core is to try and see about a bios update because I have not since getting the new core and switching to linux. Any other ideaS?

Ok, heres the deal. I have never ever seen a computer processor go half bad, meaning it would produce errors and freezes like your system does, so I highly doubt its the processor. According to my experience, the processors either work or don´t at all. So in my mind its much plausible that it is indeed you RAM or other component in your system causing the problems.

But once you get the new processor (or the old one back), install the heatsink which seems to be easier to install. We should first find the cause for the freezes, then worry about the extra cooling. After installing your heatsink I would advice to  update your motherboards Bios (this is priority) and once doned with that to run Memtest program from your livecd like instructed before. I highly advice you install the latest bios to your motherboard, as your motherboard seems to behave/recognize the memory sticks differently with different processor, you might have very old Bios installed.

Also you might want to check your motherboards manual that your memory sticks are installed on correct slots. Thats the tricky part with todays dual channel motherboards, you cannot stick the ram sticks in just any of the memory slots on your motherboard. I know your a newbie with hardware, but believe me, reading the manual with care and time and you will see these things aren´t impossible :)

ps. Like somebody before pointed out, its not very likely its the ram sticks that have gone bad, generally if a memory sticks works the first couple weeks it usually lasts for the next 10 years or more. I have only once encountered a memory stick going bad after about 6 months of usage, but since the memory is the easiest to test, I suggest running memorytest from livecd anyway :)

edit:

Also could the OP tell us what PSU (power) are you using? This is just reaching it, but if the OP is trying to run that system with say generic 300W PSU, that might cause problems also.

---

### Post by spud42 on 2007-07-10
as an engineer for compaq and hp for over 8 years i can say that i have seen dodgy cpu's of both intel and amd. what precautions did you take when you installed the cpu? were you careful about static ? a lot of people laugh at static but i have seen several systems killed by someone reaching in and touching something without grounding themselves. also from the posts you seem to have been removing memory sticks as well.

the best way to fix this problem is to start with the minimum to get it working. start by removing the cards not essential to booting the system. only try 1 ram stick at first as well. as previous posters said it is ESSENTIAL to get not only the latest bios for your motherboard but also the latest chipset drivers and anything else the manufacturer has updated. they dont do these things for the fun of it , they do it because there is something to fix. as you can boot off the live cd you can even try it without the HDD in the system . if you then get it stable. then start by adding the next ram stick. if thats stable then add the next stick. if thats ok then try adding bits one at a time. if it fails then try something else , or try removing something else and adding the part that made it fail . it could well be that the psu hasnt got the grunt to power the opteron and all the drives both hdd and dvd etc. so if on a reduced load nothing freezes but when you add all the parts it then freezes it may well be that the psu cant handle the extra load. 

intermitant faults like this can be difficult to find. patience and a good plan of attack are your best weapons. just remember 1 change at a time then test. if you make 2 changes which fixed it or killed it?

---

### Post by Shakkaa on 2007-07-13
hahahaha they say engineers make the best CEO's hehehehe and this is an example of why I it's statistically true :P........Good 1 Spud :)

---

### Post by Tumpster on 2007-07-26
Hey, so I sent the old processor back and got a new one. I'm about 10 minutes into running the new processor and i've had no troubles. How can I ensure that both cores are running? Currently I'm booting into the 686 Kernel or whichever number that is. Are there steps I have to go through?

---

### Post by bsmith1051 on 2007-07-26
> **Tumpster said:**
> How can I ensure that both cores are running?
Just go into the System > Administration menu and load System Monitor.   Under Resources you should see two cpu graphs.

---

### Post by Tumpster on 2007-07-26
I've done this and I DO NOT see 2 cpu graphs, only one. What could I be doing wrong? I have the SMP kernel loaded up and running, I selected the Intel Option, I did see the option for an AMD K7 one, is that the one I needed or does it not matter?

---

### Post by scxtt on 2007-07-27
what's the output of **uname -a** ... w/ my AMD X2 Dual Core, i get:

Linux <hostname> 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

just use the generic kernel ...

---

### Post by Tumpster on 2007-07-27
This is what i get:

Linux main-desktop 2.6.15-28-686 #1 SMP PREEMPT Wed Jul 18 22:57:30 UTC 2007 i686 GNU/Linux

But still under system monitor, only one CPU is shown.

---

### Post by Cryptic1911 on 2007-07-27
what brand and wattage power supply do you have?

---

### Post by Tumpster on 2007-07-27
Aspire 500W PSU
This one:
[http://www.apevia.com/product.php?pid=212&xcSID=fa6be416df1c82608adaf8fbbb69c0dd](http://www.apevia.com/product.php?pid=212&xcSID=fa6be416df1c82608adaf8fbbb69c0dd)

---

### Post by Cryptic1911 on 2007-07-27
hm, ok that looks like it should be rugged enough to run that machine.. i was thinking you probably had some cheezy no name power supply because it almost seems like a power issue

---

### Post by Tumpster on 2007-07-28
No, I run a well built machine. Anyone have any ideas or thoughts?

---

### Post by Spartan.II.117 on 2007-07-28
even well built psu's can still have problems, I'd get a power supply tester.

---

### Post by scxtt on 2007-07-28
> **Tumpster said:**
> This is what i get:

Linux main-desktop 2.6.15-28-686 #1 SMP PREEMPT Wed Jul 18 22:57:30 UTC 2007 i686 GNU/Linux

But still under system monitor, only one CPU is shown.try running the generic kernel, you've got nothing to lose ...

---

### Post by Tumpster on 2007-07-28
I thought i was running the generic kernel? Aren't I? If not how do I get this going?

---

### Post by Tumpster on 2007-07-28
Bump!

---

### Post by Spartan.II.117 on 2007-07-28
dude, you don't need to keep it on the front page, some of us sleep and work. anyway, open synaptic and search for SMP and a separate search for generic, check the generic ones that you also see in smp (the checked ones,) and install them. then when you restart, select the generic rather than smp in grub. then you can remove all the smp related stuff if you want.

---

### Post by kcramakrishna on 2007-08-03
I think this is a generic issue with AMD 64 bit architecture. 
Give boot parameters as "noapic nolapic" and things should run fine.

---

### Post by scxtt on 2007-08-03
my AMD 64-bit boots kubuntu (and runs fine) w/o those options ...

:> uname -a
Linux kubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f7456253-9556-48e1-8757-0b920312bc98 ro quiet nosplash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

---

### Post by Tumpster on 2007-08-04
kcrama, how would I add that to the boot option?

---

### Post by Spartan.II.117 on 2007-08-04
have you switched to the generic kernel yet? if not, his options are'nt going to help as his are for the generic kernel.

---

### Post by Tumpster on 2007-08-04
Yes I've switched several times, to two different kernels with smp support.

---

### Post by Spartan.II.117 on 2007-08-05
which kernels specifically, i just got my quad core urnning perfectly running generic

---

### Post by Tumpster on 2007-08-05
First, due keep in mind you're running FIesty and I'm running Dapper. Second, I was running the K7 Kernel for dapper and also tried the 686 kernel for dapper under synaptic but I guess thats for Intel dual cores, I have an AMD Dual Core, an Opteron 165. Ideas?

---

### Post by Spartan.II.117 on 2007-08-06
can upou post the uname -a for each kernel you've tried?

---

### Post by Tumpster on 2007-08-06
I stepped up and flashed bios and everything works beautifully!!! Thank you for all you're help!!!

---

