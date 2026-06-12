---
title: "Problem with new motherboard! please help!!"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by jclmusic on 2006-11-16
i was running ubuntu 6.06 for months on an AMD-K6 motherboard and CPU, however, it was a bit slow, and i finally saved up anough for an upgrade to an Intel Celeron motherboard and CPU. 

i installed the new motherboard and CPU, booted it up and it worked fine. i had read on some website that it's best to boot up once, to let the motherboard figure out the new setup and then shut down and start up again. so after i shut down to start up again it wouldn't turn on!

when i press the on button nothing happens. i can't figure out what it is! help me!

---

### Post by gtom on 2006-11-16
Does it POST or not? Do the fans spin at all when you power it on?

---

### Post by jclmusic on 2006-11-16
nope, no fans, no lights, nothing.

---

### Post by DOD1951 on 2006-11-16
May seem like a dumb question but is there any chance the fuse has blown in the plug? The power surge on power off/on may have blown it.

---

### Post by gtom on 2006-11-16
Well that means it's not related to your OS then if it wont POST.

What are the full specs of your machine including power supply? If nothing happens at all it would suggest a bad PSU or motherboard.

---

### Post by jclmusic on 2006-11-16
i thought bad motherboard or psu too, but then why did it boot up 1st time?

PSU: HIPRO HP-A1365F3
Motherboard: Intel Celeron
CPU: Intel Celeron, i dunno what speed, but it has this written on the top:
900/128/100/1.5V
Q142A566-0797 SL5LX

hope that helps.

how do i test if the fuse has broken? i tried a different kettle lead and the same thing.

---

### Post by gtom on 2006-11-16
I think it's a 900MHz Celeron with 128k cache and running on a 100MHz FSB. Did you install the cooler properly? I'm not sure if CPU's in those days had thermal protection or not, if you didn't it may be dead. When installing a used CPU + cooler you should clean off any old thermal paste (I use nail varnish remover to do it) and then apply new stuff (not too much and not too little).

What wattage is the power supply? What else does the PC have (hard drives, optical drives, graphics card etc.)?

---

### Post by jclmusic on 2006-11-16
i have no idea about the fan, i got that 2nd hand also. my gf's dad was clearing out all his old computer bits lol.

15Gb IDE hard drive
Intel  10/100 enet card
Nvidia 180-P002-0000-B01 graphics card

---

### Post by gtom on 2006-11-16
Test if your power supply works by doing the following:

(please note I accept no responsibility for any losses that occur by you following these instructions ;) )

1. Unplug EVERYTHING inside the case from the PSU, motherboard connector, the lot. Unplug PSU from the wall.
2. Get a paper clip and bend it so that one end is in the green wire of the motherboard ATX connector and the other end is in any black wire.
3. Switch the PSU on at the wall and at the back if it has a switch.

If the fan spins up then the PSU should work, if it doesn't then it's dead. You should not leave the PSU running like this for long.

---

### Post by jclmusic on 2006-11-16
> **gtom said:**
> Test if your power supply works by doing the following:

(please note I accept no responsibility for any losses that occur by you following these instructions ;) )

1. Unplug EVERYTHING inside the case from the PSU, motherboard connector, the lot. Unplug PSU from the wall.
2. Get a paper clip and bend it so that one end is in the green wire of the motherboard ATX connector and the other end is in any black wire.
3. Switch the PSU on at the wall and at the back if it has a switch.

If the fan spins up then the PSU should work, if it doesn't then it's dead. You should not leave the PSU running like this for long.


bloody hell! aint that really dangerous?

---

### Post by Decade on 2006-11-16
> **gtom said:**
> 2. Get a paper clip and bend it so that one end is in the green wire of the motherboard ATX connector and the other end is in any black wire.

That won't work. Modern switching power supplies require a certain amount of load to operate; even an older supply as the one I grabbed from my 386 PC clone just twitches pitifully if not given enough load.

Some companies sell specially assembled ATX plug with a resister pack to test power supplies. Lacking that, you could try attaching dummy loads to the various voltage leads. I haven't tried it with an ATX power supply yet, but a throwaway CD-ROM drive should do fine.

But back to the original question, I've heard that newly assembled devices fail the first, second time they're turned on, maybe within a month, but if they get that far they last practically forever, barring strange circumstances such as fan break or lightning.

---

### Post by jclmusic on 2006-11-16
> **Decade said:**
> 
But back to the original question, I've heard that newly assembled devices fail the first, second time they're turned on, maybe within a month, but if they get that far they last practically forever, barring strange circumstances such as fan break or lightning.

so it shoud just start working again?
will try the cd rom test now.

---

### Post by jclmusic on 2006-11-16
the cd rom doesn't seem to be reciveing any power. it won't open when i press the open button on it, so i assume it must be the psu?

i still don't get why it worked one minute and not the next, and worked fine for months with the old motherboard. very odd.

---

### Post by gtom on 2006-11-16
> **Decade said:**
> That won't work. Modern switching power supplies require a certain amount of load to operate; even an older supply as the one I grabbed from my 386 PC clone just twitches pitifully if not given enough load.


I have tried it personally with 2 PSU's and they both worked. One was a 300W (or maybe 350W) and the other was a 500W. Both were cheap jobbies - I haven't tried it on my decent one! I do agree though, one of the specially designed PSU testers would be much better.

---

### Post by jclmusic on 2006-11-16
> **gtom said:**
> I have tried it personally with 2 PSU's and they both worked. One was a 300W (or maybe 350W) and the other was a 500W. Both were cheap jobbies - I haven't tried it on my decent one! I do agree though, one of the specially designed PSU testers would be much better.

lol i'm skint. does the cd rom test prove anything?

and how common is the failing 2nd time thing? oh how i wished i'd never turned it off again lol.

---

### Post by gtom on 2006-11-16
If the CD won't eject then it's not getting power, which could be caused by a faulty PSU or by the motherboard not powering on.

Double check the headers that connect the motherboard to the front panel buttons and LED's. If they are all correct then as I said it's most likely a faulty motherboard or PSU.

---

### Post by jclmusic on 2006-11-16
> **gtom said:**
> If the CD won't eject then it's not getting power, which could be caused by a faulty PSU or by the motherboard not powering on.

Double check the headers that connect the motherboard to the front panel buttons and LED's. If they are all correct then as I said it's most likely a faulty motherboard or PSU.

all present and correct, so it must be the psu or motherboard. i still can't my head round why it'd work the 1st time and not after, tho.

---

### Post by gtom on 2006-11-16
Computers can do strange things sometimes (hardware and software)!

---

### Post by jclmusic on 2006-11-16
> **gtom said:**
> Computers can do strange things sometimes (hardware and software)!

lol very true. i just thought whatever went wrong must've occured between the 1st and 2nd boot.

thanks for ur help everyone, btw!

---

### Post by jclmusic on 2006-11-18
i bought a new psu, plugged it in, and everything worked fine, except ubunutu stopped booting at the mounting bit and had some error which made it go to a command line.

while i was searching google for a way to get the boot up to continue with the command line, the computer randomly just shut off :( !

maybe it's a bios timeout or something. problem is, it now won't even turn on again ](*,) so it's kinda back 2 square 1 :( .

help me!!

edit: i've decided i'm gonna re-install ubuntu off a cd, so the command line thing doesn't matter, but i still need it to actually turn on first!!

edit 2: i managed to get it to work again by unplugging and plugging back in the kettle lead!! so it's not as bad as the old psu! but sthis still shouldn't be happening.

---

### Post by jclmusic on 2006-11-18
ok oddly (but i am so happy lol) the problem seems to have solved itself!

thank u all for ur help :)

---

