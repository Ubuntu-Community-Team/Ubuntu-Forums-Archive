---
title: "Help, trying to diagnostic hardware problem."
date: 2011-07-18
forum: Hardware
---

### Post by Gfurst on 2011-07-18
Hey people i've got abad hardware problem:

My computer randomly  crashes, the screen get a distorted pixel patterns and a few seconds  later it completely crashes, sounds get in a kind of loop, a few times i  got the Caps and Scroll lock blinking( kernel panic).
I'm afraid it  has something to do with my graphics crad or memory, so i did a full  check up: start monitoring sensors, looked up some log files, tried a  file-system checkup( which only took a few seconds btw), did a complete  hardware clean-up, with details below:

 -At first it only  happened a few times after many hours of heavy load( games), also after  the crash happens, i restart the pc but it doesn't take that long to  happen again. This lead me to believe it was a temperature related  problem, but it doesn't seem so...
 -Then it got happening more  often, one day i got a bad circuit burning smell( without the crash), so  i suspected power problems, got a better PSU and a outlet stabilizer  with proper wattage, i though the problem was solved for a while but it  wasn't.
 -So still thinking it was a temperature problem i did a  completely clean-up of the hardware, including heatsinks, coolers and  thermal paste. My GPU effectively dropped about 10°C avarage( from 60 to  50). Again a i though it was solved for a while, but it wasn't.
  -Finally i had to face my biggest fear: bad ram or even worse, bad GPU.  So i ran a couple of memtest, didn't find anything. I didn't find any  proper applications for gpu testing on linux, so i tried on windows, an  heavy stress test( which it kept on for 15 min without errors) and some  kind of memtest for the video. Still no errors found.

As you can  see i pretty much had all possible tests done to my machine and still  couldn't find the faulty part. I very much doubt that is something  software related. I get the crash more often now, and not always on  heavy load.
Is there any other possible tests i could run?

Of course here are my system specs:
 -Ubuntu 10.10
 -Pentium E2140 dual core
 -2GB DDR2 RAM
 -Geforce 8400 GS
 -3 HDD
 -500W PSU with a reasonable fan

At this point i still suspect bad graphic card, but also i've heard it still could be bad RAM.
Any help is appreciated [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]
I  got no spare parts and i'm very reluctant to buy anything new, because   i already have a plan buying a whole new pc, but just not yet.

ps..  i got a flash error where even after the flash is closed it still  appears distorted in the same area when black pixels are there( eg with  black screen saver, the region where the flash was still appears), it  doesn't crash though, so i don't know if those can be related.

Edit:
Just uploaded a few pics showing the state of my screen, right after i got that black screen also, the other times only the pattern was different.

---

### Post by Cybie257 on 2011-07-18
With the video problems you talk about, I am thinking your video card is the problem... I know that there was a time when the 8400 series was known for weird issues. Don't know if that ever was resolved from a driver issue or if it was a hardware issue. My friend had issues similar also with an 8400 and after upgrading his card, they went away. 

I did a quick search on Google for your video card and 'crashing'. It appears that there was a lot of BSOD and related issues that came up. 

Do you have on-board video (assuming the 8400 is not embedded itself) that you can run for a while without the other card installed?

Ubuntu Linux, at least in the past, was really good about popping a message up on the screen if you had bad RAM, so I might steer away from bad RAM, but you never know. If you live near a computer repair shop of some sort, they might have the equipment to test your RAM modules... 

-Cybie

---

### Post by Gfurst on 2011-07-19
No i haven't got on board graphics, nor any spare parts.
I better search more on google like you did and see if i find anything more similar.

I'm still reluctant with video because of the stress test i've made on windows, also i had a good +- 4 years without problems with it. I brought it a lot later than release, which is said to have upgrade chipsets, hence the joyful 512mb in comparison with the 128mb common.

Another thing that could be useful mentioned is that my old psu got fried a couple times, it got that strong circuit burn smell and took me a while to notice what it was. But it kept working.

So i could imagine the frying psu could have damaged my gpu or ram, either way.
I also think it could be something the energy outlet( don't know exactly how to say), i've recently moved to a new apartment, there were no problems before. 
The wiring here is a bit weird, i often get some peaks in electricity( lights trembling), thus this could have burned my psu and damaged my components...

Either with video or ram, could be the faulty under heavy load, i usually get after playing the sims which is quite heavy on memory too, it almost fills up the 2gb ram triggering the faulty parts. And it doesn't happens after 5 min, it could go from half and hour to about three or four hours.

---

### Post by Gfurst on 2011-07-19
Okay i've got some updates on my situation, if anyone out there to help after all.

The other day i got the weirdest of issues, my system start freezing because of harddrive laggines, for example, my torrent and music player frooze for long periods, also i couldn't access any files of the target drive( my system is in another drive).
I've had to restart to gain access again.
Upon looking at syslog file, i found some i/o errors, some denied access to drive, something related to bio, i don't really know. The thing is, it solved it self after restart, this leads me to believe that my overall problem could also be related to motherboard, or pinpoint again that its a memory thing.

Anyway, i got my hads on some great windows stress test( BurnIn test), and finally got to replicate to crash on my own( in windows this time), proving to be a hardware issue, but then i couldn't get to replicate the crash after 4 times the same test run (ARGH).
Also one test showed video memory errors, just a few, so to make sure i run more test on video, couldn't get it to replicate after several ( ARGH again).

This is driving me crazy, i was like "crash damn computer, CRASH!"
I'm starting to think now that my new PSU is flawed or doesn't provide enough to my setup, causing this damn random issues.

I'll leave memtest overnight in hopes to find the bad ram bit, some threads around says that some obscure errors need several hours to detect, more obscure than Dracula you mean...

---

### Post by tgalati4 on 2011-07-19
Strip the machine down to essentials.  One RAM stick, one hard disk.  Remove as much as you can.  Run memtest from the LiveCD for 30 complete passes.  If OK, then from the LiveCD, (you'll need networking)

sudo apt-get install cpuburn

man cpuburn
burnP6 &
burnP6 &

(I'm assuming it's a dual processor).

top

If the machine survives that stress test, then you need to look into the graphics card.

sudo apt-get install phoronix-test-suite
man phoronix-test-suite

Pick a few graphically intensive tests.  If the machine locks up, then find another video card.

If you had a power supply crap out, then I would suspect some damage to the motherboard.

---

### Post by Gfurst on 2011-07-20
Apart from the Hard drives the Pc is stripped to essentials, one RAM, one CPU, one GPU( no onboard vga).

How would i run memtest from live cd? I got the 10.10 live cd but at start it jumps to the graphical installation. In that matter, what would be the difference from running memtest from grub menu?
Still i'm let it run overnight just to be sure.

I'll check out those apps you mentioned.

Yeah the PSU could damaged anything, but wouldn't the damage to motherboard be more apparent, like failure at boot up instead of very random crashes?

---

### Post by Gfurst on 2011-07-20
Just an update, i uploaded i few pics of my screen at the crash moment. This time i was only whatching and episode from "how i met your mother" which is not at all demanding.

---

### Post by tgalati4 on 2011-07-20
Does your video card have a separate power connector?  It's possible that your power supply is sagging causing the video glitch.

---

### Post by Gfurst on 2011-07-20
> **tgalati4 said:**
> Does your video card have a separate power connector?  It's possible that your power supply is sagging causing the video glitch.
No, the card is quite old( about 3 years maybe), could it be that new power suply is faulty? 
Or maybe its just my motherboard dying, hence quite random and bizarre failure?

---

### Post by Gfurst on 2011-07-20
> **tgalati4 said:**
> Strip the machine down to essentials.  One RAM stick, one hard disk.  Remove as much as you can.  Run memtest from the LiveCD for 30 complete passes.  If OK, then from the LiveCD, (you'll need networking)

sudo apt-get install cpuburn

man cpuburn
burnP6 &
burnP6 &

(I'm assuming it's a dual processor).

top

If the machine survives that stress test, then you need to look into the graphics card.

sudo apt-get install phoronix-test-suite
man phoronix-test-suite

Pick a few graphically intensive tests.  If the machine locks up, then find another video card.

If you had a power supply crap out, then I would suspect some damage to the motherboard.

Now you have to forgive me, i got this phoronix-test-suite but i couldn find my way around it, i found a couple of test to perform, but, would you mind pointing me to which could be graphic stress test relevant?

---

