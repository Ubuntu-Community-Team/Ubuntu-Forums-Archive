---
title: "How to find out what hardware are causing problems?"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by cdhotfire on 2005-04-09
Anyone know how to find out what hardware is causing problesm in my computer?

For one thing i cant install windows says there are hardware problems (duh)
Also my ubuntu crashes like constantly, is like i cant keep it up for more than 30 minutes:-|

---

### Post by az on 2005-04-09
By what you describe, nine times out of ten, you will find that your cpu fan is busted.

Check the cpu temperature.

Open the box and make sure that it is spinning.  Does it make the same sound as usual?

---

### Post by arDAWG on 2005-04-09
Could also be a memory problem or hdd errors. I recommend to dl a nice linux based collection of apps/ Swiss army knife called the Ultimate Boot CD:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
The UBCD has all the various manufactuers' hdd diagnostics & MemTest86 & so on & so forth. I almost always check the hdd & the memory for errors when I troubleshoot problematic computers clients bring to me...tho 9 times outta 10 it's Spyware / Virus infested Windoze to blame.  :wink: 
BTW, Memtest should complete several times w/ ZERO errors. Also, it would help if you posted your hardware...

---

### Post by cdhotfire on 2005-04-09
Thank you for all the suggestions.  I dont think is the fan, runs as usual.  Also i will have to try that boot disk.


P4VT8 (motherboard) I think its VIA?
Nvidia Geforce MX4400 (dont think is video card problem, i use to have ati and switched)
DVD+RW ADRW-HOOP
CD-RW 48x24
1 gig ram stick

2 hard drives:
Maxtor 2B020H1
HDS722580VLAT20

Edit: I think the 30 minute thing was only when i was using nvidia deb, now it fine.  But, one thing i do notice is that i cannot compile anything ( okay maybe only ico2png which is a 1 line compilation).  When i try to do so it just freezes my comp. :(. Also sometimes screensaver freezes also.  One last thing everytime i install ubuntu, it says some packages didnt install correctly (everytime), no matter what i do it says this.:-s (wow that was alot):sad:

---

### Post by alastair on 2005-04-09
Run a "memtest" - for quite a while (e.g. overnight). I think "memtest" is available to run from the GRUB menu (ESC at boot).

---

### Post by skoal on 2005-04-09
I use 'dmesg' to gather good information about my hardware as it boots up.

Outside of that, for issues you seem to be having, I highly recommend downloading and burning the ISO for '[Ultimate Boot CD](http://www.ultimatebootcd.com/)'.

You don't need anything but your computer and a good CDROM to diagnose just about any hardware on your system.  I used it succesfully to tell me that my Maxtor drive was fried.  I used that information to get an RMA and a replacement drive direct from the manufacturer.  This CD has just about every free IT tool you would ever need.

I use the full version which acts as a live CD with firefox/internet support.

---

### Post by cdhotfire on 2005-04-09
Ill give it a try today. :-P

---

### Post by cdhotfire on 2005-04-09
I tried some windows test, and it couldnt not get past LRAND test, sent out a bunch of errors.  Ill do a memtest tonight.  But thanks for all help, it seems im getting closer to the problem.:-)

---

### Post by arDAWG on 2005-04-09
[QUOTE=cdhotfire]I tried some windows test, and it couldnt not get past LRAND test, sent out a bunch of errors.  Ill do a memtest tonight.  But thanks for all help, it seems im getting closer to the problem.:-)[/QUOTE]

You ran the *Windows Memory Diagnostic*???
If it gave errors then u may have memory issues...which may be able to be resolved by relaxing your timings in the bios (e.g., change from SPD settings or AUTO to Expert & loosen the timings...if they're @ say 11-2-2-2 you could try 11-3-3-2 or 11-3-3-2.5 & so on) & you can always bump the VDIMM a notch up...of course, this presumes that you have these options available in the bios. Anywho, the Windows Mem Diag is more forgiving than Memtest86, in my experience.  :wink:

---

### Post by cdhotfire on 2005-04-09
[QUOTE=arDAWG]You ran the *Windows Memory Diagnostic*???
If it gave errors then u may have memory issues...which may be able to be resolved by relaxing your timings in the bios (e.g., change from SPD settings or AUTO to Expert & loosen the timings...if they're @ say 11-2-2-2 you could try 11-3-3-2 or 11-3-3-2.5 & so on) & you can always bump the VDIMM a notch up...of course, this presumes that you have these options available in the bios. Anywho, the Windows Mem Diag is more forgiving than Memtest86, in my experience. :wink:[/QUOTE]

Hmm, i have never in my life used the bios, can you tell me how to even get to it. :(

---

### Post by cdhotfire on 2005-04-10
I did memtest last night, and it showed 401 errors, in the part that said it was tranfering 32 bit. :-|

---

### Post by user-jon on 2005-04-10
To get into the BIOS/CMOS setup, reboot and watch *all* the messages carefully
(they come and go very quickly) for something like 'Press DEL to enter Setup'.
It's usually one of, Delete, F1, F2, Ctrl-S, F11 or F12.
Press this key repeatedly.. and hopefully you find yourself in the BIOS Setup.
(if not reboot and try again!)

I've have a few older PCs which get memory errors.
Sometimes replacing the memory does fix the problem..
but sometimes the memory errors remain and I the solution
was to *reduce the clock speed of the PC*.
Try this before buying new memory.

On most newer PCs, there are settings for this in the BIOS.
Look for some thing related to CPU Speed, or Frequency, or Multiplier
and reduce things one step at a time.
Older PCs may have jumpers on the motherboard for these settings
(check the motherboard manual... or use your sharp eyes to read
the small print on the motherboard itself)

Good luck!

---

### Post by cdhotfire on 2005-04-10
Seems like im gonna have to buy a new one. :(
its a 1 gig ram. NOOOOOOOOOOOOOOOOOO!!!!!

But thxs for all the help guys.:-)

---

### Post by az on 2005-04-10
There is a badram kernel patch to allow you to use a stick of ram with errors on it....

---

### Post by skoal on 2005-04-10
Or you could try to remove all the sticks of memory except one.  Test that stick, then another, etc. until you find the offending one.  Then, just use what memory you can and add another (or more) to replace the offending one(s).

Some motherboards require you to populate certain memory banks in pairs or in certain order.  Check the manual for your mobo or google for that info.

---

### Post by cdhotfire on 2005-04-10
[QUOTE=skoal]Or you could try to remove all the sticks of memory except one. Test that stick, then another, etc. until you find the offending one. Then, just use what memory you can and add another (or more) to replace the offending one(s).

Some motherboards require you to populate certain memory banks in pairs or in certain order. Check the manual for your mobo or google for that info.[/QUOTE]

I only have one in, its a 1 gig. :\

Edit: ill look for that badram kernel.:-?

---

### Post by arDAWG on 2005-04-10
You may be able to get rid of the errors by relaxing the ddr timings in the system bios. Follow user-jon's abovementioned advice as to how to enter the bios (@ initial boot up). Memory timings can be a very complicated topic & the # of options can vary depending on the manfacturer (i.e., from no options to the almost unending array that DFI A64 boards offer). To keep it simple, look for CAS Latency, T(RCD), T(RP) & T(RAS) and perhaps Command Rate (CPC w/ some NForce boards). When you see a stick of memory for sale & the timings are shown like this:
5-2-2-2-1T, that's T(RAS), T(RCD), T(RP), CAS Latency & Command Rate. Those timings are about as tight as it gets & very few sticks can run @ those settings w/out a voltage boost. Overclockers often pump up to 3.6volts & more into Winbond bh-5 based ddr (from 2,5v stock) to achieve tight(-er) timings @ higher fsb's. Anywho, that aside, you need to try to loosen the timings & try to run MemTest then. For instance, if SPD/ AUTO sets your mem to 6-2-2-2-1T, you can try 11-3-3-2-1T or 11-4-4-2.5-2T or 11-3-3-3-1T, etc, etc. Also, look for VDIMM or VDDR...a small voltage bump can allow tigher timings or SPD/Auto timings w/out errors. I have 3 NForce systems now...1 runs @ 3.10V VDimm, the other @ 2.9V & the other @ 2.7V (b/c the Shuttle AN35n only allows up to 2.7V). I would not recommend over 2.9V for sticks w/out heatspreaders & some type of fan blowing on them, tho. My main system is watercooled & I run an AXP mobile 2400 @ ~2.6ghz (12*220). My ddr is Buffalo pc3200 (2X256mb) w/ Winbond Ch5 chips. They will not run @ T(RCD) = 2, regardless of the VDIMM. MemTest will yield errors right away if I run @ 11-2-2-2 (no Command Rate or CPC setting for my rda+  :wink: ). It'll run all night @ 11-3-2-2, tho. These settings I've suggested are based on the chipset I'm running (NForce2)...if you're running an Intel based setup, they will be different...as tight timings are not as important for p4's. Regardless, if you can get into the bios and post the speed timings, plus a brief description of your hardware, I can offer more specific advice.  :wink:

---

### Post by sreid on 2005-04-10
Keep in mind that memory errors are not always due to bad memory. It could be due to overagressive memory timings (as others have mentioned), or due to bad motherboard or CPU, or maybe even something else. The only way to diagnose it is to find a way to repeat the problem (like running memtest) and then try swapping out parts until the problem goes away. If you take your system to a repair shop that is exactly what they'll do.

---

### Post by cdhotfire on 2005-04-10
[QUOTE=arDAWG]You may be able to get rid of the errors by relaxing the ddr timings in the system bios. Follow user-jon's abovementioned advice as to how to enter the bios (@ initial boot up). Memory timings can be a very complicated topic & the # of options can vary depending on the manfacturer (i.e., from no options to the almost unending array that DFI A64 boards offer). To keep it simple, look for CAS Latency, T(RCD), T(RP) & T(RAS) and perhaps Command Rate (CPC w/ some NForce boards). When you see a stick of memory for sale & the timings are shown like this:
5-2-2-2-1T, that's T(RAS), T(RCD), T(RP), CAS Latency & Command Rate. Those timings are about as tight as it gets & very few sticks can run @ those settings w/out a voltage boost. Overclockers often pump up to 3.6volts & more into Winbond bh-5 based ddr (from 2,5v stock) to achieve tight(-er) timings @ higher fsb's. Anywho, that aside, you need to try to loosen the timings & try to run MemTest then. For instance, if SPD/ AUTO sets your mem to 6-2-2-2-1T, you can try 11-3-3-2-1T or 11-4-4-2.5-2T or 11-3-3-3-1T, etc, etc. Also, look for VDIMM or VDDR...a small voltage bump can allow tigher timings or SPD/Auto timings w/out errors. I have 3 NForce systems now...1 runs @ 3.10V VDimm, the other @ 2.9V & the other @ 2.7V (b/c the Shuttle AN35n only allows up to 2.7V). I would not recommend over 2.9V for sticks w/out heatspreaders & some type of fan blowing on them, tho. My main system is watercooled & I run an AXP mobile 2400 @ ~2.6ghz (12*220). My ddr is Buffalo pc3200 (2X256mb) w/ Winbond Ch5 chips. They will not run @ T(RCD) = 2, regardless of the VDIMM. MemTest will yield errors right away if I run @ 11-2-2-2 (no Command Rate or CPC setting for my rda+ :wink: ). It'll run all night @ 11-3-2-2, tho. These settings I've suggested are based on the chipset I'm running (NForce2)...if you're running an Intel based setup, they will be different...as tight timings are not as important for p4's. Regardless, if you can get into the bios and post the speed timings, plus a brief description of your hardware, I can offer more specific advice. :wink:[/QUOTE]

wow that was alot, i already posted hardware but here it is again:

 P4VT8 (motherboard) I think its VIA?
 Nvidia Geforce MX4400 (dont think is video card problem, i use to have ati and switched)
 DVD+RW ADRW-HOOP
 CD-RW 48x24
 1 gig ram stick
 
 2 hard drives:
 Maxtor 2B020H1
 HDS722580VLAT20

I went to bios but there was nothing about times, the only thing i saw that was mentioned was its frequency wish was at 133 Mhz.  I dont know if its a bad memory im thinking its not, because its pretty much brand new.:-?

---

### Post by skoal on 2005-04-10
Do you have "RenderAccel" set to true in your X config?  If so, set it to "false".  Some people with older MX cards had issues with it.

---

### Post by arDAWG on 2005-04-11
Sorry, I must've overlooked your post w/ specs. 
That's an AsRock board correct? 
If so, according to the manual, you can set CAS latency (2, 2.5, 3):
[http://www.asrock.com/Drivers/Manual/P4VT8_UM.pdf](http://www.asrock.com/Drivers/Manual/P4VT8_UM.pdf)
It's under Advanced Chipset Configuration in the bios. You could try 2.5 or 3, the only negative I can see to trying is that you could get a non-post situation, which requires a reset of the CMOS (the jumper @ about 7 o'clock beneath the CMOS battery or item 14 here:)
[http://www.asrock.com/Drivers/Manual/P4VT8_UM.pdf](http://www.asrock.com/Drivers/Manual/P4VT8_UM.pdf)
As a long shot you could try a different DIMM slot. Otherwise, I wouldn't know what else to recommend, w/out the settings for ram timings in the bios. You could try the kernel above or try some different ram. DDR is dirt cheap now, Newegg has the Corsair Value Ram dual channel kit (2 X 512) for ~$90 right now. I know you don't need dual ch. w/ that mobo, but it still gives you a gig & they are tested to play nice together. Plus, you might have more luck w/ 2 X 512 vs. 1 X 1gig. I'll be willing to bet w/ errors in MemTest, tho, u'll never get Winders to install.  :wink:

---

### Post by cdhotfire on 2005-04-11
i will try this. :)

---

### Post by cdhotfire on 2005-04-11
Looks like im gonna have to spend the bucks. But hey thanks for all the help, i have learned alot. Special thanks to tha man arDAWG.=D>

Edit: But hey, $87.00, for a pair of 512 isnt bad.:razz:

---

### Post by az on 2005-04-11
Does memtest 86 give you consistent readings?  Are the errors in the same place?  If that is so, the badram patch should work.  If you want, I could give it a go at builing a linux-image of the stock Hoary kernel with the badram patch.  You would just have to boot with an added bootprompt for the badram blocks to avoid.

If not, Instead of throwing out your stick, send it to me and I'll put it to good use!

I was going to suggest the badram patch to the people who want to build a custom icewm ubuntu for low-end computers.  Faulty ram is common in ancient computers.

---

### Post by cdhotfire on 2005-04-11
Im a die hard gamer, and i need my games :\. So badram is no use to me, ill see what i can do about sending it to you.;-)

---

### Post by az on 2005-04-11
It did not occur to me that you would want to run windows on the machine...

If you have not already replaced the ram, would you test the badram enabled kernel I am compiling first?  You would need to boot into memtest and find what parameters to pass to the kernel.  Then install the kernel that I will upload tomorrow morning (when it finishes compiling) and boot into it with those parameters.

I just would like to know if this works on a Hoary kernel before I make it available to others.  I don't have any bad ram of my own lying around...

---

### Post by cdhotfire on 2005-04-11
sure, but how do i log the memtest?, when i do it after its done it just dies and turns my screen black.  I just saw it had 401 errors, and on the Windows Diagnotic it just would stop counting the errors.  It went up to 10,000 till i got bored and restarted my comp.

---

### Post by az on 2005-04-12
apqi.com/ubuntu/kernel-image-2.6.10-386-badram_1_i386.deb
apqi.com/ubuntu/kernel-headers-2.6.10-386-badram_1_i386.deb

"sure, but how do i log the memtest"
Running memtest, you can have it show you the errors in two ways, the second way is in the format you need to use to pass to the kernel.
It is in the menu.

You will need to write it down.  It should not be that long a thing, basically the start of the block to avoid and then end.


"when i do it after its done it just dies and turns my screen black"

It should take hours for it to be "done", but if the error messages do not change, you should be good to go after a few minutes.

---

### Post by az on 2005-04-12
add something like 

badram=0x10e9c508,0xfffffffc

to your grub kernel line.

---

### Post by arDAWG on 2005-04-12
Another thing I might add is that your 1 gig stick may not be bad...just not compatible w/ your mobo /chipset (Via pt800, if memory serves). I tried to find a memory compatibility list for your mobo on the Asrock site, but to no avail---there were just a handful of current boards listed. So, I would recommend you go w/ a more well known manufacturer for ddr (e.g., Corsair, Crucial) b/c they're modules are usually tested for compatibility. Tho, there are no hard fast rules which apply to what they test, I'd still go w/ one of the big names.   ;-) 
Another possibility would be to head over to the Crucial store:
[http://www.crucial.com/store/listparts.asp?Mfr%2BProductline=ASRock%2B&mfr=ASRock&cat=RAM&model=P4VT8&submit=Go](http://www.crucial.com/store/listparts.asp?Mfr%2BProductline=ASRock%2B&mfr=ASRock&cat=RAM&model=P4VT8&submit=Go)
The sticks they list are guaranteed to be compat. w/ your mobo, tho you'll pay a bit more. Corsair lists these sticks as being compatibile, as well:
[http://compatible.corsairmemory.com/memorysearch.aspx?modelid=1063](http://compatible.corsairmemory.com/memorysearch.aspx?modelid=1063)
Hope that helps...  ;-) 
Also, once you get it lined out, I would recommend setting up your system as dual boot w/ Ubuntu/ Kubuntu and Windows. I am really impressed w/ this distrib (Ubuntu, tho I've tried both--I prefer Gnome over KDE). I keep XP for gaming & such, but log onto Ubuntu for web surfing, word processing & almost every other task. It's nice not to have to worry about viruses & spyware and my daughter is all about Tuxracer as well. I went thru a courtship w/ Linux for about 2 mos. last fall, from Fedora Core 2 to Yoper to Gentoo to Arch 6 & I eventually removed all from my computers, b/c I found none that worked for everything I wanted to do. So far Ubuntu has done all that I've asked & has been quite easy to set up as well. Plus everything just works, which is nice & I didn't have to jump thru nine thousand hoops to get it that way.  :grin:

---

### Post by cdhotfire on 2005-04-12
hehe, this was what i was planing to do, games on xp and other stuff on ubuntu, i hate those dam antivirus programs.:???:

---

### Post by cdhotfire on 2005-04-13
[QUOTE=azz]apqi.com/ubuntu/kernel-image-2.6.10-386-badram_1_i386.deb
apqi.com/ubuntu/kernel-headers-2.6.10-386-badram_1_i386.deb

"sure, but how do i log the memtest"
Running memtest, you can have it show you the errors in two ways, the second way is in the format you need to use to pass to the kernel.
It is in the menu.

You will need to write it down.  It should not be that long a thing, basically the start of the block to avoid and then end.


"when i do it after its done it just dies and turns my screen black"

It should take hours for it to be "done", but if the error messages do not change, you should be good to go after a few minutes.[/QUOTE]

i did the memtest, and it said 83 errors, but there were only 40 on the screen so i press the down arrow, and to my surprise it restarts my computer.

---

### Post by arDAWG on 2005-04-14
Have you tried to lower the DRAM Frequency under the Advanced Bios Setup Menu??? It defaults to AUTO, but you could try manually setting it to 166(333) or 133(266) based on the spec of your 1 gig stick, i.e., is it pc2100, pc 2700, pc3200? I would try that & then run MemTest...you may take a hit on bandwidth, but it's not as important w/ a P4 system to run the memory 1:1 as w/ an AMD based system. What may be happening is that if your ddr is pc3200, it may be defaulting to 200mhz(400 ddr) w/ the AUTO setting. W/ some mobos you have to bump the voltage a bit or relax your timings to run @ 200. Also, the one timing setting you have may be misreading as not all sticks have reliable SPD info. Since you have no option to up the VDIMM / VDDR nor change any of the timings besides Cas Latency, reducing the Mem Freq. may be a viable option.  ;-)
Sorry I didn't think of this before, being and AMD AXP user I never consider running the mem / cpu outta sync.

---

### Post by cdhotfire on 2005-04-14
[QUOTE=arDAWG]Have you tried to lower the DRAM Frequency under the Advanced Bios Setup Menu??? It defaults to AUTO, but you could try manually setting it to 166(333) or 133(266) based on the spec of your 1 gig stick, i.e., is it pc2100, pc 2700, pc3200? I would try that & then run MemTest...you may take a hit on bandwidth, but it's not as important w/ a P4 system to run the memory 1:1 as w/ an AMD based system. What may be happening is that if your ddr is pc3200, it may be defaulting to 200mhz(400 ddr) w/ the AUTO setting. W/ some mobos you have to bump the voltage a bit or relax your timings to run @ 200. Also, the one timing setting you have may be misreading as not all sticks have reliable SPD info. Since you have no option to up the VDIMM / VDDR nor change any of the timings besides Cas Latency, reducing the Mem Freq. may be a viable option. ;-)
Sorry I didn't think of this before, being and AMD AXP user I never consider running the mem / cpu outta sync.[/QUOTE]

thxs for the suggestion, but ive tried this also.  The 1 gig is 133 Mhz, in the bios was set to auto, i changed it to manual and then 133, same errors.  Seems like it got damaged or something.  But today im gonna try to put it on another comp. to see it the same results occur, if not then it must be that it is not compatible with my mobo, as u stated earlier.:-)

---

### Post by az on 2005-04-14
[QUOTE=cdhotfire]i did the memtest, and it said 83 errors, but there were only 40 on the screen so i press the down arrow, and to my surprise it restarts my computer.[/QUOTE]

Take note of the first five or so and then reboot.  If they are not the same, then you have a mobo problem since the bad ram bits should not move around.  If they are the same, try again, but It doesn't look good in that memtest should not crash.  It only takes up the first few hunded bytes of your memory....

You should be able to get it to tell you the bad memory range instead of each bad bit...

---

### Post by cdhotfire on 2005-04-14
[QUOTE=azz]Take note of the first five or so and then reboot. If they are not the same, then you have a mobo problem since the bad ram bits should not move around. If they are the same, try again, but It doesn't look good in that memtest should not crash. It only takes up the first few hunded bytes of your memory....

You should be able to get it to tell you the bad memory range instead of each bad bit...[/QUOTE]

as u said in an earlier post, i changed the mode to put ranges, but thats what came out, like this:
badram=0x00041400,......

badram=0x00041400,.......,......

badram=0x00041400,.......,......,.....

they repeated each time, except that it added a new one each time.  There were only 40 visible, so i couldnt see the other 43.

---

### Post by az on 2005-04-14
Hmmm.

I really do not know.  What happens if you let it go on and on...





Please note to anyone trying to install this kernel, It will not install an initrd (since it is revision=1)
sudo mkinitrd -o /boot/initrd-badram
and add initrd /boot/initrd-badram 
to your grub stanza

---

