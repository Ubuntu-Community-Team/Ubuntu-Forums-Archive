---
title: "HP Pavilion dv4170us LCD goes blank during live CD boot"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by jonmca on 2005-07-22
I’m a Linux newbie, so please bear with me, and thanks for any help! Booting Ubuntu 5.0.4 live CD on an HP Pavilion dv4170us, (Video card: Mobile Intel 915GM/GMS, 910 GML Express chipset family). The LCD has a clear display until the boot sequence reaches the line “* Started Common Unix printing system cuspd  OK”. Then the LCD screen goes blank, flashes briefly, and remains blank but still back-lit (grey screen glows in a dark room, but no video). I can hear the musical audio of the desktop start-up sequence and can then use the touchpad to click invisible taskbar icons although the LCD screen remains blank. Any suggestions on a command line to use during live CD boot to enable a usable display?

Background:
 
Tried individually selecting each of the default screen resolutions during the live boot with no success. Tried selecting other screen resolutions closest to the dv4170us normal resolution of 1280 x 800. With all available screen resolutions de-selected, the boot sequence completes and shows only a small unchanging patch of blue color about 4” high x 2” wide on the left of the LCD screen.

At different times I tried all the following commands during live boot with no success: acpi=off, pci noapci, vga=771, vga=771 noapic nolapic, noapic nolapic.

If I boot the live CD in expert mode and select vga as the video option, I get an LCD display that is very grainy with extremely large icons. I suspect the graphics media accelerator function of the chipset is causing the problem but I’ve successfully booted Knoppix 3.9 and Simply Mepis 3.3.1 live CDs with no problem.

---

### Post by jonmca on 2005-07-24
Here's a workaround to boot the live CD on an HP Pavillion dv4170us laptop. This should also work for all HP pavillion dv4000 laptops with the mobile 915 video chipset.

1. Boot the live CD in expert mode by typing *live-expert* at the live CD boot prompt.
2. Accept all defaults, just keep clicking the "enter" key until
3. You're prompted to enter and then confirm a root password.
4. Continue to click "enter" to accept all the defaults until the screen "Configure X-server.org" appears, then scroll down and select the "vesa" option for video.
5. For all remaining screens/prompts continue to accept all defaults by clicking "enter".
6. After the actual boot sequence and text runs, you may first see only a partial screen for a few seconds, but the fullly functional Ubuntu desktop soon appears.

If you feel this is posted in the wrong forum, let me know and I'll repost it in the "Live CD" forum.

---

### Post by occy on 2005-07-29
When I installed, I had these same symptoms as are mentioned above.  I had a big giant white screen when X started.  I followed the below steps, since I wasn't using the LIVE cd,and things just worked peachy from there.

```

(From the big white screen)

1. ctrl+alt+F1 [Gets you to console]

2. Log in as your user

3. sudo dpkg-reconfigure xserver-xorg

4. Continue to click "enter" to accept all the defaults until the screen 
"Configure X-server.org" appears, then scroll down and [B]select the 
"vesa" option[/B] for video.

5. For all remaining screens/prompts continue to accept all defaults 
by clicking "enter". [B]Note: You may want to select 1280x800 as your 
resolution when prompted to do so.[/B]

6. Once you've exited the program, you'll need to do: ctrl+alt+F7 

7. Then, you'll need to do: ctrl+alt+backspace

8. After a few seconds, you may first see only a partial screen, but 
the fullly functional Ubuntu desktop soon appears.


```

The above was done from memory, I apologize if I've left any steps out.

Have fun!
Trae

---

### Post by occy on 2005-07-30
I hope you guys don't mind, but I figured I'd simply put this post here to keep all of the dv4000 posts together in this one thread.

Is anyone else experiencing funkiness with the touchpad?  It seems to work great as long as you do the proper form of typing which is, "Wrists up" typing.  I typically am quite bad about laying my wrists down on the rest pad, and the problem with the dv4000 is that your right palm(near the thumb) catches the pad all the time.  They didn't think things through when they built it and off-set the touchpad about 1/2 Inch too far to the right.

Can you have the touchpad turn off when you have a USB mouse plugged in?  That could help some of the problems, some of the time.

Thanks,
Trae

---

### Post by greyspace on 2005-08-07
I have a question for others who have the HP Pavillion DV4000 series. I recently bought this notebook and noticed an issue and was wondering if anyone else with the same model had the same problem. When typing, especially in MS Word, Email programs, or in text boxes like this, I've found that the screen will start scrolling up and down randomly, (almost as if it's trying to adjust). It's extremely annoying and I was wondering first, if anyone else experienced this, and whether or not there was a way to make it stop, or if I should just return the notebook. Any feedback would be great. 

Also, I noticed a question about the touchpad. If you go into Control Panel, and then click on Mouse, you can turn it off if you're using a USB mouse.

---

### Post by cvasquez on 2005-10-01
Download Driver, but not live CD
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1862&DwnldID=8203&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1862&DwnldID=8203&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

---

