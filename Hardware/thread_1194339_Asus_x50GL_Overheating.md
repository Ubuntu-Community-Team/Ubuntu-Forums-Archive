---
title: "Asus x50GL Overheating"
date: 2009-06-22
forum: Hardware
---

### Post by jorl17 on 2009-06-22
Greetings.

It's been a while since I last asked for any help with my endless adventure with ASUS' faulty x50gl laptop.

Up until now I had had ACPI issues which didn't particularly bother me. I fixed those yesterday, you can check the following thread for more info: [http://ubuntuforums.org/showthread.php?p=7497257](http://ubuntuforums.org/showthread.php?p=7497257)

However, about 4-5 months ago I started having some instant shutdowns while running Age Of Empires III (via Wine, ofc). It had never happened, and became recurrent. I thought it was a GFX card overheating, but now I am not sure which component overheats. Here's more info:

With the fix I applied before (check the thread) I managed to get the CPU sensor that I so much wanted. It seems that it is always above 52 degrees Celsius. It never goes below that -- and that's when Idle, OUCH!

The gfx sensor is even worse, it keeps at 60 ºC. But as soon as something heavier starts (it may not be gfx related), it jumps and, many times, hits 73ºC! I've never seen it past that, because it puffs (but sometimes it shuts down BEFORE, such as 67ºC).

I opened the laptop and cleaned the fan, it was fine. No results.

I checked Windows (it had been 5 months since I had last gone there) and verified that there are more sensors, I found these:

CPU 1 
CPU 2
GFX 1
MCP

I googled for MCP (which I don't have in Linux) and discovered that it is also related t gfx (it seems). In windows, all of these are around 55 degrees, except for MCP, which is around 60 degs. This makes me think that, in linux, if GFX 1 is at 60 degs, MCP must be roughly at 70! That must be the reason for the shutdown, since the pc only self-shutsdown on something it can sensor!

Now my question is: How can I fix this?
I also noted something funny. Even with this patch, I can't seem to find anything FAN related.

/proc/acpi/fan is empty. and dmesg | grep -i FAN doesn't show anything. But I can hear the FAN working. And with heavy load it works harder, but the air there is too HOT, it's as if it wasn't doing anything.

I am willing to do anything. But I would really like to fix this. It's becoming worse. Previously I managed to prevent crashes by keeping the gfx temperature below 70 ºC. Now it goes down whenever it is roughly above 65ºC, and I can't keep it below!

Thanks in advance:

Jorl17

---

### Post by zadehas on 2009-06-22
I have an Asus X50GL-AP042 laptop and had the same acpi issues with Ubuntu 9.04.

However, I simply solved them all by installing the 2.6.29-02062901 kernel from official precompiled .deb packages like these:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/")

I had no problems ever since and acpi controls work just fine.

As for the overheating, my GPU usually stays somewhere between 55 and 60 degrees Celsius, and CPU between 50 and 55. When running intensive applications, the GPU jumps to around 70 degrees, but the computer doesn't shutdown.

Unfortunately, it seems some nvidia mobile chips are prone to overheating, as Nvidia themeselves have admitted [http://www.engadget.com/2008/07/02/nvidia-says-significant-quantities-of-laptop-gpus-are-defectiv/]("http://www.engadget.com/2008/07/02/nvidia-says-significant-quantities-of-laptop-gpus-are-defectiv/").

If you have some patience left, I would suggest upgrading the kernel as pointed above.

---

### Post by jorl17 on 2009-06-22
Thanks for the reply.

Well, I fixed the ACPI issues, so they don't seem to be an issue by now. Could you please tell me if you see a FAN directory?

Your temperatures are similar to mine, adding a graularity of around 2 degs due to conditions over here (it's HOT in Portugal atm).

But these recurrent crashes upset me. What's even more strange is that only games tend to crash it. Day Of Defeat: Source, Red alert 3, Age of Empires III...

While compiling the kernel, the graphics card rounded the 73ºC and the CPU was around 75ºC, but it didn't crash. In fact, it was kind-of running smoothly.

Nor do my programming tasks make it crash (and I compile really big things).

So I also thought that it could be a harddrive crash. What is usually your temperature? I noticed that the place where the harddrive is is the one which conserves more heat (and it is always hotter), though it says it only rounds ~44ºC...

---

### Post by zadehas on 2009-06-23
I have an empty /proc/acpi/fan folder as well.

The hdd temperature is somewhere around 40ºC... I've seen it peak at 43-44ºC, but I think that's still within the limits.

I don't really play games, but as I said earlier, intensive cpu / gpu applications bring my gpu to 70-73ºC without crashing it.

I searched the BIOS and I found nothing about a temperature limit before shutting down.

So I guess you might be right about a hardware failure, but I think the video chipset is the main suspect.

---

### Post by Randojr on 2009-09-04
Okay i also have a problem with overheating with my asy¡us x50gl notebook overheating when I convert video or download something... so if you find a solution to the problem please tell me... I also dual boot my notebook with vista and version 8.04 of linux (Hardy Heron I think) but I haven't found a driver to connect to the internet trough wifi so if you know where I can download it that would be really helpful thank you ^^

---

### Post by jorl17 on 2009-11-12
Well, I fixed this quite some time ago. I didn't dig into it, though.

It seems that this is related to a feature in my kernel build which triggers overheating. (which is still the one here: [http://art.ubuntuforums.org/showpost.php?p=7497257&postcount=14](http://art.ubuntuforums.org/showpost.php?p=7497257&postcount=14) )

The default kernels which came with Ubuntu didn't overheat, but once I started using my own builds (and that includes kernels without the ACPI patch which I used in the aforementioned URL), overheating happened.

To be honest, I didn't really try to understand what I did, but I think that I disabled Interrupt Request Routing through ACPI. I added the line acpi=noirq to my kernel and voila!

There is one side effect which I notice (there may as well be others) -- the touchpad's dead. That makes sense, since its interrupts aren't being carried out and received through ACPI.

Still, I rarely ever need the touchpad and I prefer to know that I'm not going to overheat while playing.

I only posted this info because other people were having trouble :D

Cheers,

Jorl17

---

