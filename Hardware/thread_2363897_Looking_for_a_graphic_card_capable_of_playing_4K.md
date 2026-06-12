---
title: "Looking for a graphic card capable of playing 4K"
date: 2017-06-16
forum: Hardware
---

### Post by mohtasham1983 on 2017-06-16
Hi,

I built a PC 3 years ago. These are the CPU and the motherboard that I picked:

[https://www.newegg.com/Product/Product.aspx?Item=N82E16813131837](https://www.newegg.com/Product/Product.aspx?Item=N82E16813131837)
[https://www.newegg.com/Product/Product.aspx?Item=N82E16819116502](https://www.newegg.com/Product/Product.aspx?Item=N82E16819116502)

The CPU comes with Intel HD Graphics 4000 and the motherboard has DisplayPort and HDMI ports. My 1080P monitor has been connected to the HDMI port since then. However, now I have a new WQHD (1440) monitor. I connected it to my computer using the HDMI, however, I noticed I only get 1080P on it. Then I tried to play with xrandr using the following instructions with no luck:

[https://wiki.archlinux.org/index.php/xrandr](https://wiki.archlinux.org/index.php/xrandr)

Then I connected the DisplayPort cable that came with the monitor to the computer, however, I got no signals from computer, which made me frustrated.

I'm sorry if I sound too dumb, but I was wondering if the DisplayPort in motherboard is just a port to the integrated Intel HD Graphics 4000 of the CPU? If the answer is yes, then I guess the DisplayPort in my motherboard is broken.

So now I've decided to buy a dedicated GPU with good Linux driver. I'm not a gamer, but I'd like to be able to watch 4K movies without any issues. I'd like to spend less than $200 on it. Also, it would be great if the GPU supports thunderbolt 3 as well, as I may connect my Dell XPS 3 laptop to it at some point(very unlikely though).

I'd really appreciate if you could share your experience with me.

---

### Post by SeijiSensei on 2017-06-16
NVIDIA's GTX 750 [supports]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-750/specifications") resolutions up to 4096x2160 and is well-supported in Linux.  Mine is connected to a 1920x1080 television so I can't comment on its high-resolution performance.  I've played some Windows games on it like Dragon Age 3, and it looks fine.

You can get 750 GTX adapters for well under $200.  Here are some options:  [https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100007709%20600487564%20600487565](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100007709%20600487564%20600487565)

I'm not sure what the differences are between the 750 GTX and 750 GTX Ti.  Maybe someone else will chime in, but the couple of articles I looked at like [this one](http://www.game-debate.com/gpu/index.php?gid=884&gid2=883&compare=geforce-gtx-750-vs-geforce-gtx-750-ti) suggest those differences are small.

---

### Post by sccman on 2017-06-16
Integrated graphics means that instead of using an actual GPU for the images, your CPU and motherboard handles the images in addition to Ubuntu/Windows. A GPU helps the CPU outsource all graphics processes (gaming graphics, icons, movies, etc) to another component (GPU) that can handle it better.

And Seniji, the [750 GTX Ti]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-760ti-oem/specifications") is a little bit faster than the [ordinary 750]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-750/specifications") and has 2GB VRAM instead of 1GB. It's essentially a "GTX 750 2.0."

[FONT=Verdana]nVidia certifies that [/FONT][these]("http://www.geforce.com/hardware/technology/4k/supported-gpus?field_gpu_type_value=All") [FONT=Verdana]graphics cards can run 4k but I would recommend simply using your [/FONT]Intel HD 4000 for the 4k. It should be able to handle 4k movies with no issues. No need to spend money on an extra GPU if you don't need to :)

[https://www.quora.com/Is-the-Intel-HD-Graphics-4000-GPU-capable-of-playing-4K-HEVC-video-in-Windows-10](https://www.quora.com/Is-the-Intel-HD-Graphics-4000-GPU-capable-of-playing-4K-HEVC-video-in-Windows-10)

Personally, I'd only recommend a GPU if you're using it for gaming.

---

### Post by mohtasham1983 on 2017-06-19
I was suspecting that the CPU should be able to process 4K but for some reasons the DIsplayPort of my motherboard didn't send any signals to monitor. That's why I decided to go with a GPU. I ended up ordering GTX 1050 Ti  from ASUS. It's a new GPU. I took the risk of using nVidia's beta driver for Linux when ordering that graphic card. I'm still waiting for it to be delivered though.

---

### Post by mohtasham1983 on 2017-06-23
I got the new GPU. I tried to connect my monitor to it through DisplayPort, but it didn't work. I guess either my monitor's displayport is broken or there's something wrong with the cable. I was able to get 1440P resolution using the HDMI cable though. I intalled nvidia driver on my Arch Linux box and I was able to play 4K videos very smoothly. I even installed Steam and played counter strike in it. It worked great. My only problem was that I was getting killed non stop.

---

### Post by Bucky Ball on 2017-06-23
Check 'Additional Drivers' in Ubuntu. The recommended driver for that card should be there. Enable it and reboot. See what happens.

[QUOTE=sccman]Personally, I'd only recommend a GPU if you're using it for gaming. [/QUOTE]

Or video/graphics production/post-prod which is resource hungry (particularly rendering). ;)

---

### Post by ajlongstreet on 2017-06-23
The GTX 1050 is a great budget option with low power requirements.

---

### Post by sccman on 2017-07-02
> **Bucky Ball said:**
> Check 'Additional Drivers' in Ubuntu. The recommended driver for that card should be there. Enable it and reboot. See what happens.



Or video/graphics production/post-prod which is resource hungry (particularly rendering). ;)

Right. Haha :D

---

### Post by sccman on 2017-07-02
> **mohtasham1983 said:**
> I got the new GPU. I tried to connect my monitor to it through DisplayPort, but it didn't work. I guess either my monitor's displayport is broken or there's something wrong with the cable. I was able to get 1440P resolution using the HDMI cable though. I intalled nvidia driver on my Arch Linux box and I was able to play 4K videos very smoothly. I even installed Steam and played counter strike in it. It worked great. My only problem was that I was getting killed non stop.

Yeah it sounds like there's a problem with one of the DisplayPort connectors, or the cord itself. But, if it's working then that's all that matters.

---

### Post by mohtasham1983 on 2017-08-06
> **ajlongstreet said:**
> The GTX 1050 is a great budget option with low power requirements.

Yeah. I have been mining Vertcoin for 3 weeks already. I make $0.5 a day in average. I think it will be more than my electricity bill at the end of the month.

---

