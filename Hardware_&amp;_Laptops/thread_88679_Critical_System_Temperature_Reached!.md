---
title: "Critical System Temperature Reached!"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by uby on 2005-11-10
I have a gateway solo laptop with ubuntu installed. I just got everthing fix and working...now it says after the boot process "critcal system temperature reached 144C". I searched for some threads on this and found that you have to disable apci but I don't know how to do that. Any ideas??

---

### Post by mhancoc7 on 2005-11-10
I have had the same issue with my Compaq Armada 1750. Here is a simple way to disable ACPI.

1. Open a terminal window (System Tools - Terminal).
2. sudo gedit /boot/grub/menu.lst
3. add the following to your kernel line
    noacpi acpi=off
4. Save and Reboot

Be sure to be careful since you are editing your grub menu.

God Bless, Jereme

---

### Post by ssam on 2005-11-11
after changing the file you should run
```
sudo update-grub
```
to write the changes to the master boot record (mbr)

---

### Post by mhancoc7 on 2005-11-11
Thanks, I knew that I was forgetting a step.

Now that I think about it though, I have not run update-grub the last few times that I made changes to my menu.lst. The changes "stick" after a reboot. 

Jereme

---

### Post by slux on 2005-11-11
Grub doesn't really need update-grub to function and your modifications will take effect without running it. update-grub doesn't modify the MBR, it just automatically keeps all installed kernels in the menu.lst. Grub doesn't need to modify the MBR after every tiny change like LILO.

If I understand things correctly, update-grub might kill your special options when it's run automatically at some point if they're inside the automatic configuration list section in menu.lst though.

---

### Post by uby on 2005-11-12
All this sounds good but I can't get the laptop to boot.  Is there a way to change that setting without opening a terminal window?

---

### Post by mhancoc7 on 2005-11-12
You can edit the kernel line at boot up for that particular session. When you start the laptop watch the screen close. When the grub menu pops up press the e key. You can then select your kernel line and add noacpi acpi=off to it. Then hit enter to accept the change and then b to boot. Now your computer should boot with acpi off. If all goes well you can open the terminal and make the change permanent.

I hope this helps. If you have any questions just let me know.

God Bless, Jereme

---

### Post by r0ll3r on 2005-11-15
Turning ACPI off will solve your critical temperature errors, but not the problem. You could also check how to set the critical temperature in /proc/acpi. Maybe your acpi is badly programmed as mine. If this is the case, you will need to look at the other threads here, look for ACPI, DSDT, iasl keywords. Also here is a fine acpi documentation:[http://acpi.sf.net/]("http://acpi.sf.net/")

---

### Post by mhancoc7 on 2005-11-15
You may be right. All I know is that I added 'noacpi acpi=off apm=off' to my kernel line and now my laptop runs cool as a cucumber. The fan turns on when the laptop gets warm and then off when it cools down. Suspend also works great! That is just my experience with a Compaq Armada 1750 running Hoary.

God Bless, Jereme

---

### Post by nim278 on 2005-11-17
What are all the tradeoffs involved? I know for one, the battery status applet doesn't work in GNOME.

I am getting the same problem (though much higher values sometimes, I've hit as high as over 5000 degrees Celcius!) on my laptop after installing Breezy. Everything actually worked great under Hoary and under Breezy development the swich was made to the 2.6.12 kernel from 2.6.10. 

I feel a little uneasy trying to change my threshholds to such ridiculous numbers, as wouldn't this affect the fan speed controls? I wouldn't really know where to start -- set the shutdown at 10,000 degree? And how exactly would I go about doing this?

Any Thoughts?

Cheers,
Maciej

---

### Post by mhancoc7 on 2005-11-17
I am running Hoary with the Kubuntu package on a Compaq Armada 1750. I added 'noacpi acpi=off apm=off' to my kernel line. The kernel that I am using is a win4lin enabled kernel that I found on the forum. It is an i686 2.6.10 patched for win4lin. You can get it here if you are interested [http://ubuntuforums.org/showpost.php?p=245428&postcount=6](http://ubuntuforums.org/showpost.php?p=245428&postcount=6)[http://ubuntuforums.org/showpost.php?p=245428&postcount=6]("http://ubuntuforums.org/showpost.php?p=245428&postcount=6").

My battery status applet works fine in Ubuntu 5.4 and Kubuntu 5.4. The only thing that I have found that doesn't work is the temperature monitor applets.

But the best thing is that my laptop runs nice and cool. The fan comes on as needed and goes off when the laptop cools down.

Hope that helps.

God Bless, Jereme

---

### Post by nim278 on 2005-11-17
I had no problems with the original Hoary kernel, but Breezy uses the 2.6.12 kernel, and I prefer to think that one should upgrade to fix problems rather than downgrade :). Ideally, I'd like to figure out how to get to the bottom of this. What is causing this to happen? Clearly my laptop is not hotter than the surface of the sun.....

---

### Post by mhancoc7 on 2005-11-17
Oh I see. Yeah that makes good sense. I had considered ugrading to Breezy, but I keep hearing about people having so much trouble. I am going to stay with Hoary for now. I wish you luck in getting your issue solved.
God Bless, Jereme

---

### Post by nim278 on 2005-11-25
Well, it looks like I solved the problem! I did two things, the first I don't know if it was necessary (but it certainly didn't hurt), and the 2nd was a pleasant byproduct of the first (assembly code is fun!).

[LIST=1]
[*] Looked for a DSDT table on [http://acpi.sourceforge.net]("http://acpi.sourceforge.net") for my laptop, but no success -- it's a very small brand name (Eurocom).

[*] Followed the instructions on [https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29]("https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29") for copying, disassembling, editing and recompiling the DSDT table, and then reconfiguring the kernel to use it. My errors were, of course, very different, though I did fix all 4 of them, some with intuition, some with help from [http://forums.gentoo.org/viewtopic.php?t=122145]("http://forums.gentoo.org/viewtopic.php?t=122145")  and [http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt]("http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt") on the actual .ASL debugging.

[*] This did not solve the problem, though it seemed to make things run smoother anyways. Then I realized that the Gentoo Forums link about there had a section I never got to: "10. My DSDT is fixed, but I still have ACPI errors. Now what?" I looked for "_OS" and sure enough, there were some names being set based on "_OS", which were later used in a large chunk of the code, including the actions of the Thermal module. Rather than trying to understand what it was doing for each version of Windows and why they were all so different, I simply tried this kernel parameter suggested ```
acpi_os_name="Microsoft Windows XP"
```and rebooted. Worked like a charm!! I wish I had run across this earlier in a less cryptic place. I have a feeling this could help a lot of the people currently having problems and turning their acpi=off instead.
[/LIST]
I'll be happy to try to help anyone who needs it. Just holler!

Maciej

---

### Post by mhancoc7 on 2005-11-26
Thanks for the update and tip, Maciej. I am testing it now and so far it seems to be working. I really hope so. I never really liked turning off ACPI. Now maybe I can use the temperature monitor.
God Bless, Jereme

---

