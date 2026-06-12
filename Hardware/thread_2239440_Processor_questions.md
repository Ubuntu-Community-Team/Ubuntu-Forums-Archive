---
title: "Processor questions"
date: 2014-08-13
forum: Hardware
---

### Post by Tristan_Williams on 2014-08-13
I am searching for a new processor, because I've got too much running at any given time for mine to handle.
So here are my questions:

1. What would be the difference between an L2 cache of 6MB, and an L2 cache of 2x3MB? Seems to me like it's the same thing
2. Other than socket type (LGA775), what specs do I need to make sure are compatible?
3. Since most of the "heavy-duty" work I do is in Blender, GIMP, and Ardour, would it be better for me to leave my processor alone, and get a GPU?

---

### Post by weatherman2 on 2014-08-13
I'd guess that 2x3MB means there is one 3MB L2 cache for each core on a dual core CPU.  It might be the same as a 6MB cache - which may also be split.  May depend on the exact CPU architecture.

Besides socket type, you need to worry about: Front-Side Bus (FSB) speed, voltage, and BIOS compatibility with the CPU.  If you're looking to upgrade a CPU, the first thing to do is start with the motherboard or computer manufacturer's website and see if you can find specs.  Sometimes, especially if the system was a custom-build motherboard, they will even list specific CPUs that are known to be compatible with the board.

I don't know what CPU you have now, so I don't know what you would be upgrading from and to what.

For GIMP, you generally want more RAM and a faster CPU.  A separate GPU won't help directly with GIMP performance, but indirectly it might free up some RAM and CPU power that were previously used for integrated graphics to make the computer a tad faster.

---

### Post by tgalati4 on 2014-08-14
Most modern CPU's have two-way set-associative caches--each core can draw from either cache, so 6 MB or 2x3MB may actually be the same thing.  You can browse the [benchmarking]("http://openbenchmarking.org/result/1408141-KH-2XINTELXE40") website for CPU performance benchmarks and compare your current CPU with your proposed CPU to get an idea of improvement.  It may be less than you think because a specific motherboard can an only support a narrow range of processors.

---

### Post by em3raldxiii on 2014-08-16
As others have mentioned, check the motherboard manufacturer website for your model's supported CPUs.  You may also want to double-check that your power supply has enough jam to power a significantly more powerful CPU if such an upgrade exists for you.  The difference between the two caches (if there is, indeed, a difference) would likely be barely noticeable with overall performance when compared with other factors like clock speed and number of cores.

Some processes will benefit more from having more cores, too.  The Gimp, for instance, uses multi-threading for a number of things (although, apparently not for certain GTK processes).  You should do a little additional research into the difference between, say, 4 cores vs 8 cores (if there are even 8 core LGA775 processors, I am too lazy to check).  Typically, each core of an 8-core will operate at a lower speed than the 4-core equivalent, and some processes will benefit more from the higher speed cores.  Also, Gimp and Ardour benefit _greatly_ from more RAM, especially if it's clocked faster.  Again verify the compatibility with your motherboard, but you might consider changing out your RAM with bigger, faster modules.  Keep in mind that if you just ADD a couple of sticks of higher speed RAM, they will clock down to the same speed as the other RAM on the board.  You have to do a straight-up swap.  A new graphics card won't benefit the jobs you mention very much, except perhaps Blender (in which case you have to enable GPU rendering if I remember right).

I hope that helps you a bit!

---

