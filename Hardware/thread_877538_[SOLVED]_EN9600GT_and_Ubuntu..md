---
title: "[SOLVED] EN9600GT and Ubuntu."
date: 2008-08-01
forum: Hardware
---

### Post by Norwal on 2008-08-01
I just got a new 9600GT only to find that it will not work (easly) with Ubuntu 8.04.  How long does it take before new video cards are supported?  

I've read some of the forums but nothing has worked for me.:(  I'm going to try a fresh 64 and then a 32 install to see if that works.

---

### Post by Norwal on 2008-08-02
Well I have Ubuntu 8.04 64 up and running and so far so good. It still doesn't recognize my 9600GT, but Glxgears is at least working.  I'm downloading EVE Online now to see how bad/good it runs. :)

---

### Post by Norwal on 2008-08-02
The EVE Client is installed but no joy. :( The game will not run and the 3D tests in EVE Config all failed. With out really thinking I installed the nvidia-glx-new drives using syaptic and now X doesn't work.  I had to stratify my hopeful thinking and at least try it.:) 

Now I need to figure out how to get back to the default drives. Going to try  "sudo dpkg-reconfigure -p high xserver-xorg"

The sad think is I have to either take the video card back and downgrade or go back to XP until the card is supported. :mad:

---

### Post by Norwal on 2008-08-02
Now that is very nice.  Recovery mode has a choice to fix Xorg so I didn't have to do a thing. I love this OS!:lolflag:

---

### Post by Norwal on 2008-08-02
I got it working on my 32 bit drive.  I'm not sure why but here it is:

cpu: AMD Athlon(tm) 64 Processor 3200+
cpu_ghz: 2.01
memory: 1011
videocard_manufacturer: NVIDIA Corporation
videocard_type: GeForce 9600 GT/PCI/SSE2/3DNOW!
videocard_ram: 512
agp_aperture_size: 512
videocard_driver_version: 2.1.2 NVIDIA 173.14.12
soundcard: Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xa000, irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-19-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066

I follow the advice of tseliot and ran "sudo dpkg-reconfigure xserver-xorg" and just choice the defaults.  Then I reinstalled [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run)  the driver and it worked.:popcorn:

I going to try the 64 drive next.

---

### Post by Norwal on 2008-08-03
Just to update, I've had no luck getting my 9600GT working on 8.04 64 Bit.  I guess I'll stick with the 32 for now.  It's too bad though, my 64 bit is on a SATA and my 32 is IDE.  Hummmmm, I think I have another project on the go...... Now where did I put that Norton Ghost disk?

---

### Post by Norwal on 2008-09-03
Good news, I got the 64bit going thanks to this thread.  

[http://ubuntuforums.org/showthread.php?p=5722924#post5722924]("http://ubuntuforums.org/showthread.php?p=5722924#post5722924")

Thanks to Lantesh for the step by step fix.:lolflag:

---

