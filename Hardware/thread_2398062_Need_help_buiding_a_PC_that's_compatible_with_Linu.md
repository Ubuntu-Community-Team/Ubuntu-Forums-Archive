---
title: "Need help buiding a PC that's compatible with Linux out of the box"
date: 2018-08-07
forum: Hardware
---

### Post by John_Patrick_Mason on 2018-08-07
Is there anything I should be aware of before I start searching for components? I want the desktop to be compatible with Linux out of the box, so to speak.
I also need it to be able to edit videos in 4K using Adobe Premiere Pro in Windows 10.
Ideally -- for security reasons -- I'd like to run Windows 10 in a virtual machine, but I've read that that requires two GPUs, and, since it's my first time building a PC, I don't know how much that is going to cost. It might be more feasible for me to buy just one GPU, and to just install Windows 10 directly on the machine.

Your help is greatly appreciated.

---

### Post by rbmorse on 2018-08-07
I run Windows 10 in a VMWare Player virtual machine on a Fedora Linux host machine.  It has one GPU (nVidia 970 class) and works fine, although I do not use Adobe Premier Pro.  In fact, your message is the first reference I've seen to a requirement for two GPUs required to support a virtual machine on a Linux host.  Is this some pertaining to video editing? 

Any PC you can build to run Windows 10 should be fine with any contemporary Linux distribution.  The only area where you might have compatibility issues is peripheral equipment (very high def scanners or units with special film handling functions, some esoteric printers, etc.)

---

### Post by John_Patrick_Mason on 2018-08-07
[QUOTE=rbmorse]I run Windows 10 in a VMWare Player virtual machine on a Fedora Linux  host machine.  It has one GPU (nVidia 970 class) and works fine,  although I do not use Adobe Premier Pro.  In fact, your message is the  first reference I've seen to a requirement for two GPUs required to  support a virtual machine on a Linux host.  Is this some pertaining to  video editing?[/QUOTE]

Based on the limited research I've done, yes. See [here]("https://www.reddit.com/r/VideoEditing/comments/4236ic/is_it_advisable_to_try_video_editing_in_a_virtual/"). Read the 1st comment down by thirteeners801. It says OS emulation, as it is, requires substantial resources, and that unless you have a PC with god-like hardware, a VM solution (in the context of video editing) is going to be "frustratingly slow".
Now read 8th comment down by Flakmaster92. It, again, re-emphasizes that a high-end machine might be able to handle it, but that virtual machines do have lower performance (again, in the context of video editing) and that in order to overcome this, 2 GPUs are required with something called PCIE passthrough.

As for the last sentence, I guess I was worried about buying new hardware, and having to wait for developers to make the new Linux drivers available.

What's the deal with Nvidia drivers on Linux? I've seen repeated mention  of poor performance from open source vs proprietary drivers.

---

### Post by pqwoerituytrueiwoq on 2018-08-07
in general, nvidia's proprietary drives outperform the open source driver.
on the other hand AMD has embarrassed open source drivers, but you will probably want the lastest kernel (newer than what ships with 18.04) especially if you are using a vega gpu, i do not think free sync works yet on linux...

if you want part advice, a budget would be useful and are you looking for per-built or are you doing it yourself

for virtual machines the biggest thing you need is ram and DDR4 is expensive, even DDR3 ram is around 50% higher than it was around 5 years ago
running separate gpu for a virtual system has it advantages but is not mandatory (gpu performance is gonna suck)
[https://www.youtube.com/watch?v=SsgI1mkx6iw](https://www.youtube.com/watch?v=SsgI1mkx6iw) if you want to see how dual gpu works with guides for this use senario, different end goal but if you need better than very old integrated gpu performance in a virtualbox i guess it is a good start

---

### Post by rbmorse on 2018-08-07
You might consider equipping your new box for video work using windows as the main O/S, then set up a Linux virtual machine running on the Windows host for everything else.  I forget the name of Microsoft's in-house vitrual machine manager (Hyper-V?), but as I recall it will happily host a Linux VM.

---

### Post by deltamind on 2018-08-08
So it would be more beneficial to build a PC with Nvidia's GPU instead of AMD? If budget is not a constraint.

---

### Post by pqwoerituytrueiwoq on 2018-08-08
at present nvidia gpu's on the consumer high end amd does not have a product to compete with them, not sure about professional cards (quadro/radeon pro)
* nvidia will/should be release new gpus around the end of the month (current gen is over 2 years old)
since you seem to not have a budget you may want to look at threadripper for a cpu, but check to see how well your editor benefits from 16-64 threads, if at all
IIRC Linus attempted ti use a system with i think over 100 low clocked cores and adobe premier performed like crap

---

### Post by springshades on 2018-08-08
Your setup is EASIER using Windows as the host and Linux as the VM. You don't need to do GPU passthrough if you don't do anything visually demanding in Linux.

If you decide to do a Linux host with a Windows VM, just understand that GPU passthrough is hard. In general, most 2D stuff is fine without doing GPU passthrough, but 3D stuff is terrible and GPU compute is even worse. The latter is probably what kills most people who try to edit video in a VM. If you decide to do GPU passthrough, your most economical solution is to get a CPU with integrated graphics and an AMD GPU. Your Linux host will use the integrated graphics. The AMD GPU will be used for the passthrough. Note that to set this up properly, Linux will NOT have access to the AMD GPU. It will be stuck with the IGP. Why AMD? NVidia drivers attempt to detect whether consumer grade GPUs are running in a VM and blocks them. People have managed to get things working with various workarounds. However, it is more difficult and there is always the worry that NVidia may figure out a way to block the workarounds. Note that this is NOT an issue if you plan to get a Quadro. The entire point of the NVidia VM block is to sell more expensive Quadro cards. You can still do this with a consumer grade NVidia card as long as you understand the caveats.

Generally NVidia drivers are much better in Linux, but if you're passing your GPU on to Windows, that won't matter anyway.

Other than that, very few things have issues with Linux compatibility anymore. The things that top my list are: obscure or brand new wireless cards, dedicated sound cards, and hardware RAID cards that don't run in JBOD mode.

EDIT: One thing I realized that I forgot about. If you do GPU passthrough, each OS is going to have its own video output. Therefore, you're really going to want to have a monitor with at least two inputs and the ability to switch between inputs. That's probably not going to cost you much more than any other monitor, but you'll need to pay attention to it when you buy. A lot of monitors will have multiple inputs, but you don't want to get stuck having to use something odd like an old VGA input.

---

### Post by John_Patrick_Mason on 2018-08-08
[QUOTE=springshades]The entire point of the NVidia VM block is to sell more expensive Quadro cards.[/QUOTE]

Sounds like something that should be illegal.

[QUOTE=pqwoerituytrueiwoq]If you want part advice, a budget would be useful and are you looking for per-built or are you doing it yourself.[/QUOTE]

Since it's my first time building a PC, any part advice would be welcome. I already know what internal components make up a computer, I'm just not sure *which* components to buy. But I don't just want to be told *what* to buy, I want to be told *why* I should buy a particular component, and why you think it's compatible with the rest of the other components, so that next time I can do it on my own. Ideally, I'd like to spend between $1000-$2000. I won't complain, though, if I go a few hundred dollars over.

Assuming GPU passthrough isn't necessary to edit videos taken with a 4K camera (did I get that right?), I'm think I'm going to have to go with an AMD GPU on a Linux host. Again, I'd like to avoid running Windows 10 directly on the machine -- for security reasons. Also, depending on how much it's going to cost, I'd also like to get an SSD as the main drive.

---

### Post by springshades on 2018-08-09
> Assuming GPU passthrough isn't necessary to edit videos taken with a 4K camera (did I get that right?)

I don't think anyone has answered that for you. I did a look around on youtube and some forums, and I haven't seen anyone doing editing in 4K resolution without GPU passthrough.

My experience is that for normal use, the VM is perfectly responsive and functional. I also know that some people have done video editing in lower resolutions in a VM without issue. However, I can imagine that "responsive and functional" is not quite the same thing as being able to edit a 4K video in full resolution without missing any frames and no graphical glitches which would probably be aggravating in your line of work. At the very least, I know that you generally have a limit to the amount of RAM memory that can be dedicated to the VM for graphics, and I don't believe the VM has direct access to ANY of the GPU's memory without passthrough. I also know that a recent high end consumer GPU will double your rendering speed (vs CPU-only rendering) which will not be possible inside of a VM without passthrough.

The things that you don't need to worry about as much are CPU, RAM, and disk. When you want to do something intensive in the VM, you only need to set aside for the host ~1-2 cores, ~2-4 GB RAM, and you can run the VM on an SSD or a separate disk. The host can run with very few resources if it's just sitting there idle, and the VM will get ~95% of the performance out of all the things you pass to it for the most part (except the GPU without passthrough). If you have 8 cores and maybe 24 GB RAM, you should never have an issue because of the VM. Honestly, you might not even need that.

You don't have to do what I do, but I like to use a mixture of SSD and HDD to get a good balance of price, size, and performance. A moderately sized SSD can fit your OS, the "C" drive of your VM Windows, your swap, and your most important programs. Partitioned properly, the HDD can fit all of your data for both Linux and Windows and some of your larger programs.

---

### Post by pqwoerituytrueiwoq on 2018-08-09
I found that video i mentioned:
[https://www.youtube.com/watch?v=9mlloZT5ZyY](https://www.youtube.com/watch?v=9mlloZT5ZyY)
may as well just use a Ryzen 5 1600x or 2600x unless you do not care about spending money that gains you nothing
if you want to keep gpu passthrough as a option look for a x470 board, youtube search for "Level1Techs x470 linux test"
otherwise look at this [https://www.msi.com/Motherboard/B450-TOMAHAWK](https://www.msi.com/Motherboard/B450-TOMAHAWK) IIRC that one works pretty good under linux

contrary to what springshades said you do not need 2 video outs, it is possible to copy the frames from one gpu to the other and use one output, but the software is in early stages

---

### Post by John_Patrick_Mason on 2018-08-10
[QUOTE=springshades]I don't think anyone has answered that for you. I did a look around on  youtube and some forums, and I haven't seen anyone doing editing in 4K  resolution without GPU passthrough.[/QUOTE]

My bad, when you said 3D, I thought you were referring to doing 3D animation.

[QUOTE=springshades]If you have 8 cores and maybe 24 GB RAM, you should never have an issue because of the VM.[/QUOTE]

Are we talking "functional"-level performance? Or is that the level of hardware that's required in order to edit 4K videos in full resolution without frame drops? If it can't be done then I'd rather dual boot.

---

### Post by springshades on 2018-08-10
> contrary to what springshades said you do not need 2 video outs, it is possible to copy the frames from one gpu to the other and use one output, but the software is in early stages

Do NOT do this. The statement "in early stages" is vastly underselling the fact that Looking Glass is currently considered in an "alpha" state by the developers. You should NOT consider this software ready for anything where you want to actually get something done as opposed to just gaming where results don't really matter. In two years? Maybe. Right now? Use two inputs.

> My bad, when you said 3D, I thought you were referring to doing 3D animation.

I did mean 3D. My point is that we all know that 3D is bad. Most of us have had good experience with 2D performance. However, I don't think that anyone in here has pushed 2D performance as far as you would like to. So none of us can say with 100% certainty that you will have good results. Does that make sense? No one has any reason to believe that it won't work except for possibly the video memory limits, but those limits depend on which program is running the VM anyway. But no one can say with 100% certainty that it will work either.

Before you spend several thousand dollars, you may want to try to check with someone who has done it. I wonder if maybe someone on phoronix would know as that site is dedicated to Linux benchmarking. Perhaps check with one of the Linux youtubers and see if you get a response? They use Linux and have to edit videos. 

> Are we talking "functional"-level performance? Or is that the level of hardware that's required in order to edit 4K videos in full resolution without frame drops? If it can't be done then I'd rather dual boot.

I haven't edited 4K videos, period. I'm going based on the fact that people who edit 4K video generally say that 16 GB RAM is *enough* and a high end CPU for rendering speed is really nice. If you have 20+ GB RAM and 8 cores CPU then you'll be able to meet those requirements AND have enough left over to run your host. 20 GB RAM is actually a strange number to install in a machine (5 x 4GB chips? 2 x 8 GB + 1 x 4 GB?), so 24 GB was the next easy step up. Basically, you shouldn't be worrying about CPU/RAM/disk. The amount of hardware that you need will only cost %10-20 more than someone who isn't running in a VM in my estimation.

EDIT: Another reason why I chose those numbers for CPU cores and RAM is bang for buck. That CPU and RAM combo is probably under $500 which is well within your budget. Ryzen 7 1700 is ~$220. 24 GB RAM is probably in the ballpark of $240.

If dual booting is an option for you, it's probably much easier.

---

### Post by John_Patrick_Mason on 2018-08-15
[QUOTE=springshades]Does that make sense?[/QUOTE]

Yes.

I'm going to ask around on phoronix if any of them have any experience editing videos in 4K in a VM using GPU passthrough. I'll let you know what answers I get back. In the meantime, I'll leave this thread open for when I will need to ask for specific part advice. I might also need help when I decide to do a custom install of Ubuntu if I decide to buy both an SSD and HDD; I've done it once already, but on an old HDD.

---

### Post by mariroma on 2018-08-16
[COLOR=#333333][FONT=q_serif]In all my years dealing with pc’s there have only been a few things that linux drivers have been an issue with.[/FONT][/COLOR]
[COLOR=#333333][FONT=q_serif]graphics cards - Nvidia have been hit or miss, not just with models but sometimes an update introduced an error, often with one game or game engine.[/FONT][/COLOR]
[COLOR=#333333][FONT=q_serif]printers - MANY printer companies have limited drivers for printers, esp for some with scanners built in. I often found I had to use a generic driver with very little options & sometimes limited quality[/FONT][/COLOR]
[COLOR=#333333][FONT=q_serif]Keyboard & mouse - sounds daft doesn’t it? normal keyboard & mouse no issues, but gaming ones, well, I had a Logitech 6 button mouse & a Logitech g510 keyboard (with macro keys) I could BOTH to work but not at the same time, the Logitech software could only handle 1 device at a time.[/FONT][/COLOR]
[COLOR=#333333][FONT=q_serif]the only other times I’ve had issue with linux drivers were on things you would not use in a home set up, I used to work on shop tills, with touch screens, cash drawers etc, & devices like 24volt USB cards (yes they exist) but these are not designed for home users.[/FONT][/COLOR]

---

