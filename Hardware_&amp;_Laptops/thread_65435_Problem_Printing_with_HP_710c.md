---
title: "Problem Printing with HP 710c"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by mcmillan on 2005-09-14
I'm having trouble getting my printer to work. The driver seems to install fine, and it shows up fine as a printer, but it won't actually print anything. I found a posting with a similar problem (I forget if it was here or a different forum) suggesting that the person change the permissions of a couple files to get it to work. I tried that and I was able to print for one day, then it stopped working again. Now I can't find which files I had changed before to check if they somehow got switched again. I did find a post here that seemed to suggest it might be /dev/lpO, but I thought there was more than one before, and changing this didn't seem to help (originally set as 660, tried 666, 770 and 777, now back to the 660 in case I'm wrong in thinking this). Any suggestions, especially for something that will help for more than just one day?

---

### Post by mcmillan on 2005-09-24
Ok, I'm going to resurrect this post with some new information I've figured out on my own, and from a [post](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1868726) at linuxquestion.org :
When I try a test print I get from /var/log/lpr.log with logging set for debug

Sep 20 22:01:45 localhost pnm2ppa[19166]: Starting print job
Sep 20 22:01:45 localhost pnm2ppa[19166]: Printing page 1 (PixMap)
Sep 20 22:01:50 localhost pnm2ppa[19166]: Finished rendering page 1
Sep 20 22:01:50 localhost pnm2ppa[19166]: Print job completed successfully. 

and /var/log/cups/error_log:
Sep 20 22:01:45 localhost pnm2ppa[19166]: Starting print job
Sep 20 22:01:45 localhost pnm2ppa[19166]: Printing page 1 (PixMap)
Sep 20 22:01:50 localhost pnm2ppa[19166]: Finished rendering page 1
Sep 20 22:01:50 localhost pnm2ppa[19166]: Print job completed successfully. 

Doing lsmod gives me (among other things) lp, parport and parport_pc, which I've read can all be issues. 

In the other thread someone suggested trying: echo 'hello world' >dev/lp0 which didn't do anything. The person is thinking something's wrong with my parallel port and gave me his output for dmesg | grep lp , which was

p0: using parport0 (polling).
lp0: console ready

but I get 

lp0: using parport0 (interrupt-driven).
lp0: ECP mode
lp0: ECP mode
lp0: ECP mode
lp0: ECP mode
lp0: ECP mode
lp0: ECP mode

Does this mean anything to someone?

---

### Post by mcmillan on 2005-09-24
Actually just after I posted this I was able to get it working on my own, I needed to change the settings of parallel port during bootup from ECP to SPP (normal).

That seems to have fixed it so far.

---

### Post by openmind on 2005-09-26
Hi, I'm having exactly the same problem that you described, (even down to the  dmesg output).  

Could you perhaps describe in a little more detail how to change those settings?

Thanks

---

### Post by `GooZ´ on 2005-11-05
Maybe you should try this:
[http://www.ubuntuforums.org/showthread.php?t=77940&highlight=710c](http://www.ubuntuforums.org/showthread.php?t=77940&highlight=710c)

---

