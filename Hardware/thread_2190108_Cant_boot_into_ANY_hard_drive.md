---
title: "Cant boot into ANY hard drive"
date: 2013-11-25
forum: Hardware
---

### Post by WinterMadness on 2013-11-25
i have an asus cg5270. Recently, it stopped booting **consistently** (That is, sometimes I can boot into the hdd, sometimes I cant). I assumed the hard drive was going bad, I was able to still get into it once and a while but it would usually hang and then say that I need to insert a proper boot device.

So I bought a new HDD, a SDD actually, and I goto install Kubuntu on it (using the entire disk) and everything is fine until the installation is done and I try to boot into it. The thing is, Kubuntu noticed the hard drive, it installed to it and told me how large it was. I'm on puppy linux right now and I can see the hard drive, and I can explore it. But I can't seem to boot into it. What gives?

I dont think this is really a linux problem per se, but I think you guys can help me. 

I tried the boot order too, I selected "Hard Drive" as the first one and it didnt work. I suspect (but I cant confirm) that if I restart over and over it will eventually work but I dont know why, and i dont want to do that because its bad for the computer.

---

### Post by WinterMadness on 2013-11-26
so I tried installing on a fresh HDD. I switched it over to ide mode, installed Kubuntu onto it. Kubuntu knew which hard drive I had in the live environment, when I boot it says primary hard  drive error or something like that. could it be a bad data cable? what else could it be?

---

### Post by rackit on 2013-11-26
Check for a firmware upgrade for the SDD. I know some Samsung drives need to be upgraded to work properly, unfortunately, the firmware upgrade program for Samsung is Windows based.

---

### Post by WinterMadness on 2013-11-26
the Ssd is Kingston, and the other hard drive I used was western digital.

---

### Post by rackit on 2013-11-26
Still, see if there is a firmware upgrade available.

---

### Post by WinterMadness on 2013-11-26
How would I go about that? Keep in mind that the only way I can use my computer at the moment is via puppy linux in a live environment.

I dont have access to any "installed" OS.

---

### Post by rackit on 2013-11-26
My bad. I'm thinking that you have access to another machine. Can you boot to an "old" disk drive?

---

### Post by WinterMadness on 2013-11-26
No, this computer wont boot into any hard drive.

I just dont understand why I'm able to mount the hard drive, and view it when I'm in puppy linux, but it wont boot after an installation. I clearly see folders on the hard drive that my installation of kubuntu created. I just wrote to it, creating a blank file called "hi" but I cant for the life of me get it to boot into any of my hard drives anymore. 

I mean, this started a month ago with the hard drive that came with the computer. I think I got the computer in 09. 

I dont think it could be a firmware issue if both puppy linux and kubuntu are able to notice it. I could be wrong though, but if you think thats a possibility, how would I update such a thing?

---

### Post by WinterMadness on 2013-11-26
Is it possible that its the power supply?

---

