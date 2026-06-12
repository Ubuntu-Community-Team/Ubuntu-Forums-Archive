---
title: "OS freezes randomly on the new PC"
date: 2012-06-18
forum: Hardware
---

### Post by denis.zhdanov on 2012-06-18
Hello,

I've bought a new PC and observe sporadic problems which are yet really annoying. Tried to solve it but have no luck so far. Hope someone can show me right direction to diagnose the problem.

So, the 'bad thing' is that my OS sometimes just freezes - mouse is not moved, keyboard doesn't react (event LED button don't toogle). Hard reset button also doesn't react, the only way to go out of that is to perform hard shut down (push the button on the case).

I observe the problem under Windows installed at the same machine (other HDD), so, it looks as a hardware problem that is triggered by some condition.

What I've tried:
[LIST=1]
[*]Executed [memtest]("http://www.memtest.org/") - no problems have been detected;
[*]Executed [aida64]("http://www.aida64.com/") system stability test - the system hangs sometimes after ~50 min. No errors have been found at the aida logs and event viewer after the reboot;
[*] Tried to use not the latest nvidia drivers (the freezes still present);
[*] Installed [hardware monitor sensors]("http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/") and configured alarm condition on 80 °C - no alarm has been triggered when the system locked;
[*] checked log files under /var/log after the lookup and subsequent reboot - haven't found any mentioning about the problem;
[/LIST]

The problem seems to be related to the video subsystem because it started after I had installed nvidia drivers. It occurs sporadically, e.g. on Alt+Tab or browsing (especially flash-rich pages).

System info:

Hardware:
[LIST]
[*]cpu - core i7 3930;
[*]motherboard - asus rampage iv forumula (default bios settings, assembled at the shop);
[*]ram - 16gb Kingston KHX1866C9D3T1BK2/8GX;
[*] video cards - two GTX 570 (connected via SLI bridge but the SLI itself is not configured under ubuntu. It's active under Windows but the problem persists there as well);
[/LIST]

Software:
[LIST]
[*]OS - Release 12.04 (precise) 64-bit, Kernel Linux 3.2.0-25-generic, GNOME 3.4.1;
[*]nvidia drivers - 295.59;
[/LIST]

The biggest problem for now is that I'm unable to identify what system component is faulty, hence, can't change it. I'm asking for an advice on what else can be used to identify it. May be there are some specific system logs that might contain information about the occurred problem (I work with Ubuntu mostly as an ordinary user)?

Denis

---

### Post by ahallubuntu on 2012-06-18
It doesn't make sense that it would be a driver problem if you see the problem both in Windows and in Linux.  Could be a hardware issue.

Can you rule out the video cards by removing one or both of them and trying it temporarily that way?  If the motherboard doesn't have onboard video, then try one card at a time.

What kind of power supply is it?  Known good?  Tested?  If it's older or potentially underpowered, that could be the problem.

An overheating issue would be worse after the first freeze up - that is, when cool it would take longer to freeze than subsequently if you keep re-starting.  If you don't detect any pattern like this, it's probably NOT an overheat issue.  Blowing a fan into an open case to keep it a little cooler and seeing if that changes anything is another way to rule out heat.  Or, finding a way to monitor temperature (of the CPU and the GPUs) would be helpful.

---

### Post by denis.zhdanov on 2012-06-19
Thanks for the reply. Agree, it makes sense to try video cards one by one, will do.

Regarding overheating - I doubt that is the cause. As I've written, I tried to work with temperature sensors enabled and they didn't show any problem. The problem occurs under the cold system as well, e.g. I've experienced it just after the first boot in the morning.

Denis

---

### Post by denis.zhdanov on 2012-06-20
Tried all video card PCI-E slot combinations and ensured that the system hangs in every of them. Other ideas? :)

Denis

---

### Post by zSeries on 2012-06-20
Hi,
I have just spent two days intalling and re-installing 12.04 on a two year old PC thats been running 10.04 LTS with no problems what so ever. With 12.04 I keep getting random hangs, the only thing that works is the mouse and pointer. It has crashed before I get the sign on prompt, it crashes while typing mkdir commands in terminal. Firefox freezes and I cant even close the windows. I typically get no more than 1 or 2 mins usage without a problem then it locks up. I have tried to install drivers for my ATI by its crashed 3 times typing in commands. I have simply lost the will to continue and will stay on 10.04.
My system is a Gigabyte GA-MA785GM-US2H.  AMD II X4 600e. 2GB RAM. 2TB+1.5TB HDD.
My suggestion is install 10.04 and see if it works. You dont have to stick with it but if it does work you can be sure there nothing fundamentally wrong with your hardware.
Good luck!

---

### Post by ahallubuntu on 2012-06-20
What kind of power supply do you have?  Specs?  How new is it?

---

### Post by ahallubuntu on 2012-06-20
The original poster has the same issue in Windows, so it's probably not related to 12.04 specifically.  Trying 10.04 probably wouldn't hurt, though.

> **zSeries said:**
> Hi,
I have just spent two days intalling and re-installing 12.04 on a two year old PC thats been running 10.04 LTS with no problems what so ever. With 12.04 I keep getting random hangs, the only thing that works is the mouse and pointer. It has crashed before I get the sign on prompt, it crashes while typing mkdir commands in terminal. Firefox freezes and I cant even close the windows. I typically get no more than 1 or 2 mins usage without a problem then it locks up. I have tried to install drivers for my ATI by its crashed 3 times typing in commands. I have simply lost the will to continue and will stay on 10.04.
My system is a Gigabyte GA-MA785GM-US2H.  AMD II X4 600e. 2GB RAM. 2TB+1.5TB HDD.
My suggestion is install 10.04 and see if it works. You dont have to stick with it but if it does work you can be sure there nothing fundamentally wrong with your hardware.
Good luck!

---

