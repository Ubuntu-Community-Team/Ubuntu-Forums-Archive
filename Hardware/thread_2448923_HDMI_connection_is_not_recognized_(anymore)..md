---
title: "HDMI connection is not recognized (anymore)."
date: 2020-08-16
forum: Hardware
---

### Post by soulflight on 2020-08-16
Hello,

I had my laptop connected to an external TV screen by HDMI cable. Recently its not being recognized anymore. The TV screen shows a "connected " icon in the source selection, but my laptop wont find it. Xrandr command also doesnt show any HDMI device connected. Its working with another computer though, so I can rule out a cable malfunction. Also, the same TV was recognized by ubuntu before, but now not anymore.

Running ubuntu 16.04 on an Acer Aspire ES1-311 laptop.

Any ideas? thx :)

---

### Post by CelticWarrior on 2020-08-16
Does it work in a live session?

---

### Post by soulflight on 2020-08-16
Just tried. No, it doesnt.

On the installed OS it was working until a few days ago though.

---

### Post by CelticWarrior on 2020-08-16
After posting the above I came across this [https://ubuntuforums.org/showthread.php?t=2448913](https://ubuntuforums.org/showthread.php?t=2448913) and notice first that it was about the same machine and then it was from you, the same user.

So, it's baffling that in your other thread you considered important to mention that you have been messing with graphics drivers but here, in a thread about the HDMI somehow you felt it shouldn't matter as to not even mention it? This isn't the way to ask for help.

And considering 16.04 has lees than a years left of support, what's the point? Just install from scratch the current LTS 20.04.

---

### Post by soulflight on 2020-08-16
Take a chill pill, I know why I didnt mention that. The HDMI not being recognized anymore was the reason why the other threads problem actually emerged. I tried to update some intel drivers when something broke. Since this thread is about a problem that was present before that, and the other issue was solved, i was deliberately not mentioning that here to prevent confusion. I have been in forums way too long to count on people really reading and understanding everything when there is too much unnecessary information provided.

---

### Post by soulflight on 2020-08-17
BTW, i upgraded 16.04 to 18.04 now, which solved a lot of issues after the broken driver i had. 

But my HDMI device still wont be recognized. It definitely was working until like a week ago and when plugged with a windows device it is also working. xrandr is showing "HDMI not connected". Any help is still appreciated.

---

### Post by malangaman on 2020-10-22
I recently had a similar problem. I solved it by using Synaptic to re-install all graphic drivers (mine were Intel) that were listed as installed. After a reboot, HDMI was recognized and I am now able to use 2nd monitor again.

---

