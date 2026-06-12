---
title: "Suspend only works once"
date: 2011-05-08
forum: Hardware
---

### Post by konradsa on 2011-05-08
Hi,

I had this problem now since 10.10, and I was hoping it would go away in Natty, but it didn't.

In short: Suspend only works once, the second attempt at a suspend results in the monitor going blank as it was entering suspend, but the computer still running, as evidenced by the hard drive and fans still running. The computer can then not be awaken anymore, only a hard reset and subsequent reboot returns the PC to working state.

When I check for errors after the first suspend, I see the following errors in the log:
```

[ 8461.100062] ahci 0000:05:00.0: failed to stop engine (-5)
[ 8461.600062] ahci 0000:05:00.0: failed to stop engine (-5)
[ 8463.170076] ata9: failed to resume link (SControl FFFFFFFF)
[ 8463.170109] ata10: failed to resume link (SControl FFFFFFFF)
[ 8467.510109] ata9: failed to resume link (SControl FFFFFFFF)
[ 8467.510163] ata10: failed to resume link (SControl FFFFFFFF)

```

So it seems to me that it has something to do with AHCI. I searched for this error in the forum, but I could not find anything. I also tried various suggestions, such as using uswsusp and the hibernate scripts, and including ahci in the suspend module lust. But each of the result in the exact same behavior: First suspend works fine, second suspend fails and reset is necessary.

My detailed HW information is attached to his post.

In short, I got:
- AMD Phenom II 965
- GeForce GTX 460
- GA-880GA-UD3H
- 8 GB DDR RAM
- SAMSUNG HD103SJ

Thanks!
Sascha

---

### Post by konradsa on 2011-05-08
FYI, I tried some more things to see if I can nail down the source of the problem. I turned of AHCI in the BIOS and set the controller to plain IDE mode. But that did not make any difference.

I also tried to remove the Nvidia 3rd party driver and tried it just with the default driver. But with the default Ubuntu driver, the PC already fails to resume from the first suspend.

So no progress really.

---

### Post by konradsa on 2011-05-09
Nobody has any ideas? Am I the only one with this problem, or do other people have it also, but just don't know what to do about it?

Maybe I should open a bug report?

---

### Post by konradsa on 2011-05-12
Bug report filed: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/781977]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/781977")

---

### Post by aminalid on 2011-07-02
Have the same problem here...
Suspend works only once, but Hibernate works fine.

Ubuntu maverick
Processor: AMD Athlon X2
MB: Asus A8N-E

---

### Post by kswix on 2011-11-15
Same problem.

---

### Post by northd_tech on 2011-11-15
I posted some diagnostic commands to try at my post #21 here:

[http://ubuntuforums.org/showpost.php?p=11460223&postcount=21](http://ubuntuforums.org/showpost.php?p=11460223&postcount=21)

It would probably be best to split out the **different** graphics card manufacturers with Suspend problems onto different or new threads (I think I had the problem with the older NVIDIA 173 and 195? driver modules, and updating it to the newer NVIDIA 285.05.09 driver module seems to have fixed my suspend, I think).

Of course, checking your Screen Saver and power settings and installed packages is a good idea too:

```
 dpkg -l powe*
dpkg -l acp*
dpkg -l susp*
dpkg -l hiber*

```

---

### Post by gdea73 on 2012-02-26
Precisely the same problem. Wish this could be fixed.

---

### Post by gcbzzzz on 2013-02-26
> **gdea73 said:**
> Precisely the same problem. Wish this could be fixed.

I worked around it disabling my ethernet. it was the device that was failing to suspend in my case. (you can disable the device in the bios*)

Also, DO go to the bug reporter linked up in this thread and mark that the bug affects you! it's the least you can do :)


* side not on my BIOS... i whish everyone at Asus involved in it's design to !*%&(@*#$&@(*#$&@^%@*(#&$@#&$(*@#&$(*@&$

they call UEFI Legacy mode as simply:
"CSM"
...  which after searching the spec i learned stands for "Compatibility Support Module". and the help screen  helpfully says "Enable CSM" with some 7 lines of unused space. ...did someone get paid to write those BIOS help messages?

then instead of showing enable/disable for the onboard devices, they hid it into safeboot, and called it "locked/unlocked". I was pretty sure it was to restrict access to network booting like XPE or something. not to enable/disable the devices. of course, the help message said "lock or unlockd the device"... genius.

man, those people are just a bunch of *&@*(@&(*@&#$(*@&#$ sadists!

---

### Post by KoudelkaB on 2013-03-26
I solved this problem by adding kernel parametr to grub bootloader: **[FONT=Arial]acpi_sleep=old_ordering[/FONT]**

---

