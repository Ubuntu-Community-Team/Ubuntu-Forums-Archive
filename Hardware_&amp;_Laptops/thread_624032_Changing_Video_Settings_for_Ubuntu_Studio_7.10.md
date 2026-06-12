---
title: "Changing Video Settings for Ubuntu Studio 7.10"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by leejk_sun on 2007-11-26
Hello,

I am a new user of Ubuntu and a new member of this board and I am very excited about the capabilities of this OS.

However, like any transition, I'm having a few problems.

The biggest problem deals with the graphics card. I have installed Ubuntu Studio 7.10 on my Toshiba Satellite 1005-S157 laptop. The integrated graphics card is an Intel 830MG. When I hook up an external monitor to the laptop, the computer boots up and displays everything normally. When I disconnect the external monitor and boot up the computer, I can get the GRUB start up text, but the screen flickers and then goes to black when the Ubuntu Studio loading graphic is supposed to appear.

I have tried booting the computer in recovery mode and configuring the video settings using the "sudo dpkg- reconfigure xserver-xorg" command, but it has not helped.

I would like to use the laptop as a laptop and not be tethered by a 19 inch LCD, so how should I reconfigure the video settings to work with the laptop's screen?

Also, are there any third-party utilities or drivers that can help me out?

Thank you very much for any help.

---

### Post by leejk_sun on 2007-11-26
I have just resolved my own problem, but thank you to anyone who read my post.

Just in case any other Ubuntu Studio 7.10 user has the same problem, I'm going to post my own solution:

I booted up the computer with the external monitor unplugged from the system and pressed the ESC key during the GRUB loading screen to get to the safe mode recovery option.

At the prompt, I used this command:

"sudo dpkg-reconfigure xserver-xorg"

This will take you through a series of questions, but the first steps are the most important. Go ahead with the video auto-detection. The next scree should give you some driver options, and "Intel" was automatically selected for me, but the driver that I selected was the "i810" driver a couple of slots above. I selected this driver because I noticed a lot of users recommending this driver over VESA in other forums while I was researching this problem. 

I answered "no" to the "auto-buffer" question and went with the default selected options for the keyboard and mouse configurations. I answered "yes" to auto-detect the monitor, and I went for the default settings for most of the questions. When it ask for the resolution to use, 1024x768 was automatically selected and I continued to the next screen. 

It then asks about screen refresh and I selected the "Medium" configuration option and selected the "1024x768 @ 60 Hz" option from that menu and continued. I Said yes for everything else and it put me back at the prompt. I used the "exit" command to get out of recovery mode and the computer booted as normal and displayed Ubuntu perfectly.

I hope this helps anyone that finds my post.

Thank you.

---

