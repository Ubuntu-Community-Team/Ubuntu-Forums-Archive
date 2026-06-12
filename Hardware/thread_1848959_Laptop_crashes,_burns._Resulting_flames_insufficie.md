---
title: "Laptop crashes, burns. Resulting flames insufficient for marshmallows, dissapoints."
date: 2011-09-23
forum: Hardware
---

### Post by tylersontag on 2011-09-23
Hey all, got a hardware crash here that just for fun i was wondering if anyone could venture a guess as to the cause. [Skip to the last paragraph if you don't want the nitty gritty]

Woke up yesterday morning, went upstairs to my laptop (Dell Inspirion 1525N) sitting on the coffee table as usual and open it up, and noticed something unusual.  It was on, but there was no screen display... i could see my bluetooth dongle lit up and the quick keys (volume, etc) were responsive.  Its hard to tell when its running since i got a new SSD ~3 months ago or so but i could tell it was.  Switching to ctrl-alt-f1 to do some terminal diagnosis was futile so i resorted to the old cold boot.

On boot, the BIOS screen flashed for only a moment in this dark reddish color and then was gone.  The computer returned to a state of being on with no screen as before.  I pulled the battery and turned it off, hoping some time off might fix what appeared to be a very serious crashing problem (grasping for straws)

I got back from work and took it down to my desktop and plugged in my LCD monitor to the external monitor port on the laptop, hoping i was dealing with a dead backlight.  No luck, no signal comming out.  I thought maybe it was getting stuck on some "Don't cold boot me, jerk" screen and not booting so i tried waiting a while and hitting enter... hoping that was the magic command.  It did have an effect, the laptop would reboot shortly thereafter.  Frustrated i took it upstairs and prepared for HD extraction.   

In the jostling of taking it upstairs, something must have happened that cause the screen to work.  I tried one last boot and this time the blood red screen persisted and i was able to see everything that was going on... hitting enter caused it to boot the linux partition, upon doing so the HD would fail to drive and when trying to bring up the shell a seg fault occured that cause the computer to bounce.

I attempted to change the screen brightness, now thinking i had a bad HD and to my supprise it began looking more like normal, but as i prompted for a brighter and brighter screen i flew too close to the sun.  The screen went black and it reverted to the aforementioned behavior.

I popped the HD out and swapped back in my old HDD to see if it had any affect, but the screen was still black.  I popped my SSD into a Sata to USB dock and plugged it into my other computer and it failed to boot or even be recognized.

So, it appears some hardware failure fried both my display and harddrive all at once.  Motherboard short just fried everything on it?  Who knows.  Does anyone think either the SSD (which was like new) or the laptop are salvagable?   I'd also like to entertain any theories on what failed to cause these results, if anyone cares to venture.  Mostly, this was just a funny story and an FML moment i wanted to share with everyone :-)

---

