---
title: "Hard drive spin up/down"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by saultpastor on 2005-11-29
I have an Acer Travelmate 2310.  Breezy works great and I'm so thankful that Ubuntu rescued me from having to use windows on this laptop.

My issue is that the hard drive spins down and then 5-10 seconds later it spins up again.  (It sounds like it goes to sleep for a few seconds and then runs.)  Whenever it wakes up I get a spike in the processor to 100% for no reason that I can determine.  I have tried:

Turning off acpi (menu.lst acpi=off etc.)
I have tried shutting down services one at a time.
I have stopped laptop-support

I have 692 megs of available ram (64 goes to the sis video)

What do you think?  I have searched, I have found threads that were similar and have tried the suggestions but no luck.

---

### Post by jakev383 on 2005-11-29
[QUOTE=saultpastor]
My issue is that the hard drive spins down and then 5-10 seconds later it spins up again.  (It sounds like it goes to sleep for a few seconds and then runs.)  Whenever it wakes up I get a spike in the processor to 100% for no reason that I can determine.  
[/QUOTE]

I had a similar problem with my Dell 600m laptop. I went into /etc/hdparm.conf and changed the power settings for my drive (option S for spindown if I remember right...). You can also change them with the CLI command hdparm and see what works for you, then go back into hdparm.conf and put the setting that worked for you in there to make it apply at boot time.  
Hope that helps.

---

### Post by qrto on 2005-11-29
What filesystems do you have? Remember that ext3 is synced every 5 seconds by default, use mount with commit= option to change that (man mount for more details). Mind that by incresing that value you're increasing the risk of data loss, though 30 seconds seems to be safe enough :)

---

### Post by chele on 2005-11-29
You are using this as a laptop or as a server? Do you want the harddrive to stay down all the time to maximize  battery life, or do you want it to stay up all the time?

---

### Post by saultpastor on 2005-11-29
Thanks for the responses, great ideas.  I shouldn't wait so long to ask.

> I had a similar problem with my Dell 600m laptop. I went into /etc/hdparm.conf and changed the power settings for my drive (option S for spindown if I remember right...). You can also change them with the CLI command hdparm and see what works for you, then go back into hdparm.conf and put the setting that worked for you in there to make it apply at boot time.

used:
sudo hdparm -S12 /dev/hda (12 represent 5 second per integer for a total of 60 seconds)

Worked but since it was still having to write every few second the drive never stopped.  This would be better than spinning up and down all the time, I think it would be less wear on the drive to spin all the time, but I don't know about heat.

> What filesystems do you have?

ext3 :( 

> Remember that ext3 is synced every 5 seconds by default, use mount with commit= option to change that (man mount for more details).

Used commit=30 in /etc/fstab  works much better as it spins up and down only twice per minute. but I would like to eliminate as much as possible.

>  Mind that by increasing that value you're increasing the risk of data loss, though 30 seconds seems to be safe enough

Why does it need to be synced?  What needs to be synced?  Does ext2 or reiserfs require this?

> You are using this as a laptop or as a server? Do you want the harddrive to stay down all the time to maximize battery life, or do you want it to stay up all the time?

Laptop use, although it isn't extremely important to conserve battery since I rarely use it on battery.

---

### Post by chele on 2005-11-30
> Laptop use, although it isn't extremely important to conserve battery since I rarely use it on battery.To quote from elsewhere:>  Laptop-mode isn't enabled by default in Breezy. Edit /etc/default/acpi-support -- change the last line (ENABLE_LAPTOP_MODE) from "false" to "true" to turn it on.I also edited /etc/laptop-mode/laptop-mode.conf and enabled the laptop-mode always settings.

# Enable laptop mode always, not just when on battery?
 LAPTOP_MODE_ALWAYS_ON=1

# Enable laptop mode when the laptop's lid is closed, even when we're on
# AC power? This only works on ACPI.
LM_WHEN_LID_CLOSED=1

Note that ACPI and laptop-mode can be used on non-laptop PC's as well. All modern desktop/tower PC's use ACPI. Though I doubt the Lid_Closed stuff would be of much use without a laptop lid to close.

---

### Post by chele on 2005-11-30
... or should it be:> sudo apt-get remove laptop-mode; sudo apt-get install laptop-mode-toolsThen edit /etc/laptop-mode/laptop-mode.conf

[http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html]("http://www.xs4all.nl/%7Ebsamwel/laptop_mode/tools/faq.html")

---

### Post by saultpastor on 2005-12-01
Thanks Chele,

I set the standby to 30 second in hdparm and the  sync commit to 10 minutes.  I read a recommendation to set it to 30 minutes without problems, so I thought 10 was conservative enough.  Things are working smoothly and quietly so far.  Thanks for the laptop-mode tips I will try them if this setup has problems.

---

### Post by Gevatter Tod on 2005-12-18
I have the same problem here and tried out anything i could find in this programm. Starting/stopping laptop-mode or laptop_mode from laptop-mode-tools does not work.

Setting hdparm -S250 /dev/hda (4 hours) does not work. 

The trick with ext3fs cannot work for me because I use xfs and I did not find a similar option there to adjust the sync time.

The **cking disk gets up and down every seconds, and makes a noise which makes you wanting to throw the laptop out of the window. Although I think its not healthy for the disc, like you would turn a light-bubble constantly on and off. Especially when surfing with Firefox, it does real spinoff/up orgies...

Are there any more tricks I could try? Is there maybe a way to completly disable hard disk spindown? Under SuSE I never had this problem...

---

### Post by Yv12345vY on 2007-06-07
Great thread.  I hope all this stuff works!

---

### Post by 444 on 2007-06-07
I use laptop-mode with a very short spindown time. If it works properly it stops teeny hd accesses, only doing them every 10min.

Gevatter Tod, remove them both? No need to set it back to a long timeout if you remove whatever's setting the short timeout at startup. Only thing I use laptop-mode for is hard drive management, if you're intent on disabling it then there's no need for it at all.

---

### Post by band-aid on 2007-09-01
I'm glad I stumbled across this thread, my hard drive must be syncing every 5 seconds since my partitions are ext3. What would be a better file system to use and where would I put commit=30 in /etc/fstab?

---

### Post by wieman01 on 2007-09-03
> **band-aid said:**
> I'm glad I stumbled across this thread, my hard drive must be syncing every 5 seconds since my partitions are ext3. What would be a better file system to use and where would I put commit=30 in /etc/fstab?
I posted a simple solution here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

---

