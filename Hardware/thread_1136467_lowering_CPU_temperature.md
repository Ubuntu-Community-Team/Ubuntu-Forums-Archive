---
title: "lowering CPU temperature"
date: 2009-04-25
forum: Hardware
---

### Post by erunamo114 on 2009-04-25
Hey guys. I am running Ubuntu Intrepid 8.10, and I recently downloaded and configured the lmsensors app from the repositories. I have two questions.

1.) There are several different sensors displayed on the task panel, and I am not sure what each temperature gauge label means. They are labeled as "CUP", "temp1", "Core0", "Core1", another "temp1", "temp2", and "GPU". Could someone tell me what each of those are telling me the temperature of?

2.) MOst of the gauges are seeming to run consistently high. Once my computer has been running for about 10-20 minutes the lowest temperature out of the ones listed above is 40 degrees C. The GPU is actually running at 76 degrees right now which is way too high. Anyone have any suggestions of how to lower the temperature of these? I've tried just dusting out my desktop on the inside and everything. I know that the GPU is probably the video card, but I am currently not running any video at all so I have no idea why it's that high. Any suggestions would be much appreciated. Thanks!

---

### Post by kidders on 2009-04-26
Hi there,

> **erunamo114 said:**
> I am not sure what each temperature gauge label means.Your system probably has more than one sensor chipset, each giving you slightly different information, and calculating it in different ways. For example, Some sensors compute temperature algorithmically, rather than actually measuring it. Some things to bear in mind ...[LIST]
[*]Sensors are frequently buggy, and some don't necessarily follow the same temperature conversion rules as others in the same family. If you want to be able to rely on what lmsensors tells you, you'll need to check your sensors out to make sure lmsensors is using the right algorithms.
[*]In theory, lmsensors *could* be reading the value intended to be labelled "fan speed" and calling it "cpu temperature". You should check that lmsensors is using the right inputs, just to be sure. It's also possible that one or two of your inputs is considered "off", and is sending you garbage.
[*]You might be happier if you discard the readings from one of your sensor chips. They'll all probably give you slightly different answers to the same questions, so throw away the data you feel is less likely to be accurate.
[/LIST]

> **erunamo114 said:**
> They are labeled as "CUP", "temp1", "Core0", "Core1", another "temp1", "temp2", and "GPU".These are _possibly_ CPU (?) die temp, motherboard temp, core 1 temp, core 2 temp, and core 1 temp, core 2 temp, graphics card processor die temp.

> **erunamo114 said:**
>  The GPU is actually running at 76 degrees right now which is way too high.I have a GPU sensor that tells me that too ... I don't believe it, but I've never bothered to fix it. There's loads of documentation around about lmsensors. It's likely that *someone* will have taken the time to produce an lmsensors configuration specifically for your chipset(s) that's as accurate as possible.

I hope that helps.

---

### Post by stinger30au on 2009-04-26
the other reason it is saying the chips are hot, is becuase, they actually are very hot


if it is a desktop machine i suggest you clean the fans out with a bit of compressed air

hold a pen or something against the fans before you hit them with compressed air or they may spin too fast and fly to pieces on you


[URL="http://www.overclockersclub.com/guides/lapping/"]also if the cpu is too hot, try and lap in the heat sink, should only take about 20 minutes and well worth it
[/URL]

---

### Post by tnttrx on 2009-04-26
usually, there's a lot of room for undervolting

[http://www.linux-phc.org/](http://www.linux-phc.org/)

[https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

---

