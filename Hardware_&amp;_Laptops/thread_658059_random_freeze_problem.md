---
title: "random freeze problem"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by benner on 2008-01-04
I have read and participated in a million other threads over the last 2 releases trying to solve this problem and just gave up a few months ago with no luck ever solving it.  the machine just freezes up.  usually the mouse freezes and the caps and scroll lights flash on the keyboard.  occasionally nothing, just a frozen system.  i thought maybe it was ubuntu but now that i have a couple more hard disks installed (one with xp 32 and one with xp 64) i am getting freezes there too.  one person suggested that the flashing lights is a kernel failure.  but i get it in windows too.  another thread had me turn off the cool and quiet feature.  didn't help.  then there were a million software things that didn't help.  i thought it was a network card, changed it.  nothing.  before i chuck out the video card, switch motherboards etc... i thought i would come back here and see if anyone has a suggestion.  perhaps some sort of diagnostic tool?  apparently /var/log/messages can be of some use to someone who can interpret it.  i have reams of information in there that makes no sense to me.  any suggestions would be appreciated.

the system is:
amd 4200+ 64 bit dual core
ati x550 chipset on an asus build video card
motherboard is some chinese company called sparx but it has an nvidia nforce chipset
2 gigs of ram

please let me know any info i can provide that may help.  the problem is intermittent and i can easily imagine taking it in to someone, them keeping it for a week and finding nothing.  and i live in china.  it can be tough communicating the subtleties and all the stuff i tried.  so thanks in advance for any help on this...

---

### Post by ARhere on 2008-01-04
I have seen this before, and you are not going to like the answer.

One cheap way for the firmware on a motherboard to alert a user is through flashing the LED's on the keyboard.  This general error has happened to me in the past for...

1.  CPU or other temperature sensor triggering, which will freeze the system to keep permanent damage from occurring.
2.  Loss of sync on the master clock to any major device.
3.  General loss of communication to either the BIOS, Northbridge, or I2C buss on the memory.
4.  Bad or noisy power supply.

It has been my experience that most problems, aside from software related issues, are caused by cheap motherboards.  The MB is *arguably* the _most_ important hardware piece in your PC and a bad MB causes issues exactly like this.  I would seriously suggest getting a new MB, rebuild your system and your problem will most likely go away.  It could be that you just have a bad MB, as this is what it sounds like.  I know this can be a pain in the @ss so you can try a few of these tips before you begin ripping your system apart.  

1.  Update your BIOS or Google for known issues like this with your version of the BIOS.  Try pushing **_lightly_** on the BIOS chip if it is a DIP (*Dual In-line Package*) to see if it has wiggled loose.  If it is, it will "crunch" as it pushes back in.  _BE CAREFUL!_
2.  I am going to assume you already did a full memory check.  If not, do so first and see if you get errors.  Try slowing down the memory clock, if you can, a little in the BIOS and see if that helps.
3.  Check your CPU heat sink OR go into your BIOS and watch the "Hardware Monitor" if you have one.  At idle, the CPU should not get hotter then 60 degrees C or you have a cooling problem.
4.  Check your power supply.  There is a pin that indicates if the power is good.  You can read about it [here]("http://en.wikipedia.org/wiki/ATX_power_supply") but most people are gun-shy about messing with the hardware.  The best thing to do is swap it out with another and watch for the same error.  Personally, I would open the cover of the power supply and look for any capacitors that are bulging or oozing something, that would be a clear indication of a bad supply.  **BE VERY CAREFUL IF YOU CHOOSE TO DO THIS.**  Just turn the power switch off with the cord connected, THEN unplug the cord before opening it up.  Remember, look but don't touch.
5.  Last, there was a known batch of bad electrolytic capacitors that was distributed a few years back to a number of MB manufactures.  I just replace all the caps on my old MB 6 months back on a AMD MSI dual CPU board.  Search your MB and look for any small electrolytic caps that have a round and/or budging top.  Sometimes you can see some sort of "stuff" coming out of the caps near the solder point.

Check out this [wiki ]("http://en.wikipedia.org/wiki/Capacitor_plague")for good information on what I am talking about.

Please take a moment, and follow each of these steps and report back here.  I will try to help as best as I can.

-AR

---

### Post by benner on 2008-01-04
thanks so much for taking the time.  i will try what you suggested.  it may me a bit but i will be sure to report back to this thread however it goes.  there are so many others with similar, and so far, often unsolved, problems.  cheers.

---

### Post by benner on 2008-01-05
1.  the bios is unavailable from the manufacturer (phoenix) and the motherboard maker (Spark, their website is speedway.com.cn, it is only in chinese, but there is no bios there either) and every link on the internet leads to a site called esupport and they want 30 bucks for it.  i'm a little leary.  i don't even have a floppy drive on my machine so i wouldn't know how to install it.  better to take it back to where i bought it if that is what it comes down to.)  the chip on the board seems to be fine.

2. memory check, 5 passes, error free

3.  cpu temperature is always low.  the box is well ventilated, it is winter here and the room is pretty cold.  after last crash i think it was 25 degrees.  it happened shortly after i booted up.

4.  the power supply is new.  i just replaced it.  and i had the same problem before and after changing it.

5. i checked out the pictures on the site and didn't see anything like that on my board.  it is clean as a whistle.  the cylinders all appear well connected to the board.  no bulges or leaks.

*  as it was happening on windows and ubuntu i can assume that it isn't a hard disk problem.  they are installed on 2 different disks.

i tore everything out and am just running from 1 ide hard disk and 1 sata dvd-rw.  i have xp64 on this one.  i removed the other 2 disks, another dvd-rw, a raid card and a usb card.  i guess i will try to run everything one by one to see what happens.  the freezes are so intermittent though, it may take days or even weeks.  what'dya think?

---

### Post by ARhere on 2008-01-05
Hmmm....

I hate to tell you to go buy another MB when you have not found any physical flaws with yours.  I would hate for you to go spend the money and have the same problem.  (*changing the MB requires a new install of the OS in most cases*)  Like I have said, I have seen this before and it is always due to a cheap motherboard.  Do you have the ability to afford $50?  I will help you pick one out if that is an option.

Look on your motherboard and tell me the serial number/model/whatever you can find.  Let me research it a little in the meantime.

EDIT:  better yet, take the time to give me a full hardware list, including make and models.

-AR

---

### Post by benner on 2008-01-10
so i pulled it apart and put it back together with just bare bones.  1 hard disk (windows xp64) and the video card.  no freezes for a few days.  i added the ubuntu drive (sata) and booted into that and it was freezing up every few minutes suddenly.  very frustrating.  i uninstalled every new thing that i had put on (wine doors, automatix2, avant-window-navigator) and then switched off compiz.  so far so good.  it hasn't frozen on me tonight.  and it may be that i get a variety of freezes for a variety of reasons.  the last time i went through this i did the same and got fewer freezes.  it has been off and on since i got the machine but inexplicable.  so then i tried to boot back into windows and got an
'autochk program not found, skipping autocheck' error and then it reboots, gives the same error, reboots etc...  which apparently means that the partition is now somehow hidden so i need to look for a boot utility that i can understand to sort that out.  and now for some reason, the BIOS hangs a bit on the first page before moving on, probably around 10 seconds when it used to be just a couple.  and then the ubuntu splash screen comes up with the progress bar and that sits at about 1/5th of the way and stays there for several minutes before it moves along and boots.  i have now gone a couple hours without a freeze, but all of this other stuff is getting me down now.  and i'm sure the freezes will reappear sometime.  another thing i don't get is when it boots up i get a message that says something about 'kernel alive, direct kernel mapping' and then a bunch of numbers with an @ symbol in there someplace.  does that mean anything that could be relevant?

so this weekend i will tear it all apart again and give you some more specs.  thanks for looking out for me.  i promise that once i have internalized this stuff a bit more i will pass on the favour to someone else that needs it.  this forum is what gives me hope and keeps me using ubuntu.

---

### Post by benner on 2008-01-14
the system is an amd 4200+ dual core 64-bit
hitachi deskstar ide 80 gig (with xp pro 64
seagate barracude sata 7200 250 gigs
spark motherboard M25GT4-S0G (nvidia nforce chipset, still don't know which) 
ATI x550 chipset on an asus built video card
no name usb card
raid it812 card (no name)
2 gigs of kingston RAM
Phoenix Award BIOS 6.00PG (07/04/2006)

---

### Post by nadi on 2008-02-15
I am experiencing exactly the same problem, though I have a laptop. Both cpu's has ok temperature. It freezes sporadically, it can happen after one minute or after several hours. I do notice several things though:
1. It started happening after my recent upgrade of the kernel. I used the gutsy for a month, without experiencing this system hang.
2. I though it was networkmanager, since everytime it would hang, I could read (later after reboot) that the /var/log/debug showed some repeating messages about failure of Netwrok manager. However, I uninstalled it, and installed Wicd instead but the problem presists.

Nadi

---

### Post by nadi on 2008-03-03
Recent updates of one of the liberaries fixed this problem, though I cannot pinpoint which one. 
now everything is stable form more than a week...:)

---

### Post by benner on 2008-03-04
it has been very intermittent with me.  sometimes twice in 10 minutes, sometimes a week.  my most recent effort was to change the kernel from generic to server.  so far so good.  firefox seems to lock up a bit and need to be killed and restarted but it doesn't lock up the whole machine like it did in the past.  i have my fingers crossed...

---

