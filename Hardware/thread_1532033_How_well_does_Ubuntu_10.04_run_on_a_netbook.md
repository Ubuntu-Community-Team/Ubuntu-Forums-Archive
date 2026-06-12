---
title: "How well does Ubuntu 10.04 run on a netbook?"
date: 2010-07-15
forum: Hardware
---

### Post by Ncage1974 on 2010-07-15
Ok let me start out by giving some context here. I was looking for  something to consume electronic books. Most of the books i read are of a  technical nature: Programming & Architecture.. Currently i use my  Lenovo 15 in labtop for the purpose. I of course looked  at the kindle. I  seen many reports that the kindle was very bad for technical type  reading. For example it would reformat the source code in books to a  point where it was very hard to read. I really liked the kindle because  of eInk & long battery life but it sounds like for me type of  reading it was going to be a no go. There is of course the Ipad but   500+ for something to consume ebooks...i don't think so. This led me to   thinking on getting a netbook. While not as convient a form factor as a   slate type device its a lot more convenient then lugging around my   labtop.  It also would possibly have some new possibilities. Maybe i   could install ubuntu and get some added advantages. Right now the only   thing i run Ubuntu/Linux on is virtual machines. Maybe this would allow   me to play with some the language/database technologies ive been  wanting  to mess with for a long time: Ruby on Rwieldy for this purpose.  So of course i immediately looked into a kindle. I've read more than a  few reports that the kindle is not good for technical type books because  it will reformat your text and makeails/Python/MongoDB/CouchDB ect. 

There in lies my question. How well does ubuntu 10.04 run on a netbook  (atom based)? I don't know anyone that ownes one. I know Ubuntu runs  extremely well on virtual machines that windows sometimes can seem poky  on. I know there is a netbook edition but for what i'll be doing i'll  probably stick to the standard edition. I heard that if you don't have a  touchscreen netook then the standard edition is better anyways. I'll  just be consuming ebooks, playing with different programming languages /  databases, apache, rack, VIM, some web browsing. I'd like your  thoughts. Is the experience on a netbook with ubuntu sufficiently speedy  or will i be pulling my hair out?

thanks
Ncage

---

### Post by Revolutionary101 on 2010-07-15
I haven't used Ubuntu 10.04 on a netbook. Although, here is a video that shows Ubuntu 10.04 on a netbook.

[http://www.youtube.com/watch?v=8fff6ql61jU](http://www.youtube.com/watch?v=8fff6ql61jU)

I watched the video and it looks like a netbook with Ubuntu 10.04 on it will be able to handle what you need it for.

---

### Post by rg4w on 2010-07-16
I have an EeePC 901 which I chose because it's the smallest netbook I could find and all solid-state w/no HDD.

When I first got it I put Ubuntu 9.10 on it, and it was reasonably good but with only 600 vertical pixels it felt as cramped as the 901's small keyboard.

So I gave the Netbook Remix a try, and found that I love it.  A lot.

Ubuntu NBR makes really good use of the screen space by using a window manager enhancement that opens windows maximized in a way that puts the title bar/close box in the top panel, saving some 20+ pixels of what would otherwise be functionally dead space.

I also appreciate the simplicity of the menu system in NBR, making most things just one click away without having to go through pull-down menus.

Both the normal Ubuntu and NBR run reasonably well on that low-powered system, but it does feel as though NBR is a little bit more responsive (though that may be subjective; I've done no benchmarking, and I so love the NBR design my perceptions may well be biased <g>). Neither is particularly impressive in terms of performance, but I can't blame them for the low specs of the 901 hardware; given what they have to work with on that tiny machine I'm impressed.  I run Google Earth on it acceptably well, and have installed R and R Commander and while I'm not quite doing the most massive analytics on the planet I find they work well on this modest device.  Even LinCity holds up nicely on the EeePC, and Hulu desktop is only slightly choppy at times.

In terms of compatibility, I have no experience with Lenova laptops yet but on my EeePC everything worked out of the box, including webcam, wifi, all of it.  Not a tweak needed.

The only weakness I found was in updating:  if you start a long update and walk away the system may sleep toward the end, and in my case that left me with a FUBAR grub.  I re-installed fresh and now I'm more careful about that, and have had no problems since.  I'd chalk that up as a noob error (though for the sake of evangelism I wouldn't mind seeing the updater become more robust; there are at least a few people even dumber than me).

With coding, you face a challenge no OS can surmount:  the limit on vertical space means you won't see much of your code at any given time.  I find I do very little coding on my netbook, but when it's necessary it can be at least acceptable.  I should note though that I haven't run Eclipse on it; I use a custom IDE that's not as full-featured but is much lighter on resource requirements.  I'd be interested in hearing how your coding goes on your netbook with whatever tools you use.

For my full-sized systems I prefer having the desktop of Ubuntu, but for my netbook I really like NBR, and have recommended it to other netbook users.

---

### Post by snowpine on 2010-07-16
Ubuntu is one of the premier netbook distros. :)

Here's a hardware compatibility list for you: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

System76 sells netbooks with Ubuntu preinstalled.

---

### Post by camorri on 2010-07-16
I bought a HP Mini with a 160 gig HD, gig og ram etc. More or less what most netbooks come with for just over $300. 
Everything worked out of the box. I deleted all the partitions the system came with, set up a / swap and home. 

The only thing I would suggest you watch for is the type of wireless card. There are a lot of posts with problems getting broadcom cards to work. Mine is an Antheros chip set. 

I don't do much programming, so I can't any comment there. 

Don't expect blistering performance from the Atom, it is adequate for most common purposes. 

Buy a 6 cell battery if unplugged time is an issue. You can save some if a 3 cell battery is enough. 

I do find the built in mouse pad a little touchy. It is easily bumped when typing, then you get to look for the mouse pointer, and any messed up input you may create. 

I bought this thing for traveling. The small form is very nice. Much better than dragging a full size laptop along. 

The 1024x600 screen is bright and easy to read. More lines would help, this is part of the trade off, size vs potability. 

Some thoughts, hope this helps.

---

### Post by Ncage1974 on 2010-07-16
Thanks guys for all the helpful replies. ya i won't be doing anything to intensive just playing around pretty much. Hopefully its fast enough for my needs. It should be since linux run just fine on my phone (android) ;). Hopefully VIM doesn't max out the CPU ;). I'm actually looking at the Asus 1001P since its one of the top rated netbooks out there and gets awesome battery life. Unfortuantely i have read there are some problems with the wireless card and ubuntu 10.04 with a variety of solutions. I'll just have to work through them i guess. I also looked at the toshiba netbook which also is rated very well and it seems to be having a problem with sleeping/hibernating with linux. So it seems like each netbook has its own issues ;). I can't imagine using Windows 7 on of these things. I love windows 7 but i know how it runs on my Lenovo with a Core2 + 4GB of ram. Its not slow by any means but its not super quick either.

Anyways this will to hold me over until a better rendition of a slate type device comes out (Android, ChromeOS, Or Windows Phone 7 OS Based (i won't accept windows 7).

---

### Post by AltomineUK on 2010-07-17
Type: Netbook

Processor: Intel Atom N270 @ 1.60 GHz. Cache: 512kb.

RAM: 1GB

Graphics chipset: Intel 945 GME 128MB Shared.

HDD: 160 GB

Display: 1240 x 600 LED 

Performance? Well it runs much much faster than I thought it would. 

Sorry for the late info.

---

### Post by MattBD on 2010-07-18
Dell Mini Inspiron owner here. I run Ubuntu Netbook Edition on mine and it runs great. I dual-boot with XP and performance is far better on UNE than on XP, and in general it's just a lot better. I would go for the netbook edition rather than the regular one, though. Works great for programming with Vim, and I use Chrome as the web browser, which is pretty efficient and works very well.

---

