---
title: "Webcam video skipping"
date: 2012-09-18
forum: Hardware
---

### Post by deathbycopypaste on 2012-09-18
*Edit:  I am using Ubuntu 12.04 and have had next to no experience with linux.*

I am not sure if this is an ubuntu issue or not.  This could also be a Logitech or Compaq issue, but i came here first. 

When recording video with a Logitech webcam, the video skips.  To be more specific, it is slow to respond to motion.   It catches a few seconds at a time and stops, then continues after a second or so for a few more seconds.  The audio is recorded and plays back as one would expect from normal functionality. 

It seems to me that it is possible that the computer does not have enough memory to keep up with the video, which doesn't make sense given the amount of memory it has.  

I am using the Logitech C270 web cam with the Cheese application (this was the most referenced app for this so i went with it, if there is a better one I will try it.)

Memory 2.7GB
Processor AMD Athalon II P320 Dual-Core Processor x2
Graphics VESA: RS880M
OS Type 64 bit
Disk 243.2 GB

I executed the free -m command without cheese active and while it was recording and there was minor change... maybe this isnt memory related.

Is there a driver that should be installed (I found some threads stating logitech is not supported by Ubuntu ... but it works (mostly) straight out of the box for me).
If you would like me to link a test video, i will do that.  Just let me know.

---

### Post by deathbycopypaste on 2012-09-20
I played with the free -m command a little more and have thoroughly confused myself.

Prior to opening cheese it was sitting at a steady 1000 MB free with 20 buffers.
I then opened cheese and watched as "free -m -s 5" steadily dropped the free space to around 200 mb.  It then added another buffer and jumped up to about 900 mb free. 
I then closed the Cheese program, expecting it to drop that additional buffer and jump back up ... didn't happen.  
It actually added another buffer and continues to drop.  As I type this, it is sitting at 23 buffers and still steadily dropping in free space (Firefox and terminal are the only programs that i have initiated. (Now 24 buffers and 352 mb free)).

I need to do research to find out how the memory allocation works for ubuntu (will do that after this is submitted).

My questions: Is the issue I am experiencing with the video being recorded related to the memory?  Is 2.7 GB of RAM enough to handle a webcam?

---

### Post by deathbycopypaste on 2012-09-20
Turns out it was not an issue on my end.  The comments for the cheese program in the Software Center stated the Cheese program itself lags.  
Tried guvcview and it works much better.

---

