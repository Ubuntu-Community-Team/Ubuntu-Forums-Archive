---
title: "Acer TravelMate P614 Touchscreen Issues"
date: 2022-03-23
forum: Hardware
---

### Post by tomes2001 on 2022-03-23
[COLOR=#000000][INDENT]Hello! I'm new to the community here, so forgive me if I miss any key details/mess up on formatting. I'm also still fairly new to the command line as well, so the output sometimes confuses me.

When I first got my laptop a few years ago, my friend (who knew more about computers than I did at the time) helped me set up a partition so I could run either windows or Ubuntu, because he was trying to convince me to quit using windows. When windows updated at some point, the boot order got messed up, so it stopped letting me boot into Ubuntu, and I forgot about it. Recently, I helped a different friend do an install of Ubuntu, and remembered my partition. I got it set up again, and remembered how much I liked Ubuntu in comparison to windows, and decided to try to transition completely to using Ubuntu. I had an old version though, 18.04 LTS. After a lot of updating software, I finally got 20.04 LTS onto my machine. However, now the touchscreen doesn't work. Because I forgot about the Ubuntu side for a long time, I don't recall if the touchscreen ever worked on 18.04 LTS, but I know it worked on the Windows side. I did some poking around on the internet, and I found a few solutions:

1) check if the touchscreen is under lsusb, and try "[COLOR=#333333]sudo modprobe -r usbtouchscreen"[/COLOR] (from [here]("https://wiki.ubuntu.com/Touchscreen"))
It is under lsusb! It is listed as "Raydium Corporation Raydium Touch System". I tried the command, it ran okay, but my touchscreen still did not work. The rest of the page assumes the command worked, and it didn't, so that is a dead end.

2) uninstall and reinstall snap store (from [here]("https://ubuntuforums.org/showthread.php?t=2445152"))
The commands ran okay. Did not fix the problem, even after a reboot it's still not fixed.

3) try uninstalling and reinstalling hid_multitouch (from [here]("https://askubuntu.com/questions/1141137/elo-touch-usb-touchscreen-not-working-on-ubuntu-18-04"))
The command did not run, with the following message: "ERROR: ../libkmod/libkmod-module.c:799 kmod_module_remove_module() could not remove 'hid_multitouch': Operation not permitted"
I have no idea what this means, and I don't want to break things, so I'm not trying that again.

4) try looking for a driver online (from [here]("https://ubuntuforums.org/showthread.php?t=2463719&highlight=touchscreen"))
Because the laptop I have is a weird one, I can't find a driver. I might not be looking in the right places though.

5) add a parameter to the kernel (from [here]("https://bbs.archlinux.org/viewtopic.php?id=256678"))
While this thread seems to describe the problem I have exactly, I don't understand enough about the kernel, or the command suggested here. It is also from a forum on ArchLinux, and not Ubuntu, so I don't know if they are still closely enough related to have this fix my issue, so I'm
hesitant to even make a temporary change as this [page]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") suggests.

If anyone could even point me at some resources, I'm happy to read on my own. I'm pretty lost on what to do here. While it's not critical that my touchscreen works, I got pretty used to it on windows, and I'd really like it to work on ubuntu as well.[/INDENT][/COLOR]
[COLOR=#000000][/COLOR]

---

