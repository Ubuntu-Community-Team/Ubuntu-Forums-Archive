---
title: "Buying New Laptop – Video Editing"
date: 2019-10-07
forum: Hardware
---

### Post by eagertolearn on 2019-10-07
Hi all,
 
I’m not a techie so I’m interested in hearing from others who are.
 
I’m searching for a new laptop as my Toshiba is 10+ years old.
 
I want to do some video editing with the laptop, possibly using ShotCut.
 
I’m wondering if I can just use onboard graphics or if I’ll need a separate graphics card?
 
If I necessarily need a separate card, which manufacturer(s) (models) have you had the most success with?
 
Is there a way for me to ascertain if the proposed laptop works well with OpenGL 2.0 and that laptop also is compatible DirectX 9 or 11 drivers?
 
A friend using Linux Ubuntu shared they’ve had major issues with Nvidia graphics cards. 
 
Would an AMD Radeon graphics card be best? If so, are there particular models of AMD Radeon I should look for?
 
I’ve also read that heat reduction of the CPU is important. How might I ascertain if a certain laptop includes good heat reduction?
 
Thanks so much.

---

### Post by CatKiller on 2019-10-07
GPUs do have hardware to accelerate video encoding, which is quicker, but the you're limited to whichever profiles and settings are included in the implementation. You'd need to read reviews from people encoding the same formats you're intending to use to see if that's what you want. Your video software would also need to specifically include support for the hardware encoding. Software encoding is slower but more configurable.

Video editing also eats up a lot of RAM. You'll want as much as you can get. You'll probably appreciate an SSD, too.

There's no DirectX on Linux. OpenGL is at version 4.6. Nvidia and AMD both support 4.6; Intel are at 4.5 unless you're using the very latest software. 

Laptop reviews will generally tell you about its thermal performance. If it's just chugging through an encode you can use forced ventilation by sitting it on some big fans; those units are really simple and really cheap.

---

### Post by TheFu on 2019-10-07
I would suggest that a high-end laptop is nowhere near as good as a relatively cheap desktop with a modern CPU, modern GPU and NVMe SSD storage.  You can have both for less money than a high-end laptop and the desktop will be much faster.

nVidia solved many of their former issues with drivers in July.  If you run an LTS Ubuntu release, and you should if you are new or just want stability, then the correct nVidia driver can be easily installed.

When you buy a laptop, there's no way to add a great GPU after the fact.  That component cannot be altered.

I have an 8th generation Core i5 CPU with onboard GPU and video editing is painful.  But my I have a VM server with an AMD Ryzen 5 2600 that eats video processing like it is potato chips.  It has a $80 nVidia GPU, but I haven't looked into it using the GPU for any video processing.  The Ryzen replaced a 2009 Core i7 and it is about 2x faster CPU and  more than 50% less power use.  I actually do video editing on a Win7 machine (marking cut locations), but video transcoding under Linux.  

Cooling is always an issue when video processing is involved.  Some laptops still have cooling issues, so you'll need to search for those problems online for any model on your short list.

Of course, you might not be able to do the work you need without using a laptop. I don't know about that. I can access my Ryzen box from anywhere in the world with internet, though final edits would need to be made locally.

---

### Post by eagertolearn on 2019-10-09
Hi The Fu, Thank you for your quick and helpful reply. Is your "VM server with an AMD Ryzen 5 2600" a laptop? 
I'll need something mobile so the desktop is not an option. I'm trying to ascertain if I must buy a laptop with a slot so I cna add (or have the seller add) a separate video card? I'm trying to use ShotCut video editor. I'm not a professional video editor but easing into it as a scriptwriter doing my own (or as much as I can) video editing. Adding cooling sounds like a custom build laptop and not an on shelf item. I was hoping to buy a laptop for $1,000 - $1,500 where I could load ShotCut and edit on that. Is that possible?

---

### Post by him610 on 2019-10-09
> A friend using Linux Ubuntu shared they’ve had major issues with Nvidia graphics cards.
I have been using Nvidia graphics cards for over ten years now. I have never had any issues with Nvidia cards or drivers.
As to integrated or discrete cards, depends what your planned usage is. With a light graphics load, discrete is probably sufficient; heavy graphics load then a discrete card. Be advised an integrated gpu will use some (configurable) of the system memory.

---

### Post by TheFu on 2019-10-09
> **eagertolearn said:**
> Hi The Fu, Thank you for your quick and helpful reply. Is your "VM server with an AMD Ryzen 5 2600" a laptop? 
I'll need something mobile so the desktop is not an option. I'm trying to ascertain if I must buy a laptop with a slot so I cna add (or have the seller add) a separate video card? I'm trying to use ShotCut video editor. I'm not a professional video editor but easing into it as a scriptwriter doing my own (or as much as I can) video editing. Adding cooling sounds like a custom build laptop and not an on shelf item. I was hoping to buy a laptop for $1,000 - $1,500 where I could load ShotCut and edit on that. Is that possible?

That is a desktop. Don't think any laptop could come close to the performance for less than $1500. I built it for a little over $400 and today I could build it for closer to $300 because of drastic desktop CPU and RAM price drops.  Desktops are about 8x less than laptops.

I've never heard of any laptop that allows swapping the GPU. Is that possible? 

My laptop with a Core i5 (8th gen) was $305.  I paid more for my last Chromebook.  I've been disappointed doing video transcode work on any laptop.  Setting up cuts isn't an issue, but actually generating video is. For some v-codecs, I'll do the cuts on Windows and the batch processing on my Linux VM server. VPrj files are what I use for those cuts.

---

### Post by MartyBuntu on 2019-10-09
> **TheFu said:**
> That is a desktop. Don't think any laptop could come close to the performance for less than $1500. 
I've never heard of any laptop that allows swapping the GPU. Is that possible? 


There are external GPU's that can be connected with Thunderbolt...but like you alluded...you're not getting even close to $1500.
For $1500, the best you're looking at is a "modest" editing machine. Of course, results can be subjective...it depends on what your expectations of rendering times are.

---

### Post by TheFu on 2019-10-09
The resolution required for the rendering/transcoding matters greatly. Working at 8K is becoming much more common.  I'm not even working at 4k here.

---

### Post by CatKiller on 2019-10-09
> **him610 said:**
> I have been using Nvidia graphics cards for over ten years now. I have never had any issues with Nvidia cards or drivers.

Nvidia *cards* are perfectly fine. Good performance, day one support, feature parity with Windows, all of that. An *Optimus* setup, though, with both Nvidia & Intel, is a complete pain. If using nvenc or CUDA was a necessity I'd bite the bullet, obviously, but otherwise I would stay well clear for now, personally. There's new stuff on the horizon that, when it gets completed and works its way down, should make it a lot easier, but it's not there yet.

---

### Post by mastablasta on 2019-10-10
there was some good advice in The Guardian "*What&#8217;s the best PC for video editing for £1,000?*":
[https://www.theguardian.com/technology/askjack/2019/aug/29/whats-the-best-pc-for-video-editing-for-1000](https://www.theguardian.com/technology/askjack/2019/aug/29/whats-the-best-pc-for-video-editing-for-1000)

also another one for youtube videos "*What do I need to make YouTube videos?*": [https://www.theguardian.com/technology/askjack/2019/sep/19/what-do-i-need-to-make-youtube-videos](https://www.theguardian.com/technology/askjack/2019/sep/19/what-do-i-need-to-make-youtube-videos)

i also red a few other blogs and it realyl depends what kind of video editing you are doing. But bottom line the importance goes this way: 
1. CPU
2. RAM
3. SSD (where the video is processed) + storage (the cheaper HDD) for saving it
4. GPU

Now i saw a good i think it was Asus, 17" screen laptop reduced from 1200 EUR to 900 EUR. There are also some good HP ones the - G series should support Linux well, for others it is a hit or miss.

I would get something with good Ryzen (5 or stronger) that has both - SSD and HDD inside with at least 16 GB RAM. i don't know about 4K, maybe it needs a dedicated GPU?!

---

### Post by uRock on 2019-10-10
I admit to having issues with nvidia drivers since Ubuntu started installing drivers automatically. On my laptop, I've had to go into rescue mode and remove the driver to be able to boot and then the external HDMI was disabled. I do video editing on my desktop as I can't see trying it with a screen smaller than 23".

---

### Post by TheFu on 2019-10-10
> **uRock said:**
> I admit to having issues with nvidia drivers since Ubuntu started installing drivers automatically. On my laptop, I've had to go into rescue mode and remove the driver to be able to boot and then the external HDMI was disabled. I do video editing on my desktop as I can't see trying it with a screen smaller than 23".

I've not seen any issues since July when Ubuntu started including nVidia drivers for LTS releases, but to be honest, I don't use my only nVidia GPU as a desktop much.  It is a VM server and almost exclusively accessed through ssh and ssh X11 tunnels to show the GUI programs on other systems.

---

