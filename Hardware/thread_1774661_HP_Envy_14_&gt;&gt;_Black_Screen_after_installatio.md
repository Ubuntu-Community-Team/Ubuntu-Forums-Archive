---
title: "HP Envy 14 &gt;&gt; Black Screen after installation &gt;&gt; Help !!"
date: 2011-06-03
forum: Hardware
---

### Post by Hammouri on 2011-06-03
Hi all,

I'm new in Ubuntu forms, & i need help in installing ubuntu beside my windows 7.

after complete the installation from windows, my laptop restarts & login to Ubuntu to complete the installation. 

the installation wizard complete the installation correctly without errors, finally the laptop restarts again & i had two choices Windows 7 & Ubuntu. 

when i select Ubuntu the Grub Menu is shown i select the first choice & the screen become black & then nothing is been displayed.

& the screen remains black, noting that i have two graphic cards:

Graphics Card Intel GMA HD
Graphics Memory 64
2nd Graphics Card ATI Mobility Radeon 5650
2nd Graphics Memory 1024  

please help me, what can i do ??
i love this OS but its black screen.

---

### Post by Hammouri on 2011-06-04
No answer till now ,,,

---

### Post by eightballd on 2011-06-14
Hi Hammouri,

I've got the same laptop and the same problem.  There is a bug report for this problem being tracked here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620)

The short answer is that if you are not using the Radeon card in Linux (i.e. no intensive 3d graphics and no external displays) then you can safely add "radeon.modeset=0" to the end of your kernel line in grub.  This will disable the radeon driver and you should be able to successfully boot each time.

James

---

