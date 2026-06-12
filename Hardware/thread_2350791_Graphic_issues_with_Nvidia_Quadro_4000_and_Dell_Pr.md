---
title: "Graphic issues with Nvidia Quadro 4000 and Dell Precision T5500"
date: 2017-01-27
forum: Hardware
---

### Post by jan-pedryc on 2017-01-27
At first, many times posts from this forum helped me with my journey with Ubuntu and other distros, and I am very grateful for that for all people contributing with their answers for the dummies like me.

That said, over the years I had one major issue that seemed generally not solvable, but wasn't a big of an issue until now.

I bought an used Dell Precision T5500 with an Nvidia graphics card (Quadro 4000) and from the beginning I had issues with fans (working on 100% all the time or not at all). The card was always overheating too. I downloaded the i8kfan drivers and tried to set the speed limits on my own. Well it worked, but every restart I had to do it again. I actually wrote an script in bash (called turnCrazyFans) and manually run it after startup (am I crazy?). The best part, after couple of months, out of nowhere, I didn't had to do it. The fans started by themselves at the mid-range. "They learned it, cool!" - I thought.
[ATTACH=CONFIG]273424[/ATTACH]

Well, my mistake. After, again, couple of months, I got a crazy laser techno show on my screen:

[ATTACH=CONFIG]273425[/ATTACH]

I changed the drivers many times, between the Nvidia recommended ones and the default Nouveau driver. The Nouveau one worked for the past couple of months. But now, after the effects show in the images, I tried to fix things up. I changed the booting options - added nomodeset. After that the newest (460.xx?) Nvidia drivers worked great, the temperatures were fine. But today, after couple hours of use, first I had some green squares all over my screen, and after that it froze. I changed last time for another version of Nvidia drivers, and... it's gone :( Not only I can boot to the Ubuntu welcome screen, anything I choose from the usb live disc with xubuntu gets frozen. The only output I get is about Nouveau drivers, stuck CPUs etc., or this sometimes:



Well, I found out about special distros for repair (will try SystemRescueCD) and want try it out. I always have a clue what's the problem, and after using Linux distros for couple of years, I haven't been so stuck like this at the moment.

Was it my fault I changed the graphic card drivers like gloves? Is it a graphic card memory problem or maybe a system memory problem, it seems like a memory problem. Also, I had problem with displaying couple of letters, is this a clue? I haven't touched the X server configs at all.

If someone could guide me in finding a solution - thanks in advance.

Greetings
Johnny

PS To be honest, I have almost zero knowledge about the boot process and what is actually happening during this process, if you know a cool resource, let me know ;)

---

### Post by jan-pedryc on 2017-01-27
This one's good:

---

### Post by Autodave on 2017-01-27
Can you please give us some info on the machine: # of cores, processor speed, RAM, etc?

---

### Post by howefield on 2017-01-28
Please thumbnail or otherwise restrict the soze of you images to about 800x600 out of respect for those on slow/low bandwidth connections. Thanks.

---

### Post by jan-pedryc on 2017-01-28
Of course:
[FONT=arial]Workstation: Dell Precision T5500 
Processors: Intel XEON 4 x 2933 MHz
Memory: 12GB

I had only one HDD with only Ubuntu on it - about 300GB in size I believe.
[FONT=arial][/FONT]
The temperatures of the graphics card were in range 60C - 80C.
The temperatures of the cores were mostly about 25C - 40C. They seemed not additionally loaded - I think they worked normally as I was only listening on YouTube and writing stuff in LibreOffice.
I am not a gamer and don't do anything related to video editing etc.

Additional information that might help (some configuration I was able to make yesterday before the PC crashed):
- I disabled fast boot in Dell configurations (nothing changed - Ubuntu was booting - graphics still messy)
- Like said before, I added "nomodeset" to the boot options as I found it as a solution to a similar problem (nothing changed)
- At this part, green squares come up, I change the drivers in "Additional Drivers & Software" Tab from Nvidia 360.xx to Nvidia 340.xx, reboot, and get to the point I am now.

In summary:
I had for over a year the Nouveau driver, changed nothing but suddenly have graphic problems. Changed to Nvidia 360.xx and the things above, worked for a day. After changing to 340.xx - works nothing.
[/FONT]
Hope this helps more :/

---

### Post by Autodave on 2017-01-28
Since no one else can offer any suggestions, here are a couple things that come to my mind. First, that 60-80C sounds high to me. I am a sort of gamer and I have never seen the temp on my cards (2 different machines) ever hit 60C while gaming. Right now on this machine, I am at 30C.

Second, do you have an install disk or can you create one? If it were me, I would try that: boot into a disk (Try ?buntu) and see what happens there. (You may have to do the nomodeset there.)

Are you running Ubuntu and are you running Compiz?

---

### Post by jan-pedryc on 2017-01-28
That true, the temp is high anyway, although it is a known issue with the Nvidia Quadro 4000 ([http://www.tomshardware.co.uk/forum/368505-33-reduce-heating-quadro-4000)]("http://www.tomshardware.co.uk/forum/368505-33-reduce-heating-quadro-4000"). I cleaned it already, and although the temp was lower, is still high compared to other ones I think.

Anyway, I don't have an install disk, I always used live USBs to boot and install the systems. I thought about trying that out already (with Xubuntu live USB and now with SystemRescueCD ([http://www.system-rescue-cd.org/SystemRescueCd_Homepage](http://www.system-rescue-cd.org/SystemRescueCd_Homepage)).

I can get to the boot menu, but after I choose one boot option, I get on the screen more errors and it gets frozen after couple of seconds. There are also some random characters flickering around from time to time in random places on the screen.

After booting with nothing in the USB slot I got:

[IMG]http://i.imgur.com/T1i7yO9.jpg[/IMG]

After I tried it with the SystemRescueCD i got some additional info:

[IMG]http://i.imgur.com/RIQQVuz.jpg[/IMG]

Two new messages are standing out:
 > Incompatible video vontroller
and
> Missing operating system.

Well, that's right on time for a student during his finals.

The worst part, even if I would get to the point that I am ready to loose the data:
- I don't have a clue what the problems are
- I actually don't know how to install a new OS if everything freezes on boot time.

I am running Ubuntu without Compiz or any additional graphic managing software.

---

### Post by poorguy on 2017-01-30
> **Autodave said:**
>  First, that 60-80C sounds high to me. I am a sort of gamer and I have never seen the temp on my cards (2 different machines) ever hit 60C while gaming. Right now on this machine, I am at 30C.
Those temps aren't high if the graphics card has no fan on it.

My graphics cards on my "flight simulator x" desktop run 45 to 70 degrees Celsius when under heavy load. 

Sapphire Radeon HD 3870 X2 1GB
[https://www.newegg.com/Product/Product.aspx?Item=N82E16814102723R](https://www.newegg.com/Product/Product.aspx?Item=N82E16814102723R)
[h=1][/h]

---

### Post by Perfect Storm on 2017-01-30
It look more thatthe video card is kicking the bucket soon. I had similar experienced with cards that went south.

---

### Post by jan-pedryc on 2017-02-04
Well, after I had my finals I have now time to try to fix this issue.

I am aware that the best solution right now is to buy another card and I will do that today. It bothers me although that I can't minimize the problem.

[LIST]
[*]I tested the screen using another laptop - it works well. 
[*]I run the memory and CPU tests - everything passed. 
[/LIST]

I don't have the ability to check the hard drive and I don't have another compatible graphics card.

Like said before, the graphics card seems to be the only available option as the main problem. I believe - **the memory** of the card in specific.

The Nvidia Quadro 4000 has also additional pin-outs on one side:
[CENTER][IMG]http://i.imgur.com/xpuLprKm.jpg[/IMG]

[IMG]http://i.imgur.com/WlnKQs5m.jpg[/IMG]

[/CENTER]
As I can't access the card from a running PC, can I power the card externally and log-in at the boot sequence (?) or even interact with the processor externally, like through UART?
Do I have any debugging options?

---

### Post by jan-pedryc on 2017-02-07
Today in the morning came the new graphics card - nVidia Quadro 600. After installation, everything works fine. No glitches on display, OS works like a charm.

On the T5500 is an other PCI x16 slot.

Are there any difficulties with connecting two graphics cards at once (display connected only to the working one - quadro 600).
I red about memory testing of graphics cards and want to try it out. That - I hope - would give me an indefinite information about bad functionality of the memory.

---

