---
title: "CPU noise"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by brettr on 2006-04-30
Hey, Just recently switched over to ubuntu Dapper, from XP. So far everything is awesome, pretty much everything is working.

I just have been noticing that there is a little high picted noise comming from where the fan and CPU is. I have an Dell Inspiron 6000, just to clarify. It isn't a loud noise, but if i put my ear near the keyboard i can hear it. The thing is i just never noticed it before while running windows. I could be just paranoid... but i really don't think it was there before. 

So, does anyone think i should worry about this.. or is there some way to check if there are any serious problems... I would really hate for it to get damaged somehow...


Also Second thing is... The laptop hibernates fine while on AC power.. but when running on battery power it hangs with a blank screen and the HD activity light on. Any ideas?

---

### Post by brettr on 2006-05-01
Nobody has any ideas?

---

### Post by confused57 on 2006-05-01
I have a Dell Dimension 4550 and noticed a high pitched noise(whine) a year or 2 ago on it.  Dell support said it was coming from the fan(s) & was normal, yours may or may not be the same noise I'm hearing from my pc.

---

### Post by musther on 2006-05-01
A friend of mine has a Dell laptop, I introduced her to Ubuntu and now she uses it, that laptop too makes an odd sound (some kind of fan noise), but only at certain times.  Again, it didn't seem to make the noise in windows, and in this case seemed to make the noise when there was high network traffic.  To be honest I wouldn't worry about it, but that's me.

---

### Post by [S|G] on 2006-05-01
The CPU should make no noise whatsoever under any circumstances (unless it is seriously broken), so your problem is probably a defective cooling fan. You could try to change it if possible.

---

### Post by cykze on 2006-05-01
Pass the following parameters to the kernel:

**pci=bios idle=halt acpi_sleep=s3_bios**

It works perfectly on my Inspiron 6000. I think I got the tip from this forum.

You could do like this if you're using Grub:

1. sudo gedit /boot/grub/menu.lst
2. Find the line starting with **# kopt**
3. Add **pci=bios idle=halt acpi_sleep=s3_bios** to the end of the line.

On my system the line now looks like this:
**# kopt=root=/dev/sda2 ro pci=bios idle=halt acpi_sleep=s3_bios**

4. sudo update-grub
5. Restart, and the high pitched noise is hopefully gone!

---

### Post by brettr on 2006-05-02
Interesting, what does that command do?

And also wouldn't that do nothing because it is commented out?

---

### Post by cykze on 2006-05-02
Frankly, I don't know what it does. But the irritating noise goes away, and that's enough for me. :)

Normally a line that's commented out is treated as a comment, but not in this case. The command is used by update-grub to generate/update the menu.lst file.

---

### Post by brettr on 2006-05-02
Ah, I see.. wel you are right though the noise appears to have stopped. Thanks for the help

---

### Post by Lady Ea on 2006-05-09
I have a Dell D610, which made a high pitch noise. The Dell help desk said it is a known problem, that the CPU makes this noise when not at 100%. (It is called piezoelectricity, and is the same phenomenon that occurs in certain lamps when you reduce their luminosity.) Easy! Just force the CPU to be at maximum all the time. (The help desk said I should activate the Blue tooth, it works when on windows and provided that you have blue tooth :-?  ) In Ubuntu (Dapper) you fix it like this:

1. look in the file /etc/laptop-mode/laptop-mode.conf

2. change under "CPU frequency scaling and throttling" to:
"LM_AC_CPU_MINFREQ=fastest"

3. reboot

I think this killed the noise, but not instantly. And now I just unplugged the power supply, and the noise isn't back yet...

---

### Post by martin6 on 2007-07-09
Hi,

I also had some weird noises coming from the new Dell Inspiron 1501. 

I tried the first option (adding pci=bios idle=halt acpi_sleep=s3_bios), after reboot the kernel gave "Kernel panic, not syncing, attempt to kill init" message and stop at the boot time.

It seemed panic to me -)

I managed to restore to the previous boot by editing GRUB after boot (using escape key to enter the grub configuration), and edited the kernel configuration (by entering "e" key after choosing kernel option), deleted the added text and reboot.

The second option does not seem to fix the problem either. I am wondering whether my problem is the hardware problem since I did not use window at the first place which did not have comparison.

Cheers

Martin

---

### Post by bigken on 2007-07-09
when i did a clean install of feisty on my dell inspiron 9200 the fans went mental 
but after running all the updates the problem went :)

---

### Post by fscodelaro on 2007-10-26
The idle=halt trick used to work on my Dell Latitude D610 running Feisty. Yesterday I did a clean install of Gutsy and I am experiencing the same high pitch noise again, both passing and not passing the idle=halt kernel parameters. Anyone having the same issue? Is this related to the new tickless kernel?

---

### Post by Steven_B on 2008-02-27
idle=halt is not a very good solution, as the processor has several levels of power saving, and they do not all cause the whine.  Using idle=halt locks the processor into the least-power-saving mode, which will significantly reduce battery life.  Some better solutions, which only block some modes, are discussed here:
[http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises]("http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises")

---

