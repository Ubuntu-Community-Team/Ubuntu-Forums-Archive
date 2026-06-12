---
title: "Wonderful New Phenomenon In Ubuntu Jaunty-Dell"
date: 2009-10-06
forum: Hardware
---

### Post by johnjoy on 2009-10-06
Hi,
This post is gonna get the Ubuntu know-alls bamboozled, I'm sure.
I have had recurrent sound problems with my Dell Inspiron 1440 with Dual boot of Windows Vista and Ubuntu Jaunty.
Earlier sound used to work like, 5% of the time. Then I reinstalled Jaunty, then updated using Synaptics. But still, no sound. But headphones we working fine though. I don't like imperfection in my system. If I don't have sound, I better not have Ubuntu.
Now, I found a solution (not a solution, but a phenomenon, as I call it). When I start up my comp, I have to boot Vista, when the User/passwd screen appears, restart and now load Jaunty. By this process, always sound start working in Jaunty. Yes 100%.
But if I directly load Jaunty, no sound 100% sure.

Now this phenomenon should leave Jaunty developers red faced, for sure. Can someone help me get sound properly in my system? I have spent, like eons, trying to solve this problem.

Thanks

---

### Post by avacado on 2009-10-06
I had a similar problem with an external drive.
I think it has to do with drivers for the sound card.
something in that boot sequence uses the driver which makes it work.
but I am a newbie and guessing
try 
$ dmesg error
$ dmesg -snd
 
Try installing ubuntu on the whole HDD that might solve the problem (eg. get rid of windows)

---

