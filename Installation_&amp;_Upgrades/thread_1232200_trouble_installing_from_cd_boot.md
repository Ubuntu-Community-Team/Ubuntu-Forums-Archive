---
title: "trouble installing from cd boot"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by V4NILL4xxTHRILL4 on 2009-08-05
I have installed ubuntu 9.04 alongside windows xp. Now that I know it works on my computer I want to install it completely and get rid of windows. 

The problem is when I boot up the computer with the cd (burned iso image), all I get is one line that says something like   "isolinux ....  copyright info " and then the blinking cursor underneath it. Nothing else happens.

My computer is a compaq deskpro (dont know which one). 

Something interesting happened when I was trying to get rid of one of the hard drives, upon boot up it said that it detected the change. Underneath that it said that if I wanted to run unix that I had to use the F10 setup utility ( I guess to change something, but what? I dont know.) When I rebooted I hit the F10 button, went into the setup, but if there was a setting there I had to change, I wouldnt know what to select.

I have searched the internet, and found nothing, so if someone who knows more about computers and the problem I having can help me I would be very gratefull, cant wait to kick windows xp to the curb.

---

### Post by tripolitan on 2009-08-05
What does "...I was trying to get rid of one of the hard drives" actually mean?

Live versions do not detect "change" since they have no clue what was there in the first place and they don't care. The "change detected" means that the CD did not even boot or somehow you picked a different option that booted your existing Ubuntu install. The other possibility is that your BIOS is not setup to boot from CD and went straight to GRUB which booted your existing install and detected a change (possibly because you physically removed the HD).

Is this the same CD you used in your first install? if so, it is very possible that the burnt CD got damaged. 

There is very little info in your post, without any knowledge of your hardware setup and your Linux experience, I cannot go any further...

---

### Post by razorboy5 on 2009-08-05
same a bit more detail may be necessary
 
this is assumption of what ur trying to do 
 
1. install gparted from synaptic
2. boot liveCD
3. Systen -> Admin -> partitions editor
4. delete the windows partition
5. resize the ubuntu partition to fit the whole hard drive
(this is the method i used not sure if it's safe or clean but so far i'm having no problems)
 
or u can just reinstall the ubuntu from the CD then partition it to fit the whole HD

---

### Post by V4NILL4xxTHRILL4 on 2009-08-05
my apologies Tripolitan,

I have a near useless 4gb hard drive (windows xp not fully installed and cant format it), but so far I cant run my computer without it. My second hard drive is 120gb and has the windows xp that I have been using (but of course its not a valid copy). 

When I change anything with the drives (cd, floppy, hard drives), the motherboard detects the changes and tells me to hit F1 to save the new configuration. It is under the list of drives for the new configuration that says to use the F10 setup if I want to use unix.

 The 4gb hard drive is jumped as master / windows not fully installed. When I boot up computer it gives me like 4 seconds to switch to another OS on the list or it will try to finish set up (which cant finish because it doesnt have enough room on hd to do so.). I tried removing the 4gb hd and jump the 120gb as master - this didn't work and I dont know why, couldnt see any bios setting to help me. Had to go back to using the 4gb hd as master.

The 120gb hard drive has windows xp that I has been running my computer, and as of two days ago has ubuntu 9.04 (that is the length of my "linux expertise" as well).

As far as other hardware configuration goes:
graphics ran off Motherboard (windows xp let me use 1024x"whatever", but ubuntu only lets me use 800x600, ???) 
p3 733/133
384 mb
cd writer 
not sure what else you need to know about.

the burned cd I made still works ( I just got done reinstalling ubuntu alongside windows again) I had tried again to boot from cd (bios setting for boot order is : cdrom first, hard drive second, network boot third) but came up with the same thing as last, gives me one line of info and then doesnt do anything. I am pretty sure that if I knew what bios setting to change I could do the install booting from the cd.


_RAZORBOY_

I may try that...

If you dont hear from me, It probably means I killed my computer...

Oh well, no guts, no glory.

---

### Post by razorboy5 on 2009-08-05
that is a very unique situation which i have never heard of lol :S

hope to hear back soon heh;;;

as far as the graphics problem u probably have not installed ur GPU on ubuntu. U can go System -> Admin -> Hardware Drivers and then install hard drive then u can probably set display to equal of windows i believe

maybe u can pug in the bigger hard drive as master then add LiveCD and do a clean install.

and plz dont kill ur comp due to my advice >.< i try to do mostly everything by myself on my laptop however when i'm truly stumped and can't find a solution on the web take it to a local pro,

---

### Post by tripolitan on 2009-08-05
I would try jumpering the 250GB HD to Cable Select, hook it up to the primary IDE channel then hook up the CDROM to the secondary DE channel and discard the 4GB HD.

When you are prompted to enter BIOS setup, do so and make sure the 250 HD and the CRDOM are there and in the right place. Reboot with the Ubuntu CD in the CD drive. If you get the installation dialog, try using the entire HD for Ubuntu.

Hope this helps

---

