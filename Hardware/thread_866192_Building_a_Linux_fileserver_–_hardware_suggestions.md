---
title: "Building a Linux fileserver – hardware suggestions?"
date: 2008-07-21
forum: Hardware
---

### Post by Rhythmdvl on 2008-07-21
Hi folks, 

I’ve done a lot of reading (here and elsewhere) and hope it’s appropriate to post this question in this forum. I’ve reviewed the comptability sticky, and while very, very helpful and appreciated, I’m hoping to get a recommendation more than a check. If this is the wrong place to ask this, please accept my apologies and move or close as you deem appropriate. 

I’ve built higher-end gaming/productivity machines before (about as high as possible without getting into OCing, hence “higher-end”, not “high-end”) and some modest home desktops, but never a dedicated file server and never for Linux. I’m also a complete Linux noob, so am very much out of my element hardware-wise. 

Here’s how it will fit in to our home office: 
Relevant hardware includes: 
Mac OSX 
WinXP box 
Linksys WRT54G router (10/100) 

Activity includes: 
NAS file serving (1-3 MB Word documents, 50-100 MB graphics and Quark files) to both computers. 
Testing Web page design and function (HTML/PHP/MySQL). This is for internal testing only – the box will never be seen outside the LAN. 

That’s it. We basically just need a NAS, but I’d like to take advantage of the Web testing capabilities. No email serving, nothing else that I can think of. 

On the Linux box, I’ll be running Ubuntu Server Edition (with LAAMP), SAMBA, etc. 

I would like two drives in there running in RAID(1) mirroring. 

Our two priorities are reliability and speed. 

Reliability is paramount. One of the reasons for posting is because I understand Linux can be temperamental with some hardware (I also don’t know the hardware requirements of running a file server, so the general compatibility thread, while helpful, doesn’t provide complete guidance for me). We run an editorial and graphic design consultancy from our home office, so uptime and stability is of central importance. I tend to use Asus boards in my personal builds, but am willing to change vendors if there is a reason (i.e., noticeable difference in stability or better customer service). 

Speed is important, but I have no idea how things compare for this use. I know I don’t need a wiz-bang processor, but don’t know at what point I’m sacrificing speed for cost savings. I want it to have enough processing power to run the server, and just a little bit of overhead to make me feel comfortable. Since my old PIII 550 in my learn-Linux platform does all of the above just fine, am I safe in assuming any currently available retail Intel processor will be more than enough? I’ve seen Celeron processors available at Newegg – will those be sufficient? Would a dual-core make any difference given the server’s limited use? 

Since the router isn’t Gigabit capable, a Gigabit board is superfluous. Having it isn’t a problem, and may even be a good thing so future router replacement will increase speed. But unless the price point is very similar, it’s not necessary. 

RAID (1) on the board is essential (I think), as from what I’ve read software-RAID is noticeably slower (feel free to disabuse me if that’s wrong). I don’t fully understand it yet, but a few sites discuss how some hardware RAID isn’t really true hardware raid. Again, if there is a significant difference in speed (remember we’ll only be dealing with 50-100 MB files) I’d opt for the faster solution, though don’t want to spend a bucketload on the difference. 

In retrospect, I’m starting to wonder if RAID worth the hassle (e.g., performance hit, configuration, reading one drive separately from some controllers). I’m considering putting two drives in there, and having a backup scheduled every fifteen minutes. There’s only two of us here, so at most it will only need to copy one or two files every increment. (If you think so, feel free to tell this should be its own thread.)

I’ve always used Western Digital drives (have had great service experiences, which tends to make me loyal), but like with Asus I’ll switch (to Seagate?) if there is a significant difference. 

I don’t need any high graphics capability, but I do have a working, just-pulled-to-upgrade video card (EVGA 7800 GTX PCI-e). If it will keep costs down (and Linux will work with it) I can use it. One benefit to the card is that it has an S-Video out, which means I can use my monitor’s PIP display – a convenience. I know S-Video is crapulent, but it will allow me to keep working on something and monitor progress on the Linux box with minimal input switching. 

So, that’s it in a nutshell (I hope I didn’t go overboard with descriptions—I thought the more information the better). I’d of course like to keep the cost as minimal as possible, but don’t want to chintz out on this build in sacrifice of reliability or speed. Remember that this is just a two-person office, so hits to the server will be minimal -- just us saving our work as we go along. 

My budget is flexible, but given my assumption that I don’t need a lot of processing power, I don’t anticipate this reaching more than $3-500. I have an old Antec case, so a hundred bucks or so is saved (though I may get a new PSU to be safe). 

Any thoughts will be much appreciated. 

Thanks, 

Rhythm

---

