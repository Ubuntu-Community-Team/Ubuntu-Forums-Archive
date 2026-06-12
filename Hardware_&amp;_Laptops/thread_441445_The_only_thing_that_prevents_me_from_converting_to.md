---
title: "The only thing that prevents me from converting to Ubuntu .. (SONY VAIO)"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by loathsome on 2007-05-12
Hi there,

I own a Sony Vaio N-series laptop (N19VP to be more specific)

Ubuntu runs GREAT, except a very, very important thing; The brightness control wont work. (FN + F5/F6). What's weird, is that FN + f3/f4 works flawelessy out of the box (sound control).

I've tried the HOWTO-guide on this forum, but that's only for the FN-series (or something; It didn't work).

Please tell me there's any way I can get the brightness control to work. I mean, no way I'm dualbooting back to Vista just to change the brightness.

Thanks in advance, and have a kickass weekend!:KS

---

### Post by PerlMountain on 2007-05-12
[size=1][edit] Does this help? I hope. [http://www.google.com/search?num=100&hl=en&newwindow=1&safe=off&q=Sony+linux+video+drivers&btnG=Search](http://www.google.com/search?num=100&hl=en&newwindow=1&safe=off&q=Sony+linux+video+drivers&btnG=Search) [/edit][/size]


Well, can you check for video drivers? I'm not even sure this is the right answer, but I just re-installed Xp x64 onto my desktop last night for the first time and my monitor was *usable* but it wasn't correct.

My card vendor had no solution for me and no long range plans to develop one.
I'll **never buy another MSI product**, just because of that and that they make it impossible to put in a support ticket (really, it's impossible, for me anyhow).

It was REALLY hard to find the x64 drivers, but when I did then I could adjust everything fine.

Maybe there are some controls you can use to manage your monitor settings? I'm getting ready to dually this PC today, but first I'm going to dually my Compaq laptop 
1) to get some experience doing it and 
2) so I can support myself if I crash out the desktop.

So, I'll be going through kind of the same things because my monitor settings are kind of bad with the card installed AND no drivers. Since I don't want to remove the card, obviously, I'll need to find a solution also.

Maybe this gives you some other ideas to mess with, I'm going to be on the hunt for a solution in a few minutes too. 

Anyhow, I'm sure this was no help, but I'm thinking of you. 

Good luck,

PME

---

### Post by strabes on 2007-05-12
This is a shot in the dark but you could investigate using xbindkeys to bind the brightness command to the specific fn keys you want.

---

### Post by telosian on 2007-05-12
Howdy.  I had this exact same problem on my Thinkpad using Dapper and kernel 2.6.17.  After googling the issue and reading some forums and thinkwiki, it turns out that there was a known conflict with kernel 2.6.17 between the ibm_acpi kernel module and the video acpi kernel module.  When I disabled the video acpi module, I could adjust the screen brightness.  This has since been fixed in the 2.6.20 kernel and Feisty works like a charm.  I have seen a sony_acpi kernel module, but don't know if this is your problem, as I don't own a Sony.  Hope this helps. Good luck!

---

