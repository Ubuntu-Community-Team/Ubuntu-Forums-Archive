---
title: "Computer won't POST"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by ColonelSartoris on 2008-01-26
My computer won't post.
This is my setup:
ASUS P5N-E SLI
Intel Core 2 Quad Q6600
4 GB of DDR2 RAM
OC Geforce 8800 GTS
500 GB SATA HDD
750 Watt PSU


I had this same exact problem while building the computer, and after testing the RAM; testing the RAM in different dimm slots, trying to turn on the computer without the RAM to discover the computer isn't even getting past the CPU; removing power to the computer and the motherboard battery and resetting the BIOS; returning and replacing the CPU -and- motherboard with the same models; returning and replacing the video card with the same model; and finally replacing the PSU, the computer still would not POST. Finally, after calling ASUS tech support and going through everything with them, I was advised to put stand-offs on the screws I used to secure the new motherboard to the case. I did, and the computer booted. Supposedly, the show-stopping problem was a mobo short resulting from improper electrical insulation.

Everything works great from there on out; I run all the latest games and apps without a hitch and the hardware temperature readings are all running cool and in the green thanks to adequate case airflow. Couldn't ask for more.

Then about two months later, I start getting CMOS Checksum errors whenever I boot, forcing me to reload the BIOS settings with every occurrence. I check the battery to ensure it's installed correctly and still get the problems. Then, I replace the battery and it works fine. Few days later, I start getting the CMOS Checksum problem again. Apart from this recurring problem, the computer works fine for a week after the second coming of the CMOS Checksum problems. Today, it won't POST at all.

I went through all the troubleshooting procedures I went through before and then some and the computer still will not POST! There isn't any dust in the case or on the components, all the fans are running and working properly, nothing seems to be touching that isn't supposed to, and all the connections that are supposed to be there are secure. It was working fine yesterday, and I did not do anything to change the hardware or software setup from the state either were in while the computer was still working the day before. The RAM is fine, the GPU is fine (I have tested both in another computer), and I believe it to be extraordinarily unlikely that the cause is a fatal problem with the CPU or motherboard (not least because I had been told this before and had replaced both of them already) though I do not rule out the possibility.

Am I missing something here? Have any of you had a problem like this before?

---

### Post by ColonelSartoris on 2008-01-26
As it turns out, one of the jumpers on the motherboard came loose and fell off somehow, which may explain why the CMOS was getting corrupted. Putting the jumper back in place solves the problem completely.

---

