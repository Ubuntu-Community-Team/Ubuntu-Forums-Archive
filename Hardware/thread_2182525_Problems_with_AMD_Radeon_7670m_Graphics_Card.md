---
title: "Problems with AMD Radeon 7670m Graphics Card"
date: 2013-10-21
forum: Hardware
---

### Post by stratman15 on 2013-10-21
Hi everyone. I recently decided to use Ubuntu as my default OS and installed it on my Sony Vaio E series 14p laptop. Upon installing I noticed that I was only able to get about an hour and 30-40 minutes of battery life as opposed to the 3-4 hours I got with windows. I did some digging and found that some other users with AMD radeon 7670m graphics cards were having these problems as well and reccomended disabling the graphics card. I did this and found I was now able to get about 3 1/2 hours of battery life. I then later noticed that every time I suspended my computer and later came out of it the fan would start whirring at what I believe is the fastest it can go. It won't stop until I completely shut off the computer, just rebooting it won't stop the fan, and will go whether or not the cpu is being used much at all. So I re-installed ubuntu and now I'm back to a poor battery life. I was hoping someone might have some ideas on what to do? I need a better battery life but can't put up with the fan going crazy everytime I start my laptop up from sleep mode. Thanks in advance for any responses!

---

### Post by hammodi2 on 2013-10-21
am not a linux pro but i can tell that that AMD (or any  external gpu. usually new ones) is not fully supported by any linux distro. you can look for a propriety driver but it wont take full advantage of the hardware.

---

### Post by QIII on 2013-10-21
Other way around:  AMD/ATI provides a Linux driver that is not as capable as the Windows driver.  The Linux community has nothing to do with it or any control over it.

Does your machine only have the one GPU, or is it an Intel/ATI hybrid?  Which version of Ubuntu are you running?

---

### Post by stratman15 on 2013-10-21
It's an Intel/ATI hybrid and I'm running 13.10 but have also experienced problems on 12.04, 12.10 and 13.04

---

### Post by QIII on 2013-10-21
The OEMs have not provided good support to Linux for such systems.

I'm on my cell on the train right now, but I'll try to get back to post some urls that may provide some help.

---

### Post by stratman15 on 2013-10-21
Thank you so much for your help!

---

### Post by stratman15 on 2013-10-22
Quick Update: So far I've tried adding a script to sleep.d that turns the graphics card on before sleeping and off upon waking in order to stop the noisy fan but that didn't work. I also tried turning dpm on since 13.10 has the 3.11 kernel. After enabling it and updating grub I saw no difference in battery life. I'm running out of ideas at this point and am getting frustrated. I hope someone can help.

---

### Post by QIII on 2013-10-22
Hi!  back again.

My first suggestion would be to try to use vga_switcheroo and the open source Radeon driver.

This will not work with the proprietary driver, so if you have fglrx installed you will have to uninstall it.

vga_switcheroo is discussed [here]("https://help.ubuntu.com/community/HybridGraphics").

Best wishes.  Let us know if that helps.

---

### Post by stratman15 on 2013-10-22
Hey QIII, thanks again for the response. vga_switcheroo is what I've been using to turn off the graphics card, the problem is when the graphics card is off and I suspend the laptop and then wake it the fan will run at full throttle until I do a reboot. I've been using the Radeon driver as [COLOR=#000000]fglrx apparently does not work on 13.10 (when I tried it and rebooted I was put in low graphics mode) so I don't believe that's the problem. I'm not sure what else I can do.[/COLOR]

---

### Post by QIII on 2013-10-22
The fglrx works in 13.10 if all you have is a dedicated ATI card!  ;)

OK.  The other option is the ugly one, and I hate to say it but it is going to take some reading on your part.

[This]("http://ubuntuforums.org/showthread.php?t=1930450") thread deals with the problem.  It has gotten very long now and was started 18 months ago.  It might be best to go to the last page and browse through it towards the first page.  There are a lot of failures, frustrations and successes there.  A lot of links to other resources.

Like I said, unfortunately the OEMs have not been good to us with these systems.

You might try something else, I suppose, but I'm not sure how well it will work:  While running the Radeon driver, you can do some power management in 13.10.  Look at the power management section at the bottom of [this]("https://help.ubuntu.com/community/RadeonDriver") page for a trick with Saucy.  If you are managing the power when you close the lid, you might keep the fan from going crazy when you wake it.

---

