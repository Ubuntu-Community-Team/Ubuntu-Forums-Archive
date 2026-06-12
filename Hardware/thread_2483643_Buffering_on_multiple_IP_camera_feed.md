---
title: "Buffering on multiple IP camera feed"
date: 2023-02-05
forum: Hardware
---

### Post by macrelling on 2023-02-05
I have a workstation that is displaying IP cameras. The workstation is using a third party application to display the feeds. And the application is decoding all of the camera feeds, regardless if they are displaying or not. As there are a lot of feeds, it starts to get laggy and the streams that are displaying start buffering. When some of the feeds is removed again the buffering/stuttering stops. 

I have done some hardware logging on the CPU, memory and GPU. Cpu is never working on more than 20%, memory max 6-7%, and GPU is at about 80-90 when all feeds are added and gets decoded. 
When I get the GPU usage down to about 50-60% the stuttering stops. This doesn't really make any sense to me, why is it struggling on say 70% and upwards? Shouldn't the GPU be running on full tilt if it is struggling with the decoding?
Feel free to ask any follow up questions, and I will try to answer them. 

The software is all up to date, and the hardware is new, and the whole machine is quite expensive. The GPU is a Nvidia Quadro p4000

---

### Post by TheFu on 2023-02-06
Any wifi networking?
How much bandwidth does each stream require?  Have you added it all up and ensured the wired ethernet can handle it?

---

