---
title: "Laptop Hotkey WLan Switch"
date: 2010-03-09
forum: Hardware
---

### Post by Macsloverd on 2010-03-09
***I have been searching related solutions for few months (inc. search within the forum), and tried a lot of different ways to practice with no luck. However, recently I found some inspiring things and I thought it might be a good solution. I post this here looking for some advise. Thanks in advance.***

I've got a [COLOR="Red"]laptop with Broadcom WiFi card inside[/COLOR]. After installing Ubuntu, the system recognize this adapter as Broadcom Airforce One wireless lan adapter, but not functioning since [COLOR="Red"]it is required to press Fn+F4 key to start the adapter[/COLOR]. However, pressing the Fn+F4 makes no sense to Ubuntu - [COLOR="red"]Ubuntu simply does not know what does pressing Fn+F4 mean[/COLOR].

I searched the internet and get the idea of tracking the key code in ACPI output and somehow to let the system know the function of the combined key. But I failed to achieve so.

I am very keen on Debian/Ubuntu for obvious reason, so for months I leave the laptop there.

Today I tried install[COLOR="red"] Fedora 12 and this Fn+F4 works and successfully initiated the Wlan adapter and everything works fine[/COLOR].

I thought maybe I can make use of something related in Fedora 12 and somehow put them into Ubuntu (e.g. the key code), but I have no idea working with Fedora.

Then I am here looking for help.:KS Thanks for any help.

---

### Post by Macsloverd on 2010-03-09
Any help?

---

### Post by tgalati4 on 2010-03-09
What is the make and model of your laptop?

In Fedora, open a terminal:

uname -a

Write down the information for reference.  Post it here as well.

In the same terminal, run

xev

Put your mouse in the small box, and hit the Fn+F4 key, note the values that come up in the terminal.

On an IBM thinkpad, T43P, Fn+F5 key (which is for my wireless) shows up as:

PropertyNotify event, serial 30, synthetic NO, window 0x5200001,
    atom 0x1be (_NET_WM_ICON_GEOMETRY), time 169601433, state PropertyNewValue


The "atom" keycode is intercepted by the BIOS and (in this case) turns the wireless on and off.

In ubuntu, open a terminal and compare the kernel version:

uname -a

If you can't get it to work with a live CD, then you may have to do some tweaks if you do a hard disk installation.

---

### Post by Macsloverd on 2010-03-10
> **tgalati4 said:**
> What is the make and model of your laptop?

In Fedora, open a terminal:

uname -a

Write down the information for reference.  Post it here as well.

In the same terminal, run

xev

Put your mouse in the small box, and hit the Fn+F4 key, note the values that come up in the terminal.

On an IBM thinkpad, T43P, Fn+F5 key (which is for my wireless) shows up as:

PropertyNotify event, serial 30, synthetic NO, window 0x5200001,
    atom 0x1be (_NET_WM_ICON_GEOMETRY), time 169601433, state PropertyNewValue


The "atom" keycode is intercepted by the BIOS and (in this case) turns the wireless on and off.

In ubuntu, open a terminal and compare the kernel version:

uname -a

If you can't get it to work with a live CD, then you may have to do some tweaks if you do a hard disk installation.


Thanks for your reply. Here are some info:

[I]    Make: Lenovo
    Model: Soleil E280S[/I]

It is originally with Celeron Processor and without wifi adapter (but with key switch and LED indicator?!) I change the Processor into Pentium Mobile, and 1GB RAM.

[COLOR="Red"]uname -a displays:[/COLOR]
[I]Linux exp.local 2.6.31.5-127.fc12.i686 #1 SMP Sat Nov 7 21:41:45 EST 2009
i686 i686 i386 GNU/LInux[/I]

[COLOR="red"]xev displays:[/COLOR]
[I]    PropertyNotify event, serial 20, synthetic NO, window 0x4200001,
    atom 0x18c (_NET_WM_ICON_GEOMETRY), time 200316, state PropertyNewValue
[/I]
together with this 'atom' event there are more than above info, e.g.
[I]    atom 0x14e (_NET_WM_STATE)
    atom 0x1ae (XKLAVIER_STATE)
    atom 0x16b (WM_STATE)[/I]

I am not sure whether it is useful or not.

---

### Post by tgalati4 on 2010-03-10
Check your BIOS for a power manager setting that turns WiFi on.

Try downloading the latest Ubuntu Lucid CD.  Boot from it in Live CD mode and see if it detects the wireless.

You want a kernel at least as recent as 2.6.31.5-127.  I'm not sure what Karmic ships with.

---

### Post by Macsloverd on 2010-03-10
> **tgalati4 said:**
> Check your BIOS for a power manager setting that turns WiFi on.

Try downloading the latest Ubuntu Lucid CD.  Boot from it in Live CD mode and see if it detects the wireless.

You want a kernel at least as recent as 2.6.31.5-127.  I'm not sure what Karmic ships with.

Thanks for the advise, I will see into the BIOS settings.

And for the Live CD of Ubuntu, I tried for times, it always detects the wireless adapter, it just that Ubuntu can not do a thing with it unless the adapter is switched on.

---

