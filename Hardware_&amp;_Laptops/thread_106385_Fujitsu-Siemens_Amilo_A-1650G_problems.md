---
title: "Fujitsu-Siemens Amilo A-1650G problems"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by kitikri on 2005-12-20
Hello! This is my first post, so I'd like to greet everybody here, this is a great distro, I absolutely love it! And your support and community is great. Anyway, back to my problem.
I've got a Fujitsu-Siemens AMILO A-1650G, and I'm having trouble starting the live cd. Here are my specs:
Turion 64 ML-32 1.8GHz
Some "unknown-to-me" ATI Chipset
2x256MB RAM(-128 VGA Shared)
ATI X200M 128MB ^
Atheros WiFi Internal Network Adapter(not sure but I need ndiswrapper, right?)
Integrated Realtek AC97 audio
80GB Samsung
...

I've got a desktop system set up with ubuntu breezy, it runs smoothly. On the laptop, however, I have some problems. I tried both ubuntu32 and kubuntu64 so I post here. When I try to start the live cd, i can't get into gnome(or kde), unless I set the vga module to "vesa". This is not a big deal, though, as the system runs fine with it. If I run it with the auto-detected "ati" module, in ubuntu-32-5.10, X gives some strange seg fault(OK only msgbox) and then it asks me whether I'd like to view the log. If I don't press anything on my keyboard to get beside the ok-only message, in a few seconds it gives me the console, but with some very strange font and colors(those from the "ok-only" message). I tried kubuntu-64-5.10 and it runs perfectly with the vesa, but again, with the default ati module, it hangs up just before kde initialization and doesn't even give me a console, unlike the "gnomish" ubuntu. I planned to install kubuntu but I don't know whether I'll be able to set up my vga correctly after install, because I don't seem to find any suitable drivers in ati's website. I'm also wondering if ubuntu is by any means different in the his post-install condition, because I noticed that KDE supports my "on-the-fly" CPU multiplier changing (200MHz system bus, posssible cpu stepping: 2x;4x;9x). In windows, which comes installed with the lap, it is being set up correctly to ~400MHz(power saving), ~800MHz(normal) or ~1800MHz(full-power mode). So my two main problems are:
 ->the videocard
 ->the infamous chasis fan, afaik already solved somewhere here
...
 ->setting up the wireless, but maybe later :)

Anyone tried installation on a similar system? Have you got any tips, warnings? Thanks in advance:KS

---

