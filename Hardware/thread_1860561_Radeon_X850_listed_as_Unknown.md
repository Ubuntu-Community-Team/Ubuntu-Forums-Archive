---
title: "Radeon X850 listed as Unknown"
date: 2011-10-14
forum: Hardware
---

### Post by mickiebims on 2011-10-14
First off I'm absolutely brand new to linux and ubuntu.  I'm computer savvy and a friend recommended I try it out since my old windows hdd gave up on me.  

I'm very impressed and really like this and will hope to learn more about it as I go along.  

Question is this: 
Under System Info I see Graphics, Driver Unknown, Experience Standard.

Everything seems to be running well I'm just curious if there's a driver or something that I need to enable.  Searching the forums and the web it seems Ubuntu should support my card the radeon x850.  Any help greatly appreciated.

Thanks,
Mick

---

### Post by Gs Dewd on 2011-10-15
I to have the same problem with a Radeon x1550 xge. I think I may try installing 11.04 on this drive since I had no problems with it and then just upgrading to 11.10 and see if that fixes it. I did the smart thing and am doing the testing this time on a spare drive. I still have my great install of 11.04 on another drive that is not hooked to the computer right now so i can always just plug it back up if 11.10 doesn't workout right now.

---

### Post by Gs Dewd on 2011-10-15
Okay I think I may have the answer. I actually repaired it by accident. What I found (after the fact) is that open gl is not enables automatically. How I found this was I installed Cario dock. When I launched it (the open gl version of the 2 installed) it will say open gl isn't enabled and do you want to enable it. I said yes. I set up the dock how I am used to the i did a reboot and now everything is good. 3d works fine and now under system info my graphics is listed as Gallium 0.4 on Ati Rv 515. No I have everything installed that I had installed under 11.04 ( used the back up and re install packages commands)All Is well

---

