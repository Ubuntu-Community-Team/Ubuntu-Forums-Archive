---
title: "Ubuntu stopped booting on dual boot system"
date: 2008-08-09
forum: General Help
---

### Post by PCMike on 2008-08-09
I recently loaded Hardy Heron as  dual boot with WindowsXP Home. I have been using both OS for a week or so with no problems. Now when I start the PC and select Ubuntu it starts to boot and then returns to the OS selection menu. Booting from the CD and selecting "run Ubuntu from the CD and make no changes" fails also.

I would appreciate any suggestions.

---

### Post by caljohnsmith on 2008-08-09
When you try and run the Live CD, do you get any errors? What exactly happens when it fails to run? Also, is Win XP still working fine? It sure sounds like it could be a hardware problem if Ubuntu worked before from both your HDD and from CD, but does not work now...

---

### Post by PCMike on 2008-08-09
When I was trying to boot Ubuntu I did it a number of times, including completely powering off the system and letting it sit. WindowsXP seemed to work well and I could not find anything unusual. When I went back and booted up using the CD it booted OK this time and then it booted OK from disk. It is quite possible that something in the hardware is starting to act up. I guess I will have to just keep a close eye on it.

Thanks for the help. I didn't notice any errors when it failed to boot from disk, it just returned to the language selection screen. If I find anything definitive I will put it out.

THANKS again

---

### Post by caljohnsmith on 2008-08-10
You're welcome. :) But PCMike, I think your computer's symptoms definitely make a hardware problem a high possibility at this point. If you have a CD that came with your HDD that has diagnostic tools on it, I would definitely check your HDD. Since you also had troubles with booting a CD, I know that a HDD problem may not be as likely as something else, but I still would check it if I were you. Also, when you boot the machine, there should be a menu choice for running "memtest86+" to check your RAM (assuming you haven't taken that entry out of your menu.lst), and that's another test I would recommend running.

If you don't have any diagnostic software that came with your HDD, you could install this package "smartmontools" in Ubuntu and use that to test your HDD, assuming your HDD is "SMART" enabled. If you need specifics on that, let me know. Good luck. :)

---

