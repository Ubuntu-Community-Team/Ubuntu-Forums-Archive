---
title: "epson scanner and sane help"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by OrganicPanda on 2006-07-19
hey all can anyone help me get my scanner up and going?

i checked the lists on the sane website before i bought my scanner, an epson perfection 3490, which i now need to get working, this whole situation of backends is weird, how do i actually install this scanner, 'lsusb' detects that it is connected fine and:

[http://snapscan.sourceforge.net/]("http://snapscan.sourceforge.net/")

is the backend for it but im missing out on how to put 2 and 2 together to get a usuable scanner, can someone lend some assistance here, much appriciated,
OrganicPanda

---

### Post by zxee on 2006-07-19
Is sane installed? From a shell try 'sane find scanner'. xsane is the front end for sane and if you have that you could just open it and it should "see" your scanner. If sane isn't installed use apt or synaptic to get it. Hope that helps and let us know how it goes.

---

### Post by OrganicPanda on 2006-07-19
it says no scanners found, this sucks, it says on that page that this scanner is supported :(

---

### Post by claydoh on 2006-07-19
if you find your scanner model on the sane snapscan page linked above, you will see the name of a firmware file that you will need to get from your scanner's driver disk, or from C:\windows\system32 or someplace similar and copy it to /usr/share/sane/snapscan:

```
sudo mkdir /usr/share/sane/snapscan
sudo cp /full/path/to/firmwarefile.bin /usr/share/sane/snapscan/
```
this file is needed to make sane be able to talk to your scanner.
 
Then you need to edit with sudo the snapscan config file /etc/sane.d/snapscan.conf and edit the line near the top that stars with "firmware" to add the name of your firmware file, so it should read:
> firmware /usr/share/sane/snapscan/esfw52.bin 
There are other posts regarding your scanner model if you want to search for more info, the sane snapscan page isn't very clear for sane/linux scanner novices :(

---

### Post by noynac on 2006-07-19
I got a 3490 working, but it wasn't easy. I followed the thread at:

[http://www.ubuntuforums.org/showthread.php?t=108256&highlight=3490](http://www.ubuntuforums.org/showthread.php?t=108256&highlight=3490)

The key for me was the firmware line in the snapscan configuration file (as claydoh suggests). Once I got that line correct and the firmware file on my Ubuntu partition, the rest was easy.

BTW, the esfw52.bin firmware file is on the epson disk, but I believe it is in a CAB file that must be decompressed. I found it on my Windows partition, which contained the Epson software.

---

### Post by OrganicPanda on 2006-07-20
hey thanks for the replys peoples,

i did see that thread after i posted but it being in the breazy section kinda put me off because i heard this model works out of box in dapper, i will follow the above instructions and see how it goes, cheers guys / gals

---

### Post by OrganicPanda on 2006-07-20
ok excellent, i can't beleive i finally have some extra hardware that works in linux, flatbed scanning works a treat allthough finding the right settings isn't something i'm good at lol, i'm also in need of instructions to tell me how to scan with the transparency unit correctly, i can't seem to get the colours right

but anyway thanks you guys, i just need to get some guides then i'm done but i guess thats not for this hardware section lol, cheers

---

### Post by noynac on 2006-07-20
Glad you got everything working. The scanner does work well once installed. 

Linux has made great strides in many areas, but hardware installation is overly difficult. I tried and tried to get a Canon inkjet printer working and finally gave up.

---

### Post by OrganicPanda on 2006-07-21
ubuntu (and linux in general i guess) is a myterious beast, my epson photo printer installed fine, all by itself, i didnt need to do a thing and yet this took manual editing of config files lol, but hey at least i'm learning new things, maybe it's good that it's not as easy as windows, i like a challenge... although i will make clear there is a difference between a challenge and an impossibility, the latter are a bit more annoying

---

### Post by lonrot on 2006-08-12
I have tried to find the cab file or whatever on the CD and nothing yet. My windows is x64 so I don't have drivers. Can anyone help me a little, this is so confusing!

---

### Post by noynac on 2006-08-12
If you PM me your email address, I'll forward you the necessary file. I assume that is the difficulty.

Once you have the firmware file, editing the configuration file is pretty simple, as explained in an earlier posting.

noynac

---

