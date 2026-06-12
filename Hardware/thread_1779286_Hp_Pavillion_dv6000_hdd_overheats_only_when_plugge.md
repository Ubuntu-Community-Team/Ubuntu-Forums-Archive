---
title: "Hp Pavillion dv6000 hdd overheats only when plugged into power"
date: 2011-06-10
forum: Hardware
---

### Post by eugenicist on 2011-06-10
Hello everybody, 

I've been looking around in the forum for a few months, but couldn't find a satisfying solution to my problem, then I decided to post my issue directly. When I use vista, there is no heating problem at all, but when I switch to ubuntu 10.10, it starts to overheat and it becomes kind of painful to type, when idle it's 55 C. The machine doesn't shut down itself, so it's not that critical but still very unpleasant. Recently I noticed that, when I unplug my laptop and use it only on battery power hdd temp goes down for even 10 C, which feels great. When idle, GPU temp is always app 55. As far as I understand hdd temp is the one making me stressed. It's a WD1600BEVT, with file system ext3, 1gb swap and 15 gb total volume. I need your help and opinions very much.
it's nice to join this forum.
thanks!

if there is something unclear, please ask!
I don't wanna use any other operating system

---

### Post by mdflynn on 2011-06-10
I have the same laptop and mine to can sometimes get really hot over the hard drive area (Although I can't remember it happening any time recent, say over a year now). I don't really have anything to compare it to myself because I haven't used windows on the laptop for about four years.

Do you notice the heat only when the battery is charging, or is it still noticable when you have been runnning of AC for a while? It could be that the battery is heating up while charging and causing the rest of the laptop to heat up.

Are you running any power management packages such as laptop-mode? what is the output of (as root) for both AC and battery power:

```
# hdparm -B /dev/sda
```

Replacing sda with the name of your hard drive.

Lowering the power usage of the hard drive should make it cooler, but will also affect the performance of the drive.

Another thing which will definitely affect the temperature of the laptop is the BIOS version, run this command and compare it against the latest firmware available from HP:

```
# dmidecode  | head
```

Other than that, I can't think of anything else that would be causing problems, the GPU and CPU sound like they are at reasonable temperatures, does the fan turn on properly, does it spin up when your computer is under a heavy load?

EDIT:

You could try some of the tips on this page which should lower the temperature of the drive. [http://www.lesswatts.org/tips/disks.php]("http://www.lesswatts.org/tips/disks.php")

---

### Post by eugenicist on 2011-06-11
Hey,
Thank you for your answer.

The hdd is hot when both the battery is charging or fully charged. Here is the output of the code you sent:
 APM_level    = 254

It seems that there is a newer release for the BIOS. I will try to install the newer version and let you know if it works for me. But do you think it may be the reason, because I don't have this problem on Vista. (I'm an average user, just guessing..)

By the way, yesterday, I removed 10.10 completely and installed 11.04 with the file system ext4 instead of ext3 to check if the temp would differ. ->Not really, hdd temp is still around 55C.

What I don't understand is why the temp increases only when the machine is plugged into power :S

And the fan sounds like it functions properly. It spins up when the temperature increases slightly. It works on like 'don't worry, everything is under control' mode, although I believe the temp is abnormal.

---

### Post by eugenicist on 2011-06-11
I didn't update the BIOS, because the newer release has only a fix for wireless adaptor which sound irrelevant to my problem.

But what i did was to check the APM level when it was on battery power and it appeared to be 128.
And the laptop-mode turns on, as well.

So because I don't have overheating issue when it is on battery power, do you think I should set the APM level to 128 and turn the laptop-mode permanently to overcome the problem. Can these cause new problems in the long term.

Thank you in advance!!

---

