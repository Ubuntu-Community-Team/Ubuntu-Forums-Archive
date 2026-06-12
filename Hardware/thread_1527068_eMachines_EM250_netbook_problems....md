---
title: "eMachines EM250 netbook problems..."
date: 2010-07-08
forum: Hardware
---

### Post by Breaking.Matter on 2010-07-08
I searched the forums and I haven't found anything about this problem so...

I have an eMachines EM250 netbook (the walmart special $270 one). I've been an avid Ubuntu user for about 2 years, but this problem has me completely stumped..

My netbook has a built in mic and webcam. In Windows, the mic works, but in Ubuntu it isn't working properly... I'm running Ubuntu 10.04. I checked my "Hardware Drivers" in the System tab but it didn't find anything. The mic just doesn't work right though. It shows up as being connected (i believe I checked it right...) and when I use the Sound Recorder in my applications it works. But, when I try to use any other application, it doesn't work. Like, recording a Youtube video, Skype, etc.

I have no clue what to do. Any help would be greatly appreciated. I hate having to use Windows to record Youtube videos and to call my friends in foreign countries. 

-Zane

---

### Post by S.R on 2010-07-08
Is the mic boost enabled? OOOh and skype can be set up to automatically detect settings for you mic and sometimes they are not always right.

---

### Post by Breaking.Matter on 2010-07-08
> **S.R said:**
> Is the mic boost enabled? OOOh and skype can be set up to automatically detect settings for you mic and sometimes they are not always right.

I don't think the boost is enabled. 

But, that wouldn't have anything to do with Youtube. Skype's settings might affect IT, but what about Youtube?

---

### Post by S.R on 2010-07-08
It sounds like it is working just not well. SO makes me think you need to get in there turn on the mic boost and crank the mic volume up and just set programs like skype or you tube to manage your mic your own self. Should turn out ok.

---

### Post by Breaking.Matter on 2010-07-08
I just tried that and it's still not working. Just loud static..

---

### Post by Breaking.Matter on 2010-07-09
Bump?

---

### Post by bochan on 2010-07-19
Hello,
I had the same issue with eMachines 350. I installed Netbook Remix 10.04. I foun help here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

First of all install pavucontrol to adjust mic volume. 
 
"sudo apt-get install pavucontrol"

Then you have to  mute one channel (left or right) and set the other to volume 80-90, which works fine for me.

Iif you use Skype disable in Options/Sound devices automatic adjustment of the mixer levels, otherwise it will reset mic volume to max again.

The solution may differ from PC you are using, but this one I tried on several acer notebooks. 
-----
bochan

---

### Post by Robboti on 2011-09-02
> **bochan said:**
> Hello,
I had the same issue with eMachines 350. I installed Netbook Remix 10.04. I foun help here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

First of all install pavucontrol to adjust mic volume. 
 
"sudo apt-get install pavucontrol"

Then you have to  mute one channel (left or right) and set the other to volume 80-90, which works fine for me.

Iif you use Skype disable in Options/Sound devices automatic adjustment of the mixer levels, otherwise it will reset mic volume to max again.

The solution may differ from PC you are using, but this one I tried on several acer notebooks. 
-----
bochan
Sorry for bump, but I had same problem with my eM250 and that worked. Thanks.

---

