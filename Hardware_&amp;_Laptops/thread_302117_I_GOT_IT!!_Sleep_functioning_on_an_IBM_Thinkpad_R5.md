---
title: "I GOT IT!! Sleep functioning on an IBM Thinkpad R50e"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by leandir on 2006-11-18
I think I finally did it! Finally I got a functioning sleep with my brand new reinstalled Ubuntu 6.10 on my standard IBM Thinkpad R50e. I am still not completely sure about it, but it seems to function perfectly for now, no more graphic problems, resume problems, nothing. I really hope it is the good time ! :D 
I stumbled upon the solution by chance. First of all, I substituted the sleep.sh text with the hack provided [here]("http://www.ossgeeks.co.uk/?p=10") . Then, as it still did not function, I looked at my file /etc/default/acpi-support and had a look at all the voices...instead of just uncommenting the first line ACPI_SLEEP=true, I went on, and I have uncommented also SAVE_VBE_STATE=true (a page in the web suggested it), it was still not functioning, so I decided to uncomment also SAVE_VIDEO_PCI_STATE=true , RADEON_LIGHT=true , DOUBLE_CONSOLE_SWITCH=true . And, ladies and gentlemen, my random shot has functioned perfectly!! :D Now it really seems that the laptop is able to go to sleep and back without any problems.
I am looking forward for some feedback, I really hope it can help someone else out there.

---

### Post by adam.tropics on 2006-11-18
Ok, you have inspired me to look at getting sleep working on my toshiba....here we go again! All good though, not broken anything for a while!

---

### Post by leandir on 2006-11-18
Little errata: it seems to have still some minor graphical problems, so I have commented ENABLE_LAPTOP_MODE (it was already set to false, but just to be sure...) and changed ACPI_SLEEP_MODE from mem to standby. It seems to work, but I am not sure about it. I will keep posting my feedbacks :)

---

### Post by leandir on 2006-11-20
Ok, I have to correct myself. I still have troubles with resume and graphics, but if anything, the rate has stably decreased and it is (almost :( ) usable. I do not have the time nor the ability to look further I fear :( Maybe I will post the logs so that if someone more knowledgeable than me is around, some idea will pop up...

---

### Post by lotusburg on 2006-11-20
Hi there, 
A bit OT but I have an R50e (247/256MB RAM) and Ubuntu 6.10 won't load for installation. CD just seems to dawdle then freeze. Did you have this problem? BTW Ubuntu 6.0.6.1 LTS installed no trouble. Thanks for any advice.
Jake

---

### Post by leandir on 2006-12-09
> **lotusburg said:**
> Hi there, 
A bit OT but I have an R50e (247/256MB RAM) and Ubuntu 6.10 won't load for installation. CD just seems to dawdle then freeze. Did you have this problem? BTW Ubuntu 6.0.6.1 LTS installed no trouble. Thanks for any advice.
Jake

Sorry, no clue. I have not had this problem...try opening a thread if you have not already :)

Going back OT: I actually finally managed to get it work seamlessly, but it was not the hack I tried. It was either installing xgl and beryl or (much more probable) installing the nvidia binary drivers. I ahve not had a songle problem in weeks, I guess something changed in the configuration / the drivers fixed it. Either way, if you are not against binary drivers, I guess this is the only way to go!

---

