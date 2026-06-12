---
title: "Jaunty won't accept keyboard/mouse input"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Kakteed on 2009-04-25
Okay, so, I decided to upgrade yesterday (the 24th), when I saw that Jaunty had been released. I thought that since it was a release candidate, it would be pretty stable, an d wouldn't mess anything up too badly.

After upgrading (I upgraded from Intrepid), I restarted the computer when prompted. When I booted into Ubuntu, I saw the old progress bar for boot (from the screenshots I've seen of Jaunty, it was supposed to change?). It was very quick, and I was soon at the login page. I found, however, that it would accept neither mouse nor keyboard input. I looked around online for some instructions, and ended up trying a few things. I tried pressing ctrl+alt+F1, then alt+sysrq+h. Nothing worked. I tried unplugging the keyboard/mouse, and plugging them back in again. I didn't try switching keyboards/mice, because I don't have any spares on hand, but I can do so if that would help.

Through reading, I found something that indicated that the problem might be with 'hal', so I decided to re-install it. I started Ubuntu in recovery mode, and dropped into the root shell. The keyboard was completely responsive there, and so I did 'apt-get --reinstall install hal-info'. I let it finish, and then opted to resume normal boot. I encountered the same problem as previously, with no change.

I then decided to see if the keyboard/mouse would work if I bypassed the login screen. I have some custom log-in screens, so I wondered if maybe they were just somehow screwing up the log-in process. Maybe a stupid idea, but it was simple enough to test. I went back into recovery mode, dropped back into the root shell, logged in, and then started x. As soon as I started x, the keyboard/mouse stopped functioning. My desktop looked horrible; my background was gone -- it was completely black -- and a really blocky theme had been substituted for my theme. The files that had been on my desktop were gone. Several errors popped up (I couldn't write them down, since they were layered on each other and I couldn't move them about. The top one said that the 'switcher' had crashed). I tried almost every key combination, in hopes of provoking some response, but nothing happened. I also tried using my wacom tablet, because I'd heard that Jaunty supported them very well - nothing.

I know that I'm supposed to file a bug report, but how do I file a bug report if I can't use the keyboard/mouse? And what do I file it on? It looks to me like the keyboard/mouse thing is a problem with x, but it also looks like I have a lot more problems than "just" (it feels weird to say that, haha) not being able to use the keyboard/mouse.

[-- The next part may be stupid, since it's just me speculating --]

I feel like maybe the install somehow wasn't complete; the start-up progress bar still looks like intrepid, but the shut-down bar looks like jaunty. And that might explain why everything is really screwed up when logged in - it looks kind-of like it looked when I installed windows (in order to dual boot), the install screwed up somewhere along the way, and I had all these random problems. In that case I had to fix it by re-installing the OS, but I don't want to necessarily do that here - I have a lot of data that I want to keep, and would like to (if possible) somehow repair it? If a re-install is totally necessary, I can retrieve my data and re-install, but I hope that there's another way to fix this.

Any help that you can give me is welcome; I've about reached the end of what I'm capable of doing on my own.

EDIT: Oh -- another thing I just thought of. Does it matter that my graphics card is an ATI Radeon X1650? It did say that it didn't have the fglrx driver, but I thought it would work fine with just the motherboard video. Intrepid never really worked well with my card, and so I could never use any of the effects, so it didn't seem like it would be much of a change. Could that be part of my problem, though? I don't get the blank screen at start-up like other people are reporting, and Ubuntu *never* really recognized my video card, so I'm not sure if it's really my problem...

---

