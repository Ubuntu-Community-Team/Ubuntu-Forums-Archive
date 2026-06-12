---
title: "Plz help! laptop crashed, wont boot up!!!"
date: 2010-08-02
forum: Hardware
---

### Post by bmfc187 on 2010-08-02
Someone plz help me, my laptop has been acting funny for days, it always seems like its running fine, then i leave the room for a second and when i come back its all froze up, has colored lines on the screen and wont do anything but power down.  then if i turn it off and try to power back on, sometimes itll come on for a sec and then go right back off, then it retries all on its own, craps out again, retries...so ive been pulling the battery and walking away for a bit, then when i come back usually it fires right up.  well this time it didnt.  

i was getting sick of it, and i was actually getting ready to backup all my important stuffs so i could format my HDD and start from a clean install to see if that would help...never got that far.  it did it to me again, but this time it isnt wanting to boot at all.  ive been trying for the better part of two hours and nothing happens except it turns on for one second and then crashes. 

i dont know what to do, i kinda wanna start from scratch and see if that fixes it, but i kinda wanna backup some stuff first so i dont lose it...but right now it doesnt seem like EITHER is gonna be possible anytime soon, unless i go buy a new laptop and start over. im still hoping itll power up again if i just give it a break, but im starting to worry it may not recover this time.  anyone have any idea how to fix this, or what might have caused it?  

Im using a Compaq Presario f700 running ubuntu 9.10 Karmic, and its only been happening for about a month, not everyday but kinda often and increasingly often as time goes by it seems, i dont have any clue what couldve caused it to start doing this, i didnt make any significant changes to my system lately or anything...i dunno what else couldve caused this...

Someone plz help!!

-BMFC

---

### Post by cob on 2010-08-02
How far into the boot process is it getting?  To the BIOS?  Beyond BIOS?  To the bootloader?  Into Ubuntu?

---

### Post by Gaygerbil on 2010-08-02
Yeah you need to give a more detailed description of your problem..:\

But if you can boot in safe mode you can try repairing graphical issues or doing an fsck on your HD and see if that helps. Not sure what your problem is yet.

---

### Post by maverick340 on 2010-08-02
I have a Compaq F700AU. Its a crappy laptop with poor build quality. Couple of things, 
1. Try removing the battery and running it only on AC Power
2. Try using a cooling pad, seems like your laptop is burning up (wont blame you the vents of the F700 are pathetic)
3. This is lame but it worked for me, i opened up the back , removed the hard drive and sort of cleaned the connectors and put it back in, it behaved better.

 My problem was (is) that it hangs a lot, no hibernate or sleep and burns up fast. Dual boot of Win7/Ubuntu (primary is Ubuntu). Probably will dump the laptop or buy a new hard drive. I replace my batter and started using a Cooling pad, that helped to a good extent

---

### Post by bmfc187 on 2010-08-02
> **cob said:**
> How far into the boot process is it getting?  To the BIOS?  Beyond BIOS?  To the bootloader?  Into Ubuntu?

no it wont boot into the BIOS even...i was hoping i could get it to boot that far so i could boot my ubuntu flashdrive and backup some files but i cant even get that far, the screen never shows anything at all, it powers on for like one second or less, then just dies.  then in about another second or two it will retry to power up, without me pushing any buttons at all, and goes into this infinite boot loop where it just keeps on trying and dying and trying again.  my laptop is bricked.  

for a while i had been shutting it down after it froze, then trying to boot up and sometimes itd boot and sometimes id get a boot loop in which case id pull the battery and power adapter, and then plug back the adapter and try to power on again.  then if it boot looped i could just pull the chord, but if it booted i could just put the battery back.  

now it doesnt seem to matter what i do.  i took out the battery and have left it sit out all night and i get the same thing, wont even boot the BIOS...it doesnt seem like theres much chance of recovering it at this point.  

if you guys need any more info i dunno what else to include...ive had the machine for about 2 1/2 years, it had a previous owner, it has been dropped one time from about 4 feet high, and im dual-booting Karmic/Vista.  i hardly ever boot into windows anymore, i only use it for a couple games that wont work in wine.  

so i guess my question is, is there a way i can hook my laptop or just the HDD up to my desktop pc  and try to rescue some files off of it before i junk it?  

-BMFC

---

### Post by bmfc187 on 2010-08-02
ok well i was able to take out my HDD and hook it up to my windows desktop, then booted up into my ubuntu flashdrive and managed to backup all my important files...that was all i did there, but i have been trying all day to get my laptop to boot, to no avail.  its stuck in that bootloop pretty well, i cant seem to get it to recover.  but at least i didnt lose any important files.  

i was wondering now if anyone thinks formatting the HDD might help it recover?  
i tried booting the laptop from the flashdrive without the HDD inserted, trying to force it to boot from the flashdrive...again to no avail.  

but when i had it hooked up to my windows box and booted into the flashdrive, it gave me a long list of sector failures on shutdown?  they were all labeled dev/sdc
 (EDIT:  i checked disk utility on my desktop booted into my ubuntu flashdrive and it lists my laptop HDD as dev/sdb, and dev-sdc is my flashdrive, so now i really dont understand those errors, but since they dont really concern my HDD i dont really care at this point...ill worry about that later...)

so NOW my question is, does anyone think formatting the HDD might help, even knowing that the laptop wont boot with OR without the HDD inserted?  

im gonna try it...

-BMFC

---

### Post by bmillham on 2010-08-02
If you can't get into the BIOS, then your motherboard is most likely dead.

---

### Post by bmfc187 on 2010-08-02
> **bmillham said:**
> If you can't get into the BIOS, then your motherboard is most likely dead.

that really sucks. 

 um...im looking at the disk utility in ubuntu and its telling me that my HDD health is good, but the Airflow Temperature has failed in the past.  so i guess i burnt up my laptop, thats all i can assume.  i mean assuming that i burnt up my HDD i could very well have burnt up my MOBO, too, right?  i mean i dont want that to be right but if it is then it is...

so thats what you think...how much will a MOBO set me back?  or can i even get a MOBO for a laptop?  i dont know really cus ive never had to deal with it...

Can anyone help me out with finding a good laptop thats cheap, but has good specs and APPARENTLY I WANT SOMETHING THAT HAS GOOD AIRFLOW DESIGN...?
maybe something with at least 2GB RAM and a decent HDD, lets say in the area of 260-500GB, and a decent processor (my laptop has an AMD Turion 64 x2, it works just fine for what i use it for) i dont do PC games so i dont need anything really intensive as far as mem or graphics. 

 Then again i am into Android, and i had been tinkering with building my own Android OS, (android is the reason i came to ubuntu in the first place) and the build system does seem to put alot of stress on my cpu, maybe that could be one reason why im having this problem?  what would someone suggest that might be well suited for this but not too overly expensive?  i still dont really care about graphics as long as itll run compiz fusion without any lag or glitchiness...

someone please help me out buying a new laptop, my compaq is my first laptop, and it was bought from a friend so its not like i got to pick it out to suit my needs, i dont really know alot about hardware and whats good/whats not, so i kinda need some help getting a good quality machine without getting "F'ed in the A" pricewise.  any suggestions would be appreciated...are there any companies/websites that let you build your own laptop?  

-BMFC

---

### Post by bmillham on 2010-08-02
Some Compaq laptops had known problems like you are describing. Another symptom to the problem was the wireless would stop working.

I don't know if they still offer it, but Compaq had a special extended warranty to cover this. They fix it for free. It couldn't hurt to contact Compaq and describe the problem. If they are still offering the extended warranty you may get it fixed for free!

---

### Post by bmfc187 on 2010-08-02
> **bmillham said:**
> Some Compaq laptops had known problems like you are describing. Another symptom to the problem was the wireless would stop working.

I don't know if they still offer it, but Compaq had a special extended warranty to cover this. They fix it for free. It couldn't hurt to contact Compaq and describe the problem. If they are still offering the extended warranty you may get it fixed for free!

wow thatd be pretty sweet, im not gonna get my hopes up, but ill definitely call and see...thanks!

-BMFC

---

