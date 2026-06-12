---
title: "Velocity Micro Notemagix L80 Ultra - number of issues"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by mrpeenut24 on 2007-02-02
[SIZE="2"]Hey, I'm fairly new to Ubuntu and have found a number of issues with my computer, a Velocity Micro Notemagix L80 Ultra based on the Compal HEL80.  I'm using Edgy with kernel 2.6.17.

(to make this easier to read, I'll separate them into numbers)
1)  Intel PRO/Wireless 3945ABG (ipw3945)
First and probably most importantly, my wireless doesn't work.  In my device manager, it shows an entry for my wireless card in PCI Express Port 1: PRO/Wireless 3945ABG Network Connection, however, there seems to be no interface for it.  iwconfig doesn't show it.  It seems (according to other posts) that I need to load the module into the kernel, however, I'd rather leave that as a last resort unless I've got a complete step-by-step walk-thru (which would be greatly appreciated).

2)  Elantech TouchPad
I'd really like to disable tap-to-click on my Elantech touchpad.  I've added the lines xorg.conf for the Synaptics touchpad, but it doesn't help.  In device manager it's shown as an ImPS/2 Logitech Wheel Mouse, which doesn't make sense, but I've seen others having this problem.  I've read that someone was working on an Elantech config utility like the one for Synaptics.  Does anyone know anything about this?

3) Keyboard volume buttons
Like many keyboards now, mine has the blue Fn (function) key.  When holding this and pressing  F6 thru F8 I can turn my volume up, down, and off.  However, the only volume it changes is the headphone (PCM2) volume, and I'd really like to set it to affect the master (PCM) volume.  I tried using the xbindkeys and  got the command to change the volume, however, when I tried to get the input key, it doesn't register the Fn key (it looks like the values in Keyboard Shortcuts are like 0xb0 or "XF86AudioRaiseVolume") .  As I understand it, xbindkeys has to run everytime at startup too right?  If possible I'd just rather change they keybinding directly.

A small inconvenience:
When I click on Applications menu (or any of the menus) often it will be minimized with arrows to scroll up in the menu.  This is slightly annoying and I would rather have the entire menu shown everytime.  Anyone know how to fix this??

Any help would be GREATLY appreciated![/SIZE]

---

### Post by mrpeenut24 on 2007-02-03
Any ideas from anyone on any of them?

---

### Post by mrpeenut24 on 2007-02-06
Like a few others I'm unable to hibernate.  When I try, it starts to, then shows some message about unable to use the swap disk.  However, I don't *have* a swap disk.  I've got 2GB of RAM so I didn't think I needed it.  Do I need the swap disk in order to hibernate?

Also, does anyone have any ideas on any of the above???  Someone told me today that the wireless driver might still need to be installed, since there is no interface available.  Does this sound right?  Does anyone think ndis-wrapping would help?

---

### Post by mrpeenut24 on 2007-02-08
Also, when I put my computer to sleep, when I try to bring it out, the screen stays black.

---

### Post by mrpeenut24 on 2007-02-08
I installed beryl and kde, and when I went to run emacs, the font seemed to be missing, and all I saw were the '[]' looking characters.  i changed it to the courier font, and it seemed to be ok, but with the default font, it wasn't.  So I uninstalled nvidia, and the xorg.conf messed up (expected).  I uninstalled kde and beryl, and reinstallled nvidia, but the font is still messed up.  However, the wireless seems to be working now?!?  Any ideas on how to reinstall the fonts?  Also, when I boot up my laptop, it still shows the kubuntu load screen.  Can I change this back to the original Ubuntu one?

---

### Post by mrpeenut24 on 2007-02-08
Ok I've reinstalled beryl and it chops off the top and bottom of ALL the windows.  I can't X out, or minimize without using the Alt-F4, etc buttons.  Also, when I open the terminal, it's completely white, and I can't see anything, but I'm able to type and have it take commands.  I've tried changing the background colors and still nothing.  Anyone able to help me with any of this???

---

### Post by kwilliam on 2007-03-07
Wow... I'm shocked that nobody has replied to you yet.  Usually these forums are pretty helpful.  :-/

I am/was considering buying a laptop based on the Compal HEL80 from powernotebooks.com, but now I'm not so sure I want to.  It doesn't sound like Ubuntu works very well on it from your description.

Wish I could help, but I don't have a laptop and have absolutely no experience with wireless cards, touchpads, and so on.  Best of luck.

---

### Post by mrpeenut24 on 2007-03-07
Hey kwilliam, I've managed to get most of the main problems fixed.  After installing the extra repositories, I got my wireless to work, and after changing my xorg.conf I was able to get nvidia & beryl to work.  I got rid of kde so I don't know about that.  But I'm still having the same problems with the sound buttons and touchpad, as well as hibernating and sleeping.  I've seen that others are having the same problem with the volume buttons and I don't know that there are many people with the elantech touchpad, so I don't know that it is much of a problem in the ubuntu community, but I still don't have a solution to the tap-to-click thing.  My biggest problem now is the hibernating & sleeping.  I plan on downloading a custom hibernate/sleep script, but I just don't have the time right now.
If you decide to get an HEL80, I'll be glad to help you out with what I used to fix mine.

~mrpeenut24

---

