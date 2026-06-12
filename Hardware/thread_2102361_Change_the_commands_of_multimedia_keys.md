---
title: "Change the commands of multimedia keys"
date: 2013-01-07
forum: Hardware
---

### Post by TUOggy on 2013-01-07
I don't think that this is just a Gnome issues, but I'm not sure.

I have Japanese Sony VAIO VPCCB series laptop. I'm dual booting Windows 7 and [UbuntuGnome]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10").

My problem is using the Fn key with the Function keys to use the multimedia features. Some work and some don't.

So I have the following:
F1 - Trackpad - doesn't work
F2-F4 - Volume - works
F5-F6 - Screen Brightness - works
F7 - Projector - not sure
F9-F10 - Zoom - doesn't work
F12 - Sleep - Works

So the majority of the keys work. I assumed that I could map the others. So I checked out my xorg.conf to make sure the trackpad was initially set up correctly. Then, I tested the following commands in terminal.

synclient TouchpadOff=1 - Off
synclient TouchpadOff=0 - On

They Work!!!

So I went to the keyboard settings to set up a new custom command. The problem is that when I try to assign Fn+F1, the keystrokes aren't recognized. I can't set any commands using the Fn key.

Then I thought I would try Super+F1. It recognizes the keystrokes, but it won't run the command.

I'm at a loss here. Am I missing something? 
Why do some of these multimedia keys work, while others don't?
Why doesn't the trackpad command work even after I set the command to Super+F1?

Any help would be appreciated!!!

PS - I know about the disable trackpad when typing. It isn't sufficient for me. I was hoping for a way to disable the trackpad completely, but be able to quickly reactivate it when I am on the go with no mouse.

---

### Post by soccnut on 2013-01-07
I have a similar problem with my laptop, certain multimedia key combinations not working properly, as Fn key is a hardware key, i cant find a way to detect and map it using xev.

Anyway, one solution i have is to download jupiter, configure a keyboard shortcut for ctrl-F1 to disable the trackpad. It worked in my case.

---

### Post by TUOggy on 2013-02-25
Well, it's not exactly what I wanted, but I found a usable solution. I installed the Gnome extension Touchpad Indicator from the Gnome extensions website.

It will now automatically disable the touchpad when a mouse is plugged in. 

Still doesn't allow for key commands to enable/disable the touchpad, but it's the best solution atm.

---

