---
title: "SATA Hard drive"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Grauge on 2009-07-09
Hp Pavillion s 1132n... The bios is not recognizing the SATA drive at all even bought a new one and tried several cables but nothing. Is not power, is not a cable issue. Is there anyone with a similar problem and if so did you find a solution?

---

### Post by kerry_s on 2009-07-09
check the jumper, i came across a couple of drives that you have to remove the jumper.
jumper is that little thing that allows you to select master or slave.

---

### Post by Grauge on 2009-07-09
The old hard drive didn't have a jumper setting the new one does but the factory out of the box is not in it only recommends it when running multiple drives. So its not that either. Any more Ideas I'm completely out of ideas on this one.

---

### Post by kerry_s on 2009-07-09
> **Grauge said:**
> The old hard drive didn't have a jumper setting the new one does but the factory out of the box is not in it only recommends it when running multiple drives. So its not that either. Any more Ideas I'm completely out of ideas on this one.

that's impossible, they all have a jumper setting in case you need to run several drives on the same line.

give some details on this newdrive so i can look it up.

---

### Post by lindsay7 on 2009-07-09
Sata drives do not have a jumper for master, slave or cable select like the IDE (flat Cable) drives. You can only run one drive on a sata cable.    See this  [http://en.wikipedia.org/wiki/SATA](http://en.wikipedia.org/wiki/SATA)

There could be two things here that are causing this. 

1. There is a jumper to select a 150 or 300 speed for the drive, Some motherboards can not accomodate the 300 speed and they will not recognize the drive if it is set for 300.  Look on the internet for info on the motherboard to see what it will accomodate and set it accordingly.  They all will recognize the the 150 speed. If the drive gets seen this way you can try the 300 speed and see if that works.

2. Some motherboard - drive cominations will not see the drivers for the hard drive on start up.  Windows sometimes can see them but not all the time.  What you need to do is load Gparted, it should see the drive as unallocated and unformated. Set up a new partiton for the drive and format it as fat32. That should let Ubuntu and or windows see the drive and the drivers will get loaded by themself. Later on you can repartiton and reformat the drive as you like.

---

### Post by kerry_s on 2009-07-09
> 1. There is a jumper to select a 150 or 300 speed for the drive, Some motherboards can not accomodate the 300 speed and they will not recognize the drive if it is set for 300. Look on the internet for info on the motherboard to see what it will accomodate and set it accordingly. They all will recognize the the 150 speed. If the drive gets seen this way you can try the 300 speed and see if that works.


i think that's what i meant, but didn't realize it was for speed, instead of master/slave. thanks for letting me know. ):P

---

### Post by lindsay7 on 2009-07-09
They look the same and work the same way, just the function is different.  I have had a number of people get hung up on the speed/motherboard comparability issue and with the master/slave/cs with the jumpers.  Old habits are hard to break. These sata drives are so easy to install, we old timers with ide/pata devices keep wanting to check jumpers and ribbon protocol (ever install a floppy cable backward). Anyway the new hardware is neat and smaller but my fat fingers and bad eyes are making things harder and not easier in some cases i.e. case connections on motherboards!

---

### Post by kerry_s on 2009-07-09
> **lindsay7 said:**
> They look the same and work the same way, just the function is different.  I have had a number of people get hung up on the speed/motherboard comparability issue and with the master/slave/cs with the jumpers.  Old habits are hard to break. These sata drives are so easy to install, we old timers with ide/pata devices keep wanting to check jumpers and ribbon protocol (ever install a floppy cable backward). Anyway the new hardware is neat and smaller but my fat fingers and bad eyes are making things harder and not easier in some cases i.e. case connections on motherboards!

:lolflag: this computer i'm using is actually the first sata i have, it doesn't even have ide connectors. i got it from newegg, i just added ram & the hd, i had 4 sticks 512mb compatible ram, so used 1 of those, i yanked the sata drive from a external enclosure, just enough for a working computer ;) :
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

---

### Post by lindsay7 on 2009-07-10
Talk about bare-bones, this unit is short and sweet, no muss no fuss, just get it done!  Looks like the perfect pc for Ubuntu, Pupply, or Slitaz.  If I did'nt have four computers at home already, I would snap one of these up.  Did you bother to put in a cd drive? I think I would just go with usbs.

---

### Post by kerry_s on 2009-07-10
nope, no cd drive yet. i just used a usb flash drive to install debian testing xfce4. i am planning to put a 2gb stick in later. i'm also thinking about using the 64bit, but for now the 32bit is working so good. i also hear os X runs sweet on it, i chose that one cause it's fully linux compatible and because it can run **any** os.
i modded a linksys wmp54g pci wireless card for the internet connection, basically just took sheet metal shears to the bracket, cut it and bent it to hold the card right.

---

