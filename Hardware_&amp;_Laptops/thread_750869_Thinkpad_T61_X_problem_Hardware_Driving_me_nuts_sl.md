---
title: "Thinkpad T61 X problem? Hardware? Driving me nuts slowly"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by mherrick66 on 2008-04-09
I have a Thinkpad T61. I like it for the most part.

After I use it for an hour and 1/2 or so, the screen starts to go crazy. 

If I scroll and am looking at text, the text becomes unreadable in certain sections. If I scroll it fixes it, but becomes worse and worse.

Restarting X fixes the problem for a short time until it returns. If I reboot, it works for another hour and a half until the cycle repeats itself.

This problem has been with me since I got the laptop brand new 5 months ago. It seems to be either getting worse or I am just getting sick of it.

A have heard a similar report from a co-worker.

How do I know if this is hardware or software?

Thanks,

Mike

---

### Post by ELF_O8 on 2008-04-09
it could be that the GPU is overheating.
I still think that it is a hardware issue.
 I don't think any software could cause this kind of malfunction.

---

### Post by mherrick66 on 2008-04-09
Thanks for the reply.

Any suggestions for how to determine this / adjust?

Mike

---

### Post by ELF_O8 on 2008-04-10
you say it happens at a consistent time after boot?
you could try to find one of those laptop cooling boards.
I think either way you are going to have to take it in.
Which isn't exactly convinient, especially after only 5 months of use.

---

### Post by mherrick66 on 2008-04-10
Thanks.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61)

If the Restricted Drivers Manager fails to install the driver you can use the Envy tool from: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). This tool is unsupported and the only supported method of installing the Nvidia drivers is via Synaptics and the Restricted Drivers Manager.

I decided to update the driver and see what happens. Hey my brightness works now without having to use the virtual terminal so I have that going for me. Will report back if it makes any difference on the screen going crazy issue.

---

### Post by mherrick66 on 2008-04-11
So after I installed the new NVidia driver on Gutsy my problem seems to have gone away. Yay.

---

