---
title: "Ubuntu to slow on a &quot;good&quot; computer dont know why"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by clintfish on 2007-04-19
Greetings.

I have a "small" problem.
My computer is so slow, but first i have to say which one I have.

Here are the info:

AMD 64Bit 2x (dual core) 3800+
2 GB RAM
Mainboard : ASROCK 939NF6G-VSTA
darauf sind: Chipsatz: nFore 430
Audio: 7.1 CH Windows Vista Premium Level HD Audio (ALC88 Audio Codecs)
Lan: Realtek PHY RTL8201CL
VGA: NVIDIA GeForce6 Grafikchip

Because the lan and audio doesn't work (because i didn't find the drivers or i don't know how I can
make it work) i put the lan and audio pci cards in.
these are my lspci output of the lan and audio card:

Lan: 01:0a.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
Audio: 01:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

So my problem is that:
When I install something or but something from usb to pc (or from pc to usb) my music stops to play.
and I can't do something else just wait when it's end.
I mean I can't but picture on my computer and work at the same time.
A friend of me got the half so good computer and he can makes the things.

Please help me 
I don't know why it doesn't work.
Now I got such a good computer and it doesn't work correctly.

Thank You
Clintfish


PS: Sorry for my bad english

---

### Post by LexRoss on 2008-04-09
Same here. It sounds like Ubuntu performance and sluggishness has always been an issue. I've got a brand new Asus F5N laptop with 1.9GHz AMD64x2 Turion TL-58 CPU, 2GB DDR-2 667MHz RAM and 120GB SATA drive. I got everything working fine and man, is that thing slow! Slow to boot, slow at application startup, GUI responsivness, you name it.

I tried other distros just to check whether it was a hardware issues, and they were all lightning fast, just like DSL on my old PIII-500MHz 128MB RAM machine. But they were all optimized for KDE, which was my desktop of choice before I got hooked up on Ubuntu with its simple uncluttered interface and very limited customization, which leads to productivity increase (there isn't much playing around with computer, just work).

Anyway, back to the point, I started blaming GTK and GNOME for being sluggish until I gave Arch Linux a try as suggested on Ubuntu forums. I instaled it with both GNOME and KDE and it was really fast, even loaded with applications. The only problem is that I am not in a position to configure Arch's interface to mimic Ubuntu. Too steep learning curve for me. And I like the way Ubuntu is put together.

Still, does anyone know why Ubuntu is so sluggish. I could't find an answer so far. All basic tune-up tips did not help. There should be something with the design that slows things down.

Let's say booting up Ubuntu and Arch with the same kernel version yields the following results.
Loading the kernel: Ubuntu: 40 seconds, Arch: under 10 seconds
Starting up the system: Ubuntu: 50 seconds, Arch: 20 seconds
Starting the GUI (X and GDM and getting login screen): Ubuntu: 10 seconds, Arch: 10 seconds
Total start-up time: Ubuntu: 1min 40s, Arch: 40s

So this sounds as a non-issue. Once the kernel is loaded (although 40s to load the kernel with 43MB/s drive throughput as reported by hdparm sounds rediculious to me) the GUI loads in about the same time on both systems. Then Ubuntu takes it's own sweet time to log into GNOME for the first time, but that is a known bug we have to live it (the bug makes its way from Gutsy to Hardy too, so I just accept it as a fact of life).

But then I can see slower menu responsiveness and application start-up. Firefox loads in about the same time, slow as it is. But opening home folder or a terminal window which is a brisk in Arch, takes full 2s in Ubuntu. It is also slow on drawing icons in menus.

This behaviour is strange, and I have no good explanation to it. It's not like Ubuntu is painfully slow, it is on par with Vista for the most part performance wise. It's just that other distros are so fast. The same was true for my old laptop when I first got it with Windows 2000 loaded - lightning fast, so you know right away your money is well spent: you are getting top of line hardware.

Now Ubuntu makes my brand new laptop look 4 years old piece of crap. So I would really appreciate someone helping me out with improving Ubuntu performance or, if that fails, with setting up any other distro which is known to run fast with Ubuntu-like interface.

I am almost convinced on switching to Arch or PCLinuxOS or whatever, especially when everyone I meet expect Linux to be super fast compared to Vista, and they all got envious just when I have to tell them that is a common misconception, and Linux is no better. Both systems are rather complex and hence slow. But I like the usability of Ubuntu that makes up foe its sluggishness.

But now when I have tried Arch with the same GNOME interface, I am less willing to tolerate Ubuntu's performance issues. The responsiveness of Arch sets a new pace, and I found myself to be more productive. It's like changing from old Cadillac to less powerful but compact entry level Chevy Cavalier. All of a sudden you can drive like crazy, speeding and covering much bigger distances on the same gas tank.

Let's get cracking and resolve this performance issue once and for all. Or change horses.

---

