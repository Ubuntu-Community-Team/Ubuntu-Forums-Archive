---
title: "[SOLVED] Huh? Restarting after shutdown?"
date: 2008-10-02
forum: Hardware
---

### Post by Narc0tiq on 2008-10-02
Hi, guys,

Here's an interesting one for you: after I select the "Shut down" option in the interface and everything goes down successfully, the system stays off for about 2 seconds, and then powers on again.

I've seen this before on a co-worker's computer running Windows, whereby the only way to completely power off the system was to unplug it, however this doesn't seem to be the case here -- if I hit the power button while the BIOS is running through its POST (thus, before Ubuntu has a chance to touch it), the computer stays off.

I've also found a *lot* of threads on these forums (fora?) about shutdown/power management problems, but none of these seem to describe my symptoms, and a lot of them are referencing pre-Hardy versions of Ubuntu.

The OS in this case is a fresh(ish) installation of Hardy, with updates installed.


I can't currently fetch any hardware information about the computer, as it belongs to my mother and she is sleeping at the moment, however I would like anyone who has any thoughts on what may be causing this to chime in. I will update the thread with hardware information as soon as I can get it.


So, has anyone experienced this before? Does it sound like a broken ACPI implementation, maybe?

I intend to check dmesg as soon as I can (I know, I came unprepared and I apologize, but at the moment it was more important to just get the computer shut down, so I didn't really get a chance to grab it), and grep for anything about ACPI or APM, and will report back with that data, as well.


And thanks in advance for anything you can offer, and for your time.

Update: Issue was resolved, see post #5. It was /proc/acpi/alarm with a weird setting.

---

### Post by Narc0tiq on 2008-10-03
More data:

The motherboard is a 2004-ish Intel model; the CPU is a Pentium 4 with HyperThreading (if I recall correctly). Power supply is a brand new Corsair 450W unit.

dmesg|grep -i 'acpi' doesn't result in anything interesting, and dmesg|grep -i 'apm' shows (correctly) that APM is disabled from the BIOS.

If anyone wants, I'm willing to post any further potentially helpful data -- me, I'm stumped at this point.

---

### Post by cariboo on 2008-10-03
You may have a setting in the bios that is causing the computer to restart. Check the after power loss setting, it could be set to automagically restart. I've seen it happen on various motherboards.

Jim

---

### Post by Narc0tiq on 2008-10-03
> **cariboo907 said:**
> You may have a setting in the bios that is causing the computer to restart. Check the after power loss setting, it could be set to automagically restart. I've seen it happen on various motherboards.

I thought of that, but it's set to stay off after power loss.

With that said, I do have a different computer that's set to come back up after power loss, yet never does, but I couldn't diagnose that anyway. That does give me a good idea, though: I should look for any BIOS updates for the motherboard -- maybe one of them fixes this.

Thanks! Any other input will also be appreciated.

---

### Post by Narc0tiq on 2008-10-06
More extremely interesting data: after finally opening the case to find the motherboard maker and model, it turned out to be an MSI 865PE Neo2, mentioned also in [Launchpad bug #253629](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253629), which describes a very similar problem.

One major difference is the BIOS version -- my BIOS is v2.5 and the one in the bug is v6.1 (!). The difference is thanks to MSI, who are to be commended for pursuing user confusion to the level of *giving the same name to about four different motherboards*, with completely different BIOS capabilities. Mine does not support BIOS revisions higher than v2.x, and 2.5 is the highest on the list. Still, that might explain the difference in behavior for what might be the same bug (and if it is, Intrepid (or the 2.6.27 kernel) will probably fix it, according to the bug report mentioned above).

On the bright side, having more data, I can now continue digging around the Web for more options. Ultimately, I'll probably decide on the simplest solutions: toggling the power button on the power supply, or letting the system run forever. Either one should work.

Edit to add: SUCCESS! And solution: My /proc/acpi/alarm was reading '2008-10-** **:**:**' (just like that, with asterisks(!)), which apparently made the BIOS trigger RTC wakeup events every second (!!!) -- explaining the observed behavior of the system. echoing '2008-00-00 00:00:00' into the file resulted in a content of '2008-10-00 00:00:00', and the system shut down and finally stayed down as it was supposed to.

The final, not very important, question remaining is what was writing that value into /proc/acpi/alarm and why? I certainly didn't write it in (I didn't even know the file existed until I found it mentioned in my searches).

---

### Post by ba$il on 2008-10-17
Hi Narc0tiq,
you'll have to excuse my ignorance, newbie to Linux/ubuntu :-) .
I have exact same problem. Ubuntu Hardy Heron 8.04, machine restarts after every shutdown. Machine did not have problem before updates downloaded and installed. Now it's driving me crazy.
I've looked in /proc/acpi/alarm and found 2008-10-00 **.**.**
How do I change it to 2008-10-00 **.**.**  ?
I found that if editor used, nothing displayed in this file.
If OpenOffice.org Writer used to open file, I can see the problem,
but the alarm file is read only, and I can't change.
How did you "echo" the correct value in ????
Cheers,
ba$il

---

### Post by NWSmart on 2008-10-17
Hi,

Not sure about posting to a [SOLVED] thread but I have exactly the same problem that has only started since I did a system update day before yesterday. I am using Hardy and it is a recent install (I am a NOOB and very recent convert to Ubuntu and Linux in general)

How do I get to the file in question and how to I edit it to read correctly and, hopefully, make my problem go away?

TIA for any help

---

### Post by tarps87 on 2008-10-17
Correction, this is a better way
```
echo "2008-00-00 00:00:00" > /proc/acpi/alarm
```
You may need to be root so:
```
sudo echo "2008-00-00 00:00:00" > /proc/acpi/alarm
```
and 
```
cat /proc/acpi/alarm
```
Should show what it is set to

---

### Post by Narc0tiq on 2008-10-17
> **tarps87 said:**
> **[...]**You may need to be root so:
```
sudo echo "2008-00-00 00:00:00" > /proc/acpi/alarm
```**[...]**

I thought that would work, too, but it doesn't, presumably because of trying to write the output of sudo into the file using a non-privileged shell. Instead I did it like this:
```
narc@athena:~$ sudo -i
[sudo] password for narc: 
root@athena:~# echo '0000-00-00 00:00:00' >/proc/acpi/alarm
root@athena:~# cat /proc/acpi/alarm
2008-10-00 00:00:00
```

and that cured it, sort of. Apparently, it still doesn't always shut down on the first try, but the second time's always a charm. My guess is that's related to the specific motherboard in question, and a kernel upgrade will probably fix it later. Still, it's not a big deal for me, so I haven't researched it any further.

---

### Post by tarps87 on 2008-10-17
Strange, another solution might be to turn off wakeup/wakeon events off in the bios. /proc/acpi/alarm is suppose to be removed in Intrepid.
One of the programs that uses it is myth tv so if you use it, this may have been what edited the alarm.

---

### Post by Narc0tiq on 2008-10-17
> **tarps87 said:**
> Strange, another solution might be to turn off wakeup/wakeon events off in the bios.
Agreed it's strange, but apparently it's a BIOS bug in the MSI 865PE Neo2 that makes the ACPI implementation in the kernel think the RTC wakeup is turned on even when it's off. The Launchpad bug I linked earlier shows this on a different version of the same motherboard.


> **tarps87 said:**
> /proc/acpi/alarm is suppose to be removed in Intrepid.
Aye, kernels from 2.6.22 upwards are supposed to implement /sys/class/rtc/rtc0/wakealarm instead, but the Ubuntu generic kernel current for Hardy doesn't, which is why we still have the /proc version.


> **tarps87 said:**
> One of the programs that uses it is myth tv so if you use it, this may have been what edited the alarm.
I noted the connection since most Google search results referred to it, but I don't have and don't use MythTV, so no joy there, either. It's just weird, honestly, and while it bugs me, it's not worth tracking down, given my lack of experience.

---

### Post by ba$il on 2008-10-17
Well done guys,
Thanx to Narc0tiq and Tarps87 for their responses.
Narc0tiq, you are correct.
The trick is to get into root before trying to issue the command.

---

### Post by NWSmart on 2008-10-19
Narc0tiq - Thanks for the advice - tried it and it seemed to work for me so again thanks!

---

