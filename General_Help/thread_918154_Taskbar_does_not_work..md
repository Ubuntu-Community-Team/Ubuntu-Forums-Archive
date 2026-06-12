---
title: "Taskbar does not work."
date: 2008-09-12
forum: General Help
---

### Post by munkedal on 2008-09-12
I installed a new motherboard & CPU in my computer. After a lot of work I got it working fine.(At least I thought I had) Then I thought I would try playing a DVD. The desktop locked up.  I have removed the DVD from the drive and now the task bars do not work.  I cannot even shut down using the red button on the top right corner. I am using Ubuntu, hardy heron.
[LIST=1]
[*]Could it have anything to do with my master and slave settings of my hard drive and my DVD drive that are on the same IDE cable?
[*]Is there some way I can repair the problem? Remember that I cannot access the terminal through the desktop.
[/LIST]:confused:

---

### Post by Sycron on 2008-09-12
Does Ctrl+Alt+Backspace and Ctrl+Alt+F1 work?

---

### Post by munkedal on 2008-09-12
ctrl+alt+backspace forced me to log in again and then I got a beige screen and a grey rectangle in the top left corner. I could do nothing with this.

ctrl+alt+F1 brought up a "terminal" desktop and asked for login details.

So, I believe that ctrl+alt+backspace did not work and yes I believe ctrl+alt+F1 did work.

Thank you for your quick reply.

---

### Post by RuarriS on 2008-09-12
I have the same problem sometimes, it happens when an application locks up. For me it was wine with WoW. But same symptoms and everything. I've noticed since I fixed all the problems I was having with Pulseaudio though, the problem stopped happening. I don't know if that's coincidence or what..

---

### Post by munkedal on 2008-09-12
I was messing around with my pulse audio as well just before this happened. I did not think it was related but maybe it is.

---

### Post by munkedal on 2008-09-13
I fixed it.  Thank you to Sycron for showing me that Ctrl+Alt+F1 gets me to the terminal to type in the proper code.  And thank you to Ruarris suggesting it might have something to do with pulse audio.  
I had been messing with pulse audio so I found a solution at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) .
I did the following:
code:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
code:
sudo apt-get install linux-sound-base alsa-base alsa-utils
code:
sudo apt-get install gdm ubuntu-desktop

It was probably only the last bit of code that did the job, but I did all three.

Problem solved.

---

