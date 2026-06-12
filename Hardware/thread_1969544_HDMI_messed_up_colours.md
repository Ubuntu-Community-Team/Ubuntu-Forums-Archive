---
title: "HDMI messed up colours"
date: 2012-04-30
forum: Hardware
---

### Post by ubuntukid on 2012-04-30
I'm running Ubuntu 12.04 64-bit and I'm having problems using the HDMI out on my Thinkpad Edge 13". When I connect the laptop to my 1080p tv using HDMI, Ubuntu recognizes the screen, but the colours are way off. I've included a picture to show what I mean. Unfortunately the camera on my phone is not very good, but as you can see, the colours on my laptop and my HDTV are different. The black bars are green. The window that I have open on the HDTV is synaptic. The white area on synaptic isn't white like it should be, but has some kind of pink cast on it. I never had these colour issues with Windows 7, so most likely not a hardware problem.

Also, I have an overscan issue when using the TV. The screen area goes beyond that of the actual TV screen. In windows I could fix this, but I can't find options for this in Ubuntu. As a result, all the buttons are outside the screen area. Also, despite being a 24" tv, display settings identifies it as a 23" screen.

According to system info I'm running an intel ironlake mobile procesor. I'm not sure what kind of information people need to help me solve this problem, so let me know what commands I should rund and post the output of if needed. I've also run system update, so I am running the most up-to-date version.

---

### Post by Zvezdica27 on 2012-05-07
Hi,

I have the exact same issue.

I can solve it temporarily by suspending and re-waking the computer. Then it works fine. After reboot the situation is the same.

I will try some more, hopefully it can be resolved, because in past releases this was not the case, while all 12.04 distros have this in my case (system76 pangolin performance laptop). 

I will try a new kernel when i manage, i think this is a driver issue.

zz

---

### Post by rossmoore on 2012-05-09
I get this on my Sandy Bridge desktop. It's permanently connected by HDMI to my TV. Most of the time it's fine, but after maybe a day (and meanwhile the TV has been off and the computer left alone for a few hours) I come back and discover the colour issues you've got there.

My only fix so far is to reboot. Logging out, switching VT, unplugging the TV and replugging it - none of that seems to help. I read somewhere that this green tint issue can be caused by some handshake failure/confusion about audio over HDMI, but darned if I can figure out why it's only a problem now. I had no issue in 11.10.

I'll let you know if I figure anything out, or if an update magically fixes it.

---

