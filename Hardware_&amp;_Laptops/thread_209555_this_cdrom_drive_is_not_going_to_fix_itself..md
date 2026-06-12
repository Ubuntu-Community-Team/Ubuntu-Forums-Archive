---
title: "this cdrom drive is not going to fix itself."
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by rmg on 2006-07-05
dear sirs,

as i remarked before, my cd-rom drive totally isn't being detected after a transplant of my ubuntu bearing hard drive from its previous athlon based home to its new, seven year old salvage sale dell p3 place of residence. getting the cdrom drive to work is really a matter of life and death, as i must access my kitten feeding database on cdrom, without which some of the cats i am watching will likely receive the wrong meals, resulting in sickness and perhaps death.

obviously, no one wants to see kittens die.

please advise.

thx.

-rmg

---

### Post by atoponce on 2006-07-05
[quote=rmg]dear sirs,

as i remarked before, my cd-rom drive totally isn't being detected after a transplant of my ubuntu bearing hard drive from its previous athlon based home to its new, seven year old salvage sale dell p3 place of residence. getting the cdrom drive to work is really a matter of life and death, as i must access my kitten feeding database on cdrom, without which some of the cats i am watching will likely receive the wrong meals, resulting in sickness and perhaps death.

obviously, no one wants to see kittens die.

please advise.

thx.

-rmg[/quote]
Is that one of those CDs where you have virtual pets?  Man, those things are annoying!

---

### Post by rmg on 2006-07-05
well, since i can't read it, i'm not sure exactly what's on it other than the catfood database. perhaps if someone could offer some advice on getting the operating system to see the cdrom drive, we could find out if there are any virtual pets on the cd.

---

### Post by atoponce on 2006-07-05
[quote=rmg]well, since i can't read it, i'm not sure exactly what's on it other than the catfood database. perhaps if someone could offer some advice on getting the operating system to see the cdrom drive, we could find out if there are any virtual pets on the cd.[/quote] Seriously, you may have a faulty CDROM.  If you aren't looking for R/RW functions, you can find them for about $10 at any computer retail shop.  Just curious, are you sure that the CDROM is connected properly?  Are the jumpers correct?  It is in a master/slave configuration?  More details would be appreciated.

---

### Post by rmg on 2006-07-05
well, all i know is that the bios thinks it's the secondary ide device. it seems like it's probably configured to be a "master" device. i'm sure it works properly. my system stopped recognizing my old cdrom drive too somewhere along the way, so my guess is that the software is broken somehow.

---

### Post by cracker on 2006-07-05
Well, just as a quick FYI, OS hard drive transplants are very hard on the software. The system has all the specific drivers and configuration for your old hardware, and then you move it and it has a completely different system to work with. Linux is better at it than Windows, but in either case, it's never perfect unless both systems are identical. Possibly a kernel update or reinstall would help, but I'm not an expert.

---

### Post by rmg on 2006-07-05
as a long time linux user, i'm well aware that linux is better at not working than windows. nevertheless, i've already got one sick kitten on my hands (apparently, its usual diet does not include franks and beans) and it's going to get worse in the next couple days if i can't read my bloody cdrom of feline nutrition facts.

tell you what, since it looks like i'm not going to get any particular advice here, other than "recompile your kernel," i'll just order a pizza, hope the cats like it, and ask the delivery boy what he thinks about my hardware situation.

---

### Post by atoponce on 2006-07-05
[quote=rmg]as a long time linux user, i'm well aware that linux is better at not working than windows. nevertheless, i've already got one sick kitten on my hands (apparently, its usual diet does not include franks and beans) and it's going to get worse in the next couple days if i can't read my bloody cdrom of feline nutrition facts.

tell you what, since it looks like i'm not going to get any particular advice here, other than "recompile your kernel," i'll just order a pizza, hope the cats like it, and ask the delivery boy what he thinks about my hardware situation.[/quote] No need to get upset. I've asked you some questions that you have left unanswered.

First and foremost, are these real cats, or virtual pets?  When you refer to kittens, are you talking about acutal real life kittens that are living in your house?  If so, just go to the pet shop, and buy some freaking cat food and take it to the vet.  Anyone should know that beans, franks and pizza are not good for your cat.  You don't need a CD to tell you that.  If they are virtual pets (live inside your computer), then feed them whatever the hell you want.

Second, how is your CDROM connected?  Is it a slave to another drive or the master.  In both situations, are the jumpers configured correctly?  Having a drive wired as a master, but jumped as a slave and vise versa can cause problems.

Third, how old is your CDROM?  Is it faulty?  Has it worked before?  Why not just go out and get a new one, and install that?  I would think this would be the best option.

Now that that is out of the way, switching out hardware, after the OS has already been installed is not that big of a deal.  Rarely, almost always on no-name hardware but seldom outside of that, will the OS not recognize new hardware in replace of old.  I have worked on computer hardware for almost 10 years, and regardless if it is Unix, Linux or Windows, commonly switched out brand-name hardware has almost never been an issue.

Finally, no one has asked you to recompile your kernel or behave in any way contrary to the problem you have outlined.  Placing guilt on people just because they are not answering a question in a way you expect will not get replies.  I am concerned about helping you out, but I need to know more specifics about your problem before I can solve the issue.

So, shall we start over?

---

### Post by rmg on 2006-07-05
the cats are as real as you or i, my friend. strangely enough, one of their diet plans does include franks and beans, as indicated by the cans of franks and beans amongst the various types of food left for me to feed the cats. the problem is, i didn't give them to the right cat.

now then, it's a stock dell machine from a salvage sale. (optiplex gx110, i believe.) it has some kind of generic atapi cdrom drive. i assume it's in working order and certainly that the jumpers are in good standing. the thing shows signs of life when given a cd, but the os doesn't not recognize it.

the system must do something to figure out what sort of hardware you have. how do you make it do that? where are the logs?

---

### Post by atoponce on 2006-07-05
[quote=rmg]the cats are as real as you or i, my friend. strangely enough, one of their diet plans does include franks and beans, as indicated by the cans of franks and beans amongst the various types of food left for me to feed the cats. the problem is, i didn't give them to the right cat.

now then, it's a stock dell machine from a salvage sale. (optiplex gx110, i believe.) it has some kind of generic atapi cdrom drive. i assume it's in working order and certainly that the jumpers are in good standing. the thing shows signs of life when given a cd, but the os doesn't not recognize it.

the system must do something to figure out what sort of hardware you have. how do you make it do that? where are the logs?[/quote] So the CDROM is the original with the computer and has not been messed with?  What is listed when you type in the terminal:

```
ls /dev/cd*
``` 
Anything?  If 'cdrom' is there, then it is actually recognized and just needs to be mounted.  It can be mounted with the following command:

```
sudo mount /dev/cdrom /media/cdrom
``` 
If nothing shows up, then most likely, the CDROM is bad, and you will need to get a new one.

---

