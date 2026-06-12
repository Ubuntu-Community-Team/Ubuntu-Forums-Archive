---
title: "GA-970A-D3P  - Ubuntu only seeing half of RAM"
date: 2015-08-24
forum: Hardware
---

### Post by lynwode on 2015-08-24
Howdy Folks,

Set up:
GA-970A-D3P Mobo
AMD FX8350
2x 2GB GT160 video cards 
32GB DDR3 Ram
15.04 + ubuntu desktop

Long story short I have had to rebuild my Ubuntu 15.04 box (motherboard issues - this is newer model of what was previously in the machine). All went well until I noticed that the new system was laggy when I had a number of VMs running.
I checked the memory and there was only 16GB (or thereabouts showing). I assumed I had not set the DIMMs correctly and reset them - looked good, BIOS reported 32GB..... but upon booting Ubuntu only sees 16GB.

So after much mucking about swapping DIMMs around the OS will only see 16GB.

I have flashed the mobo BIOS to the latest version in case that was a problem - but the issue still occurs.

I have run all free -m, meminfo,  lshw etc and they report only 16GB although it I run dmidecodem all 4 DIMMs are reported.

Does anyone have any ideas? Missed Bios setting maybe.

I will try a live usb of 14.x tonight but apart from that I am stumped....

Cheers,
Tim.

---

### Post by oldfred on 2015-08-25
Not sure if Also RAM, but many issues seem related to IOMMU on Gigabyte boards.

 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by lynwode on 2015-08-25
Hi Oldfred,
Yeah I had those iommu issues as well - fixed it with the tweak to grub. 

Can't find anything relating to RAM though....

Very frustrating  !

Thanks 

Tim

---

### Post by oldfred on 2015-08-25
I think there may be another similar older thread somewhere here. But it was a while ago and I did not follow it, so do not know if resolved or not.

This was 16GB.
[http://ubuntuforums.org/showthread.php?t=1963008](http://ubuntuforums.org/showthread.php?t=1963008)
Another 32GB but no RAM issues mentions, lots of other issues
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)

Well, 640K is all you should need.
[http://quoteinvestigator.com/2011/09/08/640k-enough/](http://quoteinvestigator.com/2011/09/08/640k-enough/)

And I remember when 64K was a lot and cost about $4000.

---

### Post by lynwode on 2015-08-26
Hi,
I think I may have got to the bottom of the mystery.

dmidecode clearly shows 4 x 8GB Dimms - so it had to be something in the setup.

Whilst troubleshooting a disk mount issue I noticed that there are a number of tmpfs  that co-incidentally add upto  ~16GB:

tmpfs                        1.6G   10M  1.6G   1% /run
tmpfs                        7.9G  239M  7.6G   3% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs                        1.6G   44K  1.6G   1% /run/user/1000

As I understand it the tmpfs use RAM.... so I am assuming that something has changed in the new install - a clean 15.04. In my previous build, which was a 10.04 upgraded each release to 15.04, all 32GB showed as available and the swap was a separate partition

I am correct in thinking that this is a new way of doing things to speed up Ubuntu?

---

### Post by pmrlaw on 2015-08-26
I have seen confusion when people try and install more than 3GB of RAM on 32 bit systems. To my knowledge, a 64 bit capable CPU is needed if you want to use more than 3GB of RAM (there are exotic exceptions). But this is not the problem here. You are using a powerful 8 core (64 bit) CPU and the memory problem looks enigmatic. I would use Parted Magic to run a memtest beginning with one RAM stick...checking the speed as more sticks are added (obviously adding them after powering the machine off) and then set dual or triple channel memory mode as applicable before checking the speed (frequency) data again. it is weird problem that just might relate to the memory channel mode, my best guess.

It is also possible that the RAM has been damaged due to electrostatic discharge if it has been handled by someone who was not wearing an antistatic wristband connected to ground. Tens of thousands of volts can discharge in a fraction of a second from an ungrounded tech (low current in amps but serious kilovolts from static)

Not sure I have added much but hope it helps.

---

### Post by lynwode on 2015-08-26
Its 64bit system that was quite happily running with 32GB until I had to replace the mobo and rebuild.
I ran a test on the RAM and it all looks good - so thats ruled out. Having said that I haven't looked in to optimising it..... lost to much downtime as it is.
Thanks for your input.

---

### Post by pmrlaw on 2015-08-26
Just occurred that some Gigabyte boards have the dreaded 'dual BIOS' which caused me to pause for thought when I first encountered it as I could not initially gain access to the other BIOS screen. Your board has dual BIOS as I had a look. There is also an odd note in the Gigabyte board specifications which says as follows: (Note 2) **To support a DDR3 1866 MHz (and above) memory, you must install an AM3+ CPU first.**

First? What does that mean? Does it mean that if you had an AMD Phenom II or AMD Athlon II CPU installed on the board before you installed your socket AM3+ FX8350, that the DDR3 memory will malfunction? It probably does not mean that but I would create a tabula rasa here by pulling the 2032 Lithium Battery from the Motherboard, before putting it back, checking the BIOS settings and firing it up again. Finally, if you simply transplanted the hard drive from your old system by attaching it to the new motherboard set up, that could explain a lot. A new Motherboard really needs a fresh OS install because the hardware is different. But now I am stating the obvious.

---

### Post by lynwode on 2015-09-03
Hey - Sorry for the late reply - I didn't get notified of your repsonse.
LOL _ Dreaded dual bios - I agree!

The MB is brand new and the os is a brand new install.... trust me 5 times over !

Other BIOS screen - whats that then - how does one access it?

---

