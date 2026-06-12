---
title: "CPU Usage 100% :("
date: 2011-12-17
forum: Hardware
---

### Post by Rendel on 2011-12-17
Hello everyone.

I have installed ubuntu 11.10 on a laptop MSI CR640.
intel core i3 2.10Ghz, 4GB RAM and etc.

My problem is that my CPU average usage is 80%. sometimes 100%. (look at the picture)

Can anyone help?

Thanks anyway.

sorry for my bad english. :(

---

### Post by jcer93705 on 2011-12-17
> **Rendel said:**
> Hello everyone.

I have installed ubuntu 11.10 on a laptop MSI CR640.
intel core i3 2.10Ghz, 4GB RAM and etc.

My problem is that my CPU average usage is 80%. sometimes 100%. (look at the picture)

Can anyone help?

Thanks anyway.

sorry for my bad english. :(

My desktop gets like that that's why I don't run ubuntu. Hope there is a solution.

---

### Post by Chizzleface on 2011-12-17
Do you have a separate graphics processor or is it integrated into the motherboard? On my old PC I had a similar problem but when I put in a new graphics card, the CPU usage dropped off because it wasn't having to handle graphics as well as everything else.

---

### Post by Rendel on 2011-12-17
> **Chizzleface said:**
> Do you have a separate graphics processor or is it integrated into the motherboard? On my old PC I had a similar problem but when I put in a new graphics card, the CPU usage dropped off because it wasn't having to handle graphics as well as everything else.

It's a laptop. It has intel HD 3000 graphycs.
[http://www.msi.com/product/nb/CR640.html#/?div=Specification]("http://www.msi.com/product/nb/CR640.html#/?div=Specification") check this link for more specifications.

so i can't have ubuntu without big cpu usage? :(

---

### Post by Chizzleface on 2011-12-17
If you go to System > System Monitor, it'll tell you exactly what's hogging your CPU.

---

### Post by Rendel on 2011-12-17
> **Chizzleface said:**
> If you go to System > System Monitor, it'll tell you exactly what's hogging your CPU.

And which tab should i take a screen? Processes? Resources? or?


here are both

---

### Post by Rendel on 2011-12-17
Any ideas how to fix this problem? :/

---

### Post by madengineer on 2011-12-17
OK, that is very odd. I'm guessing that the CPU usage is very high at all times, not just when you're doing something with the computer. I'd be curious to see what the output of *top* is. On the third line of the display, you will see something like ```
Cpu(s):  4.1%us,  1.8%sy,  0.0%ni, 94.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
```. My guess is that the "sy" percentage is going to be high, indicating the kernel is doing a lot of work on something. Unfortunately, AFAIK there is no detailed task accounting for kernel mode stuff like you have for userspace.

If kernel mode load is indeed high, I would try shutting down your desktop environment temporarily to see if it goes away. To do this, hit Ctrl+Alt+F1 to switch to a virtual console, log in, and enter "sudo stop lightdm". This will shut down the display manager and take GNOME down as well. Run top in this virtual console and see what changes. If this rectifies the situation, it might be a video card issue as Chizzleface suggested. You could then see if there's a different driver you could use with it, like I can choose between nouveau and the NVidia binary blob to run my NVidia GPU. When you want to return to the regular desktop environment, run "sudo start lightdm".

---

### Post by Inphi on 2011-12-17
yeah. Ubuntu has a poor power management function.
Even when the CPU utilization is, say 3%, for about 2 minutes, the CPU is still 'clocking'. Hence, the computer gets hot, and the CPU fan spins wildly. It's very annoying and loud on a laptop.

---

### Post by bluexrider on 2011-12-17
> **Rendel said:**
> Hello everyone.

I have installed ubuntu 11.10 on a laptop MSI CR640.
intel core i3 2.10Ghz, 4GB RAM and etc.

My problem is that my CPU average usage is 80%. sometimes 100%. (look at the picture)

Can anyone help?

Thanks anyway.

sorry for my bad english. :(
I had similar issues but dropped back to 11.04 2.6.38-13-generic #53-Ubuntu SMP now my CPU usage is 12-15% unless loading heavy using photo apps

---

### Post by Rendel on 2011-12-18
Ok. Thanks guys for your replys.

**madengineer**

I did what you've said to me. Stop the desktop and work in console. tried to run "top" too and got the same effect. CPU usage is still 100%. :( I have video card integrated in procesor. But CPU works normally in windows and in MAC OS X too. Why should it use 100% of it's availability when i don't do nothing, just looking at "top" or "system monitor"?

Here is the screenshot of the top you want to see.


**bluexrider**

So if i back to 11.04 the CPU will work as it should be? How do you think?

---

### Post by bootedguy on 2011-12-18
I have had this problem with a laptop with the past three distros of Ubuntu.  The CPU usage goes nuts, and TOP show XORG as hogging the CPU.  Disconnecting the wireless for a brief period would fix the problem, but after reconnecting, problem would reappear after a while.  I could go days without the the problem reappearing, and then it might appear 2 or 3 times in one day.  I finally "solved" the problem by switching to Mint 12.

I have some screen shots of System Monitor and TOP [here]("http://ubuntuforums.org/showthread.php?t=1764396").

---

### Post by bluexrider on 2011-12-18
> **Rendel said:**
> Ok. Thanks guys for your replys.

**madengineer**

I did what you've said to me. Stop the desktop and work in console. tried to run "top" too and got the same effect. CPU usage is still 100%. :( I have video card integrated in procesor. But CPU works normally in windows and in MAC OS X too. Why should it use 100% of it's availability when i don't do nothing, just looking at "top" or "system monitor"?

Here is the screenshot of the top you want to see.


**bluexrider**

So if i back to 11.04 the CPU will work as it should be? How do you think?

From what I can see of the "TOP" print (which is hard to read) that nothing is running a muck. Leads me to believe that the kernel is at fault. Attached is a shot of my processor working at idle.

hummmmm. not a very good thumbnail, will try again

---

### Post by bluexrider on 2011-12-18
new shot

Much better.

---

### Post by JC Cheloven on 2011-12-18
@the OP: please post the output of ```
sudo lshw -C video
``` and let's see which driver etc is being used.

---

### Post by lolpenguin on 2011-12-18
Looking at your screenshots, (correct me if I am wrong) your CPU usage is actually 30-40ish. But one thing I spotted was that Core 4 was doing all the hard work. There might be a problem with multi-threading.

---

