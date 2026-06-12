---
title: "Best way to set up Ubuntu with 7+ CD burners?"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2007-06-25
I'd like to make a CD duplicator based on the Ubuntu distribution (hopefully with a touch-screen interface in the end), what type of hardware should I look for?

The goal is to set up separate processes for each CD burning, so I could have about 9 separate CD burners burning the same (or different) files at different speeds.  (Meaning the end-user doesn't need 9 of the exact same model of CD burners.)

I know this would be more expensive than modern CD/DVD duplicators, but with Apache/PHP/PostgreSQL installed and a couple of large hard drives it could easily make up for the cost in features.  (Meaning the operator could control it from the network without a touchscreen, maybe an AJAX interface that simulates the touchscreen, and they could also manage network storage locations that the device can "pull" from.

I mainly just need to know what hardware would be best to get started.  I'm pretty sure this "should" be easy with basic PC internals, but the obvious question is how do I install multiple CD burners?  Just standard IDE controller cards?  Any particular brands that are reliable and cheap?

I just want this to be as modular as possible so end users can easily swap out parts as they wear out.  (and of course any interfaces will be Open Source... there seems to be a dire need for innovation in the CD/DVD duplication community)

---

### Post by OneSeventeen on 2007-07-17
Just an update, I now have a computer case that holds 9 CD Drives, but I'll probably have to use a small form factor motherboard due to space limitations.  The case is an average width, so I should be able to modify it to support full-height PCI cards, but most micro-atx boards only sport 2 PCI slots.

Of course 2 dual-slot IDE cards would give me access to 6 IDE slots or 12 IDE devices total (including 2 on-board IDE slots).

Since one needs to be the Hard Drive, that would mean 1 "Source" drive and 10 "Destination" drives 

I think I'll try to piece it together with existing hardware I've got lying around (leaving the motherboard outside of the case) to see what controllers play well with Linux.  It looks like "Promise" controllers should do.

Here's the hardware I'm thinking of using:[list][*]MSI K9VGM-V Socket AM2 Micro-ATX board (onboard video/LAN/audio)
[*]Promise IDE controller (2 slots giving 4 additional channels total)
[*]2x512MB DDR2 RAM sticks (Crucial)
[*]AMD Athlon 64 X2 3600+ CPU[/list]
Total Cost: $200 + shipping
(FYI, 9 Lite-On DVD burners would add $333 to the project, but those will come later)

After I get the hardware working, any tips on accessing the drives independently and what will be used more when burning to 9 DVDs at once, CPU or RAM?

I would like to be able to attach a touch-screen and drag and drop files with your finger, so it will oftentimes be burning different ISO's to different drives at different speeds at the same time.  Do I need a more powerful processor, or can I go with a semperon?

---

### Post by sabrewolf2006 on 2007-07-17
Hi,

CPU would be a definite issue because of the nature of data exchange to the drive(s)
a dual core may help you out in this regard if its got a good MoBo chipset behind it (its the transport and bandwidth that'll be the big requirement)

lots of RAM wouldn't harm the process tho.. 

(good choices there.. not sure about the MoBo tho)

another thing to consider also

heat distribution.. you may need to space out the drives (and may need to install some cooling fans in those gaps too) so that cool air circulates correctly..
if the duplicator is gonna be in a 'constant' use it would be more of an issue but if its just gonna be used to fire off 8 copies of a disc and then left for a while you might be ok with just stuffing the drives in.

Hope this helps

---

### Post by OneSeventeen on 2007-07-30
Thanks for the tips.

I'm using a case that is designed for CD/DVD duplication, so I don't have much of a choice on drive spacing, but I'm going to try to throw tons more cooling at it than the manufacturer did (especially since I'm adding extra hardware).

Thanks again, I'll see what I can throw together.

---

