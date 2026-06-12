---
title: "How to avoid Intel DRM hardware"
date: 2012-06-29
forum: Hardware
---

### Post by yeehi on 2012-06-29
[COLOR="Red"]This post has been repeatedly edited! Some important information has been changed in this post.[/COLOR]

For some time Intel have been including hardware in their CPUs that restricts the freedom of software. This isn't good. It is commonly known as Digital Rights Management, but is better known as [Digital Restrictions Management]("http://www.fsf.org/campaigns/drm.html").

I spent a bit of time investigating the 'Advanced Technologies' on Intel chips and two in particular to avoid are Intel [TXT]("http://www.gnu.org/philosophy/can-you-trust.html") (Trusted Execution Technology) and [Intel Insider]("http://blogs.intel.com/technology/2011/01/intel_insider_-_what_is_it_no/") (just check out the responses to the Intel article!)

If you have to get an Intel CPU, and would like to get the most modern one without _either_ TXT or Intel Insider, then choose the following:

Second Edit!

The information I have enclosed in quotations was double checked today before I posted it. Somebody has kindly written to me and checked themselves and found that _both_ these CPUs have Intel Insider! I apologise for providing very misleading information.

> [COLOR="Red"]Mobile Processor: Intel® Core™[ i3-2370M]("http://ark.intel.com/products/53442") Processor (3M Cache, 2.40 GHz)
Desktop Processor: Intel® Core™ [i3-2130]("http://ark.intel.com/products/53428") Processor (3M Cache, 3.40 GHz)[/COLOR]

The most recent information regarding these two CPUs taken from the Intel website is here:

[http://ark.intel.com/products/53442/intel-core-i3-2370m-processor-%283m-cache-2_40-ghz%29](http://ark.intel.com/products/53442/intel-core-i3-2370m-processor-%283m-cache-2_40-ghz%29)

[http://ark.intel.com/products/53428/Intel-Core-i3-2130-Processor-%283M-Cache-3_40-GHz%29](http://ark.intel.com/products/53428/Intel-Core-i3-2130-Processor-%283M-Cache-3_40-GHz%29)

I don't know how this mistake came about, as I did check it. I can only assume that Intel updated their website today, perhaps as a result of my enquiries with their technical support staff this afternoon. I hope nobody has bought one of these Intel Insider chips as a result of my post. I used both Wikipedia and the Intel website to find my information.

End of second edit


I apologise for all these edits. I have been checking the Intel website for information and the information seems to have changed again. Perhaps I should delete this post altogether, but some of you have read it and may need to see the latest information.

If for some reason these chips just aren't fast enough, and you have to get an Intel, then the most modern CPU without TXT but (unfortunately) with Intel Insider is below:

[COLOR="red"]Mobile Processor: Intel® Core™ [i7-2670QM]("http://ark.intel.com/products/53469/Intel-Core-i7-2670QM-Processor-(6M-Cache-up-to-3_10-GHz)") Processor(6M Cache, up to 3.10 GHz)[/COLOR]
Desktop Processor: Intel® Core™ [i7-3930K]("http://ark.intel.com/products/63697") Processor (12M Cache, up to 3.80 GHz)

Edited to add:

Be careful! The Intel® Core™ i5-3210M Processor (3M Cache, up to 3.10 GHz, **_rPGA_** has Intel Insider! [COLOR="red"]They both have Intel Insider![/COLOR]

The i7-3930k is not the most modern, but is the most reasonably priced, at about $580. For the very most modern Desktop CPU from Intel with no TXT but unfortunately with Intel Insider, then chose the following, at $1000:

Desktop Processor: Intel® Core™ [i7-3960X]("http://ark.intel.com/products/63696") Processor Extreme Edition (15M Cache, up to 3.90 GHz)


[Write]("http://www.intel.com/about/corporateresponsibility/contactus/index.htm") to Intel. Tell them that you are not happy with their DRM. It won't take a moment. Get your friends to write too!

By the way, if you would like to check whether your hardware supports free software, visit [h-node]("http://www.h-node.org/"). All hardware listed there works without the need for any proprietary drivers, so you will be sure it works with your system.

Your freedom is important!

---

### Post by Yellow Pasque on 2012-06-29
The Intel Insider thing isn't a real problem, and something like TXT (TPM) has been around for a while. If your laptop or mobo allows you to turn off TPM, then you don't have to worry about this crap.

Oh, and AMD is pulling the same crap on their upcoming Fusion chips: [http://www.phoronix.com/scan.php?page=news_item&px=MTExOTA](http://www.phoronix.com/scan.php?page=news_item&px=MTExOTA)

---

### Post by hubertofliege on 2013-02-15
I found this page while searching for a message my system log keeps giving me:

> 
Feb 14 21:22:43 andrew-B53J kernel: [  478.579042] [drm:intel_update_fbc], fbc set to per-chip default
Feb 14 21:22:43 andrew-B53J kernel: [  478.579045] [drm:intel_update_fbc], fbc disabled per module param
Feb 14 21:22:43 andrew-B53J kernel: [  478.795703] [drm:drm_mode_addfb], [FB:31]
Feb 14 21:22:43 andrew-B53J kernel: [  478.811749] [drm:intel_update_fbc], 
Feb 14 21:22:43 andrew-B53J kernel: [  478.811754] [drm:intel_update_fbc], fbc set to per-chip default
Feb 14 21:22:43 andrew-B53J kernel: [  478.811757] [drm:intel_update_fbc], fbc disabled per module param
Feb 14 21:22:44 andrew-B53J kernel: [  479.442326] [drm:drm_mode_addfb], [FB:32]
Feb 14 21:22:44 andrew-B53J kernel: [  479.459652] [drm:intel_update_fbc], 
Feb 14 21:22:44 andrew-B53J kernel: [  479.459659] [drm:intel_update_fbc], fbc set to per-chip default
Feb 14 21:22:44 andrew-B53J kernel: [  479.459663] [drm:intel_update_fbc], fbc disabled per module param
Feb 14 21:22:44 andrew-B53J kernel: [  479.559296] [drm:drm_mode_addfb], [FB:31]
Feb 14 21:22:44 andrew-B53J kernel: [  479.576075] [drm:intel_update_fbc], 

Is there any connection?  Its an "intel CORE i5 vpro inside" chip, according to the sticker on my laptop.

---

### Post by Yellow Pasque on 2013-02-15
> **hubertofliege said:**
> I found this page while searching for a message my system log keeps giving me:



Is there any connection?  Its an "intel CORE i5 vpro inside" chip, according to the sticker on my laptop.
No, this thread is about Digital Rights Management.

Your log is referring to Direct Rendering Manager: [https://en.wikipedia.org/wiki/Direct_Rendering_Manager](https://en.wikipedia.org/wiki/Direct_Rendering_Manager)

---

### Post by MarcoDePollo on 2013-02-15
Just to reiterate what Temüjin said, this isn't really a problem so put the foilhats down and relax.

To quote "update 2" from that blog:

> The only people that will be negatively affected are those who wish to pirate content from services that support Intel Insider.

Intel Insider will not stop you from playing, manipulating or ripping optical media such as a DVD or Blu-ray disk (but those technologies have separate existing safeguards). Intel Insider does not affect P2P services.

---

