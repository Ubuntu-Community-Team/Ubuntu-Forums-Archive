---
title: "New build - need advice"
date: 2011-01-10
forum: Hardware
---

### Post by coldcut on 2011-01-10
Hi guys

I don't know if this thread is in the right place, I had a hard time finding the right subforum, but here it goes. If admin's think this is not the right place it would be nice if they could move it for me.

The thing is that I'm building a computer that will most likely run Ubuntu, if not Ubuntu it will be another Ubuntu-based distro. The computer will mostly be used for programming (I'm a student in Computer Science) and to stream "HD"(720p) and none-HD videos via HDMI.

The setup that I am planning is as follows:

[LIST]
[*]Gigabyte H55M-UD2H (MB)
[*]Intel i3 540 3,06GHz (CPU)
[*]Mushkin 4GB kit, DDR-3, 1333MHz (Memory)
[*]SSD Drive
[*]HDD
[/LIST]

I was wondering if it would be possible to stream videos on my TV (1366*768 - 720P) and work on my monitor at the same time. My plan was to connect the HDMI to the TV and the DVI to my HD-monitor which will most certainly never be used for viewing videos.

I welcome any suggestions and help :D

---

### Post by cchhrriiss121212 on 2011-01-10
Go with a dedicated Nvidia card, a gt210 would do. Dual monitors could be set up with nvidia-settings, then use smplayer with vdpau to play video with low cpu usage.

---

### Post by coldcut on 2011-01-10
Okay thanks for the advice. But is that really necessary?

Won't it work if I use just the CPU graphics chip. I'm running on a pretty thight budget at the moment and computer parts don't come cheap in Iceland :(

---

### Post by TechWiz2100 on 2011-01-10
Sadly I don't think i series GPUs work in Ubuntu at all. I have an i5 and Ubuntu doesn't recognize the existence of my i5 GPU at all AFAIK.

And yes, you would probably need a dedicated card because dual monitor support is more flaky on linux than it is on windows and performance suffers greatly from using a 2nd monitor. Although you can probably go for a cheaper alternative than a GT210 which is a bit on the higher end.

---

### Post by cchhrriiss121212 on 2011-01-10
A gt210 is pretty cheap in the UK, only about £30. If you want to save money, look into an AMD build and maybe pick up some bits second hand.

---

### Post by coldcut on 2011-01-10
oh darn...I was hoping to not have to a buy a GPU but well.

Another thing: I just can't believe that there's still not proper Linux drivers for the IGP in i* CPU's. It's not like it's the hottest thing on the market :(

---

### Post by TechWiz2100 on 2011-01-10
Keep in mind that most of *nix development is open source and community driven. Intel is not friendly to either which is why many Intel Wi-Fi cards fail to function properly under *nix

---

### Post by cchhrriiss121212 on 2011-01-10
You could always get a board with an integrated nvidia GPU.

---

### Post by coldcut on 2011-01-10
> **TechWiz2100 said:**
> Keep in mind that most of *nix development is open source and community driven. Intel is not friendly to either which is why many Intel Wi-Fi cards fail to function properly under *nix

My comment was never meant as an insult to the developers! It's just hard to believe because the developers have always found some way when the big companies have been holding back.

But tell me two things if you will:
 
Would it be better for me to get a low-end ATI or nVidia graphics card?

And would a chip like the nVidia GT 210 run dual monitors with different resolutions successfully? The only graphic I would possibly use on the computer monitor are some productive Compiz-things that is to say if I can resist the temptation of a tiling window manager.

---

### Post by TechWiz2100 on 2011-01-10
nVidia over ATI on Ubuntu, ATI driver devs themselves say that the drivers are a mess; lots of bugs.

Depending on how low end you wish to go... I would say spend at least a good 50USD on a decent card. You can get a decent GeForce 8 series for under that but if you can afford a GeForce 9 series, even better. 512MB+ VRAM is preferred to make sure you don't get buffer slow downs during video playback.

---

### Post by coldcut on 2011-01-12
Allright thanks.

Do you think a graphics card like the nVidia GT210 could handle the setup I described earlier?

---

### Post by TechWiz2100 on 2011-01-12
> **coldcut said:**
> Allright thanks.

Do you think a graphics card like the nVidia GT210 could handle the setup I described earlier?

Probably but I think the GeForce 8 series has a better performance to $ ratio and I think the 8800 is like 3-4 times more powerful than the 210. The 210 also seems to be supported by the closed nVidia drivers

---

### Post by coldcut on 2011-01-12
> **TechWiz2100 said:**
> Probably but I think the GeForce 8 series has a better performance to $ ratio and I think the 8800 is like 3-4 times more powerful than the 210. The 210 also seems to be supported by the closed nVidia drivers

But the 8800 doesn't have a HDMI and DVI connector. Not even the 9800GTX+ has those ports.

Would it be possible to use the i3 graphics chip to handle the HDMI to the TV and a video card to handle the monitor?

EDIT: Actually I might have a 9800GTX+ with HDMI, DVI and VGA port lined up, so I guess I'll take it if I win the "auction". Any objections?

---

### Post by TechWiz2100 on 2011-01-12
Not really but the 8400GS, 9400GT, 9500GT all have DVI + HDMI for under 50 bucks.

[Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=Property&Subcategory=48&Description=&Type=&N=100007709&IsNodeId=1&srchInDesc=&MinPrice=&MaxPrice=&PropertyCodeValue=3055:20548&PropertyCodeValue=683:10557&PropertyCodeValue=683:56835&PropertyCodeValue=683:24927&PropertyCodeValue=683:37012&PropertyCodeValue=683:40784&PropertyCodeValue=683:49638&PropertyCodeValue=683:20729&PropertyCodeValue=683:50480&PropertyCodeValue=3209:100123&PropertyCodeValue=3209:23120&PropertyCodeValue=691:9631&PropertyCodeValue=691:100223&PropertyCodeValue=691:9630&PropertyCodeValue=691:37032")

---

### Post by coldcut on 2011-01-13
> **TechWiz2100 said:**
> Not really but the 8400GS, 9400GT, 9500GT all have DVI + HDMI for under 50 bucks.

[Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=Property&Subcategory=48&Description=&Type=&N=100007709&IsNodeId=1&srchInDesc=&MinPrice=&MaxPrice=&PropertyCodeValue=3055:20548&PropertyCodeValue=683:10557&PropertyCodeValue=683:56835&PropertyCodeValue=683:24927&PropertyCodeValue=683:37012&PropertyCodeValue=683:40784&PropertyCodeValue=683:49638&PropertyCodeValue=683:20729&PropertyCodeValue=683:50480&PropertyCodeValue=3209:100123&PropertyCodeValue=3209:23120&PropertyCodeValue=691:9631&PropertyCodeValue=691:100223&PropertyCodeValue=691:9630&PropertyCodeValue=691:37032")

Well the thing is I live in Iceland. Of those video cards you mentioned the only one available here is the 9500GT and that goes for about 50$  more than the slightly used 9800GTX+ I have made an offer on. ;)

---

### Post by Yellow Pasque on 2011-01-13
Sandy Bridge graphics work in Linux, but you'll need to update a lot of stuff in Ubuntu 10.10 (or just run 11.04). Details: [http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA)

EDIT: Actually OP is running Clarkdale (not SB), so it should work in 10.10

---

### Post by cascade9 on 2011-01-14
If you are looking to build a budget system, go for AMD. You'll get more computer for your money, or pay less to get the same amount of CPU power. 

> **TechWiz2100 said:**
> Probably but I think the GeForce 8 series has a better performance to $ ratio and I think the 8800 is like 3-4 times more powerful than the 210. The 210 also seems to be supported by the closed nVidia drivers

8XXX is dead. The only 8XXX cards you can buy new are the 8400GS cards, and for desktop use a GT2XX is better than a 8400GS.  

Sure, a 8800GT is 'more powerful' than the GT2XX cards, but you'll only find one 2nd hand now (in most places anyway) and its not going to be much cheaper than a GTX2XX or GTX4XX card that is a lot more powerful than the 8800GT.

> **coldcut said:**
> But the 8800 doesn't have a HDMI and DVI connector. Not even the 9800GTX+ has those ports.

Would it be possible to use the i3 graphics chip to handle the HDMI to the TV and a video card to handle the monitor?

EDIT: Actually I might have a 9800GTX+ with HDMI, DVI and VGA port lined up, so I guess I'll take it if I win the "auction". Any objections?

Actually, there were 8XXX cards with HDMI and DVI- 

[http://en.inpai.com.cn/doc/enshowcont.asp?id=1900&pageid=2081](http://en.inpai.com.cn/doc/enshowcont.asp?id=1900&pageid=2081)

But like I said about, dont get an 8800GT. Its over 3 years old now, and there are better cards around.

---

### Post by exobuzz on 2011-01-14
> **Temüjin said:**
> Sandy Bridge graphics work in Linux, but you'll need to update a lot of stuff in Ubuntu 10.10 (or just run 11.04). Details: [http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA)

EDIT: Actually OP is running Clarkdale (not SB), so it should work in 10.10

it's relatively simple to run the new sandy bridge stuff as the packages are already available. see my post at [http://ubuntuforums.org/showthread.php?p=10358613#post10358613](http://ubuntuforums.org/showthread.php?p=10358613#post10358613)

---

