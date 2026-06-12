---
title: "HDD damaged please take a look"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by Gandalf on 2006-03-20
Hello,

Ok i woke up an hour ago to find that my Server has the HDD LED always on, i don't know what could happend, but the computer was totally out of order, no http, no ssh so i've made a hard shutdown as i can't see what's going on, i took out the vga...

But now the HDD is completely screwed i'm not sure why this happend (even that i bought it 2 weeks ago), when i turn on the PC the HDD is kinda ringing (lol) i donno why, i've record an ogg file it is [here](http://w.nasreddine.free.fr/hdd.ogg) ( Ogg 179kb), so Please tell me, is there any way i can get back the data?? I have a backup of All my websites database, but i don't have any backup of the files, as i just bought it and i needed space to put them on... please spare me from sarcastic comments as i am not in the mood for such comments now (i bet u know how i feel now)...

Thank you :cry:

---

### Post by TTT_travis on 2006-03-20
If your lucky this is just a motor error in which case the hard drive in the freezer trick might work. Google if you have no clue what I'm talking about

---

### Post by beast2k on 2006-03-20
Pray you still have a recept for an exchange, it sounds like it bought the biskit (Broken)
edit: If you feel adventurous you can try spinrite6 I have never used it myself but I have heard it has performed miracles when it comes to data. However it will cost you m0ore than a new hard drive. *cough* bittorrent *cough*

---

### Post by Gandalf on 2006-03-20
Yea i do have the guarentee, but i really don't care now about the price nor the HDD itself, but i do care about the data, it's a work of 3 years which i don't have (fool me) any backup :cry:

@TTT_travis  if it's the motor, is there a way to get the data back

---

### Post by Gandalf on 2006-03-20
[QUOTE=beast2k]Pray you still have a recept for an exchange, it sounds like it bought the biskit (Broken)
edit: If you feel adventurous you can try spinrite6 I have never used it myself but I have heard it has performed miracles when it comes to data. However it will cost you m0ore than a new hard drive. *cough* bittorrent *cough*[/QUOTE]
Well actually i'm not sure if i ever be able to detect the HDD, i mean the bios is not detecing it and that is a big problem, a software cannot help i think, unless some magical soft that bypass bios detection, anyway i'll try it thx for the tip and 10x for being so kind...

EDIT: for the first boot with ubuntu live cd, the HDD has been detected by the bios... i'll let u know what happens

---

### Post by Gandalf on 2006-03-20
:cry: Ubuntu detect it but
```

sudo fdisk -l /dev/hda

``` does nothing :cry:

```

sudo cfdisk /dev/hda

``` -> ERROR: cannot read disk drive

---

### Post by s|k on 2006-03-20
You might get more help if you post this in the hardware help forum.

EDIT: oops double posted. I don't see a delete option. :(

---

### Post by s|k on 2006-03-20
You might get more help if you post this in the [hardware help forum]("http://www.ubuntuforums.org/forumdisplay.php?f=98").

---

### Post by Gandalf on 2006-03-20
Ok then i request a moderator to move it, in order to avoid forum spaming :(

---

### Post by mstlyevil on 2006-03-20
[QUOTE=Gandalf]Ok then i request a moderator to move it, in order to avoid forum spaming :([/QUOTE]

Done. :mrgreen:

---

### Post by Gandalf on 2006-03-20
[QUOTE=beast2k]Pray you still have a recept for an exchange, it sounds like it bought the biskit (Broken)
edit: If you feel adventurous you can try spinrite6 I have never used it myself but I have heard it has performed miracles when it comes to data. However it will cost you m0ore than a new hard drive. *cough* bittorrent *cough*[/QUOTE]
SpinRite does nothing, It always say "Undetermined format" ... :cry:

@ mstlyevil  Thx :grin:

---

### Post by Leigh on 2006-03-20
Have you tired going to the HDD's manufacturer's website. They usually have utilities that do non-destructive tests on their drives. That may give you an idea as to what's wrong and whether it can be fixed.

---

### Post by Gandalf on 2006-03-20
Hmm it's a Maxtor DiamondMax 10, 300 Gb, 720RPM IDE 16Mb Cache...

I'll see what i can find, thx

---

### Post by mozetti on 2006-03-21
If nothing else works, the freezer trick is worth a shot.

---

### Post by nocturn on 2006-03-21
EDIT: Advice not relevant since drive isn't detected anymore

---

### Post by nocturn on 2006-03-21
I'm really sorry to say, but if neither Ubuntu with fdisk and spinrite show it, it is probably beyond recovery.

Also, the utils from Maxtor cannot work unless it is detected by the BIOS.

If the data is really worth it, I woul recommend contacting a data-recovery firm.

---

### Post by Gandalf on 2006-03-21
The bios is detecting it, i can see Maxtor on primary IDE but that's it, nothing beyond bios, when bios try to detect it produces that sound 3 or 4 times and i don't hear it again unless i shutdown the PC.. which is weird, it's like nothing is accessing it...

@mozetti u're the second person who tells me about the freezer trick, so am gonna give it a try, i have nothing to lose anyway, i lost my data, i can't pay 600&#8364; for the data so either it work by my tricks or so long data, i'll have over a week of work to get back 5 sites with the whole design :(

---

### Post by frodon on 2006-03-21
Hi gandalf,

I crashed my maxtor drive 3 weeks ago and fsck, fdisk and all those tools didn't help me because like you my drive was undetected or unreadable.
Install ddrescue, and reboot your computer without trying to mount your partition and run a : ```
dd_rescue /dev/name_of_device /home/Gandalf/drive-img
```It will take a HUGE time (20h in my case), but you will get an image file of what is readable on your drive.
I give you a link with useful instructions : [http://www.titov.net/category/server-administration/](http://www.titov.net/category/server-administration/)

Anyway if the disks in your drive are damaged it will not work. Let me know if it works, there are other solutions but this is one best chance you have to copy some datas from your crashed drive

---

### Post by frodon on 2006-03-21
double post, mod please delete it, thanks

---

### Post by mozetti on 2006-03-21
[QUOTE=Gandalf]@mozetti u're the second person who tells me about the freezer trick, so am gonna give it a try, i have nothing to lose anyway, i lost my data[/QUOTE]

If the data on the drive is already gone (meaning you formatted it, or something similar), then the freezer trick isn't going to work. It's a temporary solution to get the drive working long enough to pull the data off before you scrap it. But, if the data should still be on the drive, then the freezer trick may allow you to recover it. Depending on how much you need to copy, it might require multiple trips in the freezer to get it all off.

Basically, your freezing the drive to get all the parts inside to contract and hopefully get into a working condition. As the drive warms up with use, it may become unreadable again. So, you put it back in the freezer and then continue copying from where you left off. Rinse & repeat until you get it all copied. If it works, i recommend copying small amounts at a time so it doesn't crap out halfway through.

---

### Post by Gandalf on 2006-03-21
the freezer trick didn't work, i'll go with frodon idea and see what i can get with it..

BTW the store where i bought just sent me a mail that they accept to exchange it (well they save me the pain of an RMA with maxtor directly) but they decline any responsability on the data, also they gave me 15 days to accomplish the return so am gonna try today, tomorrow will send it weather i had my data or not...
anyway i think I have a backup since Jan 1st i'm trying to list the content but it take a huge time to iist file in a bizipped 15Gb file... hopefully i have at least the projects i spent hours and hours making them :cry: now i know how Precious is rsync, *hugs* rsync :(

---

### Post by AndrewB on 2006-03-21
If you pick up a second identical drive (matching firmware rev's) you can try switching controller boards from New functional drive to new dysfunctional one.  Not for the faint of heart, but a way to retrieve valuable data none-the-less. _This will totally void the warranty on both drives._

---

