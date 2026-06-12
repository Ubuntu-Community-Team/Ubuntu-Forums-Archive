---
title: "Newbie - problem fully booting computer so I can get onto instalation process"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by evanm457 on 2009-08-20
I have never rebooted or installed any os before so i am new to this. The problem at the start was that windows 98 would not load so I tried to fix this in the bios setup this was blocked with a password which i didn't know so I took apart the computer and took out the motherboard battery which reseted to default which didnt have a password. On my new laptop I downloaded a copy of ubuntu and image burnt it onto a cd. I then brought across this cd to my old computer and rebooted it. Everything worked perfectly, I choosed the language then got onto the screen which says: -try ubuntu without any changes to your computer  -install ubuntu etc.... i tryed both but the same thing happens to the two of them. It does the ubuntu loading thing for about five minutes and then the screen goes blank. Now this is very similar to what it does with windows 98 it stays stuck on the loading screen. how can I fix this. please remember the only program I can use is BIOS 1999 I think anyway. Any help is really appriciated. Thank You

---

### Post by Partyboi2 on 2009-08-20
Hi, what are your system specs? Are you sure you met the requirements to install Ubuntu?

---

### Post by evanm457 on 2009-08-20
ah yea the computer is only 256mb ram. But the intel is right. is there any linux that runs under 256mb?

---

### Post by Partyboi2 on 2009-08-20
You could try [[COLOR=Blue]Xubuntu,[/COLOR]]("http://www.xubuntu.org/") or try installing Ubuntu using the [[COLOR=Blue]alternate cd[/COLOR]]("http://noncdn.releases.ubuntu.com/jaunty/"), which is a text base installer and does not provide a live environment to check ubuntu out.

---

### Post by cascade9 on 2009-08-20
Yeah, theres plently of linux distros that run with 256MB ram. Ubuntu + Kubuntu are probably a bit 'heavy' for 256MB, but will still run. Xubuntu is a bit lighter, but does prefer a bit more ram if possible. 

You could try- Puppy linux, DSL (damn small linux), Siltaz and theres other 'light' distros as well. 

Bit of a pain that your install isnt working the way it should. Theres 2 easy things you can try though. 
1- Try not installing ubuntu, try running it as a live CD...if that works you could try installing from the liveCD  
2- try running the memory test from the CD, and see if that gives you any errors.

---

### Post by evanm457 on 2009-08-20
ok cascade9 thanx ill try some other small linux. 

1-would 'try ubuntu without any changes to your computer' be the live cd effort.
2-I ran the memory test and nothing came up wrong but i'll try it again and i'll tell you if something wrong pops up.

see I don't think its the installation in it thats going wrong because this also happens when windows 98 trys to load up. There must be something wrong with the load up screen. Any ideas for that?

---

### Post by cascade9 on 2009-08-20
Yep, " 'try ubuntu without any changes to your computer" is the liveCD. Its worth a shot.

BTW, those are only suggestions as far as other distros go. You've already got the ubuntu install CD, and if you can get it working there is no harm in trying it. I would try one of the 'lighter' distros if you are getting really slow performance with ubuntu..and even if that happens try "sudo apt-get install xfce4", logout, log back into the Xfce desktop. 

Not that there is anything wrong with the other distros, but you may find them harder to install software, get support, etc.

---

### Post by Mark Phelps on 2009-08-20
I believe that the desktop CD can not install in 256MB of memory, which explains why you're not seeing anything.  The alternate CD can, but it's not just the memory size that's a problem -- it's also the processor speed.  A Win98 box is most likely using a P III processor, which, even if you DO get Ubuntu or Xubuntu installed, you will find is so slow as to be useless.

cascade9 is right -- you need to try a different Linux distro, one that is designed to run on machines with little memory and slow processors.

---

### Post by evanm457 on 2009-08-20
I tryed the live cd, unfortunatly it doesn't work. The same thing happened. 
But I did notice something that said: [0.000000] acpi:bios age 1999 fails cutoff 2000 acpi=force is required to enable acpi. Now I kind of get this its like acpi (a power distributer) is a year older than it should be in other words it fails the cutoff point of the year 2000. But can still be tryed to run by forcing it to run in the command prompt by typing in acpi=force. I cannot get onto windows therefore I don't have command prompt so I don't think I can do anything about this or can you access the command prompt through bios or something. Anyway I didn't think that that would be much of a problem of course not having will slow down the computer a bit but I wouldn't think that you need it for windows 98 or ubuntu to work. Does any one have any ideas?
Help very much appricated

---

### Post by russu52 on 2009-08-26
have you tried puppy linux, or damn small linux (DSL)? DSL is intended to run on old machines. worth giving a try.

---

### Post by oldos2er on 2009-08-26
You might want to search for a BIOS update.

---

