---
title: "After installing updates for 11.10, startup hangs at &quot;Checking battery status&quot;"
date: 2012-01-03
forum: Hardware
---

### Post by djehuti on 2012-01-03
Hi everyone, new problem that just started last night. I've been using oneiric ocelot on a Dell Inspiron 1525 laptop for about a week. Everything's been perfect until last night, when I called "apt-get updates" for the first time and then reset the computer when they were done. Login goes like normal until it gives the message "Checking battery status..." and then it simply hangs. Control-C does nothing, and the only way I found to get out was to hit the Sleep button on my laptop to abort the entire process. First it checks VMWare, then the LAMP apache server, and then battery status, which is where it hangs. I left it on for 8 hours while I slept, so I know it's not an issue of patience.

There wasn't any problem before installing updates, and if I boot in Recovery mode, I can get to Terminal just fine and log into my profile at the Terminal prompt, though I don't know how/if I can enter the Ubuntu shell from there. I haven't brought a copy of my startup text since it doesn't have any error messages and I can't transfer it electronically, but if it's necessary, I'll write it down and show it here.

I do know this laptop has battery problems, because I let it run down once in 2010 and now it refuses to charge to more than 22% capacity. So Ubuntu might be trying to solve a legitimate problem, but as far as I'm concerned the battery's unfixable (not that I've tried it, but anyway).

So I can see at least two routes to solving this:

1. Find a way to bypass/prevent the battery status check from happening at startup;
2. Find a way to enter the Ubuntu shell after logging in via recovery mode;

And if there're others, even better. Also, if anyone suggests removing the battery, I've never done it before on this computer and I'm both short on know-how and afraid of repercussions. So I don't know if I'm ready for that yet, unless someone has a really good guide on it. Thanks.

---

### Post by yugnip on 2012-01-03
I may be incorrect, but I always assumed the 'battery check' was for the computer's internal battery (the one that runs the computers clock). Laptop (external) battery life itself shouldn't be an issue, as you can always run the laptop plugged-in to power.

Sorry, I know this doesn't help much.

---

### Post by djehuti on 2012-01-03
That may also be worth seeing, because a few times in the last month, I've had my Windows clock switching to GMT, and then a few days later, it'll change back to US Central time without my doing anything. So that, too, may be a clue as to the problem.

EDIT: After looking more around the forums, this problem has sometimes been related to Nvidia graphics cards, which I admittedly don't have. lspci returned this for my display drivers:

*Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller*

Some say it takes re-installing the graphics drivers, but how to do that from a command prompt has me lost -- unless there's some way to boot into the desktop from recovery mode.

EDIT 2: Canned and re-installing. This is a bug that's been around since 10.04, and since it doesn't look like there's any clear way to solve it or known solution, I just decided to wipe Ubuntu and start over. Thankfully I won't lose much, but now I just need to never update my packages.

---

