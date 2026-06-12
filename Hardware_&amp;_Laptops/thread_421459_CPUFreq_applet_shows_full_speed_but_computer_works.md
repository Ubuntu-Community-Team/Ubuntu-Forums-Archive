---
title: "CPUFreq applet shows full speed but computer works at half speed"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Batuhan on 2007-04-24
Hi!

First post in forum, first time Ubuntu user. Trying out Linux after some years for the first time, and I'm very very impressed with it. I'm using my laptop for live audio, on stage. And I'm very happy about the switch from Windows.

I have a ASUS S96J laptop which has a Core 2 Duo T7200 @ 2Ghz CPU on it. This CPU supports speedstep.

I was using CPU Frequency Scaling monitor to monitor and modify CPU speed. The modification option was not enabled by default so I did:

sudo chmod +s /usr/bin/cpufreq-selector
sudo dpkg-reconfigure gnome-applets

So this enabled me to select the steppings that my CPU's supported.

I made a live music performance setup with various effects and such connected to JACK. Jack was showing ~7-8% CPU load. The CPU load indicator(on JACK) was not changing when I was modifying the speeds of my cores(~7-8%) which I found very strange. (And the load was high for the simplistic setup for a c2d CPU).

So I rebooted, disabled speedstep from my BIOS, CPU frequency scaling applet complained about not being able to scale CPU speed as I disabled it from BIOS.

Then I opened the same session and JACK was showing half the load around 3%.

Is this a bug? And if it is, what can I do to report it? (sorry I'm such a noob)

Oh and btw, I use glxgears to test and speedstep enabled and disabled sessions did not make a difference. It was running around 4100fps in each situations. But if speed step is enabled, the first 5 seconds would have a lower framerate(which may indicate a stepping change?).

So maybe, My computer is scaling the CPU correctly but failing to report and/or modify by hand? Or ~4100fps is a limit for glxgears? Is there any more software to test performances?

I do not want to use stepping in live audio situations, because I always want to have the full power of my CPU, as realtime frequency scaling invites glitches and unstability to audio. And sometimes I instantly load CPU and OS fails to update CPU freq that fast which makes it problematic. I can handle the situation by disabling stepping from BIOS, but it would be very very cool if I could manage it by hand from within the os. (ie. disabling frequency scaling manually from inside the OS by selecting a certain step that my CPU supports).

Any suggestions?

Oh and btw, feisty rocks! Audio works with low latency without glitches and xruns.

Thanks!

---

