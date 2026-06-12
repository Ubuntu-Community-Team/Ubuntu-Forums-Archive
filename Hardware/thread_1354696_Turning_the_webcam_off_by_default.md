---
title: "Turning the webcam off by default"
date: 2009-12-14
forum: Hardware
---

### Post by siddartha on 2009-12-14
On an eee pc 1005 ha there is a webcam that can be turned off with an echo 0 to a file. Now, the camera is disabled by the bios, yet that is not a good enough reason for the Linux kernel. As the CPU and battery spend the extra time to support the graphical interface is there a way to avoid the terminal and do that in a graphical way?

---

### Post by IcarusR on 2009-12-14
I do not know of any gui way of doing this but is simple to do by adding the relevant module to /etc/modprobe.d/blacklist which will stop it loading at boot so the hardware will not work.

You can stop services from running with 'sysv-rc-conf' which you run from a terminal & gives you a very basic gui.

---

### Post by siddartha on 2009-12-14
> **IcarusR said:**
> I do not know of any gui way of doing this but is simple to do by adding the relevant module to /etc/modprobe.d/blacklist which will stop it loading at boot so the hardware will not work.

You can stop services from running with 'sysv-rc-conf' which you run from a terminal & gives you a very basic gui.
Hahahahahaha
Starting a terminal, to do a sudo, to start an app that would use the whole screen and not just the bottom line ;-) Sometimes I wonder why do we bother loading X and all those badly written apps. I remember when powertop was created the gnome-power-manager was the worst offender to wake up the computer... it should say a lot about the team behind gnome and the level at which things evolve. But I know that we start the GUI because it is nicer and because we want to say we do have our own free Windows. Weak. I moved to Linux only about 12 years ago, yet this laptop came with XP preinstalled and I have kept the first partition for XP. Over there you have a small tray icon to change the resolution of the screen and enable/disable the cam and wireless. Also Windows does honor the Bios options so disabiling the cam there means no cam in the system. And the barbaric way you proposed is replaced by a clean Device manager where you can enable and diable devices without connection with the sysv rc (that does not do it for kernel modules by the way).

---

### Post by IcarusR on 2009-12-15
I was only trying to help & made the suggestion in the absence of a gui. I shall stop waisting my time answering peoples post now.

If you don't like Free Linux by all means go back to Expensive Microsoft.

You have to remember that most of Linux (apps & base system) is written & maintained by people free of charge to you !! 
Microsoft charge you & thousands of people for a license & therefore can afford to pay developers to write & maintain the OS. 

Both of my suggestions are a one off terminal method, do it & forget about it. So should not be much of a hardship if it achieves the desired result.

Of course you could always write your own gui.

---

### Post by siddartha on 2009-12-15
> **IcarusR said:**
> If you don't like Free Linux by all means go back to Expensive Microsoft.

You have to remember that most of Linux (apps & base system) is written & maintained by people free of charge to you !! 
Microsoft charge you & thousands of people for a license & therefore can afford to pay developers to write & maintain the OS. 

Both of my suggestions are a one off terminal method, do it & forget about it. So should not be much of a hardship if it achieves the desired result.

Of course you could always write your own gui.

Sorry. It wasn't an attack against you. It was so darn funny to read that Linux is so advanced (single boot at home for 12 years or so) yet, it's abilities are about the same with Win 3.1 which it emulates rather well with Wine.

On the other hand, this message is sad, very sad. Just throwing clichees which I assume you actually believe. Let me explain you and the others who live in LaLaLand.

1. Free Linux vs Expensive Microsoft.
1.a Free Linux is a concept vehiculated because people NEVER read licences. GPL supports the idea that you can be charged any sum as long as you have access to the source. Just because you can "pirate" it the same as Windows does not mean it is free. Just that you can't face serious charges if you have download it from some site.
1.b Expensive Microsoft is another mith perpetuated from back when windows 98 came out more expensive than windows 95. There are quite a few licences available. And most people I know do not need anything than the Home (Basic) Edition. Every kid feels the need of "power" for 10 minutes every day. Otherwise there's no need for the more advanced licences.

2. Most apps are done by people free of charge. Bull-****! 
2.a It's done by companies free of charge for me. Novell pushes Evolution. It's big, it's slow, and it's a corporate war against Microsoft Outlook. It's about the vendetta between two old "friends". Novell was twice almost killed by Microsoft. Now, they are using the licence of .net and other technologies in a try to pay Microsoft back. Back in the days of Star Office, nobody gave a f***. Than Sun discovered it as a cheap way for them to push Java even further (to rival with Visual technologies) and pay Microsoft back for some offences (Visual J++ anyone?). And so on.
2.b It's done by people who hope to wake up next morning with an invitation from Google or any other company with a big budget PR department. They are doing the work in hope to be "seen" by somebody, anybody. Gaim went so far as to break the work of other people just to get a job from Google. MySQL is owned by Sun and maybe later by Oracle.
2.c And the final category the people so naive to buy into this propaganda you spread and who work for themselves. They have a system, they need it working and the fix can be done fast enough to avoid changing software.

3. Microsoft charges... in my case it came preinstalled. It was paid, of course. But the Linux system is either unavailable or at the same price. Don't read the international press report and sit on your ***/couch and think how you know the s*it. In real life the dealers do not let the real alternative. The Linux systems are either cheapest usable crap (Wallmart) or just used for marketing (Dell) in order to push Microsoft's hand into a cheaper OEM licensing. And I can't get my money back, no dealer would do it. They are going to tell you that this is how the system came and you either buy it or not. So your holy Linux is actually having to pay extra in qualified hand to install it and tune it. And boy, you have a lot of fixing to do! My netbook implied installing by hand the ethernet and wifi drivers for the former Ubuntu version. It's a **netbook** dude! A networkless netbook??? And the list is looong. Linux does make certain hardware unusable. Is it better than the crashing system that plagued old Windows versions?

4. I do know that comand line stuff. I just won't do it. It's a matter of personal taste. I spend the CPU cycles, the battery life and a few seconds of my life for loading a GUI that has no real value besides eye candy. That is bad. Sure I can start the terminal, but why should I start it? If I needed the terminal I won't go booting the GUI. If I booted the GUI I want the functionality you have since Win'95 - System/Device Manager and disable a certain hardware device. A decade and a half later Linux can't do that! And everything on top of the excellent technology of the '60s. See the debate Linux vs Minix.

5. It is not do it and forget about it. That's a fairy tale. It's Linux! Linux changes every two months. Each time you have a security patch something changes. Each time you have a new version things are moved around. And in time, your "write and forget" options won't do a s*it because that particular command is deprecated! The parsing inteligence of a Linux app is at best at the level of its author. Which has no idea what your write and forget was. If you would run a few servers in the background (the only ones kind enough to notify you of changes in config files) you would notice quite a few times in a year that you are asked by apt what to do with the old config. Desktop apps just crap in your config or create a ~/.myapp-xx and this way your "by hand" means finding out which one is which. I know a couple of apps which went from ~/.myapp to ~/.myapp-xx and back to ~/.myapp at the third version because the idiot geeks assumed that everybody moves along their system of choice.

6. That is the most idiotic remark I keep reading in the last 15 years. You can write your own app, GUI, whatever. When it comes to political choices 6 year old minds in mature bodies like yourself would start their own parliaments, armies... just like in Warcraft. Right?

---

### Post by IcarusR on 2009-12-15
Sorry I spoke !!

I'm going to shut up now.

---

