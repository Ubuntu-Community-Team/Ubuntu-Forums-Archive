---
title: "Different track speeds for touchpad and mouse?"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-01-10
Is there any way to set a separate tracking speed for my laptops touchpad and my USB mouse? When I am using the touchpad, I have to crank up the cursor speed so it is usable. When I plug in my mouse, the cursor moves way too fast and I have to re-adjust it.

I found a piece of software called touchpad on add/remove that claims it will let me configure my touchpad. I don't know if it will help me with my problem. When I try to run it, I get this error 
> 
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


If this app would help me solve my problem, how do I get past that error? If the app is useless for the problem I described tell me so I can uninstall it.

---

### Post by defaulk on 2008-05-26
Did you set that option in your xorg.conf?  You will probably have a section dedicated to a synaptics device.  the option goes in there as 
```
Option "SHMConfig" "true"
```

As for the different speeds, I don't think it will help you.  If there's anyone who knows how to get different sensitivities between the mouse and the touchpad though, please help us out!

---

