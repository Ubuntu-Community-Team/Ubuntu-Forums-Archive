---
title: "Acer TM7720G - Graphics refuse to diplay"
date: 2008-06-18
forum: Hardware
---

### Post by Penfoud on 2008-06-18
I had Ubuntu 7.10 working perfectly, with the ATI drivers from their own site etc. Then, one day, while watching an episode in VLC(tried various other players and codecs after that, all same result), the graphics just turned to crap. I had not touched any configs or anything before the change, so I tried a reboot, or what I thought would be a reboot. Now I can't even login in GUI environment, or load any application with GUI. Everything is CLI.
I also sent it for service stating the Graphics card was probably broken, I recieved it back today assuming it would work. It's all the same.
So I'm basically out of ideas, anyone know how to solve my problem?

(I'm a pretty new user, got help off friends with years of Linux experience as well as browsing these forums a bit)

---

### Post by robert.cooper on 2008-06-18
why not upgrade to 8.04? when you boot up do you get a message regarding the xserver? (i don't know what CLI means.. if that might provide more information about the problem, or just some expression).

---

### Post by prshah on 2008-06-18
> **Penfoud said:**
> Now I can't even login in GUI environment, or load any application with GUI. Everything is CLI.


> **robert.cooper said:**
> 
(i don't know what CLI means..

try the following command in your CLI (Command Line Interface - basically text shell) ```

startx
```
 
and post back output if it doesn't work. You probably need to reconfigure your graphics card if you get an error similar to "FATAL: no usable screens found". You can reconfigure it with the command ```
sudo dpkg-reconfigure xserver-xorg
```

---

