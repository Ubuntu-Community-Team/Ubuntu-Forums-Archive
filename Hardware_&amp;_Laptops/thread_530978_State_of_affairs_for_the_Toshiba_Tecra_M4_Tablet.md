---
title: "State of affairs for the Toshiba Tecra M4 Tablet?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by mapage on 2007-08-21
About a year ago my Toshiba Tecra M4 died a slow and painful death.  (The video system died.)  Prior to it's untimely demise I ran Ubuntu Dapper on it exclusively (or was it Edgy...)  Now that I have graduated from school and am employed, I'm thinking about resurrecting the old tablet.

So my question is this...  How is the state of affairs for the Toshiba Tecra M4 and the most recent Ubuntu version?  (What's it called?  Goofy Gophers?  Gummy Goobers?  Galloping Gwendolyn?  Ohh wait...  Gutsy Gibbon...  That's it...)

Specifically I'm looking at things that didn't work so well before...
CPU Voltage regulation?
hibernation?  (It used to hibernate slowly, but it was a crapshoot whether it would come back or not.)
sleep/standby - 10 minutes to standby, 15 seconds to come back, if it came back...
the accelerometer
Screen rotation seems to have worked pretty well.
On screen buttons,
Bluetooth...
My memory is failing me...  I don't remember what other things I struggled to get to work correctly...  So as a catch-all, is there anything that now works well that didn't work well before?

I know that this is an open ended question, so I especially appreciate anyone who takes the time to answer with useful information.

---

### Post by 23meg on 2007-08-21
> **mapage]How is the state of affairs for the Toshiba Tecra M4 and the most recent Ubuntu version? (What's it called? Goofy Gophers? Gummy Goobers? Galloping Gwendolyn? Ohh wait... Gutsy Gibbon... That's it...)[/QUOTE]

I haven't done much testing on recent Gutsy with the M4 said:**
> CPU Voltage regulation?

What problem did you have with voltage regulation? If you mean frequency scaling, it has always worked out of the box. 

> **mapage]hibernation? (It used to hibernate slowly, but it was a crapshoot whether it would come back or not.)[/QUOTE]

Still the same, but I've seen people reporting success with custom kernels.

[QUOTE=mapage]sleep/standby - 10 minutes to standby, 15 seconds to come back, if it came back...[/QUOTE]

Same as above.

[QUOTE=mapage]the accelerometer[/QUOTE]

I haven't tested it.

[QUOTE=mapage]Screen rotation seems to have worked pretty well.[/QUOTE]

Still works very well.

[QUOTE=mapage]On screen buttons,[/QUOTE]

They work said:**
> Bluetooth...

Works.

[QUOTE=mapage]My memory is failing me... I don't remember what other things I struggled to get to work correctly... So as a catch-all, is there anything that now works well that didn't work well before?[/QUOTE]

The Geforce Go6200 (if that's what you have) still performs poorly with 2D rendering, and the black window bug with Compiz persists. The tablet stylus now works out of the box, without any need for configuration. The configurable button on the upper right side of the casing now works. 

Except suspend and hibernate, pretty much everything works out of the box. Whether you'll want to resurrect the machine will perhaps depend more on how much you care about its Achilles' heel, which is still there: lots of heat and loud fan.

---

### Post by mapage on 2007-08-21
> **23meg said:**
> I haven't done much testing on recent Gutsy with the M4; the below is the state of things in Feisty.


Has there been any noise from Gutsy that some of the other things not mentioned as working below will work?  I can't imagine that this two year (or so) old Tablet is high on the priority list...

> **23meg said:**
> 
What problem did you have with voltage regulation? If you mean frequency scaling, it has always worked out of the box. 


You are right that frequency scaling always worked pretty well.  I was referring more to being able to change the CPU Core voltage.  Lower voltage means less heat and consequently, less fan noise.  Under Windows there is a utility that allowed me to run my laptop for anything other than graphic intensive tasks without the fan coming on at all.  It was nice and quiet, but who wants to run Windows if they don't have to?  I remember you experimenting with this and lunching a mainboard in the process...  I was hoping it was something built in and not a fringe custom-kernel thing anymore.

It sounds like the things that annoyed me the most about the tablet with Ubuntu haven't changed.  That's CPU undervolting and suspend to ram.

Thank you for your informative reply!

---

### Post by 23meg on 2007-08-21
[QUOTE=mapage]Has there been any noise from Gutsy that some of the other things not mentioned as working below will work? I can't imagine that this two year (or so) old Tablet is high on the priority list...[/QUOTE]

I'm not sure, and it's hard to know without testing and some backing information. I'll test the tablet with Gutsy Tribe 5 when it's out and post back.

[QUOTE=mapage]You are right that frequency scaling always worked pretty well. I was referring more to being able to change the CPU Core voltage. Lower voltage means less heat and consequently, less fan noise. Under Windows there is a utility that allowed me to run my laptop for anything other than graphic intensive tasks without the fan coming on at all. It was nice and quiet, but who wants to run Windows if they don't have to? I remember you experimenting with this and lunching a mainboard in the process... I was hoping it was something built in and not a fringe custom-kernel thing anymore.[/QUOTE]

I don't think CPU undervolting will be supported in any kernel version and in any mainstream OS, for any computer and CPU model, ever. It's an undocumented and dangerous hack that has potential to fry hardware, and as you've mentioned, I've proven that potential once. 

I'll be the first to admit that an undervolted M4 is very attractive, with almost no fan noise, and very cool operation, but it's the wrong fix. The source of the problem is the inherently flawed design of the tablet's internals (yes, I've studied it), which in turn cause the heat and noise, and that can't be fixed with software. 

[QUOTE=mapage]It sounds like the things that annoyed me the most about the tablet with Ubuntu haven't changed. That's CPU undervolting and suspend to ram.

Thank you for your informative reply![/QUOTE]

You're welcome. The CPU thing isn't specific to Ubuntu, but to the machine itself, and I'll keep you posted on suspend and hibernate in Gutsy.

---

