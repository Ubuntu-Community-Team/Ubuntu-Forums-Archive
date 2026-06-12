---
title: "Unknown hardware issue causing computer to crash."
date: 2013-03-15
forum: Hardware
---

### Post by pearldrums on 2013-03-15
Alright, this thread might not belong here because A) I have bailed on ubuntu and gone to linux mint (sorry) and B) I don't think it has to do with software at all, but I've always found very caring people here on these forums so at the very least I'm hoping someone can point me to another forum that might be more suited to this problem. I don't mean to abuse everyone's help.

My computer has been "crashing" where everything will stop, my screens will go blank, and my fans will spin up to full speed. I cant do anything and I have to termnate power to shutdown, the normal buttons do nothing. This happens intermittently. At first I thought this might be software because I only experienced it in Ubuntu and not Windows, but I booted from a live CD and experienced the same problem. I then did a memtest and found a bad sector and replaced my ram. I thought this solved the problem because I was able to re-format and partition two disks and install a new OS (mint) and run the computer for 2 weeks with no issues, but it happened again last night.

At this point I'm thinking about components left to test. I'm going to check my hard drives tonight. Perhaps one is failing as I still havent experienced this in windows, but windows is on a different physical drive. That isn't saying much though as I don't really run windows much. Other components I can think of would be the main board and processor, but I don't know why they would cause intermittent issues like this. How would I go about diagnosing this? Could there be a connection issue between components, or could momentary issues in power supply cause something like this?

Thanks for hearing me and any help you would be willing to offer.

---

### Post by tgalati4 on 2013-03-15
What is the hardware?  How old is the computer?  All it takes is one failing capacitor to cause intermittent behavior.  You have lots of capacitors in both the power supply and the motherboard.  If this is a desktop computer, check the voltages in the BIOS or use a voltmeter and test the 5VDC and 12VDC on a spare set of power leads.  If this is a laptop, try removing the battery and use only the powercord to boot.  If you have trouble booting with only the powercord, then it could be your power supply is weak.

---

### Post by mörgæs on 2013-03-15
> **pearldrums said:**
> and my fans will spin up to full speed

Sounds like overheating. Have you opened the computer and cleaned if from dust, especially around the fan and heat sink?

---

### Post by kuifje09 on 2013-03-15
Intermittended crashes can also be caused by memory problems. Easily checked with memtest86+.
Just run the whole cyclus once or twice.
Oops, I see you already did, but also after replacing the faulty ram.

I can tell from own experience, it can be caused also when the powersuply is not stable enough. Indeed probably degrading caps.
Quite normal unfortunatly with cheaper powersupplies and then after some yearch of use.
In such case, spikes on the net can crash the system. Very disturbing.
I placed an extra net-filter between the net and the computer, wich solved the problem.

---

### Post by pearldrums on 2013-03-15
> **tgalati4 said:**
> What is the hardware? How old is the computer?

Its a home built computer with parts installed from 2006-2010. I don't know exactly what power supply I have, but it is an Antec 550 watt from somewhere around 2008. The Mainboard is a Biostar TA770 installed in 2009. I have an AMD dual core 2.3 ghz (I think) processor from about 2007. The video card is a EVGA 512-P3-N871-AR GeForce 9800 GTX+ from 2010. I did run memtest again with the new ram (actually not new, I just removed excess ram and re-seated some known working ram) twice to be sure. I supposed it has been a while since I've cleaned the box out, but not an excessive amount of time. 

I will clean out my box tonight but Im not really sure what I should be doing with a voltmeter. What voltage information should I post from my BIOS? What exactly is a net filter?

---

### Post by kuifje09 on 2013-03-15
A netfilter filters the spikes on the mains line,  what goes into your computers powersupply.
Like this:   [http://www.platenspeler.com/background/netfilter/netfilter_schema.gif](http://www.platenspeler.com/background/netfilter/netfilter_schema.gif)

Why I did add this ( selfbuild ) was because I heard via the speakers from the amplifier beside the computer havy cracklings.
Somewhere below me there ( in an appartment ) has someone a loosy electrical connection.

---

### Post by tgalati4 on 2013-03-15
In the BIOS, there is a tab called "Health Monitor".  It shows the CPU temperature, fan speeds and voltages:  1.75VDC, 3.3VDC, 5VDC, 12VDC.  If the displayed voltages are 10% lower or higher then that could cause problems.

---

### Post by tgalati4 on 2013-03-15
In the BIOS, there is a tab called "Health Monitor".  It shows the CPU temperature, fan speeds and voltages:  1.75VDC, 3.3VDC, 5VDC, 12VDC.  If the displayed voltages are 10% lower or higher then that could cause problems.

Remove all of the non-essential cards.  Put your finger on all of the bare chips on the motherboard.  If any are too hot to keep your finger on, then you have found the culprit.

---

### Post by mörgæs on 2013-03-16
If you are going to inspect the capacitors, look for signs of pressure inside the cap or fluid/gunk leaking from it. 

[http://www.wheresmydrink.com/wp-content/gallery/may-2009/capci.jpg](http://www.wheresmydrink.com/wp-content/gallery/may-2009/capci.jpg)

If caps are the problem you can often buy a new set online for your particular motherboard. However, as your board is new I doubt that's the problem (it happened mostly to older boards; I have found it in Dell and Medion, but many more were affected).

Googling 'bad capacitor' will yield a lot more information.

---

### Post by kuifje09 on 2013-03-16
I would suggest to swap the powersupply if you have a second one and see if it helps. It is easy to do if you already build your system yourself.
Randomly crashes are not easy to solve, can even be some loose contact. But also my guess, if not the memory, probably one or more caps in the powersupply.

---

### Post by pearldrums on 2013-03-16
Alright guys I feel a little foolish. I was really sure I cleaned out my box about 3 months ago, but when I looked at my heat sync... Ive never seen so much dirt in a computer before! I must have been mistaken. Also, we've moved into a new house recently and pehaps all the activity created more dust in the air or something .There were litterally large spots on my heat-sync 'blades' (I'm not sure what you would call them) that were so built up with dirt air could not pass. I think we have found the problem, and I feel guilty for not figureing it out on my own. I have run the computer for most of a day while doing some heavy video editing and gaming to try and work the components and no issues. I'm going to switch this to solved but if the problem happens again I will see if I can borrow a power supply from a friend and check that out as well as the capacitors on my main board.

Sorry for the Noob lack-of-troubleshooting, and thanks again for your help!

---

### Post by pearldrums on 2013-03-16
Um I can no-longer find the button to mark this as solved... I'm really not feeling smart right now.

---

### Post by kuifje09 on 2013-03-16
Yep dust can cause overheating.  Your powersupply sucks up a lot of dust too.
If you dare you can clean it out also, but the guarenty seal wiil be broken ;)
I just cleaned out one, a few weeks back, it was realy messy in there, also the CPU cooler.

---

### Post by mörgæs on 2013-03-16
Good, from now on I guess you will not place it on the floor :-) I have made an extra shelf under the desktop (=table surface) and put my desktop (=computer) there, free from dust but still accessible.

The 'solved' function is not working these days. I have changed it manually.

---

