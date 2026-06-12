---
title: "fan will not stop running after opening up computer"
date: 2014-08-30
forum: Hardware
---

### Post by Ben_Cook on 2014-08-30
So I've just installed Xubuntu on an older desktop.  It was running XP, so I had to change the boot order in the BIOS to install it.  In order to make changes in the BIOS I had to remove the battery to get rid of the password protection. (someone gave it to me because they had got it from someone else, so retrieving the password was not an option).  Anyway, it was the first time I've actually opened up a computer and dug around.  I had to unplug a bunch of things to get at the battery, but eventually I did and plugged everything back in.  The fan would not stop running after that.  I shut it down, opened it up again and made sure everything was as it should be.  I have no idea why it is running constantly, it is very frustrating.  Any help is appreciated!

---

### Post by ThatBum on 2014-08-31
Removing the CMOS battery reset all the BIOS settings in addition to the password, perhaps something governing the fan speeds has been reset. Poke around and see what you can find. Look for ACPI, SmartFan, PC Health settings, stuff like that. Just don't change anything that you're not sure what it does.

---

### Post by Ben_Cook on 2014-08-31
So after much searching there is no fan settings in the BIOS.  The only thing I can find is under system summary and it just says the fans are working.  I downloaded GKRellm, but I really have no idea what I'm doing.  I saw where it said fan in the configuration menu, but there were no options for it.Anyone have any ideas how I can calm my crazy fan down?

---

### Post by Ben_Cook on 2014-09-01
Any suggestions anybody?

---

### Post by Mark Phelps on 2014-09-01
It's most likely running constantly because your processor is running hotter under Linux than under XP -- a common problem with recent Linux kernels.  If you find a way to FORCE the fan to run slower, without slowing down the processor, you're either going to burn out the processor or crash the PC.  You might look into using "tlp" -- but I wouldn't be too hopeful.

---

### Post by Ben_Cook on 2014-09-01
Well, that might be the case, but I don't think so.  As SOON AS I turn the power on, the fan is going.  It was a cold night and it was on the floor below a window, it was a cold night - I think the temperature outside was 10-14 celsius (about 50 farenheit).  Even with nothing running, it is running.  It doesn't stop - ever.  It never turned on when running XP and I know this because it is extremely loud.

---

### Post by Ed_Hoy on 2014-09-01
I would recommend installing an earlier version of Lubuntu or Peppermint.  I had amazing results with Peppermint 4 on my old XP machine.  The fan ***barely ever*** ran.  Now that I have updated to Lubuntu 14.04, my fan runs much more often (though not constantly thank goodness).

Additionally, I would mention that before installing Lubuntu 14.04, I tried Xubuntu 14.04, and it was nowhere near as smooth ( on this old machine) as Lubuntu is.  I am kind of wishing that I had stuck with my Peppermint 4 however.  I might still revert, although Lubuntu has a very nice, easily navigatable , and logical user interface.

---

### Post by Ben_Cook on 2014-09-01
The thing is, Xubuntu is running very smooth.  I have 4 internet tabs going right now and a program running in the background with not even a hint of slowdown.  So, I really don't think the problem is with workload.  I would expect AT SOME POINT the fan would shut off.  I have an intel core 2 duo processor (2.33Ghz), so I don't know what is ideal to run Xubuntu, but as I said, it is running very well

---

### Post by ibjsb4 on 2014-09-01
You could install gnome-system-monitor.  This will allow you to monitor cpu usage.

What is the make/model of your computer?

---

### Post by Ben_Cook on 2014-09-01
Lenovo thinkcenter model #601-A3U, if that helps.  Also,    Intel core 2 Duo, E6550 @ 2.33Ghz, 1.96 GB RAM.  I have Gkrellm installed too, but I don't really know what to do with it

---

### Post by ian-weisser on 2014-09-01
Check the manufacturer website for BIOS updates.
Perhaps this was a BIOS bug long fixed...until you reset the BIOS.

---

### Post by Ben_Cook on 2014-09-01
So...after my wife telling me for a while to unplug the battery for a minute she went ahead and did it and it solved the problem.  I had checked for BIOS updates, but couldn't find any.  I have no idea why it works now, but it does and that is all I care about.  Thank you for the help everyone!

---

### Post by ian-weisser on 2014-09-01
My spouse is usually correct, too.

---

