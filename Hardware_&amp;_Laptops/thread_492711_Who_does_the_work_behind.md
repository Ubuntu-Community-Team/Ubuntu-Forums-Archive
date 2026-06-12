---
title: "Who does the work behind?"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by YigalB on 2007-07-05
I wonder: who does the real work behind? for example: someone must write and integrate software drivers for the hardware behind, such as chipsets.
As new chipsets are introduced very often, there must be a real activity behind the scenes - how does it work? who pays for all that?
This leads me to the next question: is there a list with all chipsests that Ubuntu supports? or plan to support? This should be a relevant question for every one who purchase a new computer, i guess.

---

### Post by avik on 2007-07-05
As far as who's doing the work, it's the community.  That's the beauty of open source: people who want to fix something have the power to.  They don't ask for payment, they just do the work.

That much I do know...

---

### Post by gercokees on 2007-07-05
And this is done in a tremendous pace. Take a look at this site, for example:
[http://www.ubuntustats.com/](http://www.ubuntustats.com/)

---

### Post by IntuitiveNipple on 2007-07-05
Despite the 'community' ethos the GNU/Linux kernel is developed mainly by a small core of developers employed by a similarly small group of companies and organisations.

See the LWN article [Who wrote 2.6.20?]("http://lwn.net/Articles/222773/") for the tables.

---

### Post by avik on 2007-07-05
> **IntuitiveNipple said:**
> Despite the 'community' ethos the GNU/Linux kernel is developed mainly by a small core of developers employed by a similarly small group of companies and organisations.

See the LWN article [Who wrote 2.6.20?]("http://lwn.net/Articles/222773/") for the tables.

But that doesn't mean those who changed only a couple of lines didn't do anything.  Every contribution is important, and some of those smaller things are only possible because these people were able to add something.  Besides, code isn't the only way to help in the writing of the kernel; there are people submitting bug reports and relevant information, and so much more.

---

### Post by YigalB on 2007-07-06
"As far as who's doing the work, it's the community"

That doesnt make sense when are are talking chipset support. Chipset support requires tight connection to the hardare, and mostly cant be done without gettiing a detaied spec of the internals of the chipset, which is confidential. So there must be some connections to the chipset vendors, and this cant be done by "community", since NDAs should be signed, etc.

Also, I saw no answer for my main question: where can I find a support matrix for chipsets?

---

### Post by az on 2007-07-06
> **YigalB said:**
> "As far as who's doing the work, it's the community"

That doesnt make sense when are are talking chipset support. Chipset support requires tight connection to the hardare, and mostly cant be done without gettiing a detaied spec of the internals of the chipset, which is confidential. So there must be some connections to the chipset vendors, and this cant be done by "community", since NDAs should be signed, etc.?

Well, in some cases, the manufacturer releases a linux driver.  People who are interested in getting it to work tweak and integrate the driver into the kernel.  Once there is a big enough community around the project, it has a chance of getting into the upstream kernel.

When the manufacturer releases anoter release of the driver (for say, new hardware) the established community makes sure it can integrate with the kernel.

In other circumstances, the driver is just reverse-engineered.  

With only a very small number of exceptions, that's how all of the drivers in the linux kernel are handled.

> **YigalB said:**
> "
Also, I saw no answer for my main question: where can I find a support matrix for chipsets?

It would help if you specified the kind of problem you are having.

---

### Post by d3n0 on 2007-07-06
> **IntuitiveNipple said:**
> Despite the 'community' ethos the GNU/Linux kernel is developed mainly by a small core of developers employed by a similarly small group of companies and organisations.

See the LWN article [Who wrote 2.6.20?]("http://lwn.net/Articles/222773/") for the tables.

[http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=571&mode=thread&order=0&thold=0](http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=571&mode=thread&order=0&thold=0)

---

### Post by YigalB on 2007-07-06
> **az said:**
> 
It would help if you specified the kind of problem you are having.

OK - Here is my problem: I am going to buy 5 computers for a youth club, and I have several offers from several vendors, including motherboard details, so I also have a list of chipsets.
How can I tell which of these chipsets are already supported or p[lanned to be supported? 
For example, MSI and Gigabyte claim they have Linux driver support in their web site, but no clue about Ubuntu. That the same answer I got from their tech support team.
So I assume there is a list of chipsets or motherboards that are supported, and I was searching Ubuntu web for that list, but failed to find.

So how can I confirm I will not have compatability issues prior to purchasing stage?

---

### Post by az on 2007-07-06
> **YigalB said:**
> OK - Here is my problem: I am going to buy 5 computers for a youth club, and I have several offers from several vendors, including motherboard details, so I also have a list of chipsets.
How can I tell which of these chipsets are already supported or p[lanned to be supported? 
For example, MSI and Gigabyte claim they have Linux driver support in their web site, but no clue about Ubuntu. That the same answer I got from their tech support team.
So I assume there is a list of chipsets or motherboards that are supported, and I was searching Ubuntu web for that list, but failed to find.

So how can I confirm I will not have compatability issues prior to purchasing stage?

If these are commodity off-the-shelf motherboards, I wouldn't worry.  I don't think there is a motherboard for a desktop computer on the market that doesn't run linux.  You will run into compatibility issues with things like some wireless devices, printers, and graphics devices.  Ubuntu ships with some non-free wireless and graphics drivers so that even if there is no native linux driver, the devices do work.

So, unless these motherboards are cutting-edge and include some wierd SATA RAID hardware, I wouldn't worry too much.

If you can find one in a running computer, you can always boot the live cd to confirm that it works honky-dory.

---

### Post by YigalB on 2007-07-06
> **az said:**
> If these are commodity off-the-shelf motherboards, I wouldn't worry. 

I will do so because I have no choice. I still think compatability list brings Ubuntu into a better position, and the strange thing is that the info exists somewhere.

Yet again - what choice do I have?

---

### Post by YigalB on 2007-07-06
> **az said:**
> If these are commodity off-the-shelf motherboards, I wouldn't worry. 

So it seems I have no much choice, do I?

I still think that compatability list is something nice to have, and the info is avilable. This will give people more confidence.

Atthis stage, I am not worried.
Within few days I will get the computes, and I will be able to report if the "dont worry" approach succeeded.

Thanks.

---

### Post by az on 2007-07-06
> **YigalB said:**
> So it seems I have no much choice, do I?

I still think that compatability list is something nice to have, and the info is avilable. This will give people more confidence.



Sure, but you can't account for every single chip on every single motherboard.  Especially when they all work.

Like I said, most of the hardware problem are with wireless, printers and some graphics cards.  Other doodads like webcams may or may not pose a problem.

The best strategy is to ask the vendor.  It really is their job to do the research, isn't it?  And if hardware sellers knew that customers were buying for linux, this problem would eventually go away.

---

### Post by YigalB on 2007-07-07
> **az said:**
> Sure, but you can't account for every single chip on every single motherboard.  Especially when they all work..
I found in MSI web pages several motherboards which specifically said they will not work with Linux.
And why can't one account them? Comatability list is part of any product manager work. There is no much work here - just being orgenized.

> **az said:**
> The best strategy is to ask the vendor.  It really is their job to do the research, isn't it?  And if hardware sellers knew that customers were buying for linux, this problem would eventually go away.
The vendors are not doing it. So what's now? to say it's their fault?
I agree it's their interest to that, but it's Ubuntu's duty to demonstate it.

Perhaps the best thing is to adopt the USB way: they have plugfest, in which many vendors come and plug USB products and prove it works with others, and even meaure peformance etc. 
Imagin a plugfest where many vendors of hardware come and get a qualification from Ubuntu that their hardware is 100% workinng with Ubuntu? both sides will benefit from that.

---

### Post by IntuitiveNipple on 2007-07-07
Have you checked out the [Hardware Compatibility Guide](http://ubuntuforums.org/showthread.php?t=182834) and [Desktop Hardware Compatibility List](http://ubuntuforums.org/showthread.php?t=361236) ?

---

### Post by YigalB on 2007-07-07
> **IntuitiveNipple said:**
> Have you checked out the [Hardware Compatibility Guide](http://ubuntuforums.org/showthread.php?t=182834) and [Desktop Hardware Compatibility List](http://ubuntuforums.org/showthread.php?t=361236) ?

That what I was looking for.
Although the list is too short, ans probably needs more maintenance, that's it!
Thanks.

---

### Post by az on 2007-07-07
> **YigalB said:**
> I found in MSI web pages several motherboards which specifically said they will not work with Linux.


In my experience, those sort of pages are usually outdated or simply the vendor stating they don't support linux.  That doesn't mean that someone else hasn't written a driver or that the thing doesn't work with a generic driver.  Can you post a link?

If a component of a motherboard on a desktop computer does not work in linux, it's a bug and those are usually fixed quite fast.

---

