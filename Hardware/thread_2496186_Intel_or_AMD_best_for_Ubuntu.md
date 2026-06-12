---
title: "Intel or AMD best for Ubuntu?"
date: 2024-03-17
forum: Hardware
---

### Post by dialyt-7 on 2024-03-17
I’m looking to purchase a laptop and I can have a choice of these two CPUs for the model I’m looking at. 

13th Generation Intel® Core™ i5-1335U Processor (E-cores up to 3.40 GHz P-cores up to 4.60 GHz)

AMD Ryzen™ 5 7530U Processor (2.00 GHz up to 4.50 GHz)

Which would be best for Ubuntu, Linux Mint, Fedora? 

Or does it not matter?

---

### Post by TheFu on 2024-03-17
16400 - Core i5-1335U
16400 - Ryzen 5 7530U

So from a performance standpoint, they are so close to the same that it doesn't matter.  

Next, I'd look at price and the laptop vendor.  I've been unhappy with most vendors after 30 yrs.  Today, I'm left with just 2 vendors I'd even consider for a laptop like this.  Dell or Lenovo.  Both are well supported, eventually, by Linux.  

Then I'd look at price and ports for external connections.  For example, I want a GigE rj-45 always.  I'm tired of being forced to carry a USB3-to-Ethernet adapter around for places that don't allow wifi and I never use wifi at home.  It is a corporate and client security problem.  Wifi isn't secure.

Intel has more "sensors" built-into the kernel. With many AMD CPUs, sensor support comes later, if ever.  Since I run 5.xx kernels, the sensor support for my CPU isn't there beyond basics.  I've read that it will be better in the 6.x kernels.

Looks like that i5 has Xe graphics, which hasn't been well supported. Recently, in the last month, I've been seeing more and more about Xe GPU support in Linux.  That means in 6 months, the support will finally get to our distros and us.  Are you willing to limp for 6 months?

The Ryzen 7xxx series is also really new, so it bleeds a bit.  When it comes to support for new hardware, it is best to wait about a year for the most seamless installs.  Really new hardware takes time for the new chips with new features to be added to the kernel.  Additionally, new wifi, sound, GPUs are usually added to those new CPUs, so each of them needs time for the driver sub-projects to get a device and code for the specific chips.  

With all that said, and even though I prefer AMD for my desktops and servers - they have longer motherboard socket support and far more CPU upgrade paths than Intel does.  Every Intel CPU upgrade I've ever done required a new motherboard, so instead of a $130 cost, it is a $230+ cost to "upgrade".  However, with a laptop, the CPU isn't going to be upgraded, ever, so only the SSD/HDD and RAM are considerations.  Flip a coin for which is better.

I have specific laptop size and weight requirements.  I like 13.3 or smaller screens and ~ 2lbs with 1080p screens.  That usually would remove one of the vendors or cause the price to be massively different, so my choice would be made.

And since I give presentations, I need an HDMI port for output to a projector.

Lastly, I've had 1 AMD laptop and at the time, AMD power use was much higher than intel, so instead of 6 hrs of battery, I'd get 2 hrs.  I think that's all changed, but I KNOW that Intel laptop power use can get 10+ hours, if the battery included is sufficient and there isn't a discrete GPU.  I had a 2 lb 13.3 1080p laptop that got over 10 hrs of my use in 2016. I just turned the screen to be dimmer when running on battery.  I'd travel to client locations and didn't take a charger.

> Ubuntu, Linux Mint, Fedora? 
Depends on your personal preference.  Fedora has shorter support periods, so they have newer kernels.  But expect to do a system upgrade every year.  Ubuntu/Mint are on the LTS cycles which are 3 or 5 yrs from Canonical, depending on your chosen DE. For most people, it makes the most sense to upgrade systems every 2 yrs.

---

### Post by MAFoElffen on 2024-03-17
+1 with TheFu -- Even on brands.

I like both Dell and Lenovo. Both sell laptops with Ubuntu pre-installed...  I used to do onsite warranty support fro Dell, Lenovo, and HP. HP makes their hardware more ingrained with Windows, even though they do offer a very few (select) machines with pre-installed Ubuntu. Dell even has a Linux repo for their hardware drivers.

For example: With Lenovo (on their official website) > Go to "Build Your Own" > Select the model (I know they got their ThinkPads certified for Ubuntu) and hardware options > When you get to the OS choice, select "Ubuntu" << That is actually -$140 cheaper than getting it with Windows 11!

For Dell models: Dell XPS, Precision, Latitude, and OptiPlex systems can come with Ubuntu pre-installed from the factory.

EDIT: (Further)

As a Certified Warranty Tech for all 3, I would get frustrated calling their Tier 1 Support for Ubuntu pre-installed machines... Their Support Website section refers their customers to this Forum for Ubuntu OS support. But we were still required to call Tier 1 for the warranty support coordination (period)...

So just be prepared. I would occasionally have to tell their support people, that their own company does sell devices that are pre-installed with "Ubuntu" Linux. That they needed to be more aware of what they supported.

---

### Post by Yellow Pasque on 2024-03-18
> **dialyt-7 said:**
> Or does it not matter?

Both the CPU's you list should work well with upcoming Ubuntu 24.04 LTS

> **TheFu said:**
> Looks like that i5 has Xe graphics, which hasn't been well supported. Recently, in the last month, I've been seeing more and more about Xe GPU support in Linux.  That means in 6 months, the support will finally get to our distros and us.  Are you willing to limp for 6 months? 

Note that "Xe" is a general marketing term and refers to different generations of hardware (kind of like "Centrino"). Support for Raptor Lake graphics (what OP is asking about) has been out for a while since it's similar to Tiger Lake. It should be fine in 24.04. The Arc/Alchemist GPU's, also branded under "Xe", might be a bit rougher, though I just helped out someone with Arc graphics on a Meteor Lake laptop and they seemed happy with Ubuntu 23.10: [https://ubuntuforums.org/showthread.php?t=2495988](https://ubuntuforums.org/showthread.php?t=2495988)

---

### Post by karyk on 2024-03-20
How do you find the Dell laptops with Ubuntu pre-installed?  I'm not seeing that on their site.  Chrome OS, yes.

Also, is there a price advantage at all?  The way Dell works is if you make even a tiny change you might pay a lot more over their pre-configured system, so say 16GB of ram rather than 8GB might cost a ridiculous $250 or more!  If no price advantage I'd rather get Windows, do a backup of that setup, and then install.  Thoughts?

---

### Post by TheFu on 2024-03-20
> **karyk said:**
>  If no price advantage I'd rather get Windows, do a backup of that setup, and then install.  Thoughts?

I have a new SSD and swap their SSD, before ever booting, and put mine in before doing anything else. This way, if any warranty work is needed, I can put their SSD/HDD back in and ship it for warranty work.  After the 1 yr warranty period is up, I have a spare storage device, since I'll not be loading MS-Windows ever anyway.

---

### Post by karyk on 2024-03-21
That might not be a bad idea since the only SSD I've ever had fail was an OEM Dell unit.  Your way you can pick the brand/model for reliability.

---

### Post by TheFu on 2024-03-21
> **karyk said:**
> That might not be a bad idea since the only SSD I've ever had fail was an OEM Dell unit.  Your way you can pick the brand/model for reliability.

It was just another option to consider, but if you are already overflowing with backup storage devices, like a spare SSD, I'd use one you already have.  I don't use SSDs for backups, but for spares and for USB-based sneaker*net needs on devices that may not have as much internal storage as I'd like.  For example, when I travel with a laptop, it is easier for me to load up a few movies and a few hundred GB of music on an external USB-SSD for hotel/evening entertainment.  A $13 USB-to-SSD enclosure makes that possible.

Options. Lots of options.

---

### Post by MAFoElffen on 2024-03-22
> **karyk said:**
> How do you find the Dell laptops with Ubuntu pre-installed?  I'm not seeing that on their site.  Chrome OS, yes.

Also, is there a price advantage at all?  The way Dell works is if you make even a tiny change you might pay a lot more over their pre-configured system, so say 16GB of ram rather than 8GB might cost a ridiculous $250 or more!  If no price advantage I'd rather get Windows, do a backup of that setup, and then install.  Thoughts?
I just got off chat with a Dell Sales Rep.

You can order these 4 Dell Laptops with Ubuntu Pre-Installed. You can also change the memory & storage options:

[https://www.dell.com/en-us/shop/dell-laptops/latitude-5540-laptop/spd/latitude-15-5540-laptop/gctol5540usvp?redirectto=SOC&configurationid=3c46e837-8404-4f38-8b7b-948d979533b9](https://www.dell.com/en-us/shop/dell-laptops/latitude-5540-laptop/spd/latitude-15-5540-laptop/gctol5540usvp?redirectto=SOC&configurationid=3c46e837-8404-4f38-8b7b-948d979533b9)
[https://www.dell.com/en-us/shop/dell-laptops/precision-3581-workstation/spd/precision-15-3581-laptop/xctop3581usvp](https://www.dell.com/en-us/shop/dell-laptops/precision-3581-workstation/spd/precision-15-3581-laptop/xctop3581usvp)
[https://www.dell.com/en-us/shop/dell-laptops/precision-5680-workstation/spd/precision-16-5680-laptop/xctop5680usvp](https://www.dell.com/en-us/shop/dell-laptops/precision-5680-workstation/spd/precision-16-5680-laptop/xctop5680usvp)
[https://www.dell.com/en-us/shop/dell-laptops/xps-13-plus-laptop/spd/xps-13-9320-laptop/usexcucto9320rpl01?ref=variantstack](https://www.dell.com/en-us/shop/dell-laptops/xps-13-plus-laptop/spd/xps-13-9320-laptop/usexcucto9320rpl01?ref=variantstack)

The last one. the XPS-Plus, they just changed the name to that, That Laptop was previously called their XPS Pro-Developer.

It looks like going through them, that you only save about $68 having Ubuntu Pre-Installed, rather than Win11. But then they stand behind it on their warranty.

---

### Post by karyk on 2024-03-23
Thanks, so it's not every device, apparently.  Too bad. I'd like to see some low end choices. 

But on that last link you would save $400 going with Windows, or $350 going with Windows Pro.  That's the type of pricing thing I was talking about with their site.

---

### Post by Yellow Pasque on 2024-03-23
> **karyk said:**
> But on that last link you would save $400 going with Windows, or $350 going with Windows Pro.  That's the type of pricing thing I was talking about with their site.

Yeah, that's crazy that a free operating system costs $400 more than one with licensing fees. Why would anyone get a laptop with Linux preloaded with that price disparity? Just get it with Windows, wipe it, and install Linux.

---

### Post by him610 on 2024-03-24
> Yeah, that's crazy that a free operating system costs $400 more than one with licensing fees
It is the process that involves something out of the ordinary, and I would guess that M$ subsidizes it somewhat.
Just do like TheFu suggested in #6, order the Win machine and replace the boot device with you own. That saved $400 can buy a lot of NVME/SSD.

---

### Post by MAFoElffen on 2024-03-24
I'm thinking of talking what Dell Sales and asking them the why of that. Just to stir things up. That does not make sense.

---

### Post by karyk on 2024-03-25
I think it's simply because they have those pre-boxed with only Windows.  It's like the changes I mentioned originally where a small change in memory will cost a fortune.  The Dell site is very odd that way, and pre-boxing is the only reason I can think for the change.

Back in the day each major auto manufacturer made about 30,000 (or some huge number) models of car if you considered all the option possibilities.  They've limited that a lot today by packaging options together, and requiring other options to get a particular option.  Apparently reducing the number of different type models going out the door greatly reduces costs.

---

### Post by Yellow Pasque on 2024-03-25
> **karyk said:**
> Back in the day each major auto manufacturer made about 30,000 (or some huge number) models of car if you considered all the option possibilities.  They've limited that a lot today by packaging options together, and requiring other options to get a particular option.  Apparently reducing the number of different type models going out the door greatly reduces costs.

Yeah, I get all that, but $400(!) is a lot for a product in in the $800-1000 range

---

### Post by MAFoElffen on 2024-03-26
I pulled a request to the Dell Sales Team to answer that for me... It doesn't make sense to me that a free OS (Ubuntu) is there as more than something that has a paid License (Win 11 Pro). Especially when I told them that Lenovo, for their Ubuntu Preinstalled Laptops, actually have a cost savings... Sort of like, if you want to match their offer... follow "common sense".

I am an IT Consultant. I know how to work this. If they want recommendations from me to my customers, that might mean sales for them, I need some answers. That really didn't make sense to me. Honestly.

We will see what happens. I should get an email in a few hours.

If it is more expensive, then I will tell them that is makes more sense to buy a Win11 machine and replace the storage drive, to keep the original drive for warranty, unchanged. While installing Ubuntu on a new, fresh drive. Doing that would still be cheaper than what was in those links, adding a premium for Ubuntu being pre-installed.

because if I order a Dell PE Server, the base price is without an OS. If I order it with Win Server datacenter , for 4 cpu's. that is around $4K. If I order it with vSphere, RedHat, SUSE or Ubuntu, the price is $0...

Why is their other products the reverse of that?

---

### Post by Yellow Pasque on 2024-03-27
> **MAFoElffen said:**
> <Stuff that makes too much sense>

You go, man. Fight corporate stupidity!

---

### Post by MAFoElffen on 2024-03-27
> **Yellow Pasque said:**
> You go, man. Fight corporate stupidity!
It is just that... They are conflicting with "their own" pricing structures... LMFAO!!!

In my onsite warranty tech certifications with Dell, Lenovo & HP... HP also has some pre-installed Ubuntu Machines, but I would not recommend them for several reasons...

The top being, that the versions of Ubuntu they do pre-install are not what I would consider as 'current'. Second, their choices in their BIOS, which are not Linux friendly.

---

