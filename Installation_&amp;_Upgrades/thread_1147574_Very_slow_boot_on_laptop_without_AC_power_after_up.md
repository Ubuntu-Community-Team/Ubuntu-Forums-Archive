---
title: "Very slow boot on laptop without AC power after upgrading from 8.04 to 8.10 to 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by sananth on 2009-05-03
Hello all,

 I had 8.04 64-bit installed on my HP DV6748 via wubi, and did not want to upgrade to 8.10 (only wanted LTS releases on my laptop). However, I had to choose the 8.04->8.10->9.04 upgrade path, and now I notice via bootchart that its takes ~85 seconds to boot while not on AC power, and ~45 seconds with AC power. Vista seems to boot within 30 seconds, and I was really hoping to get rid of Vista for good once I heard about 9.04's boot times.

Can anyone help me out here? I can post my bootchart images if needed.

One strange thing I noticed is this (when running on battery power):
When booting, I saw that the progress bar had stopped. So, when I increased the volume using the hardware keys, the progress bar increased in perfect sync with my volume button presses.

---

### Post by luquiton on 2009-06-21
I am having the same exact problem on a fresh Jaunty install.

if i boot up on battery the bar will stop unless i press any key and keep on pressing it till it gets to the end, otherwise it will not boot.

also on battery it will not turn off.

thnaks for the help

---

### Post by jbaserga on 2009-06-22
Same issue with an HP Compaq Presario F700. It only proceeds with startup when pressing a key. Also when shutting down with battery it keeps waiting until it is plugged again. I upgraded from Hardy 8.04 to Jaunty, and in Hardy I never had a problem with this

---

### Post by palaciosora on 2009-07-01
same problem here in a hp laptop dv6500 upgrade from 8.04 > 8.10 > 9.04.

i used to worked fine with 8.04, so i dont know if i have done something wrong during the installation process, although i dont think so, cuz i only did what the system told me to do.

also the computer would not wake up from sleep mode does not matter if i have it pluged to the ac power or not

please i need help, giving that i need to move my computer in a regular basis.

thank you

---

### Post by eroeurbano on 2009-07-06
I have the same issue,
on battery mode my laptop only starts if I keep 
any button pressed..
Could you manage to fix it???

---

### Post by ecmatter on 2009-07-06
You could disable power management.

Applications > System > Services (in xubuntu.  I can't remember where it's located in ubuntu -- somewhere in the system menu would be my guess.)

---

### Post by sananth on 2009-07-06
> **ecmatter said:**
> You could disable power management.

Applications > System > Services (in xubuntu.  I can't remember where it's located in ubuntu -- somewhere in the system menu would be my guess.)

I tried to do what you suggested, but it did not work. I do feel that this is an issue with some kernel parameters at boot time, but, I haven't figured it out yet.

In ubuntu, this is option is under System > Administration > Services

---

### Post by eroeurbano on 2009-07-07
Hi thank you all firsto of all :)
I think the issue of bad "battery mode" management,
might be also the cause of Suspension, Hibernation not
working properly..

Anyway I don't want to disable power-management,
I just want to make it work :)
Is there a way to check ALL the parameters that are used?
Like, when I use battery, do you know if it reduces CPU power
to make the battery last longer and these kind of things?

---

### Post by jbaserga on 2009-07-07
Hi there!
well, after some (looong) investigation I managed to solve this. The issue is related with ACPI (the power management system) and the PC capabilities definition File called DSDT. Apparently HP compiles this DSDT with a Microsoft compiler which is not very strict to the standard, so the result is a "buggy" DSDT.

There are 2 solutions, one easy, just add acpi=noirq in the /boot/grub/menu.lst boot option. This a workaround for this problem, but I didn't test it 100% to be sure there is no collateral damage. I also found several variations to this as acpi=nohme, noacpi, but none of them was tested thoroughly.

The second solution goes to the root of the problem, so it makes your computer boot OK and also solves the suspension problem (you will still have to fix then wireless lan wake-up connection problem if you happen to have an Atheros card, but that's another thread and easily solved! ;) ). The solution involves re-compiling the DSDT file and overriding the original with this during boot. There is a very detailed Howto here: 

[http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")

After this I had no more problems during boot and suspend.

What bothers me of this bug is that in Hardy the machine booted OK with battery, so this "strictness" is rather new. To any Ubunbtu olympian god that may stumble into this, if we want Ubuntu to be used by everyone, this things must be taken into account, because the solution is not implementable by a newbie, least to say my mother. If you can't fix ACPI (in the end is part of the Linux Kernel!) at least you should take mesaures to have a package of "politically correct" DSDT (you can find them in acpi.org) that can be applied during installation. I honestly don't think HP will change its product policies for the 0,5 % of the systems sold.

Hope this ends your problems too!

---

### Post by eroeurbano on 2009-07-07
Thanks :)
I'll test it later at home..
I'm seriously concerned as well :)
Thanks a lot :)

---

### Post by eroeurbano on 2009-07-07
Thanks Jbaserga :)
it worked for me :)
I don't know exactly what i have done,
but now startup suspension and hibernation work well :D
Thanks a lot again :)

---

### Post by sananth on 2009-07-07
> **jbaserga said:**
> Hi there!
well, after some (looong) investigation I managed to solve this. The issue is related with ACPI (the power management system) and the PC capabilities definition File called DSDT. Apparently HP compiles this DSDT with a Microsoft compiler which is not very strict to the standard, so the result is a "buggy" DSDT.

There are 2 solutions, one easy, just add acpi=noirq in the /boot/grub/menu.lst boot option. This a workaround for this problem, but I didn't test it 100% to be sure there is no collateral damage. I also found several variations to this as acpi=nohme, noacpi, but none of them was tested thoroughly.

The second solution goes to the root of the problem, so it makes your computer boot OK and also solves the suspension problem (you will still have to fix then wireless lan wake-up connection problem if you happen to have an Atheros card, but that's another thread and easily solved! ;) ). The solution involves re-compiling the DSDT file and overriding the original with this during boot. There is a very detailed Howto here: 

[http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")

After this I had no more problems during boot and suspend.

What bothers me of this bug is that in Hardy the machine booted OK with battery, so this "strictness" is rather new. To any Ubunbtu olympian god that may stumble into this, if we want Ubuntu to be used by everyone, this things must be taken into account, because the solution is not implementable by a newbie, least to say my mother. If you can't fix ACPI (in the end is part of the Linux Kernel!) at least you should take mesaures to have a package of "politically correct" DSDT (you can find them in acpi.org) that can be applied during installation. I honestly don't think HP will change its product policies for the 0,5 % of the systems sold.

Hope this ends your problems too!

Thanks a lot jbaserga!

I implemented the permanent fix tha you suggested, and it fixed all my issues. I got 0 errors and 0 warnings after compilation. In case someone else is interested in fixing the compilation errors/warnings, and bringing them to zero, please follow the instructions here (on page 1 and page 2):

[http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html)

If you need some help fixing up the code, PM me.

---

### Post by rny629 on 2009-07-07
Hey JB.
I just happened to have the boot issue on my wife's. Did you get your DSDT from that link you provided? ([http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)) I got to the before point of no return and happened to get over 200 errors. Backtracked to read this post and noticed you where the one who happened to have the same issue and laptop Compaq f700.  Just got my Adidas wet again with UBUNTU.


Oh PS. I ran the command for showing the output and I get "Object does not exist." any IDEAS? I really am trying to understand this but its overwhelming to say the least.

---

### Post by jbaserga on 2009-07-08
rny629, I got your private, but here I can attach my DSDT. If yours is not an F700, or in doubt I suggest to run a diff against your original DSDT, make changes, compile and check if it is OK.

Also you can check sananth's post for an URL to assist in correcting errors.

Hope this is the last time you ruin your Adidas :p . You must have already learned not to tamper with the Authority's computer!

---

### Post by jvijayv on 2009-07-12
This dsdt file worked fine on my compaq F700 laptop. Thanks for uploading it. I can boot up without having to press some key or connecting the ac power supply.

Thanks once again!

---

