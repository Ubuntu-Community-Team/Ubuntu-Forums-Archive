---
title: "Mushkin ssd dieing on me, or not?"
date: 2010-11-21
forum: Hardware
---

### Post by Zilioum on 2010-11-21
A few weeks ago I bought a mushkin callipso desluxe 60gb ssd. I put it in the notebook I owned at that time and everything worked perfectly. A week ago I bought a new notebook, put the ssd in and installed the 10.10 beta. The disk utility showed some bad sectors and showed an elevated "Reallocated sector count". The icon was still green so I didn't worry to much although I know I have to replace the disk at some point. I think that I didn't have this sector problem on my old notebook, which also ran 10.10.
Now the real Problem: I tried to wake my notebook up from the "suspend" state but the screen stayed black and I only saw the little arrow flickering around. I pressed the power button to reboot and I got the message "No boot device found"-the filesystem was gone (more details in[this old thread]("http://ubuntuforums.org/showthread.php?t=1595536"))

I went to the store and had them replace the ssd. Now I reinstalled ubuntu 10.10 on this new SSD and the disk utility gives me the same error message. I think this pretty much rules out the possibility that the problem comes from the disk itself.

I found some threads on the internet saying that disk utilities have trouble reading the SMART Status from some ssd. 

I don't mind a wrong SMART Status, but I don't want my whole filesystem to crash on me again. How can I protect against this?
I'll make an ISO of the clean install, but in the long run this is no real solution.

---

### Post by stefangr1 on 2010-11-21
It could indeed be a problem between your IO-board and your ssd-drive. If there are no known issues with your mushkin callipso, and other disks don't give problems on your laptop, a hardware compatibility problem seems the obvious.

I think it's unlikely that it's something related to Ubuntu and your disk, as it's usually not that disk that matters but the controller. So then I would expect that you would have the same problem regardless of the type of disk.

---

### Post by Zilioum on 2010-11-21
Thanks for your answer.
> I think it's unlikely that it's something related to Ubuntu and your disk, as it's usually not that disk that matters but the controller. So then I would expect that you would have the same problem regardless of the type of disk.
What does this mean in consequence?

As I mentioned the problems only occurred when the pc woke up. Does anyone have an idea why this happened? Or how I could find out why?

As long as this doesn't happen again I can live with the messed up SMART status.

---

### Post by Zilioum on 2010-11-22
I thought some more about my problem and thats my conclusion:
It may very well be that the messed up SMART status and my old disk failing are two different issues.

When the disk utility tells me that the reallocated sector count is 864, does that mean that the utility did something with those sectors?

This is important, because as long as the SMART status doesn't interfere with my SSD working properly every things fine (I only have to hope that the disk failure of my old SSD was a manufacturing error).

---

### Post by Zilioum on 2010-11-22
I found the answer to my question above: 
In the disk utility under ID 5 it says:
> 
Count of remapped sectors. When the hard drive finds a read/write error, it marks the sectors as reallocated and transfers data to a special reserved area (spare area).
That count is at 864 (and has been for the last few days, I don't know at what value it started though).

How can I find out if this is necessary? I'm pretty sure that this is an error.

Strangely enough the count for ID 196 (Reallocation Count) is 0. Shouldn't be there a connection?

---

