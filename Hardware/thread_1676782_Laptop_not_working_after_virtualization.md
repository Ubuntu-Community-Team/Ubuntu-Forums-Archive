---
title: "Laptop not working after virtualization"
date: 2011-01-27
forum: Hardware
---

### Post by fero4u123 on 2011-01-27
OKay so my computer is not usable at the moment now. Maybe someone here can help me.
 
I have been trying to get Ubuntu working on my laptop (which I have  everything was working fine). I installed virtual box and ran my  original os (windows XP) inside it following the direction here in another forum. I had  some trouble getting it working because I kept getting "MBR 1FA:" for a  while but then after reading run1206 post in this thread I got it to  work. (His thread said to run this command "
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/SystemHD.vmdk -rawdisk /dev/sda -register )
So, anyway here is what happened. Once I was done playing inside xp on  virtualbox, I restarted my computer. When the boot selection screen came  up this time i selected Windows XP on dev/sda1. It asked me to choose a  hardware profile, so I chose the one called RawBoot (because I had  created this hardware profile inside virtual box on the previous run, I  was told this is a good idea to do. This was a clone of the current  hardware profile running inside of virtual box) 

Okay so now this brings me to my problem that I am really hoping someone can help me with.

Once I selected RawBoot, The computer came up but the keyboard and mouse  were not working...so I press the powerbutton and the computer shut  down. Once it turned back on the Screen on my Laptop just stayed blank  as if it was turned off. I can tell the computer is working because it  makes all the sounds and everything like it use to... but THE MONITOR  JUST STAYS BLACK / OFF NOW .

So anyone have any ideas on how to fix this problem ? I have tried  restart several times. It's really hard for me to troubleshoot  anything when nothing EVER comes up on the screen, not even the Original manufacturer boot screen which says stuff like press F2 for setup, F9 for boot order etc is coming up.

Someone please help me if possible. I would greatly appreciate it.

---

### Post by fero4u123 on 2011-01-27
I've been trying to play around with and I am still getting nothing. A POST screen does not even show so i'm limited to really just turning it on and off. I'm starting to think that maybe none of the hardware (keyboard, mouse, etc) are working on my Laptop. I really just don't know what to do. I also tried hooking up to external monitor (lcd tv with vga cord) tried pressing the fn key to switch between the monitors and still nothing :-( just this black screen all the time. I have no way of telling, but I dont think the keyboard or mouse is working either on this laptop (HP DV6000)

Please can someone offer me some insight on this ?

---

### Post by bhaverkamp on 2011-01-27
You should try a livecd boot to check out your hardware and disk partitions. Assuming the Live CD works you can then start to figure out what went wrong. The idea of running the original OS in a VM is interesting but tricky and very easy to screw things up. I don't dual boot anymore these days it keeps things simpler. Pick your primary OS and run the alternate OSs in VMs.

---

### Post by fero4u123 on 2011-01-27
Thank you for your response :-). I appreciate it. 

but, 4

I have tried that also and I am still getting nothing. Just a Blank black screen. As I said the initial POST screen doesn't even come up (The manufacturer screen that says press F2 for setup, F12 for boot options or something like that etc.)

It turns on and I can see all my lights on and the I can hear the fan blowing, but I just get no activity / interaction it seems.

If anyone needs anymore explanation or can help please let me know.

---

### Post by fero4u123 on 2011-01-28
Okay So i have fixed the problem of my computer not displaying anything period at all. It turned out i had to open up my laptop, leave the motherboard battery out for a while, put it back in then bam back to normal :-)

Now my problem is that from Grub whenever I try to boot into windows it will come up, but my keyboard and mouse will not work, and when I restart my computer I am back at square one (Nothing works again, NO POST, or anything, just the lights turn on.) Then I have to turn off the computer, pop the motherboard/bios battery out and reset.

Good news is as long as I am not trying to get into my original OS (XP) I can boot into ubuntu just fine. I will would like to know how to get everything back working though.

Thanks to anyone that viewed this and hopefully if anyone have any similar problem with NO POST screen and No keyboard and mouse working they'll see this and know to just pop their bios/motherboard battery out and wait, then put it back in.

---

