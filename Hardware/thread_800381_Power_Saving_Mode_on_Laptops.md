---
title: "Power Saving Mode on Laptops"
date: 2008-05-19
forum: Hardware
---

### Post by CarlosinFL on 2008-05-19
I installed Ubuntu Linux 8.04 on my Dell Latitude laptop. This is my 1st time using Linux on a laptop after years of Debian Linux usage on a desktop PC. My only complaint is that when I shut the lid, the laptop battery is drained / dead in maybe one hour. If I had Windows XP installed, when you shut the lid, the laptop goes in some kind of suspend state where the battery can hold a charge for days and it takes only seconds to bring the machine back to life.

Anyone know if this is possible? These features seem to be basic on all Windows XP / Mac OSX laptops.

Thanks for any info!

---

### Post by sdennie on 2008-05-19
Go to System->Preferences->Power Management.  You can decide what happens when you close the lid on either AC or battery power.

---

### Post by CarlosinFL on 2008-05-19
Whats the difference between suspend and hibernate. What does Windows XP and OSX do nativly when I close the lid? I want something that will preserve battery life when the lid is closed but then when I decide to resume, I don't want it to 30-45 seconds to wake up - in that case I could have simply shut the machine down and booted it back up to begin with...

---

### Post by sdennie on 2008-05-19
I've not used either outside of a VM so I'm not sure what their default behavior is.  It sounds like what you want is suspend though.  That will drain a minimal amount of power while the laptop is closed and the system should come back up in about 5 seconds.  Not all laptops suspend well under linux so, if it doesn't suspend or resume properly, you may have to google for your specific laptop and see if there are any tips on fixing it (of course, it may work just fine without any tweaking).

---

### Post by CarlosinFL on 2008-05-19
I set it to suspend and shut the lid for 15 minutes. Sure enough the laptop power LED would slowly flash to show the the laptop was in suspend mode as it would in Windows XP or OSX. I then opened the lid and the machine was locked so I tried to enter my password and I had zero keyboard and or mouse response from the laptop. I tried everything and waited 5 minutes but when it comes from suspend mode, the laptop has no keyboard or mouse. The touchpad and the mouse eraser thingy on the keyboard both were not responsive so I had to reboot using the power button. Is there a way to resolve this?

Seems like this would be something simple to fix. I just don't know where to start.

I have a Dell Latitude D430 notebook.

---

### Post by sdennie on 2008-05-19
Suspend/Resume problems are very laptop specific but, it's usually quite easy to fix problems on Dells.  I would ask on [The Ubuntu Dell forum]("http://ubuntuforums.org/forumdisplay.php?f=342") and see if anyone else has had your problem.  Although your machine isn't an officially Dell supported linux machine, you could also look at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) and [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04) to see if there is any information there that can help you.

---

