---
title: "Ubuntu running slowly on my machine."
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by MohanaRao on 2009-08-25
Hi sir/madam,

 I am newly started using ubuntu with dual boot and installed ubuntu 9.04 in unallocated space in harddisk 20gb. My harddisk capacity is 80gb. Ubuntu is running slowly on my machine.
     This is my system configuration.
      Processor -  Intel celeron 3.06GHz.
      Ram -          1.5GB.
      HDD-           80GB.
      
I don't have graphic card on my mohterboard, but i am using compiz effects it's working fine without any problem. And one more thing is when i am viewing youtube videos the processor running at its peak level continuoesly. I tried both browsers firefox and opera. Apart from that everything is working fine. So suggest me what are the changes should i make to run ubuntu smoothly. If you need further information i will provide. Thanks in advance and thanks for spending your time for me. 

Regards, 
Mohan

---

### Post by Mark Phelps on 2009-08-25
You say that Ubuntu is running slowly ... but the only specifics you provide is that YouTube videos are slow and you admit that you're using both onboard graphics and have compiz enabled.  You also didn't mention your onboard video chip but I wouldn't be surprised if it was an ATI X300 or some other low-end video processor.  Which means, you're likely using an open source video drivers.

That's the price of using video effects with onboard graphics.

If you want more responsive video, disable video effects, add a decent video card, or both.

---

### Post by MohanaRao on 2009-08-25
First of all Thanks for your reply 
This is my video card.
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02).
This is onboard graphics card. i don't have any other graphics cards and even i tried with swiftfox browser it wouldn't solve my problem.

---

### Post by Mark Phelps on 2009-08-25
> **MohanaRao said:**
> First of all Thanks for your reply 
This is my video card.
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02).
This is onboard graphics card. i don't have any other graphics cards and even i tried with swiftfox browser it wouldn't solve my problem.

OK, so you have the infamous Intel video chip.  I don't personally have experience with these, so I suggest you do a search in the Video subforum using the Intel chip model number.  You should then be able to find a number of posts dealing with that Intel chip and video issues.

---

### Post by P4man on 2009-08-25
You could try turning of visual effects and see if things improve. But its a really crappy onboard videocard you have there. 

Perhaps there are ways to squeeze more performance out of it, but I would consider buying the cheapest somewhat recent discrete nvidia card you can find, even something like a cheap, 6600 would be an order of magnitude faster than that intel 945 and hardly cost anything at all. If you lived any closer, Id say drop by and pick one up :)

---

### Post by P4man on 2009-08-25
ok, I searched a bit further, and there seems to be a bug that relates to your videocard and affects compiz(desktop effects)  and videoplayback performance:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/375264](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/375264)

It states a bugfix was released in june, so did you install all available upgrades? If not, its worth trying.

---

### Post by MohanaRao on 2009-08-26
> **P4man said:**
> You could try turning of visual effects and see if things improve. But its a really crappy onboard videocard you have there. 

Perhaps there are ways to squeeze more performance out of it, but I would consider buying the cheapest somewhat recent discrete nvidia card you can find, even something like a cheap, 6600 would be an order of magnitude faster than that intel 945 and hardly cost anything at all. If you lived any closer, Id say drop by and pick one up :)


But this crappy graphics card works fine with windows xp, i getting the problem when login to ubuntu. Taking new graphics card  not good solution in my concern.

---

### Post by inobe on 2009-08-26
> **MohanaRao said:**
> But this crappy graphics card works fine with windows xp, i getting the problem when login to ubuntu. Taking new graphics card  not good solution in my concern.

what they are trying to say is' with desktop affects disabled you will experience better graphics performance, it would actually almost equal in comparison for all platforms when it comes to performance.

compiz affects requires a little more than what onboard intel graphics has to offer, disabling affects will give you much better performance.

:)

---

### Post by zkriesse on 2009-08-26
Intel combined with Compiz extra effects equals CRAPPY VIDEO AND DISPLAY! Trust me, it's not your fault it's just how it is. Disable or uninstall the effects and it should run alot better

---

### Post by MohanaRao on 2009-09-06
@above Thanks you your response.
 
 As you suggested me i disabled all the compiz settings but my problem didn't resolved completely because before disable the compiz effects my cpu usage is 100% and after disabling it cpu usage 80%(when i am browsing the internet). i am totally frastrated with that. I wanna go for new 512mb AGP card nvidia, so suggest me best model for me as per my system configuration. 

cpu - intel celeron 3.06ghz
hdd - 80gb
motherboard - intel 945 chipset.
Ram - 1.5gb.
swap memory - 4gb.

Thanks you guys.

---

### Post by orlox on 2009-09-06
Well, I've used a lot of time checking out different alternatives to get decent performance on intel cards, and I found a decent solution recently...

This solution is...update to karmic! Well, this is actually a good solution for me. I'm used to trouble so  can easily get myself using alpha versions (which, actually are impresively stable)...but perhaps some people wont get past some annoying details, or the large amount of weekly updates...

There are although ways to improve performance in jaunty, but given the current state of karmic, I think the most stable and simple option is using karmic.

Perhaps you could try the alpha 5 of karmic. If you dont have anything relevant on your ubuntu partition yet, you could download the iso and give it a try. If you have some small issues with that, id reccomend you to keep with it, cause almost everything should be sorted out in a month when karmic is near beta.

But, if you can keep up living with a reduced performance, you can take the safe option and just wait till the release of karmic in october.

---

