---
title: "re-install stuck at &quot;Checking Battery...&quot; HELP!"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by riteandritual on 2009-01-23
HELP!

I've been using Ubuntu Intrepid for 2 months now, using a 30GB partition for my /, and 1.1TB for my /home . Last week I figured I'll install XP again for games only, but then I couldn't figure out how to reinstall grub. I couldn't find how to access this elusive 'recovery mode', search as I might. So I deleted the XP partition and the Ubuntu partition and tried to reinstall.

It looks like it installs fine until the screen goes blank and then goes to a 
 * Checking battery state...                                  [OK]
screen and stays there indefinitely. I don't have a battery since I'm on a PC, so this makes me nervous.

So, I start up with the USB ubuntu I made when Intrepid still worked (lucky I did), and it gives me the same problem! So, I type [ctrl]+[alt]+[F2] and get a command prompt, and I type in startx, and here I am, on the USB linux.

Question 1: How do I fix this in my install - and why now, when nothing (hardware) has changed? why?
Question 2: My home with 400GB worth of data is on a 1.1TB partition... will a reinstall overwrite this? can I incorporate this into my install? Or do I have to re-install with a new "home", making it necessary to mount and piecemeal save this data..? 


Athlon 64 4000+ CPU
Gigabit motherboard
2 gigs ram
sata hdd
sata dvd drive (only change since original install)
ATI a-i-w X1900 gpu. 

I'm currently looking for solutions for this problem on the forum and will post my success (if any) for others - in the meanwhile, I'd greatly appreciate help getting my ubuntu back.

PS: In desperation I've tried PCBSD and it seemed to have a problem with my graphics card too.... but my graphics card used to work fine on my original ubuntu install!](*,)

---

### Post by riteandritual on 2009-01-23
Status Update: 

following hints I found in other parts of the forum, I tried 

>    sudo apt-get install xorg-driver-fglrx jockey-gtk 
                sudo ati config --initial


.....and now all I have is a blank screen, from which I don't know how to get out of. I don't know what to do, and I'm totally confused because the first few installs I did had no problem what-so-ever.

---

### Post by riteandritual on 2009-01-24
ok... temporary fix for problem: installed Sabayo Linux, which works out the box. I find it slightly slower than Ubuntu, and I feel disorientated with KDE, but it works for now, and that's all I want for now. Maybe I'll just sit with Sabayo till the next Ubuntu release and maybe that'll work on my computer again.

---

### Post by riteandritual on 2009-01-26
I don't like Sabayo linux and it feels slower than Ubuntu. So what I did was try to install Ubuntu again after I installed Sabayo linux. And it worked. No Check Battery State, no xserver complaints....

I don't know if its something weird to do with grub or the boot process, but it really feels like installing the grub through another linux made the Ubuntu install itself work. 

So, if you are getting that problem - xserver wont start, booting always stalls with a "Checking Battery State...........[OK]" ... then my only advice is to try to install another linux on another partition first, and if it works then go back to trying to install ubuntu. Don't know why, but it might work for you too.

EDIT:

Update - I think its a harddrive issue. Harddrive partition has errors, and it wasn't installing another linux that helped but another rewrite of the partition table or partitions. I don't know, I'm a newb. But I do have Jaunty working now (cross fingers).

---

