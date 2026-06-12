---
title: "Use Ubuntu with both Integrated Graphics and disable NVIDIA for VGAPassthrough"
date: 2016-12-13
forum: Hardware
---

### Post by complexity2 on 2016-12-13
Hello all,

I'm pretty new to Linux, however, I do know the basic commands.
I have an [HP Envy 700-229eb]("http://h20564.www2.hp.com/hpsc/doc/public/display?docId=c04126526"), of which the graphics card has been replaced with an NVIDIA GTX 1060.

The documentation on the website of HP says that the integrated graphics and the ATI card cannot be used at the same time, but with my NVIDIA card, I can use them both at the same time.
I've been doing this is Windows and it's working great.

I have one monitor which has an analog (VGA) and Digital (DVI) output, I can switch between them with the help of a button.
My NVIDIA card is connected to my monitor using DVI, the integrated graphics is connected to my monitor using VGA (Using a DVI piece between the motherboard output and the VGA cable).

Now, I've disabled my PCI slot containing my NVIDIA card and I install Ubuntu.
This works great, on full resolution, and my monitor outputs over VGA.

After installation, everything is running sucessfully.

Now, when I enable my PCI slot containing my NVIDIA card (Note: I set the integrated graphics as the primary boot device), the GRUB boot loader is only showed over the DVI channel (NVIDIA) and the VGA channel does not output anything.
Moreover, I cannot boot to Ubuntu because of an error `/dev/sda clean (number)/(number)`.

The only way to boot my computer is by adding `nomodeset`, but offcourse, then the resolution is very bad.

When I install Ubuntu with both cards enabled, (Integrated Graphics and the Primary), I only have output on the NVIDIA card, and I cannot boot due to the same error `/dev/sda clean (number)/(number)`.
Booting with the `nomodeset` flag does work, and then I can install the NVIDIA drivers and than the machine runs fine.

However, I don't was to use my NVIDIA card because I want to use it for VGAPassthrough.
So, I would like Ubuntu to output only over the VGA channel (Integrated Graphics) on full resolution, without booting errors and use the NVIDIA card for VGAPassthrough.

It seems just so difficult, however, there must be a simple solution.

Any help is greatly appreciated since I'm struggling for a whole week.

---

### Post by TheFu on 2016-12-13
VGA passthru for what purpose? 

Not all systems can support it to run a Windows virtual machine, if that is your intent. The "Virtualization" subforum might be able to help. There are long threads there about doing it, which I haven't followed in about a year.  It was non-trivial then.

---

