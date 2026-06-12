---
title: "cant boot live cd or install"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by puppetj on 2008-12-15
at boot get stuck at busy box with
tops at #setting up ramfs tree#

then repeats:

ide:-cd timeout: cmd 0x20 timeout
hda:dma timeout retry
hda:timeout waiting for dma
hda: status error: status=0x58
at bustbox i get:

driveready seek complete datarequest
ide: failed opcode was: unknown
hda:drive not ready for command







which also i got the small ubuntu to install but after boot i get the small issue i can continue to boot but i need to type exit like 8 times

---

### Post by icanfly0307 on 2008-12-15
What type of CD are you using (ie LiveCD, Alternate)? Those type of "timeout" errors make it look like your CD or your CD Drive is failing. what speed did you burn the CD at? Would Network Install be an option?

Sorry if I'm overwhelming you with my questions, but I don't want to leave anything out. :)

---

### Post by puppetj on 2008-12-15
NP about asking alot im just glad i got a reply,
Im using the cd that are free that are sent in the mail, i have same issue with other linux distros also, but windows boots and installs fine. network install would work because i still get the issue when booting up when i got the mini ubuntu installed, which installs fine but after install i get the issue at boot up like i mentioned "which also i got the small ubuntu to install but after boot i get the small issue i can continue to boot but i need to type exit like 8 times"

---

### Post by icanfly0307 on 2008-12-15
Since you're saying that Network Install would work, I'd recommend that you go ahead with that. Check out this link: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

PS. Make sure that you are using a WIRED internet connection and not wireless. This will reduce the risk of you messing up the install. Also, Ubuntu 8.10 is buggy and depending on your hardware, you might want to try out Ubuntu 8.04. 8.04 is better, stable, and better supported. Again, it's up to you. :)

---

### Post by puppetj on 2008-12-15
yeah but why does windows install

---

### Post by abn91c on 2008-12-15
> **puppetj said:**
> yeah but why does windows install

make sure your cd is free of fingerprints, scratches, dirt, etc, linux is not as forgiving as a scratched up windows cd. if you have compressed air give your drive a couple of shots, like [COLOR="DarkOrange"]icanfly[/COLOR] said you cdrom may be going...

---

### Post by puppetj on 2008-12-16
the cds are in excellent condition, i just booted aup windows and installed it again, no issues, could it be that most linux distros cant support this drive?  even when i got it install using mini ubuntu i only the these errors after installing and booting to hd. so why can mini ubuntu be the only linux to boot install and fail when the others, b/c i tried like about 15 distros and they just fail to boot even before live cd boot or install.

thanks

---

### Post by Therion on 2008-12-16
> **puppetj said:**
> yeah but why does windows install
Because your Windows CD is stamped, not a "burn".

What I can suggest is trying a different media.  I've found that when it comes to getting a distro to install ANYthing can make a difference, not the least of which is different brands of install media.  If you're using a TDK CD, try Memorex.  If you're using Memorex, try TDK.  Sometimes I've had the best luck with cheap no-name media like the ones I got at the local office supply store.

Another odd-ball suggestion that worked for me was switching from a 40-wire connector cable to an 80-wire connector cable for my optical drive.  Both have 40 pins, but the extra wires in the 80-wire cable filter out electromagnetic "noise" that can prevent a CD from being read properly.

You have to keep in mind that not all CD's are equal.  Burning an .mp3 to a CD is one thing, but when you're trying to get an entire operating system to run off a single disc, that's a little different and even the tiniest error can turn a disc into a "coaster".

---

### Post by puppetj on 2008-12-16
> **Therion said:**
> Because your Windows CD is stamped, not a "burn".

Please read all my posting, thanks :


and the ubuntu cds that are sent in the mail arent stamped?

and what about the mini ubuntu cd that was burned with verbatim media that worked?




the drive is using a 80 wire cable

---

### Post by mrbiggbrain on 2008-12-16
i hope this helps, i had a cd drive that linux kept polling ( i recived those errors) and it either wasnt polling back, or not correctly. the timeing out means the drive cant (for some reason) talk to the drive. have you tryed running with the safeboot, failsafe, or nohotplug, ect options.

in slax (my favorit live cd) this is achived by

slax nohotplug - skips hotplug detection

slax nocd - dosnt mount a single cdrom, useful if its your only cdrom and your not running off ram (as your cdrom is take up anyways)

honestly id try the nocd option if your distro has it, it can be useful for skipping hardware that always errors due to incompatible hardware/firmware or drivers.

---

### Post by puppetj on 2008-12-16
> **mrbiggbrain said:**
> i hope this helps, i had a cd drive that linux kept polling ( i recived those errors) and it either wasnt polling back, or not correctly. the timeing out means the drive cant (for some reason) talk to the drive. have you tryed running with the safeboot, failsafe, or nohotplug, ect options.

in slax (my favorit live cd) this is achived by

slax nohotplug - skips hotplug detection

slax nocd - dosnt mount a single cdrom, useful if its your only cdrom and your not running off ram (as your cdrom is take up anyways)

honestly id try the nocd option if your distro has it, it can be useful for skipping hardware that always errors due to incompatible hardware/firmware or drivers.


slax was not one i tried, but that can boot up without any commands lines that you gave me and that was on a burnt cd, so what does that mean for ubuntu?

---

### Post by mrbiggbrain on 2008-12-17
it means ubuntu is trying to do something different then slax and failing. maybe ubuntu does a deeper check of the drive, or maybe ubuntu doesn't include the drivers or features needed for running the drive, did u try running slax under slax copy2ram and using the CD drive? if it gets errors trying to read then the drive is having issues with Linux and slax is just not complaining well it boots (because its getting what data it needs)

also i know that my copy of ubuntu 8.10 install has a failsafe kernel, does the livecd have one too? trying that might prove useful as it might just finish up even with errors. and i think my  PC might have actual just final given up and continued CD drive or no Cd drive

---

### Post by puppetj on 2008-12-17
> **mrbiggbrain said:**
> it means ubuntu is trying to do something different then slax and failing. maybe ubuntu does a deeper check of the drive, or maybe ubuntu doesn't include the drivers or features needed for running the drive, did u try running slax under slax copy2ram and using the CD drive? if it gets errors trying to read then the drive is having issues with Linux and slax is just not complaining well it boots (because its getting what data it needs)

also i know that my copy of ubuntu 8.10 install has a failsafe kernel, does the livecd have one too? trying that might prove useful as it might just finish up even with errors. and i think my  PC might have actual just final given up and continued CD drive or no Cd drive




and mini ubuntu [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) boots installs fine? but after installed then  boot up fails??

---

### Post by icanfly0307 on 2008-12-17
I know I've said this already. Can't you go with a Network Install? It'll save you the hassle of burning a new CD and checking it for errors. Of course, if you don't have high speed internet, it won't work. What's your bandwidth speed for your internet? Mine was around 210kB/sec and it took around an hour to install everything.

---

### Post by puppetj on 2008-12-17
network install maybe help to install it, but it still going to fail on start up remember?

---

### Post by icanfly0307 on 2008-12-17
How exactly does it fail? Post the error message that you get when you use UNetBootin (see my first post on this thread.)

---

### Post by puppetj on 2008-12-17
i did plenty of times...sigh look at my 1st post it the same error i get read what i said about mini ubuntu

---

