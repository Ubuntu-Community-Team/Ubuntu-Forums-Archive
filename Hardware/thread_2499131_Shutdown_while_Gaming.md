---
title: "Shutdown while Gaming"
date: 2024-07-13
forum: Hardware
---

### Post by Shibblet on 2024-07-13
My computer will randomly shutdown while I am in the middle of a game.

This makes me think that it may be overheating... but I really can't be sure.

I don't even know where to begin to troubleshoot this.

What can I do to figure out the problem?

---

### Post by Tadaen_Sylvermane on 2024-07-13
Usual suspects. Make sure fans work. Clean out dust. First things to do

---

### Post by currentshaft on 2024-07-14
What computer? What game? Most importantly, what temperatures?

---

### Post by Doug S on 2024-07-14
> **currentshaft said:**
> What computer? What game? Most importantly, what temperatures?Additionally, what processor make and model?

---

### Post by &amp;KyT$0P# on 2024-07-14
> **Shibblet said:**
> My computer will randomly shutdown while I am in the middle of a game.

Does it actually shutdown (like if you had initiated shutdown from your desktop environment), or abruptly power off?

> it may be overheating... but I really can't be sure.

Look up maximum temperatures for your CPU and GPU, then use [FONT=monospace]psensor[/FONT] and keep an eye on it while gaming to see what temperatures are actually reached?

---

### Post by deadflowr on 2024-07-14
Review the logs of the end of the last boot with
```
journalctl -b -1 -n 100
```
that'll give you the last 100 lines of the last logging for the last boot session.
You can change the boot session by increasing or decreasing the -1 option.
Putting nothing means current boot, -1 is the last boot, -2 is the boot before that, and so on.
Hope it helps.

---

### Post by Shibblet on 2024-07-14
> **Tadaen_Sylvermane said:**
> Usual suspects. Make sure fans work. Clean out dust. First things to do
That was the first thing that I did.

> **currentshaft said:**
> What computer? What game? Most importantly, what temperatures?
It's a Minisforum HX90G.  I was playing Remnant: From the Ashes
Not sure what temperatures.

> **Doug S said:**
> Additionally, what processor make and model?
It's a Ryzen 5800HX, with AMD 6600M GPU
It's a mini computer... so for all intents and purposes, it's a laptop with no screen.  ;-)

> **halogen2 said:**
> Does it actually shutdown (like if you had initiated shutdown from your desktop environment), or abruptly power off?
It actually shuts down.  It does not abruptly power-off.

Thank you all!  This gives me a great starting point.

I will check the psensor information soon.

---

### Post by Shibblet on 2024-07-14
Psensor shows EDGE = at max 55C, but Junction at Max = 114C.

sensor (terminal) shows
edge:         +35.0°C  (crit = +100.0°C, hyst = -273.1°C)
                       (emerg = +105.0°C)
junction:     +36.0°C  (crit = +110.0°C, hyst = -273.1°C)
                       (emerg = +115.0°C)

So, Edge is the Overall GPU Temp, and Juction is probably the "hot-spot."

Not sure how to keep that hot-spot temperature from hitting 115C, which is "Emergency" and probably initiates a shut-down.

---

### Post by him610 on 2024-07-14
> My computer will randomly shutdown while I am in the middle of a game.
> Not sure how to keep that hot-spot temperature from hitting 115C, which is "Emergency" and probably initiates a shut-down.

Suggest you consider finding another game to play.

---

### Post by currentshaft on 2024-07-15
> **him610 said:**
> Suggest you consider finding another game to play.

This, or build a computer with a better cooling design. This one is clearly not optimized for performance. It's just basic thermodynamics.

---

### Post by Shibblet on 2024-07-15
> **him610 said:**
> Suggest you consider finding another game to play.

> **currentshaft said:**
> This, or build a computer with a better cooling design. This one is clearly not optimized for performance. It's just basic thermodynamics.

Helpful.  Thanks.

---

### Post by Shibblet on 2024-07-16
So, does anyone know how to keep the GPU "hot-spot" from going over it's limit?
Are there any utilities like AMD's Adrenaline Drivers, only for Linux?

---

### Post by him610 on 2024-07-16
> how to keep the GPU "hot-spot" from going over it's limit?
Would some sort of kludge external cooling device work?

---

### Post by him610 on 2024-07-16
[https://www.guru3d.com/review/minisforum-hx90g-(ryzen-9-5900hx)-mini-pc-review/]("https://www.guru3d.com/review/minisforum-hx90g-(ryzen-9-5900hx)-mini-pc-review/")
> ... The HX90G has seven heat pipes (3 for the CPU and 4 for the GPU), liquid metal for both the CPU and the GPU, and a twin fan inside for heat dissipation. Even when fully loaded, it will operate silently.

End users interested in this product should be located in the low-level gaming, SOHO, Net PC, or HTPC markets....

I am not one who plays games other than solitaire or mah jongg so I don't put much stress on CPU/GPU.

Can the BIOS be set so your GPU temps do not exceed 90 C so it would not damage GPU due to overheat?

---

### Post by currentshaft on 2024-07-16
> **Shibblet said:**
> So, does anyone know how to keep the GPU "hot-spot" from going over it's limit?
Are there any utilities like AMD's Adrenaline Drivers, only for Linux?

By designing air flow and components in a way which optimizes performance over cost. This is the opposite of what happened to the device you purchased.

You won't solve a hardware design flaw with software.

The best you can realistically do is reduce demand on resources by scaling down resolution, upscaling, etc.

---

### Post by him610 on 2024-07-17
@currentshaft
> You won't solve a hardware design flaw with software.
That is an excellent observation.

Another way to put it is to stay within the system constraints. A muleskinner would not load 400 pounds on a mule whose limit was 200 pounds.

---

### Post by Shibblet on 2024-07-17
> **him610 said:**
> @currentshaft

That is an excellent observation.

Another way to put it is to stay within the system constraints. A muleskinner would not load 400 pounds on a mule whose limit was 200 pounds.

Here's the deal...  I own this computer outright.  I don't want to spend the money to build a big large clunky desktop just to play a few games.  This computer can handle most everything I throw at it...
The only problem is that it will shut down (I think) when the CPU Hot-Spot hits 115.0C.  Strange part is that the GPU Temp never gets above 60.  It's just the hot-spot temp.

But it doesn't just shut off, it actually goes through the shutdown sequence.

So, this is a conundrum.  I've searched the internet to no avail... and after running a bunch of tests, that's the only plausible reason I can find.

---

### Post by Tadaen_Sylvermane on 2024-07-17
> Here's the deal...  I own this computer outright.  I don't want to spend  the money to build a big large clunky desktop just to play a few games.   This computer can handle most everything I throw at it...

Based on your statement I'm assuming this is an all in one? I love those but they are useless for any kind of gaming if only due to thermal limits. Just because the hardware can do it doesn't mean the cooling will keep up. That is your problem. All the hardware in the world is worthless if it can't be cooled somehow.

---

### Post by Shibblet on 2024-07-18
> **Tadaen_Sylvermane said:**
> Based on your statement I'm assuming this is an all in one? I love those but they are useless for any kind of gaming if only due to thermal limits. Just because the hardware can do it doesn't mean the cooling will keep up. That is your problem. All the hardware in the world is worthless if it can't be cooled somehow.

I'm finding that out.  It's a Mini-PC.  Minisforum HX90G.  So in essence it's a laptop without a screen.

I just realized that this issue only started when I got a new monitor.  I didn't even THINK that could be the problem.  But what I think I am finding, is that my old monitor topped out at 60hz, so my GPU never had to work that hard to produce 60fps.  Now I have a 144hz monitor, and I find that if I put it into 60hz mode, the problem doesn't happen.  So, now I am being "tech-snobby," and I want my better FPS with this new monitor.

I can't really notice much over 72fps anyway... it all looks the same to me after that.  So if I could find a way to limit my games to 72fps, I probably wouldn't have a hot-spot that overheats.
This machine has an HX5900 CPU and a 6600M GPU, and I can play most games on 1080p (Ultra Settings), with 60+ FPS.  A lot of newer titles have options for limiting the frame-rate, so I can get by.  But a lot of other titles I have, do not have the ability in the options.

So, I am looking for the ability to limit the FPS to ~72fps.

---

### Post by Tadaen_Sylvermane on 2024-07-18
> 
**Frame rate limit**


The DXVK_FRAME_RATE environment variable can be used to limit the frame rate. A value of 0  uncaps the frame rate, while any positive value will limit rendering to  the given number of frames per second. Alternatively, the configuration  file can be used.

[https://github.com/doitsujin/dxvk](https://github.com/doitsujin/dxvk)

I'm assuming you are using dxvk in some fashion. I can't live without it on Battle.net via Bottles.

*EDIT* I just tried this in Bottles, seems to work. In WoW the FPS is floating between 49 and 50 right now (I personally don't see much difference beyond 45 or 50 anyway).

---

