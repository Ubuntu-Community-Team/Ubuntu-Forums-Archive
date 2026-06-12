---
title: "Gateway M275 Will not completely shut down"
date: 2008-08-07
forum: Hardware
---

### Post by backstept on 2008-08-07
hi folks

I have a Gateway M275 convertible tablet laptop and I'm dual booting XP tablet edition and Ubuntu 8.04 (by way of wubi, love it!) and whenever I shut down from ubuntu it ends up on a black screen with the hdd indicator lit up. I have to manually hold the power switch for 5 seconds to completely power down . . .

any idea why this happens?

I haven't noticed any problems as a result of turning it off manually, but I would rather have the laptop turn itself off automatically

many thanks :D

---

### Post by ichthus on 2008-08-15
I actually have a similar problem: my gateway m275 tablet runs kubuntu 8.04.  It seemed to run normally at first, but since I used baghira for a day, it randomly is unable to shutdown, reboot, restart X, or log out from my KDE session frequently.  I am occasionally able to, but more often unable.  I end up with a frozen computer, blank screen, and must shut down manually by means of the power button.  I have tried to reinstall kwin, kde, kdm, and purged baghira; and have, with some research, I believe, determined that the video card/driver is likely to blame.  
I am trying to determine if uninstalling xserver-xorg-drivers-nv or installing either envy or nvidia-legacy-? would work to solve the issue.

---

### Post by PBrn46 on 2008-10-11
I would also like to say that I have the same problem, with my Gateway M275. It seems that for every build of Ubuntu, I have a different problem that's keeping me from using this lovely operating system on my laptop. My only successful install I believe was 7.10. Just a 3 more weeks until the release of 8.10, I couldn't wait. Hopefully things will be solved by then, as I have no money to buy computers. =(

---

### Post by ichthus on 2008-10-23
After some more research, I've determined that the video card isn't to blame:oops:: the gateway m275 uses an intel itegrated video card, and I've found the issue attached to a problem with a random keyboard/pointing device freeze ([http://www.technologyquestions.com/technology/tablet-pc-gateway/4813-gateway-m275-keyboard-locks-up-verizon-5220-aircard.html](http://www.technologyquestions.com/technology/tablet-pc-gateway/4813-gateway-m275-keyboard-locks-up-verizon-5220-aircard.html)) that basically requires upgrading the bios.  Is(are) your bios[es] current?  If not, you might try to upgrade them.
(I know - it looks irrelevant; I just can't find the ubuntuforums post on that right now.):confused:

If you can't upgrade the bios, you can always use the alt+sysrq hotkeys to shutdown.  This is a very extreme way of shutting a linux computer down, and shouldn't really be used unless in an extreme situation, but upto the point and after I had to replace my hard drive, I basically noticed that I have to reboot twice normally for the computer to be able to not hang up, which is probably why I crashed my hard drive.  If I don't have 2 normal reboots, then, the keyboard/mouse freeze (I've determined that by trying the alt+sysrq hotkeys after the freeze, with no effect:(.  But, in order for the hotkeys to work, you're either going to have to do it before logging out of your session (It appears that once the computer has started to freeze up,it might actually freeze up EVERY time you shutdown, log out,  or change to a different virtual console), or install some service to send them across your network (such a service exists to send the hotkeys as ICMP requests (I think - haven't actually used it).  This is VERY INSECURE but is the only way to shut the computer down without the power down button + head crash. 

As long as you have the original Gateway-installed windows XP tablet edition, or access to a restore CD set, It is best to use the winphlash utility included to flash your bios.  If you don't have the original, call tech support and get them if you can.  They cost ~$10 for an OS restore CD set.  Unfortunately, my set came with a corrupt \windows\system32\config\system:mad:, which stores a part of the registry that tells the machine how to start and whom to log on, so I'm pretty much stuck with a kubuntu gutsy (or ubuntu hardy) live boot CD and kinda using the alt+sysrq hotkeys to shutdown so I don't have to buy another hard drive.  Maybe I'll just take it out until I can figure out how to flash my BIOS safely or get some working CD's from gateway.  There is a way to do this without using winphlash in XP ([http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)), but I don't want to try it, because if doesn't work, I'll end up with a $1K+ coaster#-o.  So, in *this* case,:eek: I actually would have to say, do it in Windows or don't do it at all! (unless you're really, really, really good at techie stuff).

---

### Post by MGaddict2000 on 2008-12-08
Well, no offense, this isn't all that helpful. I have the latest BIOS on my M275 laptop and I still am having the problem with 8.04. I can't get 8.10 to install at all for some reason and I find other people with this laptop had the same problem. We'll wait and see what happens, sounds like 9.04 is in the making, keep your fingers crossed.

---

### Post by xSkApOnEx on 2008-12-29
I'm also very sad :( to see that it hasn't been fixed yet. I really love Ubuntu, but don't wanna fry my hard drive every few months. Anybody have anymore luck yet?

---

