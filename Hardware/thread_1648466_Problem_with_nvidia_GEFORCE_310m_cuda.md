---
title: "Problem with nvidia GEFORCE 310m cuda"
date: 2010-12-18
forum: Hardware
---

### Post by crownclown on 2010-12-18
Well im using 10.04 ubuntu and i install the nvida driver as it say so...
after installation is complete then i restart after restart and enter the ubuntu there only a blank screen?
what should i do with it or it doesnt support ?
after reformat almost 5 times.
then i just used 10.10 but dint install the nvdia.
i afraid it just happening again..
thx...
plss help...
NEWBIE here :p

---

### Post by crownclown on 2010-12-18
OMG =.=
after using ubuntu 10.10 i install the nvidia as its recommended me to install..after install it become worse T.T
now after boot the ubuntu it just come out the terminal?
after install graphic just terminal comes out ? oh noooooooooo!!! :cry:

---

### Post by Youth on 2011-01-08
iv got the sam problem, installed the recommended nvidia drivers then i get a blank screen upon load up.... iv been looking around and read that you got to delete the drivers installed. then ubuntu will automatically load the default ones which was in use before.

im trying to find out how to delete those drivers from grub commandline.... but cant find much info on how to delete files through grub command

some links that may help 

[http://www.techsupportforum.com/forums/f64/nvidia-drivers-in-ubuntu-didnt-work-need-to-restore-145490.html](http://www.techsupportforum.com/forums/f64/nvidia-drivers-in-ubuntu-didnt-work-need-to-restore-145490.html)

[http://www.youtube.com/watch?v=Sh4ZmBdFCuU](http://www.youtube.com/watch?v=Sh4ZmBdFCuU)

---

### Post by cascade9 on 2011-01-08
crownclowns problem was 'optimus' (switchable graphics). Here is a thread on optimus, and the fix should work for you- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1657660](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1657660)

---

### Post by crownclown on 2011-01-09
> **cascade9 said:**
> crownclowns problem was 'optimus' (switchable graphics). Here is a thread on optimus, and the fix should work for you- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1657660](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1657660)

thx cascade...
well i've try..but seems it get the same result.. T.T
Well hope nvdia notice the driver for ubuntu...

---

### Post by cascade9 on 2011-01-09
I posted that more for Youth than for you crwonclown (I dont think Youth has the foggiest idea of what switchable graphics or optimus is). 

nVidia isnt even working on a linux optimus driver. :(

---

### Post by 3602 on 2011-01-09
Well I'm happy that I switched computers (new specs see sig) and no problems with proprietary ATI drivers. Now I can run TORCS at a glorious 40 FPS. All hail the great Tux.

---

### Post by capone_sin on 2011-01-10
I have the same problem, but if you get the black screen, don't reinstall ubuntu :) Just type in the Terminal "sudo rm /etc/X11/xorg.conf" and you're done. Still..., can't find a solution to install the drivers :(

---

### Post by 3602 on 2011-01-10
> **capone_sin said:**
> Still..., can't find a solution to install the drivers :(
There is none. nVidia isn't working on it.

---

### Post by capone_sin on 2011-01-10
Yes I know, but I heard that it could work with a custom EDID file. Not switching between devices, cause I know Optimus is not working, but at least to use only the nvidia.

---

### Post by 3602 on 2011-01-10
> **capone_sin said:**
> Yes I know, but I heard that it could work with a custom EDID file. Not switching between devices, cause I know Optimus is not working, but at least to use only the nvidia.
Oh, then I can't help you. A search turned up external screen resolutions and not switching. But if your BIOS doesn't support hardware switching then... Good luck.

---

### Post by cascade9 on 2011-01-11
> **capone_sin said:**
> Yes I know, but I heard that it could work with a custom EDID file. Not switching between devices, cause I know Optimus is not working, but at least to use only the nvidia.

IMO if it was as easy as EDID, nvidia would have done it.....though if you've got a link to anything about this, I'd be interested to see it.

---

### Post by capone_sin on 2011-01-11
> **cascade9 said:**
> IMO if it was as easy as EDID, nvidia would have done it.....though if you've got a link to anything about this, I'd be interested to see it.

Look here [http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

This guys have the nvidia 310m, just as I have, but the topic is about Sony notebooks. I have a MSI CX623 (and from what I know the Optimus technology also). Some of them seems to have solved there problem with a custom EDID. 

I'm not interested that Optimus works. I want to use only my nvidia and not the integrated Intel chipset.

Please tell me if I misunderstood the problems and if these are two different things.

But from what i understand is that you could make the nvidia work without the Optimus option if it wasn't for the display problem.

Please forgive my bad English

---

### Post by cascade9 on 2011-01-11
Your english is fine. ;) 

Since I cant read the sonycw.txt file, I dont know what is in there. It could be that it forces the system to use the nVidia graphics only. 

That would work, but it end up just being the same as a BIOS switch, but messier. Which is typical Fony.....

---

### Post by capone_sin on 2011-01-11
Yup! You're right, but if you can't do a BIOS switch, that is the only chance.

---

### Post by crownclown on 2011-01-12
> **capone_sin said:**
> Yup! You're right, but if you can't do a BIOS switch, that is the only chance.

ya there is not swtichable for graphic in asus too...
hummmm hope got any solution about this optimus technology ...
right now by using the integrated intel graphic doesn't have the best quality...

---

### Post by capone_sin on 2011-01-12
Yeah, when I installed the system I was by default using my Integrated Intel Graphics. 

My desktop effects were working. Not to good, but at least they were working. 

Than I tried to install and force my nVidia to work, of course without any success.

Now I tried to reactivate my Integrated Graphics, but I don't think they are working as they should, cause my desktop effects are not working anymore... any solution?

---

### Post by crownclown on 2011-01-20
> **capone_sin said:**
> Yeah, when I installed the system I was by default using my Integrated Intel Graphics. 

My desktop effects were working. Not to good, but at least they were working. 

Than I tried to install and force my nVidia to work, of course without any success.

Now I tried to reactivate my Integrated Graphics, but I don't think they are working as they should, cause my desktop effects are not working anymore... any solution?


it seems we get the same problem and no resolution...
well right now im using the intel just like that...no doubt about it..
but never mind right now the graphic seems find to me even not using the nvidia....

---

