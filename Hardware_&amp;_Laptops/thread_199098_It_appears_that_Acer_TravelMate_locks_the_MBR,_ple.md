---
title: "It appears that Acer TravelMate locks the MBR, please help!"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2006-06-18
I tried to install Ubuntu 5.10 on my Acer TravelMate 292ELC. The installation process goes nice till the system reboots. And then it says it can't boot the hard disk though it looked like Grub was installed. Tried twice. The BIOS is very poor and there's no something like "Lock/Unlock MBR" there. It appears that Acer lets you install the bloody Windows only. :mad: Think I could sue them!!! Any suggestions? Thanks in advance!

Edit: I also tried installing Grub on /dev/hda from Live CD, and it says "Permission denied"

---

### Post by PryGuy on 2006-07-07
6.06 solved my problem!!! :D :D :D

---

### Post by Ptero-4 on 2006-07-07
How it did. Can you pls tell the story, at least we would see which clever tricks did you to defeat your Acer's anti-Linux MBR locking mechanism.

---

### Post by PryGuy on 2006-07-07
The thing is, I did nothing at all to make 6.06 work on my Acer TravelMate, just an ordinary install. Ah, except for the fact that I had to choose safe graphics in the boot menu. Notebooks gurus, please tell us is that a common practice that the notebook manufacturers protect MBRs or was it just my hardware independent problem with 5.10? I can't believe it's so, you just BUY a notebook and that means you CAN install ANYTHING on it 'cause IT'S YOURS!!!:mad:

---

### Post by Ptero-4 on 2006-07-07
pryguy. I actually never heard of that b4, but knowing a lot about TCPA and TPM chips (and having had first hand experience on that technology after suffering it on several HP Desktops at home and work) I knew it was just matter of time b4 this would be implemented somewhere. And believe me, it is just getting worse. And BO, they don't think that your computer is your's anymore.

---

### Post by jdelcom on 2006-07-07
I just came here looking for some help. Not sure if this is the right thread, but it helped me, so here it is:
I have a Travelmate 2420. It came with M$XP, but since I need to work with a couple of -only-M$- programs, I can't just dump it.
I decided to install Ubuntu in a partition. 
The Live CD was fine, but it took AGES to load anything. I tried to install it, and I never even got to see the install windows, although the HD was working as if the world was ending.

Having read this, I booted in safe graphics mode, and managed to run the installation. 

In the middle of it, it says it can't read the FAT32 partition with XP (hda2, since in hda1 it has the restore thing), but could read an hda3 fat partition. Weird. 

Right now it's installing. I'll let you know how it ends, specially since I'm concerned about that restore thing linked to the MBR.

---

### Post by jdelcom on 2006-07-07
OK, looks like everything is working fine. Grub shows me several boot options (not sure why), I'll need to config it to boot by default and that.

Thanks for the tip on safe graphics.:) 

Oh, BTW, Ubuntu looks a bit too "bright" in this laptop. I'll see if I can change that.

---

### Post by PryGuy on 2006-07-08
> **Ptero-4 said:**
> pryguy. I actually never heard of that b4, but knowing a lot about TCPA and TPM chips (and having had first hand experience on that technology after suffering it on several HP Desktops at home and work) I knew it was just matter of time b4 this would be implemented somewhere. And believe me, it is just getting worse. And BO, they don't think that your computer is your's anymore.I didn't mean any TCPA or TPM chips actually, though it worries me a lot and this is one of the reasons why I chose Linux. Just remember some older BIOSes (I don't see it on the modern motherboards, probably I'm just lucky) where you could enable the "Protect MBR" option. The idea of it was to help fighting the MBR viruses and all. ACER could do it the same way, but just without any ability to turn it off, the BIOS in my notebook has just a few settings, it lacks even the vital ones. I'm probably wrong about that, and I'm just blaming ACER for nothing and I was just doing something wrong trying to install 5.10, but why the 6.06 installation went that smooth then?

---

