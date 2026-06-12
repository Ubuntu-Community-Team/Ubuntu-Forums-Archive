---
title: "Impossible to install 8.10!"
date: 2008-10-30
forum: General Help
---

### Post by thayle on 2008-10-30
Everytime I try after the orange bar loads I just get some iwlagn error about timeout at 500ms

I'm pretty sure it looked like this:
iwlagn: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms. 

Please help, I really want ubuntu. Oh and if your answer is to turn my wifi switch off, I can't, there is NO SWITCH!

---

### Post by scouser73 on 2008-10-30
I'm not teaching you to suck eggs here, but did you burn the ISO at the slowest speed? If not then that may sort it for you.

---

### Post by thayle on 2008-10-31
So burning it on the lowest speed didn't help. Also, 32-bit and 64-bit both don't work. And the error is actually:

iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.

---

### Post by cariboo on 2008-10-31
Your problem is unfortunately is a known bug. See this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

Is there any way you could use the alternate install cd? Once you get up and running you should be able to download the proper driver.

Jim

---

### Post by thayle on 2008-10-31
> **cariboo907 said:**
> Your problem is unfortunately is a known bug. See this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

Is there any way you could use the alternate install cd? Once you get up and running you should be able to download the proper driver.

Jim


What exactly do I do with the alternate CD? I'm sort of a noob with linux and Ubuntu...

---

### Post by 3rdalbum on 2008-10-31
The alternate CD is just an "install-only" CD; it boots up a text-based installer. Don't worry, it's not as difficult as it sounds - it uses a sort of GUI that is just made up of text and controlled through the arrow keys, spacebar, and tab key on the keyboard.

The alternate CD doesn't try and set up all your hardware all at once; it leaves that job to the operating system it installs, which means you're more likely to succeed in installing Ubuntu from the alternate CD.

---

