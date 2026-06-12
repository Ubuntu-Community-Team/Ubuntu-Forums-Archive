---
title: "My new awesome computer is not performing so awesome.... =("
date: 2010-03-03
forum: Hardware
---

### Post by darkenemy on 2010-03-03
I have recently built a new computer that is not performing anywhere NEAR what it should.

The reason I believe this is because the computer I upgraded from ([Athlon X2]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3273142&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET03SHIP"), [Asus M2N-E SLI]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=2907957&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET03SHIP"), [Crucial RAM]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=2513637&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET03SHIP")) FAR outperformed this one, which leads me to believe something has gone arye.

The computer specs are the following: 
[Asus M4A78T-E Motherboard]("http://asus.com/product.aspx?P_ID=cf8IZzbU4m6GHKnW&templete=2")
[AMD Phenom II X4 965]("http://www.amd.com/us/products/desktop/processors/phenom-ii/Pages/phenom-ii.aspx")
[8 GB Corsair Dominator DDR3 PC10666 1333MHz]("http://www.corsair.com/products/phenomii/default.aspx")
[HIS Radeon X1650]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=2484235&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET03SHIP")

I am dual booting in Ubuntu 9.04 x64, and Windows 7 Pro x64, and I have had some serious performance issues.  I built this new computer for two main reasons, to have increased performance in virtualization (booting a XP x86 guest with a Ubuntu host in VirtualBox), and, more importantly, the ability to use powerful windows/mac only audio programs (dual booting into Windows 7) more effectively (Ableton Live, Reason, Adobe Audition, Sibelius, Guitar Pro).

This new computer should, all specs considered, at least double the performance of my previous computer, but infact, it does worse.  Virtualizing with VirtualBox is slower, and Windows 7 was barely moving at a snails pace when dealing with applications that were moderately good with my old Athlon and 4 gigs of ram.

I dont know exactly where to start, but I have included some pictures I took of some of my Bios Screens and a Memtest.
I did not flash the Bios directly, although I did perform all the upgrades from the disc that came with the motherboard, one of which I believe to have updated the Bios.

Regardless, please ask if you would like me to post anything, and I apologize in advance for being so vague on exactly what the problem is.  All I can say is that my computer is loading and running applications very slowly, and I would like to figure out why.

---

### Post by IcarusR on 2010-03-03
Was your old box running 9.04.
Exactly how does it run slower... video, ie redrawing screen. Loading apps ??

---

### Post by darkenemy on 2010-03-03
Yes, my old box was running the exact same configuration, operating system-wise.

Here are some examples of things that are slower:

I use Songbird for my huge music library (300 gigs, 80,000 tracks), and I hoped that this new computer would be better equipped to handle all my songs at once, but it freezes often, where my old box did so-so and rarely froze

I understand that Flash with Ubuntu64 is still a little shaky, but with my new machine it has been really really troublesome. (i.e. the player wont start, the player wont allow me to move the time slider, the player wont stop once it has started, etc.)

As stated before, when I dont absolutely have to dual boot, I use a virtual machine through VirtualBox (a 32bit XP Pro).  My old machine did pretty well in handling the virtual machine (with only 4 gigs of ram), but now (with 8 gigs) there are intense latency issues with the audio programs I use, and everything is slower, from the typing buffer to scrolling pages on firefox.  Until Ubuntu64 gets better support for audio applications and Flash, my life is much easier with a well oiled virtual machine. I have become quite used to using the virtual machines to combat these problems.

On windows, and yes I know this is not a windows forum, I have also had problems with heavy applications like Itunes, Ableton Live, and Adobe Audition, such that my current problems with my new and 'improved' machine are worse than they were with my old machine.



all this makes me think there is something wrong with my hardware, and I dont know a better place to turn than these forums....

---

### Post by realzippy on 2010-03-03
I would run some benchmarks in windows to compare.
If it is not faster,something is wrong.
For ubuntu:
Have you installed the ATI fglrx driver for your graphics card?
Has your old machine NVIDIA graphics?

---

### Post by darkenemy on 2010-03-03
In Windows, my AMD Overdrive Utility gave me a benchmark rating around 1500....

When I looked at other benchmarks posted around the net, I figure that my rating should be something like 7000 or 8000 at least.

----

Coincidentally, I am using the same graphics card (the HIS card linked above) on this machine as my old one.  Seeing as I dont play any games more demanding than the first age of empires, I saw no need for this machine to get a new graphics card.

In Ubuntu it seems that fglrx is up an running just fine, aside from a few hiccups: some of the animations take a second to think (like when I drag a smaller window up to maximize it, it freezes in place for a second, all stretched weirdly, before it maximizes --- a problem I didnt have before, with the same exact video card)

One of the big selling points for my processor was that it is great for multi-tasking, something I do alot of.  The strange thing is, my machine in its current state is far from capable of handling many applications at once, on windows or Ubuntu.


-------

on another note, I saw that my bios was revision 2208, and updated it to 2503.   It doesnt seem to have changed anything.

---

### Post by darkenemy on 2010-03-03
let me pose the question this way:

Does anyone know of a reliable way (other than the Memtest) to check whether the individual hardware pieces in my computer are fully functioning?

---

### Post by shazbut on 2010-03-03
Dunno about most of your problems, but on the virtualbox side of things make sure you have the processor virtualisation features (AMD-V) enabled in both the BIOS and the VM settings within VBox.  The V icon in the Guest status bar will tell you whether the feature is enabled.  The performance difference should be very noticeable.

---

