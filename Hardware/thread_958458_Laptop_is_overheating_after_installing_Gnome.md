---
title: "Laptop is overheating after installing Gnome"
date: 2008-10-25
forum: Hardware
---

### Post by snova on 2008-10-25
I've been happily using Kubuntu for several months now, but a few days ago I decided to give Gnome another try. I installed the ubuntu-desktop package, started everything, and now several things are happening.

First of all, when Gnome starts up, it opens a message box saying "Failed to initialize HAL".

More importantly, it gets to over 160 F, even without X running- logged into a console running "watch acpi -tf", it steadily increases until I shut it down. The fan did not start even at these temperatures. The normal operating range is about 120 F, although this may lower now that it's been cleaned.

In addition, Gnome is sometimes unresponsive to the point of freezing entirely. The last time it happened, I had to give it a hard reboot.

This has nothing to do with being dirty. My laptop has probably been dirty a long time, there's no way it suddenly inhaled that much fuzz over the length of time it took to install Gnome. Either way, I took it to a PC store earlier today and they cleaned it out. No difference from yesterday.

If it makes any difference, ubuntu-desktop pulled in many dependencies that weren't there previously. I don't remember which ones they were, but likely everything that kubuntu-desktop didn't depend on already.

It is nearly two years old and is a Dell Inspiron E1505.

---

### Post by Sponzenbroekske on 2008-10-25
> **snova said:**
> I've been happily using Kubuntu for several months now, but a few days ago I decided to give Gnome another try. I installed the ubuntu-desktop package, started everything, and now several things are happening.

First of all, when Gnome starts up, it opens a message box saying "Failed to initialize HAL".

More importantly, it gets to over 160 F, even without X running- logged into a console running "watch acpi -tf", it steadily increases until I shut it down. The fan did not start even at these temperatures. The normal operating range is about 120 F, although this may lower now that it's been cleaned.

In addition, Gnome is sometimes unresponsive to the point of freezing entirely. The last time it happened, I had to give it a hard reboot.

This has nothing to do with being dirty. My laptop has probably been dirty a long time, there's no way it suddenly inhaled that much fuzz over the length of time it took to install Gnome. Either way, I took it to a PC store earlier today and they cleaned it out. No difference from yesterday.

If it makes any difference, ubuntu-desktop pulled in many dependencies that weren't there previously. I don't remember which ones they were, but likely everything that kubuntu-desktop didn't depend on already.

Sounds like a hardware-issue, maybe your HD is dieing, or your fan is broke.
And if your laptop gets to hot, then you could expect some freezes.

How old is your laptop and what brand is it?

---

### Post by snova on 2008-10-25
It will be two years old in a few months (Christmas). Dell Inspiron E1505.

The fan did kick in at one point yesterday, but I don't know how hot it was before it did. It never went below 150 F even after it activated. More like 156/158.

Should have mentioned that before...

---

### Post by Sponzenbroekske on 2008-10-25
You could try reinstalling Kubuntu and staying away from Gnome.

Can you also feel the heat? (and I'm calculating in °C, so I really have no clue how much 150°F is)

I guess that laptop can handle up to 80°C, before freezing.

But isn't there a safety that shuts down your laptop when it hits 80°C or something? You sure can install it, maybe look in synaptic or adept.

It's a good brand and its not old at all, so this is kinda strange that it is happening :s.

And is it your CPU that is getting so hot, or is it your chipset?

I know a few tips:
You might need new cooling paste for your CPU (I think that costs € 5,00, and a little effort)
You could replace your fan (€ 10,00)
A cooling dock, but then your laptop will lose his function and it will have to stay in one place (€ 25,00)
Or off course a new laptop :s (€ 300,00-3 000,00)

Anywho, try the advise of reinstalling first, maybe that works and else you gotta get some help from some hardware"geeks", or bring it in for repair.

---

### Post by snova on 2008-10-25
> **Sponzenbroekske said:**
> You could try reinstalling Kubuntu and staying away from Gnome.

I'm still not certain it's the fault of Gnome. I really hope it isn't, actually, since it appeals to me in a way KDE does not.

I've been thinking about reinstallation anyway, though. There's a few rough edges that have accumulated over the past year or so that would be a lot easier to fix by reinstallation than by asking and solving them one at a time.

> **Sponzenbroekske said:**
> Can you also feel the heat? (and I'm calculating in °C, so I really have no clue how much 150°F is)

Not sure. (150 F = 65 C, see [http://www.wbuf.noaa.gov/tempfc.htm](http://www.wbuf.noaa.gov/tempfc.htm))

I'm just watching "acpi -t".

Sorry, American here. :) Unfortunately I can't approximate temperatures (like, 50 F is cold, 90 F is too hot to go outside, etc...) in Celsius.

> **Sponzenbroekske said:**
> I guess that laptop can handle up to 80°C, before freezing.

176 F. I didn't know until today that a computer can actually degrade in performance due to higher temperatures. That would also explain Gnome's unresponsiveness.

> **Sponzenbroekske said:**
> But isn't there a safety that shuts down your laptop when it hits 80°C or something? You sure can install it, maybe look in synaptic or adept.

Probably. At any rate the CPU will shut itself off if it tops somewhere between 100 C and 120 C, but at that point, I'm screwed...

> **Sponzenbroekske said:**
>  It's a good brand and its not old at all, so this is kinda strange that it is happening :s.

That's good to hear.

> **Sponzenbroekske said:**
> And is it your CPU that is getting so hot, or is it your chipset?

Again, I really don't know. I just noticed that acpi was showing unusually hot temperatures and that the fan was running when it usually didn't (which was the tip-off).

> **Sponzenbroekske said:**
>  I know a few tips:
You might need new cooling paste for your CPU (I think that costs € 5,00, and a little effort)
You could replace your fan (€ 10,00)
A cooling dock, but then your laptop will lose his function and it will have to stay in one place (€ 25,00)
Or off course a new laptop :s (€ 300,00-3 000,00)

I would like to get a cooling thingy. One that props it up a bit would be nice...

> **Sponzenbroekske said:**
>  Anywho, try the advise of reinstalling first, maybe that works and else you gotta get some help from some hardware"geeks", or bring it in for repair.

That's my intention. I'm going to bring it in in a few days. Mom brought it to the shop earlier to have them clean it (false hope, but it needed it anyway), but I guess I'll be going back.

Idea! Live CD. If I get the same result, it's the fan. Otherwise, a reinstallation would be my best bet. I've been meaning to repartition things anyway...

Wouldn't have thought of that, thanks for the idea.

---

### Post by snova on 2008-10-25
All right, I booted into an Intrepid live CD (Kubuntu Alpha 3, to be exact) and it never topped 120 F (48 C).

I have not attempted booting into the hard drive with KDE yet, however the last time I tried I got the same results as with Gnome.

I am now almost entirely certain that this is a result of one of the dependencies pulled in by ubuntu-desktop, and not my fan. Unfortunately, I don't know what was installed, except that the process involved over 100 MB of downloads.

Fortunately, it should be easy enough to remove ubuntu-desktop and the offending package once I pinpoint the problem. I'm going to browse packages.ubuntu.com and see which dependencies look suspicious, and try removing them.

---

### Post by Sponzenbroekske on 2008-10-25
> **snova said:**
> 

65°C aint that hot, maybe a little. If I block (by accident) my cooling holes, it shifts up to 80°C in no time and I still can use it without any issues.

And I know that 32°F is 0°C (freezingpoint).

And maybe it is easier to download/order an **Ubuntu**cd, instead of installing 2 desktopmanagers, I did that too and all th programs are scrabbled, aint fun to work with, I suggest a fresh Ubuntu install.

And then that cooling thingy :p, I hope paste is the right word (in Belgium (Dutch) we call it "pasta").
So its in a tube, you put it between your CPU and your cooling block, it helps to bring the heat from the CPU to the cooling block more effectively, if you want to use it, make sure that old cooling paste is removed.

And you say you can run it from the livecd without any problem, so I guess it wont be your CPU or chipset.
If it is hardware-related then it will be your HD, cuz this isnt tested during the uwe of the livecd.

---

### Post by snova on 2008-10-25
> **Sponzenbroekske said:**
> 65°C aint that hot, maybe a little. If I block (by accident) my cooling holes, it shifts up to 80°C in no time and I still can use it without any issues.

And I know that 32°F is 0°C (freezingpoint).

And maybe it is easier to download/order an **Ubuntu**cd, instead of installing 2 desktopmanagers, I did that too and all th programs are scrabbled, aint fun to work with, I suggest a fresh Ubuntu install.

And then that cooling thingy :p, I hope paste is the right word (in Belgium (Dutch) we call it "pasta").
So its in a tube, you put it between your CPU and your cooling block, it helps to bring the heat from the CPU to the cooling block more effectively, if you want to use it, make sure that old cooling paste is removed.

And you say you can run it from the livecd without any problem, so I guess it wont be your CPU or chipset.
If it is hardware-related then it will be your HD, cuz this isnt tested during the uwe of the livecd.

The trouble is that I'm not certain if I want to stick with Gnome- I might go back to KDE, especially after KDE 4 stabilizes. I also like some of the KDE programs more than their Gnome counterparts, so I'll probably have at least the base of KDE installed, if not more.

One thing that really bothers me is that KDE control center modules show up on Gnome menus, making them really long.

I doubt that it's the hard drive.

But I've about made my decision- I'm going to reinstall after Intrepid comes out. It's only a week to wait. Then I'll boot it, update my backup (rsync is *great*!), and install.

I have other reasons for it anyway, so this is just the final prod.

Thanks for everything!

---

### Post by Sponzenbroekske on 2008-10-25
You can run KDE apps in GNOME, that's no problem :), so that's not a reason to stick to KDE :p, but indeed KDE4 is nice.
Dualboot Kubun/Ubun, and after a few weeks you will know which one will stay. I'm gonna bet on KDE, cuz you're used to it.

---

### Post by snova on 2008-10-25
I already know KDE apps will work, but if I go back to KDE 4, it's going to be because of Plasma. I like the idea of having multiple Folder Views around, it's so much more flexible than a static Desktop directory.

On the other hand, I really like certain elements of the Gnome interface, particularly the usage of panels. I could probably achieve similar results in KDE, but not everything.

The Gnome approach to configuration is nice- gone is the Apply button! for change happens immediately.

But I *HATE* the way desktop icons are all different sizes. They don't line up!

---

### Post by Lord Xeb on 2008-10-26
Try this out and see if it helps lower you temps: [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)

This will allow you to adjust the fan manually when needed. Also, try cleaning out the heat sink by spraying a can of air into it when the laptop is off. Dust is a big problem for all computers.

---

