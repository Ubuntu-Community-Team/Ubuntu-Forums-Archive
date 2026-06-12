---
title: "Displays not working after moving computer"
date: 2021-10-20
forum: Hardware
---

### Post by woses21 on 2021-10-20
So just as the title says, my displays (3) were working just fine a few hours ago. I unplugged everything and moved my computer to a new location, and now the displays will not work. I have a MSI Gaming GeForce GTX 1050 with DVI, HDMI, and DP, however the DP is the only one working. I have swapped cables around enough to verify the DP is the only port working and the displays all work. I'm at a loss for what to do, please help.

---

### Post by mIk3_08 on 2021-10-20
> **woses21 said:**
> So just as the title says, my displays (3) were working just fine a few hours ago. I unplugged everything and moved my computer to a new location, and now the displays will not work. I have a MSI Gaming GeForce GTX 1050 with DVI, HDMI, and DP, however the DP is the only one working. I have swapped cables around enough to verify the DP is the only port working and the displays all work. I'm at a loss for what to do, please help.

Can you show us the result of this command below;
```
hostnamectl status
```
and this
```
sudo lshw
```
and this
```
sudo dmesg
```
Please paste the result wrap with code here in this thread. Thanks
Did you try to reconfigure your display under the Ubuntu System Settings?

---

### Post by woses21 on 2021-10-20
Here are the requested outputs. I did try to configure the displays in the settings, but no monitors were detected other than the one plugged in to DP. I was also unable to change any settings such as resolution or orientation, which I have never encountered before.

[https://paste.ubuntu.com/p/432Whb64g5/](https://paste.ubuntu.com/p/432Whb64g5/)

---

### Post by TheFu on 2021-10-20
Because you mention moving, I'd first think it was something physical as the root issue.
Reconnect all the cables, check the power cable inside the case from the PSU to the GPU.  Reseat the GPU in the slot. While you are in there, clean out any dust and dirt from the system and all the fans.
Any thermal warnings in the logs?  Do you monitor temperatures?

---

### Post by woses21 on 2021-10-20
Reseated GPU and power, problem persists. The machine is only a few months old so no dust to clean out. I don't monitor temperature and I don't know how to check any logs.

---

### Post by woses21 on 2021-10-20
> **TheFu said:**
> Because you mention moving, I'd first think it was something physical as the root issue.
Reconnect all the cables, check the power cable inside the case from the PSU to the GPU. Reseat the GPU in the slot. While you are in there, clean out any dust and dirt from the system and all the fans.
Any thermal warnings in the logs? Do you monitor temperatures?

Reseated GPU and power, problem persists. The machine is only a few months old so no dust to clean out. I don't monitor temperature and I don't know how to check any logs.

---

### Post by woses21 on 2021-10-20
So something is up with my graphics card. When I hot swapped the DP cable the resolution I couldn't change the resolution of the new monitor. I rebooted plugged in to the new monitor and the resolution adjusted on its own. 

I also noticed the fans are not spinning on the graphics card. I started up Skyrim and my CPU usage maxed out immediately and the program couldn't even run the opening menu smoothly.

How can I look at the hardware in my machine and see what is going on?

---

### Post by TheFu on 2021-10-20
Seems your GPU fan is out. Fix that or buy a new GPU.
Would be bad to let it overheat, right?

---

### Post by woses21 on 2021-10-21
> **TheFu said:**
> Seems your GPU fan is out. Fix that or buy a new GPU.
Would be bad to let it overheat, right?

Uh, any help on this front? This is a brand new GPU and shouldn't be broken from just moving across a room. I don't know the first thing about going about fixing it. Can I do anything on teh software side?

---

### Post by TheFu on 2021-10-21
> **woses21 said:**
> Uh, any help on this front? This is a brand new GPU and shouldn't be broken from just moving across a room. I don't know the first thing about going about fixing it. Can I do anything on teh software side?

If it is brand new, then take it back to the store for replacement. Tell them the fan isn't spinning.  If it is just "brand new" to you - used - perhaps it is still under manufacturer's warranty? Contact them for an RMA. If it is outside the warranty .... keep reading.

Can you pump gasoline into your car using "software"?  It is very likely that this is a physical connection thing. That means getting your hands inside the machine and trying to find the electrical connection or whatever is preventing the fan from spinning.  On a 1050, those fans should be spinning all the time, just the speed is in question.

I have a 1030 - which I bought specifically because it doesn't have any fans.  It is nowhere near the capabilities of a 1050, however. Not even close.

Oh ... I figured out how you can use software to pump gasoline.  You'd use your smartphone to order gasoline and have someone else come out and pump it for you.  I bet you can do the same with computer hardware issues.

Now, if you boot from any other OS ... even a _Try Ubuntu "Live boot"_ environment and **the fans work**, then it isn't a hardware issue and you can blame software.

Moving computers has risks.  In the late 1990s, I was transporting an AIX server between 2 company offices 4 hours apart in my hatch back. I'd setup the server in my office (we had 2 identical systems) and needed to get one to the other office and get it all working there. Drove up on a Friday afternoon, setup the system, it seemed to be working, then I spent the night and drove back home the next day.  The local guy there watched me do everything and it seemed to work great when we both left.  Come Monday morning, they main software they used wouldn't run, but all other software ran fine.  He had IBM support come out. They figured out that 1 of the CPUs in the server wasn't being seen and that licenses were tied to that CPU. They reseated the CPU and all was good - $500 later (service charge). Somewhere during transport, one of the CPUs had come loose, but not completely.  I may have laid the computer down in the hatchback on the wrong side.  That little thing (I'd never looked inside the server), mean that the CPU got looser, rather than tighter, in the CPU slot.

1 more question.  Have you tried lightly "thumping" the GPU fans with an eraser(pencil) while the system is running? Perhaps that would dislodge any fodder and let the fan run or get the electrical short to not be shorted so you can see the fan turn?  Even if the fan doesn't come on and work forever, just seeing that it works tells you that it is most likely the connection between the card and the fan.  I've seen Youtube videos about swapping GPU fans out - usually people replace noise fans for quieter fans.

Just some ideas.  Troubleshooting is about simplifying the problem and testing, then repeat until the most simple thing has to be the issue.

---

### Post by woses21 on 2021-10-21
> **TheFu said:**
> If it is brand new, then take it back to the store for replacement. Tell them the fan isn't spinning.  If it is just "brand new" to you - used - perhaps it is still under manufacturer's warranty? Contact them for an RMA. If it is outside the warranty .... keep reading.

Can you pump gasoline into your car using "software"?  It is very likely that this is a physical connection thing. That means getting your hands inside the machine and trying to find the electrical connection or whatever is preventing the fan from spinning.  On a 1050, those fans should be spinning all the time, just the speed is in question.

I have a 1030 - which I bought specifically because it doesn't have any fans.  It is nowhere near the capabilities of a 1050, however. Not even close.

Oh ... I figured out how you can use software to pump gasoline.  You'd use your smartphone to order gasoline and have someone else come out and pump it for you.  I bet you can do the same with computer hardware issues.

Now, if you boot from any other OS ... even a _Try Ubuntu "Live boot"_ environment and **the fans work**, then it isn't a hardware issue and you can blame software.

Moving computers has risks.  In the late 1990s, I was transporting an AIX server between 2 company offices 4 hours apart in my hatch back. I'd setup the server in my office (we had 2 identical systems) and needed to get one to the other office and get it all working there. Drove up on a Friday afternoon, setup the system, it seemed to be working, then I spent the night and drove back home the next day.  The local guy there watched me do everything and it seemed to work great when we both left.  Come Monday morning, they main software they used wouldn't run, but all other software ran fine.  He had IBM support come out. They figured out that 1 of the CPUs in the server wasn't being seen and that licenses were tied to that CPU. They reseated the CPU and all was good - $500 later (service charge). Somewhere during transport, one of the CPUs had come loose, but not completely.  I may have laid the computer down in the hatchback on the wrong side.  That little thing (I'd never looked inside the server), mean that the CPU got looser, rather than tighter, in the CPU slot.

1 more question.  Have you tried lightly "thumping" the GPU fans with an eraser(pencil) while the system is running? Perhaps that would dislodge any fodder and let the fan run or get the electrical short to not be shorted so you can see the fan turn?  Even if the fan doesn't come on and work forever, just seeing that it works tells you that it is most likely the connection between the card and the fan.  I've seen Youtube videos about swapping GPU fans out - usually people replace noise fans for quieter fans.

Just some ideas.  Troubleshooting is about simplifying the problem and testing, then repeat until the most simple thing has to be the issue.

I appreciate your help with this issue. I have found the fans do spin, but stop spinning once any software is loaded. The fans spin on power up but once Ubuntu, Ubuntu Live, or even BIOS is loaded the fans stop spinning. I loaded all the defaults in my BIOS but nothing changed, the fans still stop spinning once any OS is loaded.

---

### Post by TheFu on 2021-10-21
> **woses21 said:**
> I appreciate your help with this issue. I have found the fans do spin, but stop spinning once any software is loaded. The fans spin on power up but once Ubuntu, Ubuntu Live, or even BIOS is loaded the fans stop spinning. I loaded all the defaults in my BIOS but nothing changed, the fans still stop spinning once any OS is loaded.

Did you try using a different "Try ubuntu" boot flash drive?  Did that work as expected?  There are known problems with nvidia and Wayland. I think those are documented in the Release Notes.  Ah ... I see you are on 20.04 - so that isn't it.  Xorg is the default there. I'm getting confused between different GPU issues ... and I'm working on a new system build here which I expect will have igp issues too.

---

### Post by woses21 on 2021-10-21
> **TheFu said:**
> Did you try using a different "Try ubuntu" boot flash drive?  Did that work as expected?  

Yes, I used a spare boot drive I have around and the same thing happened. As soon as the kernel loads the fans stop spinning.

---

