---
title: "Black screen after install"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by stewieK on 2009-09-26
Hello
I have been searching for anything that could help me all day, but to no avail.
There are similar questions but nothing that has been useful to me.

Im trying to install ubuntu srever 9.04 on a brand new machine, there is no previous OS on this thing and i built it myself. (which could have something to do with it)
After I run the installer disc, it says that it is successful, ejects the disc and prompts me for a restart. But upon restart (and after the splash screen for the BIOS) all I get is a black screen, no cursor, no loading signal, nothing...
Also nothing happens if I try 'control alt F1' or any other key combo (not even the konami code works :(

I have read about people being able to boot from a 'live' CD but I don't seem to have anything that gives me that option.
I have tried both the 64bit and 32bit disks thinking that might be it, but I get the same thing.

Any thing any one can suggest, or even point me to a previous post, would be greatly appreciated.

Also I'm originally a Mac user and this is my first attempt at anything out side that pretty little bubble, so be kind :)

thanks

---

### Post by cgroza on 2009-09-26
You should check disk integrity ...if everything is ok then try another version...can you go to command shell...you could do something from there.

---

### Post by rreese6 on 2009-09-26
I suspect you forgot to install the grub boot loader in the MBR.(Master Boot Record). Since Bios boots, and you probably get a really quick flash of the HD lED, but then nothing.
so what would I do?
Put the CD back into the drive.
power up.
Run Ubuntu from CD Rom to make sure it works.
you did say Server though...are you wanting to run a basic server
no GUI?
answer some more questions and then we will fix it.
Are you wanting a minimal Server or Desktop?
did your HD LED flash after BIOS screen?
DO you know the "run the LiveCD" Means to Put the CD in the CD Rome Drive and boot from it?

---

### Post by QIII on 2009-09-26
To use the LiveCD, choose the option that says something like "Try Ubuntu without changes to your machine."

Could you please post the specs of your machine?  I'm particularly interested in the graphics chipset, but if your could give us as much as possible it would be helpful.

---

### Post by stewieK on 2009-09-26
Cool, thanks for the quick response every body.
specs are:
ASUS P5KPL-AM/PS INTEL G31/ICH7 LGA775 mATX DDR2 PEI-E Motherboard
Intel Pentium Dual Core #E5300 2.6Ghz LGA775 2M 800FSB
Transcend DDR2-800 2GB CL5 JetRam
Western Digital caviler green 1-TB HD
and an Asus PATA DRW.
I was just running the on-board video and sound stuff.
oh and my mac keyboard

Im pretty sure Grub was installed (we made a joke about it at the time) but its possible that it didn't do it properly.

when I boot up the disc i get the following options:
Install  (tried this a couple of times)
Check disc (seems to be ok)
test memory (which throws the screen into a black pit of doom)
boot from first hard disk (again black screen)
rescue a broken system (i got confused and ran away from this)
and then just the extra stuff at the bottom like languages and stuff.
I cant see anywhere that would let me boot into it from here

@cgroza: I cant seem to find ssh but maybe its in an option i haven't seen yet

@rreese6: I first thought that cuz the desktop version came with a GUI that the server would too, but sadly not. Basically what Im trying to set up is a small web sever for hosting my own site and for development, basic file sharing and also a place to store all my music and movies.

@QIII: spec are above.

Cheers, thanks guys

---

### Post by stewieK on 2009-09-26
WOW, could I be absolutely retarded and be trying to install onto my CD drive somehow and not the hard drive? And if so how do I NOT do this???

---

### Post by rreese6 on 2009-09-26
I don't think the installer would work if you tried to write to a read only drive (CD ROM) so you are ok there.
ok so you have tried to install a few times.
when you boot up grub, could you highlight the one you want then hit "e"
then go to kernel line and hit "e"
then go to the end of the line and if you splash and/or quiet there, backspace over those and then hit "enter"
then hit "b" to boot up.
if you fail you will get to see it.
Maybe the system isn't totally compatible..so a nice 8.04 server install would be better.

---

### Post by stewieK on 2009-09-27
W0OT! I think Im in now, i disabled the 'quick boot' and 'full screen logo' settings in the BIOS menu and every thing seems to load up, and I am presented with a login.

Thanks for your help guys :)

---

