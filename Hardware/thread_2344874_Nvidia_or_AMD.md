---
title: "Nvidia or AMD?"
date: 2016-11-28
forum: Hardware
---

### Post by jackbn on 2016-11-28
I have little experience with Ubuntu, beyond the GUI.
Presently have an i7-6700K with Samsung 1TB SSD and 32GB of RAM, now using the CPU graphics and Ubuntu 16.04.
Not big on gaming, but want to be able to run two or more 4k videos at once, as well as less demanding processes.

Thinking about the new graphics cards, like the Nvidia 1060 or Radeon RX 480.
Which driver is simpler and less troublesome to install: Nvidia or AMD?

---

### Post by oldfred on 2016-11-28
I have always use nVidia, but now my requirements are fine with the Intel internal video. I used to add a $100 video card just to have decent video, but newest Intel has enough horsepower for all my needs now.

This site does comparisons with either the open source drivers which are limited for both nVidia & AMD or the closed souced drivers. But AMD is in middle to changing from closed source to just the open sourced versions.
       AMDGPU-PRO vs. NVIDIA On Linux With OpenGL & Vulkan
[http://www.phoronix.com/scan.php?page=article&item=2016-tday-vulkan&num=1](http://www.phoronix.com/scan.php?page=article&item=2016-tday-vulkan&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia-linux-10years&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-linux-10years&num=1) 
    
 The Best, Most Efficient Graphics Cards For 1080p Linux Gamers Sept 2015
[http://www.phoronix.com/scan.php?page=article&item=1080p-b-value&num=1](http://www.phoronix.com/scan.php?page=article&item=1080p-b-value&num=1)
Why you often have to install the proprietary driver
The Dirty List Of GPUs With Open-Source Drivers Gone Wildly Wrong
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwNjU](http://www.phoronix.com/scan.php?page=news_item&px=MTcwNjU)
18-Way GPU Linux Benchmarks, Including The Radeon RX 460 & RX 470 On Open-Source
[http://www.phoronix.com/scan.php?page=article&item=amd-rx460-rx470&num=1](http://www.phoronix.com/scan.php?page=article&item=amd-rx460-rx470&num=1)
22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1) 

 Open Source only drivers AMD & nVidia cards 2015 Sept
[http://www.phoronix.com/scan.php?page=article&item=open-power-value&num=1](http://www.phoronix.com/scan.php?page=article&item=open-power-value&num=1)

---

### Post by gtippitt on 2016-11-28
NVIDA cards will cost a bit more than ADM/ATI cards but they are dead simple to use either the open source or NVIDA drivers with UBUNTU.  I have used NVIDA cards for GPU number crunching for years without a problem.  I bought a new AMD RX470 and a RX480 a month ago to test and have not gotten them to work in any machine I've tested.  AMD drivers and support for Linux are useless.

For what you have described the NVIDA 1060 is probably overkill.  The NVDIA 1050 will work nicely for you.  Besides costing half as much as the 1060, it is smaller and draws less power, which may save headaches when upgrading.  The link below is great for comparing the capabilities of different cards and GPUs. For 4K video, older cards might be fast enough but not support [HDMI2]("https://en.wikipedia.org/wiki/HDMI#Version_comparison") for 4K

[https://www.techpowerup.com/gpudb/](https://www.techpowerup.com/gpudb/) 

Greg

---

### Post by QIII on 2016-11-29
AMD support is useless?

Not according to my testing or phoronix.com's.  I've encountered no problems at all installing AMDGPU or AMDGPU-PRO and getting them to run.  I've encountered one user on the Forums wh has encountered issue with the install script.

If you would like to say that it would be wise to be very cautious about purchasing an AMD card right now due to a complete transition in how AMD will be supporting Linux going forward - with the understanding that AMD is working extremely closely with open source developers - then you would be accurate.

---

### Post by jackbn on 2016-12-02
Thanks guys.  I have always used Radeons before when I needed a video card, but in light of your comments, I am leaning toward the Nvidia 1060.

The most telling comment is from gtippet, suggesting that the 1060 may be easier to install successfully.
Moreover, AMD could be in trouble if their new CPUs disappoint the public.

A few years ago I installed a lower-to-middle grade Radeon on Ubuntu. 
As I recall, the Radeon performance was was no better than the CPU alone. 
I never learned why (perhaps driver installation), and simply quit using video cards.
That Radeon experience is why I am most concerned about ease of driver installation.

---

### Post by happydog500 on 2016-12-02
> **QIII said:**
> AMD support is useless?

Not according to my testing or phoronix.com's.  I've encountered no problems at all installing AMDGPU or AMDGPU-PRO and getting them to run.  I've encountered one user on the Forums wh has encountered issue with the install script.

If you would like to say that it would be wise to be very cautious about purchasing an AMD card right now due to a complete transition in how AMD will be supporting Linux going forward - with the understanding that AMD is working extremely closely with open source developers - then you would be accurate.

You have to keep in mind, that thousands of people all over the world are giving up on AMD, because it has been useless to keep trying to get them to work, when they don't. 

If a person survives a car wreck, without a seatbelt, doesn't mean that most people should not wear them. Glad you are the exception on getting AMD to work. I sure can't and I worked on it for about a year. 

 Chris.

---

### Post by QIII on 2016-12-02
There are millions for whom the drivers do work.  I'm not an exception.  By what metric do you derive that thousands are giving up?  How many are moving the other direction?

Do you understand what the whole AMDGPU push is about -- for both Linux and Windows users?  Did you know that Canonical is joined at the hip with AMD?

AMD is actually in the process of giving the Linux community exactly what it has been asking for.

You do realize, of course, that there are plenty of NVIDIA help requests on these Forums, too?

Where are your posts requesting help with AMD?

Didn't I say above that right now might not be the best time to buy AMD video hardware?

---

### Post by happydog500 on 2016-12-03
> **QIII said:**
> There are millions for whom the drivers do work.  I'm not an exception.  By what metric do you derive that thousands are giving up?  How many are moving the other direction?

Do you understand what the whole AMDGPU push is about -- for both Linux and Windows users?  Did you know that Canonical is joined at the hip with AMD?

AMD is actually in the process of giving the Linux community exactly what it has been asking for.

You do realize, of course, that there are plenty of NVIDIA help requests on these Forums, too?

Where are your posts requesting help with AMD?

Didn't I say above that right now might not be the best time to buy AMD video hardware?

  Very sorry for confusing Mint and Debian with Ubuntu. Didn't realize that 16.04 Ubuntu was completely different then Mint and Debian. Anything past 14.04 has xorg 1.8, which makes fglrx no go. The open source drivers don't work (blank dual monitor screens). Massive problems all over the Internet, Debian and Mint forums. I've actually tried about 15 dirstros in the last year and not one has worked. I saw one where a reply to the open source driver was, "no way no how." 

 I then searched Ubuntu forums and found the same thing here. Blank video with the open source drivers. Not only have there been massive posts on forums, but articles in Linux mags, Linux websites, all over the place. 

People all over the Internet have sworn off AMD forever. "I'll never own another AMD video card ever" has been expressed more then once. The year of AMD Video Hell I've been through has me thinking I'll never own another AMD Video either. 

I was even going to offer to pay for help, but it didn't work out. 

 This is why I posted here, to see if after a year of trying, a ubuntu user could get it to work. 

 What wold be your suggestion, when Ubuntu boots with blank screens with the open source driver?  

P.S. Can't run anything in a terminal, because the screens are blank. 

PP.SS. Since fglrx works good, the best thing is to use those. Only problem, Ubuntu can't use them past 14.04. How do we know that? People have tried. Why did they try? Because the open source didn't  work.
Blank screens.

Thank you for replying,
 Shows that you want to help and, you stick up for AMD who is helping with the open source community. 

 Chris.

---

### Post by gtippitt on 2016-12-05
First off QIII, I meant no disrespect toward you with what I said about AMD graphics card's poor support, and I deeply appreciate your helping me try to get my AMD RX470 and RX480 to work for number crunching.  What I meant by lack of support from AMD, is that I think it was unconscionable to abandon their existing installed base of GPU users by giving up on drivers for those cards and introducing half-baked drivers for their new ones.  While yes there are many questions from users who have problems with NVIDIA cards as well, their problems are most often because they are confused by the difference between the open source Nouveau, proprietary binary drivers from the UBUNTU repos, or the versions downloaded from NVIDIA' website.

As I said in our other thread, I have 35 years of UNIX experience, and getting these new AMD cards to work for anything more complicated that playing a UTube video has been  near to impossible.  I don't know what the differences in our other hardware is that permits the drivers to run on your systems and not mine.    It may be that I am trying these new cards in some older motherboards.  I have a Beowulf cluster with 144 CPU (AMD Operteron) cores that I've had in storage for 2 years that I am now putting back together.  When I took it down prior to moving, I was running several different  NVIDIA cards ranging from GTX 260, 590, and 670 cards  and Tesla co-processor cards.  They all played together nicely without any difficulty other than the oldest cards required an older version of the driver.  My old GPU cards use too much power for their performance, so I was hoping to replace them with RX470's and 480's.  My old NVIDA cards generate so much heat, I can only run them at full usage in the winter.  The cluster actually heated my home in east Tennessee for 2 winters without any other heat.  I was hoping that the AMD graphics cards would generate much less heat, so I was testing the new cards in the first node of the cluster when I started setting it up again.

The ease of configuration and software support from NVIDIA is vastly different from that of AMD.  I think it is sad, because I've been a fan of AMD CPUs since they introduced their 133MHz 586 chip in '95 that would allow you to replace your Intel 33MHz 486.  Getting a 4x speed improvement from your same motherboard was a big deal then.  Actually a 4X speed improvement without replacing a motherboard would be a big deal today as well, since going from a single core to quad cores isn't the same as a 4X improvement in speed for desktop applications.  Although AMD outperformed Intel for servers for many years, especially in multiprocessor configurations, sadly they seem to now be focused primarily on Windows desktops and have neglected the Linux workstation and server market for the most part.  

If someone is running a Windows desktop, the AMD graphics cards are a great deal for their performance.  AMD's upcoming Zen APUs to be announced next week sound like really great chips for new desktop systems in 2017.  If they were to produce a version that supported SMP multiprocessor motherboards, with good Linux drivers, I think it could be a really interested chip to compete with NVIDIA's Tesla systems and Intel's Xeon Phi systems for number crunching workstations and supercomputers.  For Linux users that want more from a graphics card than playing videos, such as gaming or number crunching, I still think they're best to avoid AMD graphics cards.

Greg

---

### Post by QIII on 2016-12-05
You did not disrespect me.  I don't have a dog in this hunt.  I'm not an AMD apologist -- I'm a facts guy.  You won't see me recommend AMD over Nvidia to anyone.  My general answer is to buy based on budget and need after researching.  Indeed, there are a couple of threads on the forum where I have said that for the moment it might be best to avoid the turmoil and avoid AMD.

As for number crunching:  I don't have access to review SETI at Home's code, but even though it does not have (and never has, so far as I can tell) an "ATI" GPU component, running it now on a machine with an 8350 Black edition, the R9 380X GPU by itself now completes 5 times the work that the CPU alone was able to complete.  I'm getting six times the work out of the machine.  That is with the AMDGPU-PRO driver on 16.04.  The code appears to detect the GPU/driver as another OpenCL device.  It would not use my R9 290X with the fglrx driver at all.

In 16.10, installation of AMDGPU-PRO is dead easy.

Phoronix has done tests and published results regarding AMDGPU-PRO with Rx 480 hardware, so clearly it can be used.

Even back when people complained about how hard it was for people to use fglrx for number crunching, I never had problems.  So I don't know what prompted all of that - except that so many people I helped here on the forum had followed bad advice from random websites and had done things incorrectly.

But you will find the exact same questions from Nvidia users all over these forums, and I wouldn't say Nvidia cards are "worthless".

AMD did not abandon their users.  Canonical moved forward with a graphics stack that is incompatible with fglrx before AMD had AMDGPU available.  Support was experimental in 16.04 and it is full in 16.10 -- even as AMD continues with aggressive development.  If you run one of many other distros, fglrx still works.  Besides that, the ever-improving Radeon driver, which AMD puts a lot of effort into in concert with the open source community, still supports those cards.

Please have a look at the membership of The Linux Foundation.  You will find both AMD and Nvidia there.  AMD has been a member for a long time.  They aren't trying to "dump" Linux.

---

### Post by happydog500 on 2016-12-07
1. My Xubuntu 16.04 is working with both video screens. Unbelievable after a year with about 15 distros. 

 2. I replaced my 486 with that 133MHz 586 chip. Thought it was a 6x86, and later then 95, like the next year or two. Still remember going from that to a 166MHz!! What a difference!!! Then upgraded to the 233Mhz. Thank you for the memory. 

 3. *"AMD did not abandon their users. Canonical moved forward with a graphics stack that is incompatible with fglrx before AMD had AMDGPU available."* Thank you for this. After having people after people tell me AMD abandoned Linux, I was going to start a thread, "Did AMD leave Linux, or did Linux leave AMD?" I thought with Xorg. 1.18, not being able to use fglrx, AMD didn't leave Linux, Linux moved away. 

 Nicely put, thank you for this. I love Ubuntu. 

 Chris.

---

### Post by oldfred on 2016-12-07
I think it is a bit more complicated that Canonical changed driver stacks. Its the Linux kernel, AMD & Canonical all together.

It is all related to the use of UEFI Secure Boot and the integration of signed drivers into kernel.
Even with Windows 10 Microsoft requires all drivers to be signed.

       Why disabling &#8220;Secure Boot&#8221; is enforced policy when installing 3rd party modules 
[http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules](http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules)

---

### Post by happydog500 on 2016-12-07
Just wanted to give an update. Second monitor doesn't work now. Linux wrecks movie night again. Have to boot into windows to watch a movie again. :(

 Chris.

---

### Post by gtippitt on 2016-12-08
Just a few days after I said that AMD new ZEN APUs with both x86 CPU and Radeon GPUs on the same chip would be a game changer for the desktop market, I read today that Intel is apparently afraid of the same thing. [Intel is reportedly in talks with AMD]("http://www.pcworld.com/article/3147846/computers/intel-may-use-amd-gpus-to-challenge-nvidias-rising-power.html") to licence the Radeon GPU tech for their own APUs!  Intel and NVIDIA have been in patent wars for years, so Intel has decided to they need AMD's help.

---

### Post by oldfred on 2016-12-08
It may not be that Intel will use AMD's video, but just patent cross licensing. Then they will not sue each other for any video related technology. 
Supposedly Intel has similar license with nVidia.

---

