---
title: "Best hardware for linux"
date: 2010-02-12
forum: Hardware
---

### Post by phpworm on 2010-02-12
I apologize if this is a common or annoying question. My current desktop needs to be replaced, and I want to build a new one that has the best possible hardware available in the current market for Ubuntu.
 
The only thing I know that I want for certain so far is a mini case which will require a miniATX motherbaord. As for the remaining components, I think I want to go with Intel because it has non-proprietary drivers (even though some proprietary drivers will work I don't think it's a good mix). And I've been told that linux can't use more than 256 MB video ram, so anything better than that would be a waste of money?
 
So despite what I'm using my computer for, and having a budget of around 2k, what is the best possible (and newest) hardware I can buy for an Ubuntu only desktop?
 
I want something that will give me the best possible performance for the longest duration of time, assuming I'm using linux to its full capabilities.

---

### Post by recluce on 2010-02-12
> **phpworm said:**
> I apologize if this is a common or annoying question. My current desktop needs to be replaced, and I want to build a new one that has the best possible hardware available in the current market for Ubuntu.
 
The only thing I know that I want for certain so far is a mini case which will require a miniATX motherbaord. As for the remaining components, I think I want to go with Intel because it has non-proprietary drivers (even though some proprietary drivers will work I don't think it's a good mix). And I've been told that linux can't use more than 256 MB video ram, so anything better than that would be a waste of money?
 
So despite what I'm using my computer for, and having a budget of around 2k, what is the best possible (and newest) hardware I can buy for an Ubuntu only desktop?
 
I want something that will give me the best possible performance for the longest duration of time, assuming I'm using linux to its full capabilities.

I believe that you need to do some research first and ask more specific questions to get good answers here.

Intel chipsets are generally good for linux, Intel graphics are "hit and miss", depending on many factors. You would probably do better by using a dedicated NVIDIA graphics card. The proprietary NVIDIA drivers work very well and give good performance. So unless you are religiously against closed source....

I never heard about a 256MB graphics memory limit in linux, my NVIDIA driver sees 512 MB memory on my Quadro NVS 140 graphics card.

---

### Post by RyanLeaf on 2010-02-12
There really isn't a definitive guide to what is the best hardware for Linux. I would say supported hardware is the best, but that is vague at best.

Here's what is important:

- Computer performance. How fast does that computer need to be to do what you want it to do? If you are only checking your email, using a word processor, and other basic functions, would it make sense to get a top of the line Intel Core i7 processor? Or would a  basic Intel Core 2 Duo suffice? The same goes for a graphics card. If the latter example is true, then would it make sense to have a top of the line nVidia GeForce GTX card? Or would it make more sense to have integrated Intel graphics.

As for compatibility, here are the basics: If you want it to work out of the box, you might want to look at manufacturers who build Ubuntu computers. System76 and Dell both have Ubuntu offerings that guarantee compatibility with Linux. But if your going to build your own, or buy a Windows pc that you'll install Ubuntu on, then you will want to check forums and compatibility lists for other users comments. In general, you should have pretty good luck if you have Intel hardware (such as my Dell laptop, which everything worked right out of the box. I have an Intel Core2 Duo, Intel Wireless-N built-in, integrated Intel graphics, Intel chipset. Everything works perfectly.), or something based upon an Intel chipset. Other hardware works, but you'll want to check hardware compatibility lists: [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

Hope this helps.

Ryan Leaf

---

### Post by phpworm on 2010-02-12
> Intel graphics are "hit and miss", depending on many factors. You would probably do better by using a dedicated NVIDIA graphics card. The proprietary NVIDIA drivers work very well and give good performance. So unless you are religiously against closed source....
Yes, I am religiously against closed source. Could you give me a few examples of the hit and miss factors you're referring to?
> would it make sense to get a top of the line Intel Core i7 processor? Or would a basic Intel Core 2 Duo suffice? The same goes for a graphics card. If the latter example is true, then would it make sense to have a top of the line nVidia GeForce GTX card? Or would it make more sense to have integrated Intel graphics.
I want this computer as top of the line as it can get, so yes an i7 would be the way to go.
 
I guess I'm confused as to what to believe about the graphics, which is where I'm stumped now. That could end up being the most expensive part of the computer, or it could make no logical sense because linux will never use that kind of power. I don't know. That's what I'd like to find out. I'm not using WINE or any closed-source software.

---

### Post by MindFusion on 2010-02-12
I'd recommend a 4 GIG RAM minimum, an nvidia (no ATI- ATI is no more than trouble) graphics card, an AMD/ Intel processor (although Intel will generally cost you more) with 2 mghz +.

---

### Post by msrinath80 on 2010-02-12
> **phpworm said:**
> Yes, I am religiously against closed source. Could you give me a few examples of the hit and miss factors you're referring to?

I want this computer as top of the line as it can get, so yes an i7 would be the way to go.
 
I guess I'm confused as to what to believe about the graphics, which is where I'm stumped now. That could end up being the most expensive part of the computer, or it could make no logical sense because linux will never use that kind of power. I don't know. That's what I'd like to find out. I'm not using WINE or any closed-source software.

Get the i7 620M with integrated graphics. Good performance at a reasonable price. Well, relatively speaking anyway. But bear in mind, it could be well around 6 more months before the graphics driver for the 620M matures and reaches an acceptable level of stability.

Edit: Oh and I use the Intel GMA 950 integrated graphics on my Lifebook. Works flawlessly in Debian Lenny. There, that's a hit for you ;)

In my experience, I've consistently seen that 1-2 year old hardware works *best* with any kernel released now. This may be a consequence of the fact that I'm using Debian. But rest assured when I say *best* I mean very very stable, no less!

---

### Post by phpworm on 2010-02-12
Okay, let me re-phrase my question...  How would I find out whether or not linux has a memory limit for video, and what that limit is?

---

### Post by recluce on 2010-02-12
> **phpworm said:**
> Okay, let me re-phrase my question...  How would I find out whether or not linux has a memory limit for video, and what that limit is?

There is no reason for a memory limit per se. My NVIDIA driver proofs that at least 512 MB is possible. Since you want to use the FOSS drivers exclusively, I guess you should check out the various projects and see if those drivers have any specific memory limit.

As to FOSS graphics drivers, I would not recommend NVIDIA then. The FOSS driver is very basic, with no 3D support (desktop effects will not work either). There is a FOSS "neauveau" driver, but that is alpha and who knows where the project will go? Intel open source drivers are broken in Jaunty but reported to work in Karmic, but chipset graphics and "as top of the line as possible" preclude each other.

So based on your requirement, I would recommend ATI. The ATI FOSS drivers work well in Jaunty, even though they are broken in Karmic, this mostly concerns notebooks/netbooks (no resume after suspend). In Karmic, I install the ATI Jaunty drivers, which work fine.

---

### Post by Bluebearbevis on 2010-02-12
Hi phpworm,

 If it weren't for your religious opposition to closed source, I would recommend a system76 computer.  I love my Pangolin laptop even tho it's so 2009.  Some of their high end desktops look awesome, but pretty much all of them use nVidia graphics.  Not only is the hardware compatible, but Ubuntu/Linux specific.  Neither have I heard about this 256 thing.  My Pangolin has an nVidia G105M w/ 512 MB memory and with all the bells and whistles running in Compiz, I'm glad of it.  Consider making an exception to your rule regarding display drivers.  In my experience, there's nothing better than dedicated graphics.  Good luck with your decisions.

Richard

P.S.  Oops, did I recommend system76 after all?

---

