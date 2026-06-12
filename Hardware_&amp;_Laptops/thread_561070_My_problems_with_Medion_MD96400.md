---
title: "My problems with Medion MD96400"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by Staach on 2007-09-27
Some time ago I was running Ubuntu on my Medion MD 96400. No problems (other than the wireless not easy to set up). However, not long ago I descided to switch fully over to Ubuntu instead of a xp/Ubuntu dual boot. This has only given me problems:( I chose 7.04 but found that my laptop suddenly can´t set APIC up. So, followed the workaround wit "noapic". This made it possible to install Ubuntu, but even when  it has been fully updated the screen "flickers". I tried to reinstall xp on the pc, just to see if there was something with the HW, but everything runs smoothly.

Plz, can any one tell me why the screen suddenly flickers and why apic suddenly doesn´t work?

---

### Post by ajgreeny on 2007-09-27
Did you have an older version of Ubuntu before, when you were dual booting?  If so, it would seem likely that the monitor details, which includes resolutions, and the vertical & horizontal scanning figures was not detected properly this time when you installed; strange why not, if it was in a previous version, but such things happen.

Get the figures for vertrefresh and horizsync from the monitor specs in the handbook that should have come with the computer.  Now add lines like these to your /etc/X11/xorg.conf file, with the right figures, of course, leaving the other lines not highlighted as they were:-

    Identifier     "SONY CPD-E40"
    DisplaySize     370    270
    [B]HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0[/B]
    Option         "DPMS"
EndSection

Hopefully now when you boot or restart x you will get the right refresh rates for your monitor.  I'm sorry, but I cant help with the apic problem, not something I've seen.

---

### Post by Staach on 2007-09-29
I´m sorry to say that I did something entirely different: I tried to install another Linux distro, Opensuse10.2. I had no problems at all regarding neither APIC nor flickering screen. This tells me that my HW is ok - which is good. The flipside is that it also tells me that Ubuntu apparently has some challenges ahead. I really like Ubuntu and don´t want to change to Opensuse - so can anyone maybe tell me what would be the next step? Is there any way to pinpoint the difference regarding the APIC problem between Ubuntu and Opensuse and hopefully mending the "gap"? 

I am not really interestet in just turning APIC off by writing noapic..Also, when looking for threads regarding the APIC (and related) problem it seems quite a lot are experiencing this problem..Can I see anywhere if this is something the ever vigilant Ubuntu staff is working on and therefore could be amongst other fixes on Gutsy? (tried to install Gutsy just to see..no success at all..couldn´t install in any way).

---

