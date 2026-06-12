---
title: "Computer restarts automatically"
date: 2011-09-03
forum: Hardware
---

### Post by tech291083 on 2011-09-03
Hi,

I have Ubuntu 10.10 installed as the only OS on the hard disk. The pc worked well until this morning when it just started restarting itself every few seconds for no apparent reason. There is no virus etc problem. It restarts itself automatically once I power it on. Can't figure out the problem, please help. I am sure it is not a software issue. When it restarts there is American Megatrends screen and there is a message on this screen which goes - 

```
Warning ! over clock fail
```I have never changed anything in the BIOS and I have never even dreamed of over-clocking if this is what this error message means. I do not even know how to overclock. The motherboard is Biostar G31-M7 TE and BIOS is from AMIBIOS ie American Megatrends.

Please help. The pc is almost new like. Thanks.

---

### Post by lmarmisa on 2011-09-03
This seems a problem related to the BIOS setup. Try to enter your BIOS menu and select an option similar to Load Optimal Defaults or Load Failsafe Defaults.

[The CMOS battery]("http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory") could be the cause of the problem too, but you say that the computer is quite new.

---

### Post by tech291083 on 2011-09-03
Yes, I have just selected the saved the Load Optimal Defaults in the BIOS and the pc now reboots itself only after a few minutes instead of few seconds, so the situation has improved a bit but the automatic rebooting continues.

Attached to this post are some of the screenshots of a software called CPU-Z, it is a tool that gives you some info about the cpu. These were taken just a couple of days ago when there was also Windows XP Pro installed and the system/pc was was a dual-boot one with Ubuntu as the second OS. But I have installed and re-installed both Ubuntu and Windows so many times on the pc only and there has never been a problem like this. Please help. Thanks.

---

### Post by lmarmisa on 2011-09-03
Try to boot into an Ubuntu Live CD / USB and check if the system is stable in this case.

---

### Post by tech291083 on 2011-09-03
> **lmarmisa said:**
> Try to boot into an Ubuntu Live CD / USB and check if the system is stable in this case.


Yes, tried Ubuntu CD and booted off it and tried Ubuntu (did not install it, just tried it as there is an option called Try Ubuntu), but after a few minutes the same problem ie it restarts for no reason.

---

### Post by lmarmisa on 2011-09-03
Disconnect the power plug and remove the CMOS battery during some minutes.

Then insert the battery again and connect the power.

Enter the BIOS menu and select a more conservative option than Load Optimal Defaults. Try Load Failsafe Defaults better.

[URL="http://www.dewassoc.com/support/bios/bios_password.htm"]http://www.computerhope.com/issues/ch000976.htm
[/URL]

---

### Post by tech291083 on 2011-09-09
> **lmarmisa said:**
> Disconnect the power plug and remove the CMOS battery during some minutes.

Then insert the battery again and connect the power. 

Enter the BIOS menu and select a more conservative option than Load Optimal Defaults. Try Load Failsafe Defaults better.[URL="http://www.dewassoc.com/support/bios/bios_password.htm"]
[/URL]

Thanks a lot Imarmisa, it worked and the pc is working well now, without any problems.

---

### Post by lmarmisa on 2011-09-09
Great!.

Please, mark the thread as SOLVED (look at Thread Tools).

---

### Post by tech291083 on 2011-09-09
Hi,

A new problem has started now, whenever I power up the pc the cpu fan starts, the power supply fan starts (I guess power supply/PSU is working fine), but there are no LED lights on the front of the case and there is nothing on the screen. Can you please help. The pc is hardly 1 yr old.  Thanks.

---

### Post by tech291083 on 2011-09-15
Please help me. I have Windows XP and Ubuntu installed on the system. Dual boot. Is there any utility that I can download from the net and write to a CD to make it bootable? Is there some way I can boot my pc? Thanks

---

### Post by msandoy on 2011-09-15
> **tech291083 said:**
> Hi,

A new problem has started now, whenever I power up the pc the cpu fan starts, the power supply fan starts (I guess power supply/PSU is working fine), but there are no LED lights on the front of the case and there is nothing on the screen. Can you please help. The pc is hardly 1 yr old.  Thanks.

The problems described in this thread, really sounds like a dying power supply. Try to test with a different one if you have one at hand.

---

### Post by diasf on 2011-09-15
Try a live CD. If that doesn't boot, hardware problems -> maintenance

---

### Post by lmarmisa on 2011-09-15
> **tech291083 said:**
> Please help me. I have Windows XP and Ubuntu installed on the system. Dual boot. Is there any utility that I can download from the net and write to a CD to make it bootable? Is there some way I can boot my pc? Thanks

Try to boot into an Ubuntu Live CD / USB.

---

### Post by tech291083 on 2011-09-16
I tried a new power supply, but to no avail the pc still does not boot. Tried my power supply in a different pc and it works well on that pc. So I guess it is not about to die. The LED light is working properly now. CPU fan works fine when I power up the pc and so does the power fan. I did try to boot with Ubuntu and Windows CDs but still the problem continues. Can you please help me out? Thanks

---

### Post by msandoy on 2011-09-16
Ok, you have tried another power supply, and you have tried to boot from a live cd. Please give us a bit more info on the actual symptoms, like, when you push the power button, is the screen coming on? Is the preboot information on the screen normal? Since you have a dual boot system, is the GRUB menu showing? If some of the above mentioned things does not happen, what is on the screen? If the screen is black when it stops reacting, has anything been shown on the screen before it went black?

Just small things like that might help in a diagnose.

---

### Post by tech291083 on 2011-09-16
> **msandoy said:**
> Is the screen coming on? Is the preboot information on the screen normal? Since you have a dual boot system, is the GRUB menu showing? If some of the above mentioned things does not happen, what is on the screen? If the screen is black when it stops reacting, has anything been shown on the screen before it went black?



There is nothing coming on the screen. No GRUB menu nothing at all, totally blank, but then I have already tried the monitor on another pc and it works very well. So I guess the screen is perfect. Thanks a lot for trying to help me, appreciated.

---

### Post by msandoy on 2011-09-16
Have you installed a separate graphics card, or are you using the built in Intel graphics?
By the way, when you switch it on, does the hard drive light flicker, indicating activity?

---

### Post by tech291083 on 2011-09-17
> **msandoy said:**
> Have you installed a separate graphics card, or are you using the built in Intel graphics?
By the way, when you switch it on, does the hard drive light flicker, indicating activity?

Hi, I have not tried to install a graphics card, just using the onboard one. I am not much into gaming etc. Yes, the hard drive light flickers. Thanks

---

### Post by msandoy on 2011-09-20
> **tech291083 said:**
> There is nothing coming on the screen. No GRUB menu nothing at all, totally blank, but then I have already tried the monitor on another pc and it works very well. So I guess the screen is perfect. Thanks a lot for trying to help me, appreciated.

This and the flickering of the hard drive light might indicate a problem with your onboard graphics card. You haven't indicated if you have the usual sound when the system reaches the login screen.

---

### Post by tech291083 on 2011-09-20
> **msandoy said:**
>  You haven't indicated if you have the usual sound when the system reaches the login screen.

The system does not reach the login screen at all, it stays totally blank, thanks. I am not sure which sound you are talking about. but if you are talking about the sound that is played when Windows boots, then it is perfect, but I have not set the start up sound for Linux. Thanks.

---

