---
title: "Gigabyte AMD motherboard"
date: 2008-04-29
forum: Hardware
---

### Post by edjog on 2008-04-29
I am a new Ubuntu user and am hoping to get rid of Windows altogether very soon :)

I've been looking for a silent non-gaming system and I've found the mobo I am looking for: [http://www.overclockers.co.uk/showproduct.php?prodid=MB-115-GI]("http://www.overclockers.co.uk/showproduct.php?prodid=MB-115-GI")

But then I realised Ubuntu might not support it. Indeed Ubuntu might not support many new motherboards. So what advice do you have? Do linux drivers tend to come out soon after windows ones. Is AMD and Gigabyte generally OK with linux?

---

### Post by daengbo on 2008-04-29
The video is likely to give you some trouble setting it up. See:
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg01352.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg01352.html)
audio appears to work but the DTS doesn't:
[http://ubuntuforums.org/showthread.php?p=4817626#post4817626](http://ubuntuforums.org/showthread.php?p=4817626#post4817626)

---

### Post by edjog on 2008-04-29
Thank you Daengbo! It looks very difficult but seems possible. I suppose the DTS might be made to work sometime in the future?

---

### Post by CREEPING DEATH on 2008-04-29
AMD does/did offer nearly identical boards with NVidia chipsets, they works wonderfully with 6.06.

CD

---

### Post by edjog on 2008-04-30
Thanks. I checked out some amd/nvidia specs but I am going to go for the original Gibabyte board because it's been installed OK [here.]("http://ubuntuforums.org/showpost.php?p=4523334&postcount=6")

In all the searching around, it seems ubuntu supports most things so I am even happier now!

---

### Post by nujnxrzkppmvoc on 2008-05-03
Hey there,

i own that mobo you guys are talking about (twas the gigabyte GA-MA78GM-S2H, right?).

I'm also quite new to linux, so maybe this helps the OP:

The latest Ubuntu 8.04 runs "out of the box". 
Don't be surprised if the screen resolution looks terrible (800x600 or so), 
you only need to set up an internet connection to download the ati-drivers.
These can be found via the integrated packet-manager of Ubuntu called Synaptic.
Synaptic allows you to search, download and automatically integrate software into your Ubuntu.
After a restart of the Desktop (press ctrl+alt+backspace) you should see that everything is working just great (1240x1200 or so ^^)!!!

[Okay, and here 3 tips on installing this linux thingy, since i am also "new" to Ubuntu i found out about this peux-a-peux:

- What Ubuntu version? 
I'm using a 32bit desktop-version of Ubuntu, but (!) there's also an alternate-version which offers optional harddisk encryption when you install it, how cool is that?!

- Where to place systemfiles?
Make sure you know how you want to partition your harddisk space, 
i.e. make an extra logical drive for your "/home" folder.

- ???
Use the integrated Ubuntu-guide if you're stuck, it helps a lot! ... sometimes.

- Can i has internets?
Most important on a new system is internet i guess...to get help! 
Get it all working by opening a terminal, which is a dos-like environment.
The terminal can be found in >Menu >Accessories >Terminal.
Type in the command:   sudo pppoeconf          and then your password.
Work through the menu.
Then start the connection with the command:   pon dsl-provider
thats it, everything should be manageable via the ubuntuforums.
Hope that helped, have fun :D ]

---

### Post by edjog on 2008-05-05
Thanks. Great to know it runs out of the box on that mobo! Thanks for all the tips as well, very helpful.

---

