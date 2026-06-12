---
title: "problems with installing xbox 360 wirless adapter in jaunty"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by NoUrOtherLeft on 2009-08-05
ok so i tried to install and configure my xbox 360 wireless adapter.  I found an explanation of how to install and configure the controller at this site

[Install and configure Microsoft® Xbox™ and Xbox 360™ controllers under Ubuntu 7.10 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Xbox360Controller#WirelessIssues") 

i know it says that it is for 7.10 but most things for earlier versions of ubuntu usually work in jaunty for me.

everything seemed to be going fine but the problem is when i try to create the makefile i keep getting errors.  I am really new at linux in general and i was hoping that someone would be able to give me step-by-step instructions on how to make this thing work.

here is the output of what i got when i tried to do the makefile:


germs@germs:~/xpad$ KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)
bash: shell: command not found
bash: KERNEL_PATH?=/usr/src/linux-headers-: No such file or directory
germs@germs:~/xpad$ 


it seems i have no idea what i am doing and im completely lost when it comes to makefiles.  can someone explain this to me?:confused:

---

