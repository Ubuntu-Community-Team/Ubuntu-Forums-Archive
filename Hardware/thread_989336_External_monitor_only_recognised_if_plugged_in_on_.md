---
title: "External monitor only recognised if plugged in on boot"
date: 2008-11-21
forum: Hardware
---

### Post by Juhla Mokka on 2008-11-21
Hi people. I hope there is an easy solution?

I often watch online TV or DVDs with an external monitor plugged in my laptop. The trouble is that Ubuntu does not recognise the monitor if I connect it to the laptop whilst Ubuntu is already running. Ubuntu only recognises the monitor if it is already connected when I boot the laptop.

This is annoying because I have to to re-boot the laptop if I want to use the monitor. Help?

Specs: Laptop Advent 9112. Monitor Hanns-G HW191D. Ubuntu 8.04.1 kernel 2.6.24-21-generic. 

Thank you :)

---

### Post by urgnom on 2008-11-21
Just a thought.... did you hit the CRT/LCD switch? I sometimes have to toggle this a couple of times before it works, but I use my Ubuntu laptop for presentations a lot, and this makes it work with projectors connected over a VGA cable.. Good luck!

---

### Post by Juhla Mokka on 2008-11-21
Thanks urgnom. That got me on the right tracks. My crt/lcd switch does not work, but I did a web search and...

I found a command that tells what's connected
```
xrandr -q

```

and couple of commands that switch between displays
```
xrandr --output VGA --auto

```
```
xrandr --output VGA --off

```

The link is here: [http://yyhh.org/node/12](http://yyhh.org/node/12)

I am inexperienced and nervous editing files I don't know about. Could somebody help me assigning the command on my crt/lcd switch? Also, how can I change the external monitor resolution? At the moment it is cloned.

Thanks :KS

---

### Post by goathunter on 2008-11-26
hello. I am having a similar problem. When I boot with the vga plugged in my laptop screen goes blank, but does not show up on the lcd tv. When i plug in the vga when the laptop is already on nothing happens. I am using an acer aspire 3000 with a dedicated ubuntu 8.04. Its an amd mobile sempron with a  VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter.
 I have tried these commands but nothing happens.
> marcus@marcus-laptop:~$ xrandr --output LVDS --auto --output VGA --auto
marcus@marcus-laptop:~$ xrandr --output LVDS --auto --output VGA --auto
marcus@marcus-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   1024x576       60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        60.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  
marcus@marcus-laptop:~$ xrandr --output VGA --auto


I'm a bit out of my depth here so any help would be appreciated.

---

### Post by goathunter on 2008-12-06
bump

---

### Post by Juhla Mokka on 2010-02-02
Hello helpful people. I am the original poster, I still cannot use my monitor...and it is more than a year ago I posted my question. Could any one give me some advice? Not being able to use my external monitor with my laptop on Ubuntu is the only reason why I still use Vista :-/ yghhh..

ps. I am on Hardy Heron now.

---

### Post by Juhla Mokka on 2010-02-15
Help, anyone? :redface:

---

### Post by pjdfred on 2010-03-16
> **Juhla Mokka said:**
> Thanks urgnom. That got me on the right tracks. My crt/lcd switch does not work, but I did a web search and...

I found a command that tells what's connected
```
xrandr -q

```and couple of commands that switch between displays
```
xrandr --output VGA --auto 
```

Since you're still evidently looking for a reply - I just solved this myself for Kiku, which is Ubuntu with XFCE instead of Gnome, but the fix should be the same. The solution is
[FONT=Courier New]
xrandr --output VGA --auto[/FONT]

- if it finds a VGA display it increases the desktop size if necessary and mirrors it on the output; if it doesn't find one, it turns off the VGA and resizes the desktop for your LCD. 

If you go under Settings->Keyboard shortcuts, you should find that the 'XF86Display' key (usually Fn-F5) is set to some sort of xrandr command. Edit it to the command above, and you should be OK. Note that the result won't be quite the same as the Windows functionality - Fn-F5 will be a "make it work" key.

---

