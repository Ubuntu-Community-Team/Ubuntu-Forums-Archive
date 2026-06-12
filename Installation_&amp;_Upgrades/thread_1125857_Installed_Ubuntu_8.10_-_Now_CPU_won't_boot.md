---
title: "Installed Ubuntu 8.10 - Now CPU won't boot"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Asreial on 2009-04-14
Hello. 

Two nights ago, I took a copy of Ubuntu 8.10 and tried to install it on a computer that I built. 
I thought the installation took so I turned off my cpu and went to bed. 

Yesterday, I turned on my computer to find that my floppy disk drive doesn't work and my computer won't boot.

I need any and all suggestions that you all might give me. 
(Oh.. this was my first attempt at building a computer and installing an OS.)

Thanks for reading and thanks in advance for your advice.

---

### Post by Trafficflow on 2009-04-14
Need name and model. and any other info might help

---

### Post by Therion on 2009-04-14
What do you mean it won't boot?  Does it POST?  Can you acess the BIOS?  Give us a little something to go on here...

---

### Post by Asreial on 2009-04-14
My (crappy) set up
Main Processor : AMD Athlon 64 X2 Dual Core Processor
Hard disk : WDC 320 SATA
CD disk drive : Old
2 GB of RAM


If you don't mind, could you name exactly what I need to tell you. I am a big noob. :)

---

### Post by Therion on 2009-04-14
> **Asreial said:**
> If you don't mind, could you name exactly what I need to tell you. I am a big noob. :)
Okay... What happens when you hit the power switch to turn on the PC?  

Do the fans spin up?  Do you see hard drive activity, in short does the system POST?

---

### Post by Asreial on 2009-04-14
> **Therion said:**
> What do you mean it won't boot?  Does it POST?  Can you acess the BIOS?  Give us a little something to go on here...
 

My cpu turns on with lights and stuff. 
and the first screen pops up with my processor info.

I know that I can get to the BIOS screen by pressing delete.

---

### Post by Therion on 2009-04-14
> **Asreial said:**
> My cpu turns on with lights and stuff. and the first screen pops up with my processor info.
And then what happens?

---

### Post by Asreial on 2009-04-14
> **Therion said:**
> And then what happens?ss

It will say Floppy disk(s) fail (40)


F8 to enable system configuration
F9 to select Booting after POST
F1 to continue, DEL to enter SETUP


nothing happens if I press F8 or F9.

When I press F1 it goes to a different screen and freezes

---

### Post by abn91c on 2009-04-14
press Del key to go into BIOS, see if there is a setting for "setup defaults", "best performance settings" or something similar. some bios you press f6, f7 for those settings then f10 to save and exit.
Also look for a setting to disable the FDD controller, then save and exit

---

### Post by Asreial on 2009-04-14
> **Asreial said:**
> ss

When I press F1 it goes to a different screen and  freezes
 

I just looked at the F1 screen. 
The top of the screen says : 
Internal LAN MAC address 
Hardware Monitor...

It gives some computer stats, then near the middle of the screen it says this : Verifying DMI Pool Data............

It freezes there.

---

### Post by Asreial on 2009-04-14
> **abn91c said:**
> press Del key to go into BIOS, see if there is a setting for "setup defaults", "best performance settings" or something similar. some bios you press f6, f7 for those settings then f10 to save and exit.
Also look for a setting to disable the FDD controller, then save and exit

I will try this and I will be back in a moment. 
Thank you and everyone for the advice. :)

---

### Post by abn91c on 2009-04-14
something else i remember googling for a similar problem I had was to put a blank floppy disk in the drive during booting

---

### Post by sigurnjak on 2009-04-14
No offense is meant , but do you really need floppy drive ?
I find them more trouble than  they are worth . Also you can look for reset cmos jumper and info in mobo manual on how to reset your bios to factory defaults . 

Also recently i was building pc for as relative  and i have put ram in the wrong channel  and it would not boot .  Try switching ram from one channel to another and see if that  helps . Good luck .

---

### Post by Asreial on 2009-04-14
> **abn91c said:**
> press Del key to go into BIOS, see if there is a setting for "setup defaults", "best performance settings" or something similar. some bios you press f6, f7 for those settings then f10 to save and exit.
Also look for a setting to disable the FDD controller, then save and exit

I followed your directions. 
the floppy disk fail isn't happening.
Now, it's freezing on the screen that says :
Internal LAN MAC address
Hardware Monitor...
some computer stats, then near the middle of the screen it says this : Verifying DMI Pool Data............

> **sigurnjak said:**
> No offense is meant , but do you really need floppy drive ?... Also you can look for reset cmos jumper and info in mobo manual on how to reset your bios to factory defaults . 

I need it(the floppy) sometimes, but not often. I have already reset the CMOS jumper. Also, My mobo didn't come with a manual..., only a pamphlet.

> **sigurnjak said:**
> ...Try switching ram from one channel to another and see if that  helps . Good luck .

I will try this in the morning. Thanks.

---

### Post by sigurnjak on 2009-04-14
Somethimes  when reseting cmos it is good to remove battery for 10-15 min to discharge all current from mobo to ensure it is completely reset . 
Just my 2 cents , now i am broke !:lolflag:


Also could you let us know mobo model , maybe we can hunt down some more info on it ?

---

### Post by Asreial on 2009-04-15
> **sigurnjak said:**
> Somethimes  when reseting cmos it is good to remove battery for 10-15 min to discharge all current from mobo to ensure it is completely reset . 
Just my 2 cents , now i am broke !:lolflag:


Also could you let us know mobo model , maybe we can hunt down some more info on it ?

My mobo : Biostar MCP6P m2+

---

### Post by rcayea on 2009-04-15
Did you have a previous OS installed before you installed Ubuntu?

---

### Post by sigurnjak on 2009-04-15
Good mornin' fell !
Here is a link with your mobo info :
[http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=370](http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=370)

 If you are still experiencing trouble set it to optimized settings  , make sure it is set to boot from cd first then hd , maybe set hd on a separate line  from cd if it is ide drive and make it secondary master . 
Since this is fresh install  and you say you are a noob , like me try hardy instead , it is little more conservative and stable than cutting edge release . 

Got to go to work now . C U LATER !

---

### Post by Ryangarve on 2009-04-15
Can you confirm that the BIOS has been set back to default?  That is going to resolve a majority of issues with this.

Verifying DMI Pool data can also occur because cables are not fully plugged in so double check those.

It also might not be a bad idea to check the integrity of your hard drive.  Not under the BIOS, but under system configuration you should be able to run a HDD scan.

FYI: Your title is mis-worded a little. Your CPU is actually the small chip on the Mobo that does the processing for the computer.  At this point it appears that your OS isn't booting.

---

### Post by Asreial on 2009-04-15
> **rcayea said:**
> Did you have a previous OS installed before you installed Ubuntu?

I did not.

---

### Post by Asreial on 2009-04-15
> **Ryangarve said:**
> Can you confirm that the BIOS has been set back to default?  That is going to resolve a majority of issues with this.

Verifying DMI Pool data can also occur because cables are not fully plugged in so double check those.

It also might not be a bad idea to check the integrity of your hard drive.  Not under the BIOS, but under system configuration you should be able to run a HDD scan.

FYI: **Your title is mis-worded a little. Your CPU is actually the small chip on the Mobo that does the processing for the computer.**  At this point it appears that your OS isn't booting.


I'm a noob. I'm sorry.

I will try to check the connections when I get home later. 

Once again, I thank you all for your advice.

---

### Post by Asreial on 2009-04-15
I'm going to reset the BIOS now.

---

### Post by tom66 on 2009-04-15
Go into your BIOS, and see if you can find "Boot Order", "Device Order" or something like that. Make sure that Hard Disk Drive and CD drive are above Network/LAN controller and everything else. If required, put floppy drive after the HDD and CD drive.

---

### Post by Asreial on 2009-04-15
The Boot order is 
CD Drive
HDD
USB Drive

---

### Post by Asreial on 2009-04-15
> **Asreial said:**
> The Boot order is 
CD Drive
HDD
USB Drive

After resetting the BIOS, I am getting a new message :

My first screens says this:

IDE Channel 0 Master : None
IDE Channel 0 Slave : (my cd drive)

SATA 1 Device : my HDD
SATA 2 Device : None
SATA 3 Device : None
SATA 4 Device : None

Floppy disk(s) fail (40)
CMOS checksum error - Defaults loaded

---

### Post by Asreial on 2009-04-15
i guess no one knows what installing did to my system.

:(

---

### Post by sigurnjak on 2009-04-15
From another forum :
Floppy Disk (s) fail (40) or floppy disk (s) fail (80)
The floppy drive does not match the entry in the CMOS or the floppy drive can not be reset. 

[http://forums.techarena.in/guides-tutorials/1121897.htm](http://forums.techarena.in/guides-tutorials/1121897.htm)

Try booting without floppy .

---

### Post by toystory on 2009-04-16
hi there

I think you have a memory problem or a motherboard problem. Are those under warranty? 
To test the memory you have the ubuntu disk, when it first boots, there's an option to do a memory test. If that comes out clean, then i would suggest two things:

1- the power source of the computer is new? do you happen to know the wattage (300w, 400w, 500w?)
2- take the mainboard back to the shop, and have it exchanged
3- test your hard drive in some other computer to see if it works (preferrably linux so if you have ext3 partitions, it can be read). In windows it will show under Control Panel, Administrative tools, Storage, and probaly as unknown partitions.

Can you try all those things? 

Best regards, and welcome to the ubuntu community

---

### Post by Asreial on 2009-04-16
Success!

I had to reset the BIOS/CMOS and disable everything but the CD 
drive.

Thanks to everyone that gave advice to me.
You are all awesome. 

Now, I need an uncorrupted disk to install!

---

### Post by Frak on 2009-04-26
Let me guess, you got this board with a kit of 2GB of 667 Kingston RAM with a PowerUp! case and a 2.4GHz AMD Processor?

All of the boards that Tigerdirect sold during that sale had defects or possible defects. Of course, assuming you bought it from TG.

---

