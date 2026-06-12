---
title: "Insane Battery Monitor"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by Max Luebbe on 2006-06-30
I use a Sony VGN-FS760.
99% of the time this laptop is awesome for linux compatibility, everything works out of the box and I got XGL/Compiz working a long time ago without any trouble.

One of maybe three things that isn't perfect is the battery monitoring.
I get nonsensical messages that say things like 95% charge remaining, you have 14 minutes left, and before i changed the power options, it would procede to shut down the machine.

Is there anyway to enable the power settings to take action based off of percentage remaining, so that they become usable, or somehow train the laptop to come up with better time estimates?

---

### Post by mpvano on 2006-06-30
You're not alone!

I did a clean install of Dapper on my old Sony VAIO pcgf-540 and have kept up all the upgrades.

It generally works well, but I am experiencing the same thing when operating on battery. Every few minutes, the battery level monitor jumps all over the place in erratic fashion. It's never actually shut the machine down prematurely, but it keeps warning that the battery is low as much an hour before the battery runs out. A few seconds after the warning, it often goes back to indicating the correct state of the battery.

It almost looks like the mysteriously undocumented Gnome battery applications don't properly read values that are changing during the read operation.

It also usually reports that there was a suspend failure, upon the subsequent resume - even though the suspend operation appears to have worked fine.

Another acpi related bug is that on resume, the password dialog sometimes times out very quickly (less than two seconds) the first time it appears. It's not till the second time you invoke it that you can log back in.

I'm guessing these problem only happens with the the sonypi acpi driver. Since my two IBM notebooks don't exhibit them. (Although they DO seem to have a few OTHER scary acpi interface error messages).

I'd report all three things as bugs, but even though I supposedly have a valid password that is accepted by the Malone bugtracker login dialog I never actually get logged on so that I can report bugs! (And so far can't seem to find a way to report this bug or get help on it without logging into the malone bug system!)

In the meantime, I too would like to see more configuration control so that this and other annoying forced behaviours in the new dapper gnome applet versions could optionally be disabled.

Mario

---

### Post by coffeecat on 2006-06-30
I use a Vaio VGN-FS215B, and I've seen similar odd behaviour with the battery monitor in SuSE 10.0. Shortly after booting into Gnome it would come up with something like, "Warning, only 99% charged. You have only one minute left." :? I've now set this machine up as a quad boot with Ubuntu Dapper, Fedora 5, SuSE 10.1 and Windows. I've never seen the problem in Fedora or SuSE 10.1, and only a couple of times in Ubuntu - **which I use most of the time** :) in case anyone was wondering. :wink:

As it happened in SuSE 10.0, I wonder if it's a Gnome bug. I never did cure it so, sorry, no answer here.

[quote=Max Luebbe]I use a Sony VGN-FS760.
99% of the time this laptop is awesome for linux compatibility[/quote] 
Do your Fn + function keys work? (brightness, volume, etc). They don't on mine. I found a howto for Breezy, but when I tried to compile one of the scripts it threw all sorts of errors. If you know how to get them working please do share with the rest of us otherwise happy Vaio users. Thanks.

---

### Post by mpvano on 2006-06-30
The function keys on the pcgf-540 work fine out of the box with Dapper, although they're mapped a little different than sony intended. I haven't tried using the 3 special buttons that are user programmable under Windows for applications, etc., but I suspect they're available with keycodes for mapping via Xmodmap.

I agree that the bug looks like a bad interaction between gnome and the sony ACPI. I think it's aggravated by the fact that my Sony (All sony's?) seem to provide a raw reading of the projected standby time where some programs expect to see the remaining battery time?

Mario

---

### Post by Max Luebbe on 2006-06-30
On my VGN-FS760 none of my Fn keys work and to the best of my knowledge, neither do my programmable (s1 or s2) to the best of my knowledge.

I've seen some posts on the Gentoo forums regarding patching the sonypi module.
Has anyone had any success with this?

I know there is a solution, I ran into someone in a coffee house in Tucson several months back with the exact same laptop who was running a beta of dapper with working xgl and fn keys.
As I was working on 5.10 then, seeing his setup is what encouraged me to go ahead and try the beta back in March.

Its possible, but how?

---

### Post by coffeecat on 2006-06-30
[quote=Max Luebbe]Its possible, but how?[/quote] 
[Here is]("https://www.granny.homelinux.org/%7Elinho/files/delta.ubuntu") the howto I was following. It's for Breezy and I hoped it would work in Dapper, but it was when I got to compiling the sonyfn.c file that I got the errors.

I've found similar howtos in [this]("http://www.linux-laptop.net/hosted/ubuntu_sonyvaiovgnfs315b.html"), and also in [this]("http://users.skynet.be/thomasvst/linux-on-laptop/"). The Fn key howto is well down on the page on both.

Also while googling I found a reference about the Sony Fn keys* being incorporated into the Ubuntu kernel. Perhaps the next kernel update..... Here's hoping.

I'll try again with those howtos again sometime. Perhaps the links for the downloads for the second two may be different. Well - possibly.

* **Edit:**I'm a muppet. Not the Fn keys - the Fn keys **driver**. :roll: :wink:

---

### Post by Max Luebbe on 2006-06-30
What errors are you getting?
I'm going to attempt to solve this problem one way or another, and I can use all the information I can get.

I'll try and follow this guide and see if I can get it to work on my machine.

---

### Post by coffeecat on 2006-07-01
The errors seem to suggest that there's bad code in the script - which is odd. But I'm not a programmer so I could be very wrong. I'm not using my laptop at the moment, and I have quite a few other things to do first, but later today (I'm in the UK) if I get time I'll try re-compiling the script and post the errors.

---

### Post by coffeecat on 2006-07-01
OK. I've had a chance to look at the howto again. This is the howto in the first link I've given. I've not looked at the others closely yet.

The sony_acpi.c file compiled OK when I did it a couple of weeks ago, but when I try to compile the sonyfn.c file, I get the following errors:

```
coffeecat@ubuntu-sony:~$ gcc sonyfn.c -o sonyfn
sonyfn.c:1:19: error: stdio.h: No such file or directory
sonyfn.c:2:20: error: stdlib.h: No such file or directory
sonyfn.c:3:19: error: errno.h: No such file or directory
sonyfn.c:4:20: error: unistd.h: No such file or directory
sonyfn.c:5:19: error: fcntl.h: No such file or directory
sonyfn.c:6:23: error: sys/ioctl.h: No such file or directory
sonyfn.c: In function ‘get_volume’:
sonyfn.c:29: error: ‘O_RDONLY’ undeclared (first use in this function)
sonyfn.c:29: error: (Each undeclared identifier is reported only once
sonyfn.c:29: error: for each function it appears in.)
sonyfn.c: In function ‘set_volume’:
sonyfn.c:42: error: ‘O_RDWR’ undeclared (first use in this function)
sonyfn.c: In function ‘getBrightness’:
sonyfn.c:112: error: ‘FILE’ undeclared (first use in this function)
sonyfn.c:112: error: ‘handle’ undeclared (first use in this function)
sonyfn.c:116: error: ‘NULL’ undeclared (first use in this function)
sonyfn.c:118: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c:120: warning: incompatible implicit declaration of built-in function ‘fscanf’
sonyfn.c:122: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c: In function ‘setBrightness’:
sonyfn.c:131: error: ‘FILE’ undeclared (first use in this function)
sonyfn.c:131: error: ‘handle’ undeclared (first use in this function)
sonyfn.c:142: error: ‘NULL’ undeclared (first use in this function)
sonyfn.c:144: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c:146: warning: incompatible implicit declaration of built-in function ‘fprintf’
sonyfn.c:148: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c: In function ‘getCodes’:
sonyfn.c:155: error: ‘FILE’ undeclared (first use in this function)
sonyfn.c:155: error: ‘handle’ undeclared (first use in this function)
sonyfn.c:159: error: ‘NULL’ undeclared (first use in this function)
sonyfn.c:161: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c:163: warning: incompatible implicit declaration of built-in function ‘fscanf’
sonyfn.c:165: warning: incompatible implicit declaration of built-in function ‘exit’
sonyfn.c: In function ‘main’:
sonyfn.c:177: warning: incompatible implicit declaration of built-in function ‘printf’
coffeecat@ubuntu-sony:~$
```

Doing it as sudo makes no difference. As you can see I'm doing the compile in my home directory (name edited - I **don't** call myself coffeecat in everyday life :wink: ), but I'm sure that's right. The instructions are explicit. Compile, then move output to /usr/sbin.

The error messages are beyond me. Any thoughts?

---

### Post by Max Luebbe on 2006-07-01
I am a programmer and this does make sense to me!
Whats going on is that additional files called header files (.h) that are used in the C programming language to specify the interface for how certain functions are used, and to define them to be used cannot be found by the compiler.

The ones missing are all low-level and very standard so installing the ubuntu build-essential package should take care of it, and get all the basic stuff you would need to compile things in the future.

sudo apt-get install build-essential

After you get that, your compile will work no problem.
(It compiled for me anyway! Still have to test it)

Let me know if it works, and if you have any more problems.
(Also hope you're getting a chance to watch the Quarterfinals right now!)

---

### Post by coffeecat on 2006-07-01
[quote=Max Luebbe]I am a programmer and this does make sense to me![/quote] 
That's the best news I've heard today. :D Thanks. I'll try it.

---

