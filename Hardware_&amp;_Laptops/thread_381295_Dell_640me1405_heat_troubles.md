---
title: "Dell 640m/e1405 heat troubles"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by tschneiter on 2007-03-10
Hi all-
Ive tried my best not to start a new thread on here, but it seems that it has come time for me to ask for personalized help. I have managed to fix many of my problems thus far by reading other threads, and have a system that I really, really like going now. Beryl is a beauty, and everything is responsive and powerful, as the case should be.
Ive pored over countless i8k threads, heat threads, what-have-you, but this really has me baffled. Any help is appreciated.
Here goes:

Specs:
Dell 640m
Intel core 2 duo @ 1.83ghz
Intel i945gm graphics
1024mb ram
5400rpm 120gb hdd
Broadcom wireless


Under Edgy, my laptop runs hot. I have loaded the i8k module (sudo modprobe i8k force=1), and gkrellm can detect my fans and their speeds. When I make changes by using the manual 
setting, it doesnt seem to have any effect, however. The main fan IS running though, of its own accord.

I am getting heat from the entire computer. Not just the processor, or the hard drive, but a number of spots spread throughout the chassis. Main hotspots are under the sticker for bluetooth (even though I have it disabled in bios), under where one's left palm would rest, and the ram area. Under windows, these are all relatively cool to the touch, warm at worst. Under Linux, they can actually be too hot to have resting on my stomach or leg. It almost seems like no component is allowed to sit idle, but is running at full-capacity all the time.
I do not believe this is linked to the processor, as scaling is working properly, and I have even limited it to 1ghz to see if that was the reason.

Upon switching into windows, the heat dies down and the laptop becomes cool in ~3 minutes.

I will give any diagnostics/information anyone asks for, but as I am stumped on this and not informed enough to make a proper diagnosis, I dont know what to put up.

Please help. Windows is miserable, and I really dont want to have to go back to using it full time.

Thanks, ive seen a pile of knowledge dumped here, hopefully some of it will apply to my problem!

---

### Post by tschneiter on 2007-03-11
Interesting addition:

I removed the battery, as a test on a whim. and ran purely off AC. CPU temps dropped by 10c, and the entire laptop felt as it should, as it does while running windows. I plug the battery back in (still using AC as well), and within minutes, heat spots are arising and the cpu temp has risen, though not as hot as before I unplugged & replugged the battery. Same result running purely off battery power. 


Whats going on here?

---

### Post by tschneiter on 2007-03-11
Well, I seem to have found a solution.

I decided to try out Feisty to see if I had any luck with that. Lo and Behold, I have a cool laptop! Support seems vastly improved in this version.

I dont know whether it was the kernel upgrade from 2.6.17 to 2.6.20 or the whole feisty upgrade that did the trick, but everything is MUCH happier!

Hope this might be able to help someone, somewhere along the line.

---

