---
title: "Faulty bios or cpu or motherboard?"
date: 2012-01-01
forum: Hardware
---

### Post by jonnyboysmithy on 2012-01-01
I was using my computer under high load It's an old dell d610. so anyway, all of a sudden everything goes really jerky and I couldn't do anything with it. so I hold the power to turn it off and after it wont boot, it tells me its in manufacturing mode level 67. I put a different cpu in it and now it will sometimes boot. often the screen wont come on. just keep trying and eventually it goes.. Any ideas what happened? Its running ok now but I'm not sure if its the cpu or the keep trying bit. by the way I succesfully reflashed the bios as well.

EDIT: by the way I've never had any problems with it before this, it took 81 tries to get it to boot 3 times

---

### Post by MoreOrLess on 2012-01-01
Based on this thread, I suspect a CMOS battery gone bad: [http://www.howtofixcomputers.com/forums/dell/manufacturing-mode-level-67-a-207175-2.html](http://www.howtofixcomputers.com/forums/dell/manufacturing-mode-level-67-a-207175-2.html)

---

### Post by jonnyboysmithy on 2012-01-01
Thanks for the link:)

The system sometimes just freezes and jerk stop and continue going occasionally sometimes it'l stop 
alltogether. It reboots when coming out of suspend which is really weird.
I have changed the cpu, I had another lying around which is working. it doesn't seem to like the one that was in it. I suspect I may have overheated it but I'm not sure.:-k

---

### Post by jonnyboysmithy on 2012-01-02
Yup might be the cmos battery, it reads 2.86v. I'd better try get a new/other one..

---

### Post by Mark Phelps on 2012-01-02
All a dying CMOS batter would do is prevent you from saving BIOS setting changes and other info; it would not affect the real-time functioning of the PC.

The symptoms you mentioned, especially the freezing and overheating are more likely caused by a know Linux kernel bug.

See the info below:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by MoreOrLess on 2012-01-02
Mark: read the link. Dell's have a maintenance mode

---

### Post by spacecheck on 2012-01-02
While under "high load", the system may have had too much to do to satisfy an impatient user, perhaps while also indexing files and other background tasks. There is often a way to properly close frozen apps, without killin the whole machine (think of the probable failed cache write-backs). Ctrl+Alt+F1 would get you into a terminal, where you could run sudo init 6, for example.

 	Aside from that, lookin at board, CPU & bios just  doesn't whip the whole willy, but just rubs the tip (of the iceberg). What about a tired  pld power supply not keeping its voltage & amperage quite up to  snuff? Might there be a lot of devices attached to it, while also having  the CPU max out its power draw could be making it sweat a bit too  much...especially if the graphic card is also  sucking back a lot of  juice for video output.

That mentioned, what about an upset memory module or two? An intermittant error here & there could send the system into a kernal panic as well as anything else mentioned. Might one or more need to be removed & reseated, tested? replaced ?

Of course, the HDDs could be reaching error limits, too, if years of i/o ops have left it begging for retirement and threatening to strike (data backed up?).

If none of the above, perhaps its only 2012, letting you know the end (of your system) is near.

Good luck!

---

### Post by Mark Phelps on 2012-01-02
> **MoreOrLess said:**
> Mark: read the link. Dell's have a maintenance mode

OK, so I read the stuff in the link.  Still don't see how that is all solved by replacing a weak CMOS battery...

---

### Post by lisati on 2012-01-02
** Digression **
> **Mark Phelps said:**
> All a dying CMOS batter would do is prevent you from saving BIOS setting changes and other info; it would not affect the real-time functioning of the PC.

The symptoms you mentioned, especially the freezing and overheating are more likely caused by a know Linux kernel bug.

See the info below:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

I agree, CMOS battery problems usually only mess with the ability to save BIOS settings and other info. Having said that, I recall seeing a reference to checking the CMOS battery when researching a possible PSU fault with a DELL I have that won't power up. (citation needed: different set of symptoms to those described by the OP)
** Digression ends **

---

### Post by jonnyboysmithy on 2012-01-02
No I haven't had issues with the bios retaining its settings, so the cmos battery should be ok.
I keep an eye on the cpu temperature and it ussually sits at 46-54 degrees Celsius  and 64C under heavy minecraft loads (I purposely tested to see how hot it got).
 When its that hot everything still runs fine.
I have all data backed up don't worry.
SMART says my disk is perfectly healthy.

 I suspect a motherboard or PSU fault..

---

### Post by jonnyboysmithy on 2012-01-02
No I haven't had issues with the bios retaining its settings, so the cmos battery should be ok.
I keep an eye on the cpu temperature and it ussually sits at 46-54 degrees Celsius  and 64C under heavy minecraft loads (I purposely tested to see how hot it got).
 When its that hot everything still runs fine.
I have all data backed up don't worry.
SMART says my disk is perfectly healthy.

 I suspect a motherboard or PSU fault..

By the way I applied the workaround you mentioned.
EDIT: When it comes out of suspend it immediately reboots as if it was off and I just pushed the power button, this happens with ubuntu and windows, so definitely a hardware problem.

---

### Post by spacecheck on 2012-01-02
If it goes into suspend, there must not be much/any activity going on. There also has to be enough RAM (and swap space) available for the snapshot AND there will usually be a lot of disk activity (read) required to write the system image to RAM.

IF it is in suspend long enough, it may also be set to move from there into hibernation. In that instance, there would be a lot of write-activity to the disk. After writing the entire operational RAM-content as a system image to the disk (if there was enough RAM and IF there is enough disk and swap space), it would turn off. A restart (power switch) would be required to start, but it wouldn't be a complete reboot, but would run through POST and the boot process to Grub. If you select the same OS,  the hibernation image and session is called up with all apps and related open files in their prior state, instead of a fresh start.

Increased CPU temp can cause an increased case temp, which can cause an increased GPU temp, which can also cause a system shutdown.

Good luck!

---

### Post by jonnyboysmithy on 2012-01-02
Suspend has always worked for me. I have 1gb ram and 2.1gb swap which should be plenty. Its the hardware that is the problem, like I said this also happens on windows when it has always worked before I had issues. (by 'issues' I mean that it takes a few tries to boot and suspend doesn't work and that things stop jerk even when its not to hot..

I'll run a memory test.

---

### Post by spacecheck on 2012-01-02
Did you already remove and reseat the Dimm(s) ? You flashed the BIOS,  did you go back through and reset all the settings afterwards?

The settings can bump to defaults or failsafe defaults, possibly affecting power management options, in addition to CPU & RAM frequency and voltage.

---

### Post by jonnyboysmithy on 2012-01-02
> **spacecheck said:**
> Did you already remove and reseat the Dimm(s) ? You flashed the BIOS,  did you go back through and reset all the settings afterwards?

The settings can bump to defaults or failsafe defaults, possibly affecting power management options, in addition to CPU & RAM frequency and voltage.
The frequency and voltage settings can't be changed so that shouldn't be a problem. No I havent reseated the RAM yet I'll do that now..
EDIT: ram reseated.

---

### Post by jonnyboysmithy on 2012-01-03
I think the jerking may be a ubuntu  problem I was doing some games on windows and a scan and it never jerk or stopped. Can you guys help me diagnose it? Could it be because of the liqourix kernel I installed even though I'm not running off it?
Another thing, when it jerks/stops I can keep typing and it takes about 5 seconds and then everything carries on and the text I typed shows.
EDIT:Strangely the booting problems seem to have disappeared.

---

### Post by DS McGuire on 2012-01-03
Nobody (I think ) has suggested this yet but it could be over heating, you said that it gets jerky and you can't do anything and this could well be the case. Use xsenors from the Software Centre and see how hot the computer is getting, plus you can also monitor voltage in you PC.
 
Good luck.
 
Edit: Can you tell me the spces of your computer?

---

### Post by spacecheck on 2012-01-03
SO there may be one or more background tasks using enough CPU cycles to cause your keyboard entry to have to use the buffer. Why not take a look with task monitor, or system monitor, sorted to CPU load, to see which process(es) (show all processes) is/are taking what percentage(s) of CPU ?

System monitor and sysinfo can also show additional resource use/availability. 

As always, you could also run ps aux in terminal.

AND, if you use a wireless keyboard, then battery strength, distance and obstructive items between transmitter/receiver can also result in choppy entry and stumbling mouse.

Good luck!

---

### Post by jonnyboysmithy on 2012-01-03
pentium m 1.6ghz 2x512mb ram, motherboard is i915gm (I think?) graphics  is ati mobility x300 with 64mb, and only support for temperature  readings in the cpu  (according to sensors-detect) you **cant**  change the cpu voltage in the bios but you can if you do the 'pin mod'  to change the frequency and voltage:  [http://www.notebookreview.com/default.asp?newsID=3226&article=pin+mod](http://www.notebookreview.com/default.asp?newsID=3226&article=pin+mod)  

I **know** the cpu isn't getting to hot I **dont know** about the gpu though. 
I'll keep an eye on the processes when it gets jerky.
EDIT:And believe it or it resumes out of suspend ok now (?????)
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```

---

### Post by spacecheck on 2012-01-03
My goodness! I certainly enjoyed a couple of those definitions... :-)

Glad booting has improved. Perhaps the Dimms now have improved contacts.

Next time you're in the BIOS, check to ensure the correct 64 MB aperture for the x300. Other intricate BIOS settings (PCI bus, wait states, SATA/DMA rates, etc.) may have dropped to less sporty or efficient defaults, so you may want to wade through each tab and section to detect and correct any reduced or inefficient setting. There may be an option to let the OS make decisions about the HW resource assignments, instead of the BIOS, which is a good idea under Linux. You could test both ways & compare.

I would not recommend the "pin mod" overclocking method by any means. Unless you have a supply of spare parts, including CPU, mainboard, RAM, and etc., or are already seeking an excuse to recycle it, say perhaps for its precious metal value.

In an older system, dust may have accumulated in the fan blades, heat sink and air ducts, which might make an overtaxed processor & GPU sweat even more than normal and the fan may be louder/more annoying.

The thermal paste of some older systems can also dry, crumble and become less efficient, but if replacing, the amount shown in the picture is a bit too thick. I've had good results with Arctic 5.

Good luck!

---

### Post by jonnyboysmithy on 2012-01-03
Yea me too!:D:D
mm its just faulty, I think I'll pass it to my younger brother and get something else, because it now struggles to boot again etc etc etc, Quite frankly I think the board is screwed.
Thank you all for helping me on this!  ;)

---

