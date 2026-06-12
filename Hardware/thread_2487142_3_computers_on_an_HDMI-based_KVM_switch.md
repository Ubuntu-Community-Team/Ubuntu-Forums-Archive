---
title: "3 computers on an HDMI-based KVM switch"
date: 2023-05-24
forum: Hardware
---

### Post by Tom_ZeCat on 2023-05-24
I've got three Dell PCs that I need to use on the same keyboard, monitor, mouse, and speakers.  That's a job for a KVM switch, of course, but so far I've only had luck with two of the three computers, the two which have HDMI ports.  

The third PC is one I don't own.  The company I work for issued it to me to use for the work that I do for them.  Unlike the other two, it's a mini PC that could be attached to the back of a monitor if you so chose.  It unfortunately has no HDMI port.  Instead, it has one VGA port and two DisplayPorts.  

I initially tried using an adapter that goes from VGA to HDMI, but I think I made a mistake.  I think it's meant to plug into an HDMI port and then put that signal into a VGA monitor.  That's backwards to what I need.  

This is the KVM switch that I have: 
4K HDMI KVM Switch 4 Ports for 4 Computers Share One HD 4K Monitor, 3 USB Devices Keyboard Mouse Printer, 2 3.5mm Headphone Jack, Including 4 HDMI Cable and 1 Remote Controller

And this is that adapter: 
BENFEI HDMI to VGA, HDMI to VGA Adapter (Female to Male) with 3.5mm Audio Jack Compatible for TV Stick, Computer, Desktop, Laptop, PC, Monitor, Projector, Raspberry Pi, Roku, Xbox and More &#8211; Black

I think I probably bought the wrong adapter.  Its photo on Amazon shows it plugged into a cable (probably an HDMI), and that plugged into the laptop.  Then its other end is VGA, as if that one is going out to a VGA monitor to display the laptop's screen.  

Thus, I'm pretty sure the problem is having gotten the wrong adapter.  However, I hear it may be a blessing in disguise.  I've heard that a DisplayPort is way better quality than a VGA port anyway.  Thus, I should be trying to convert from DisplayPort (on the PC) to HDMI (into the KVM).  

My KVM has one side with an HDMI port that you plug into from the  monitor, and then it has some USB ports and a lime green sound port.  So into that, I've plugged the USB-based dongles for my Logitech Mouse and my Microsoft keyboard.  Then the other end has 4 HDMI ports, each which can go out to a computer.  However, the cable that goes from the KVM and into a computer is not a regular HDMI cable.  It's HDMI on the end that plugs into the KVM.  Then the other end splits into one HDMI end and a USB end.  It looks to me like the HDMI end handles the video, and that the USB end is so that the computer can get the feed from the keyboard and mouse dongles.  

As near as I can tell, to make this work, I need to: 

Plug into the KVM switch with an HDMI end, which then goes into the both work PC's DisplayPort.  That same end also splits to plug into a USB port (so that the keyboard and mouse work.  

The cord I have will do part of that I need.  The HDMI-only end plugs into the KVM just fine.  Then the other side, the one that splits into both HDMI and USB ends will plug into that computer's USB port, but not into the DisplayPort or the VGA one.  Therefore, I need an adapter that goes onto the end of the cable with both HDMI and USB; it attaches to the HDMI end, converting the male HDMI end to a male DisplayPort end that can go into the computer's female DisplayPort.  

I think I have it right this time.  I thought I had found what I need, but its photo shows a male HDMI end and a female DisplayPort end.  That's exactly backwards.  

I've been searching for things like &#8220;HDMI to DisplayPort adapter.&#8221;  Am I using the language backwards?  Should I be searching for &#8220;DisplayPort to HDMI adapter&#8221;?  Find one of those that has a male DisplayPort end that converts to an HDMI female end that attaches to the cord I've described.  Am I right?  

Another thing I thought of was this: I've been thinking in terms of placing an adapter on the end of this cable at the end with the male HDMI and male USB ending, putting it on the HDMI one.  Maybe it's possible to replace this whole cable with one that converts?  In other words, the replacement cable would have: 

A male HDMI end that plugs into the KVM switch.  
The other side has a male DisplayPort end and a male USB end.  Does such a thing exist?  

I'd bet there's someone here with more experience than I have who had a good idea what I should send off for.  Thank you in advance for any help offered.  

Tom_ZeCat

PS: In case you need to know, my two PCs are running Kubuntu 22.04 LTS.  The work PC is running Windows 11.

One more thing.  In case it's helpful, here's a picture of the KVM's cable: 
[IMG]https://i.postimg.cc/vTkt9dwS/KVM-cable-final.jpg[/IMG]

---

### Post by TheFu on 2023-05-24
"HDMI to DisplayPort"  - I have one of these cables.  It was $9 from Amazon.  My main monitor doesn't support HDMI, but it does have Displayport.  The KVM is HDMI only.

If you want to connect "Displayport to HDMI", that's what you should search for.

With my VGA-KVM, I had an HDMI (or was it DVI-i?) to VGA active adapter.  When all the GPUs stopped providing VGA out, I was forced to switch to a new KVM, retiring my 15+ yr old Belkin VGA KVM that had been working perfectly.

With the new KVM - HDMI and USB - I'm fairly unhappy. When switching between systems, it isn't instant like it was with PS2 keyboard/mice.  I have to wait for the USB devices to reattach to the next computer. This takes 5-10 seconds, not instantaneous like before.  Additionally, the keyboard KVM-switch scroll-lock pressed twice doesn't work anymore.  USB sucks.
The KVM I got is 4K @ 60Hz, uses USB for keyboard/mouse and supports both separate USB devices and audio.  The only thing that works well is the HDMI part.  On 1 of my systems, the USB keyboard/mouse never works.  This is odd since I have an identical system (same motherboard, CPU, GPU, RAM) connected, but 1 works and the other doesn't.  I tried to get support from Logitech.  They side-stepped the question ... until I forced a yes/no answer from one of the CSR people - he admitted they don't do any testing with KVM switches at all.  Yes, I've swapped the cables and swapped the KVM ports used.  the issue is tied to the computer ... but it works if I directly connect the keyboard and mouse to the computer.  USB sucks.  I'll probably never buy a USB keyboard or mouse again, definitely not from Logi due to their total lack of support for something I consider basic.  I had other issues with the keyboard too, so it isn't just this.  Of course, I never mentioned Linux - that is just asking for "we don't support that" answers immediately.

So ... anyway ... you probably have the wrong cable/adapter.

---

### Post by Tom_ZeCat on 2023-05-28
An update: I received my new adapter, and it works!  I needed on that converted the male end of an HDMI cable to a male DisplayPort one, and that plugged right into the work computer's female DisplayPort.  It totally worked, and the quality is good.  This problem is solved.  I appreciate the help very much.

---

