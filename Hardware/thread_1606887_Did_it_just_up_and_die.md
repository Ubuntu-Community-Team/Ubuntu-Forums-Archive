---
title: "Did it just up and die???"
date: 2010-10-27
forum: Hardware
---

### Post by ghost25 on 2010-10-27
Howdy Ubuntu-ers!

I have a somewhat massive issue that just cropped up tonight. I'm hoping for the best, but at this point expecting the worst, maybe someone can help me out here.

I've got an Acer Aspire 5570z that I got from my girlfriend last year, and have replaced three or four parts on it. 

Right now it's running Ubuntu 10.04 LTS, with the following for hardware:
*2GB DDR RAM
*Seagate 250GB SATA HDD
*Intel CPU (not sure of the exact CPU model)
**not sure what other specs would be needed, ask and I'll find out

I have been using my desktop tonight, which is set up with the same OS, albeit a little slower. My girlfriend IMed me a couple YouTube links, which I wanted to watch on the laptop due to the desktop's sluggish performance when multitasking. I grabbed it and went to take it out of hibernation, however while it was warming up I ended up moving my leg or something and it slid, I barely managed to keep the whole shebang from crashing on the floor. It fell to my left side, but I managed to grab it on the right side of the touchpad, however I think this may have "shocked" part of the system.

I waited to get it connected to my wireless and found, for some odd reason, that the entire networking option had been disabled; certainly wasn't disabled when I'd last used it! Odd, but nothing to worry about, simply re-enabled networking. It connected, but then when I went to hit the Internet shortcut key, it froze completely. Wouldn't react to CTRL-ALT-BACKSPACE, holding power button, anything. I ended up doing a battery pull and restarting it.

I turned it back on and logged in, but moved the cursor and it locked up again.

After progressively worse symptoms including non-responsive keyboard and locking up completely on boot (froze with a blinking cursor) it has now regressed to the point it will not boot even to show the BIOS prompt.

I can now pull the battery and run it solely off AC power, pull AC and run off battery, run off both, and nothing. It will power on, however nothing appears on screen, the processor indicator light flashes once or twice then the whole thing shuts back down but the power indicator stays lit (even the fan shuts off by itself now) and it won't respond at all to pushing the power button, I can only kill it by removing all power sources.

Being that I got this laptop for free, I'm not going to be terribly surprised if being dropped did dislodge something (can't think what would have been dislodged however, I'll get to all that in a minute) but being that I use this laptop for school and I have a class that 90% of my notes are stored on this computer, I kinda need to know now if I have to make an emergency trip to get a new laptop.

Things I've fixed/replaced on the laptop:
*New battery
*New hard drive
*New power cord (old one shorted out)
*New thermal module (this I had to replace due to shot bearings in the CPU fan, it sounded like a chainsaw with a bad chain trying to chew through rubber)

Things I have tried already:
*Checked the HDD seating (screwed in, but stranger things have happened)
*Reseated both RAM sticks (no result)
*Powered laptop on with battery, AC, and both simultaneously (no result)

Any ideas or advice on what I could possibly check? I had to drop 240 bucks on supplies for hunting in two weeks, so I'm really not looking forward to dropping another $400 on a new laptop that I'd have to install Ubuntu on as well.

Thanks in advance for any help; and again, if you have any ideas for what I could try that I missed, I'll gladly try it - if you need more info, please ask. Thanks!

---

### Post by rt! on 2010-10-27
Oops.

I think that the impact (on your leg/side/sofa..) will not have been hard enough to actually damage something inside; I would rather think that the catching was the killer. You wrote that you caught it on the side of the trackpad, that could have squeezed the pad dead. As there's not a lot of room between components in a laptop, you have a good (or rather bad, in this case) chance of simultaniously damaging something underneath.

I would suggest that you remove the harddisk, unplug the trackpad, take out the ram and try to boot again, to see whether any of these stop the machine from booting. Look for damage on the mainboard under the trackpad.

Was the AC plugged in when it fell? Have you cracked the charge socket off the mainboard?

BTW, you wrote about the 'processor indicator light', I take it that you mean the harddisk access led (has a kind of drum symbol next to it).

hth

rt

---

### Post by ghost25 on 2010-10-27
Thanks for the reply rt.

First of all, you basically confirmed my suspicions that I borked something when I caught it.

I have not yet tried removing the HDD, RAM and touchpad to see if those will work; I will have to try that later today.

For the AC, no, I had it running solely on battery power, it was only when I noticed wonky behavior that I tried running it on AC. So, no problems with the AC port being cracked.

As far as the processor indicator light, no, there is a light dedicated, as you said, to the hard drive activity (no action from this indicator). There is also a light that notes caps lock (obviously) but then there is one more light that notes processor activity. Like I said, it's an Acer, so yeah, they have weird things going on.

Thank you for the prompt reply, and I will give those a try when I have gotten some sleep so I don't screw it up more (if that's possible haha!).

---

### Post by msandoy on 2010-10-27
Since you have replaced the cpu fan earlier, I'm guessing you are not afraid of dismantling it. What I would do is to remove as many accessories as possible (screen(use an external one), touchpad, keyboard, cd-rom, floppy(if it has one) and hard drive and try to start and reconnect one by one. If it does not start after removing all of the above, I'm sorry to say, most likely the main board has died.

---

### Post by TBABill on 2010-10-27
That kind of impact from you catching it quickly could also have dislodged the RAM if one of the fragile locks (not sure what they're called) on each end of the RAM got slightly damaged during all the work inside the machine. I did that once and didn't realize I had cracked it. I saw you mentioned checking your RAM already and that's an easy one. I just know my RAM came loose after I broke one end of the clip and worked great after I firmly reseated it...hasn't borked again yet in many months.

---

### Post by ghost25 on 2010-10-28
Well, I finally got it narrowed down (I think anyway... don't really have the energy the last few days to have checked) to the hard drive. I can't say I'm entirely surprised, it's just disappointing.

I figured this one out by making an emergency trip to Walmart the night it happened, and picking up a cheap Compaq; got it home, set up Win7, then immediately swapped hard drives. After 12 hours using it, the new laptop started acting up as well. I re-swapped the drives, putting each drive into its original machine, and the new laptop works just fine. I'm inclined to say it's the hard drive because even though it booted to the login screen just fine, even with the new laptop it would not accept keyboard input from the built-in keyboard.

I'm thinking it's gonna be time to set up a dual-boot system with Ubuntu and Win7, then wait a couple months for my student loan to come in and get an external adapter for a 2.5" drive so I can grab all the data off this one, put it on my NAS drive, and use the failing drive as a paperweight.

Just for arguments' sake, I will continue with the suggestions given here once I have time (aside from being a daddy and being in school) and let you know what's going on. Thanks for the help guys!

---

