---
title: "No monitor mysteriously ... troubleshooting tips?"
date: 2008-12-27
forum: Hardware
---

### Post by Bucky Ball on 2008-12-27
Hi all. This is not directly Xubuntu related but thought I might throw this up and see if anyone had any ideas before I proceed.

Booted up my desktop and one of the hard drives seems to be playing up. I have XP and Xubuntu on the machine. On the opening screen where the machine checks the drives and hardware, tells me:
> 
Maxtor 80Gb hard drive S.M.A.R.T compatible but disabled.Fair enough. To the grub menu with no problems but then the machine starts freezing and I can hear one of the drives spin down (switch off). This is not good. I have always been suspicious of that maxtor. I had it in an external case for a year and a half and had just recently put it in the desktop box and reformatted as ntfs. Now being used for recording dv from my camera. Luckily there is only one folder on there with a few small files.

Anyhow, here's where things get icky! I decide to unplug the Maxtor to make sure that is the one spinning down. Sounds like nothing else is crashing now, except for the fact that the machine is now not even switching the monitor on. Just green monitor light flashing at me. Plug the Maxtor back in just in case. No different. The monitor is unresponsive. Unplugging the Maxtor made a difference: it made a worse problem.

So, I'm thinking it is the monitor (all connections are fine), or one of the other hard drives. Problem is, can't get to bios to boot from cd to actually get into the machine and change or test anything!

So, next step is to unplug all the drives I guess, except the one with the OSs on, and see what gives. Might not be the Maxtor after all. Failing any faults there, fork out for the low energy screen I've had my eye on for the last week (building a machine for someone else often gives me an appetite for new hardware!). But I will test the old one more thoroughly first, of course ...

Any thoughts ... ?

* Update: Was just thinking, maybe the Maxtor drive problem is coincidental and my vid card just died.

---

### Post by Bucky Ball on 2008-12-29
The story so far. 

Green light on monitor blinking when I switch computer on. Doesn't boot. So ...

I rip the cover off and have a look inside. Check cabling, noodle about. Unplug the drive I have been suspect of and switch on. No different. Light just flashing at me. I plug that drive back in. Nothing different. Still not booting monitor when switch the computer on.

I'd read somewhere to try popping the battery for awhile. A long shot, but I give that a try. As I'm plugging the monitor back in to test things out, I notice the vid card is a little loose. I have checked it is in the socket but the screw on the case which holds it in place is a little loose and it is actually on the slightest angle. That could be enough as once or twice it booted okay and then just froze. I could still move the mouse but nothing reacted. No keyboard. So I stick another screw in there and make the video card solid, boot up and hey presto, it works!

For awhile. Back to square one suddenly. When trying to boot, I notice the clicking noise I have been trying to identify is in fact the DVD/CD combo drive, the light comes on for awhile then off, the hard drive light in tandem with it. So I unplug that. Boots straight away but everything takes forever. I fiddle with the BIOS which has been set back to default after popping the battery, but still takes forever and it is having a problem identifying the drive with the OSs on which is IDE. I have 3 SATA drives in the box, IDE DVD/CD (which I just disconnected from the second connection on the cable, not the end) and the IDE OS drive.

Now, I have had that drive since not sure when. Does this sound like it is dying? I got to Xubuntu splash eventually, but as I say, things are so slow it is not usable. Everything perfectly normal but totally slow motion (I haven't bother waiting to get to a log in screen, let alone the desktop). When in the BIOS, normal, not slow but not running from that drive either. All other drives are identified when I switch on, just a 2 minute wait to get to the IDE. Also, it identifies one of the SATA drives as the primary master and puts the IDE last (not sure if I had tweaked the BIOS to deal with the IDE/SATA mix before all this).

Anyhow, hope that is kinda clear. Any suggestions gratefully accepted at the point. I really need that computer to run ... soon. :) :confused:

---

### Post by Bucky Ball on 2008-12-29
Currently ...

The machine is currently plugged back together exactly how it was and, for the moment, operating normally after I've popped the battery again and poked, prodded and generally inspected the interior of my computer case for an hour or so. One problem; occasionally it just freezes. Things were working normally there for about forty five minutes then suddenly no keyboard or mouse. Only option is to re-start with button. Won't switch off with power button.

So, vid card, combo drive or any number of things. Booting fine but there is obviously something wrong re the random freezing. Curiouser and curiouser ...

This is getting too mysterious. Any ideas welcome.

---

### Post by markbuntu on 2008-12-29
Something is loose or beginning to crap out on you. Replug everything. Take the plugs out and plug them back in, same with any cards, ram, etc, take them out of their sockets and put them back in, just pushing on them will not always fix something that has become misaligned. If the bios is dropping out replace the battery. Run a memory test.

If the problem persists disconnect one thing and reboot. If the problem persists reconnect it. Repeat until system is stable.

good luck

---

### Post by Bucky Ball on 2008-12-30
Thanks for that, markbuntu. Now I have a cpu usage graph running and booted up this morning. All fine for about 10 minutes then freeze. Graph shows nothing untoward, no 100% usage spike, just frozen on cruising.

Reboot, all fine for the last two hours (in fact great). All was fine for about 7 hours last night after an initial freeze.

If this happens again, which it probably will, I will unplug everything and plug it all back in again to see if that makes any difference. If it happens again after that I will go for the device by device approach. Problem is, it might take a day to crap out so pretty hard to identify which bit is dying (if that is the case). Could be battery, has crossed my mind as popping it and putting it back in again seems to do something. That could be incidental. I did think about the fact I was using the rt kernel (xubuntu with ubuntu studio rt kernel and applications, no desktop or art work). But the freeze has happened originally on my XP install. 

Right now, I am going to investigate how to run a disk check on my IDE and SATA drives. Is the a quick and easy way in Ubuntu through the terminal? I'll do a bit of research on that one.

Thanks for chipping in, I often babble on to myself here for a week before eventually fixing my own problem!

:)

---

### Post by Bluebell392 on 2008-12-30
By disk check, do you mean "check all files to see if they are in a good state", or "check the disk's health"?

---

### Post by Bucky Ball on 2008-12-30
Disk health.

---

### Post by Bluebell392 on 2008-12-30
You could try smartctl, in the package smartmontools. Sample of output:```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   109   096   006    Pre-fail  Always       -
       21696654
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -
       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -
       1334
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -
       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -
       35484194
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -
       2095
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -
       592
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -
       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -
       0
190 Temperature_Celsius     0x0022   062   051   045    Old_age   Always       -
       673579046
194 Temperature_Celsius     0x0022   038   049   000    Old_age   Always       -
       38 (Lifetime Min/Max 0/19)
195 Hardware_ECC_Recovered  0x001a   084   072   000    Old_age   Always       -
       129606289
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -
       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -
       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -
       0

```
Basically, when a value hits a threshold, consider replacing it. Of course, this depends if it is a old age value or a pre-fail value.

---

### Post by Bucky Ball on 2008-12-30
Yea, use that on the laptop but this is a recent refurbiishment of the desktop workstation, so will drop it on and give it a whirl. Thinking of something that will check the sectors on the physical drive systematically. chdisk?

Incidentally, very doubtful it would be a corrupt file as this freeze happens in XP as well as Xubuntu. Unless the BIOS has gone awry, also doubtful but possible. Has been operating fine for last few hours after the initial freeze ten minutes in. Restart and fine. Weird.

---

### Post by Bucky Ball on 2008-12-30
And who knows what this is about ... noticed that when I shut down, it takes me to the login screen! Then hit shut down and the machine shuts down. Weird. Must be hardware ... but what?

---

### Post by Bluebell392 on 2008-12-30
Hmm... Have you tried sudo shutdown -h now?

---

### Post by Bucky Ball on 2009-01-05
> **Bluebell392 said:**
> Hmm... Have you tried sudo shutdown -h now?

Bluebell392, yes that did work. Shuts down without going to the login screen then having to shutdown from there. Is there anyway of making it a permanent fix?

---

