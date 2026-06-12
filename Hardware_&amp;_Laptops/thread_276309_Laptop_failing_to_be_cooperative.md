---
title: "Laptop failing to be cooperative"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by omghax on 2006-10-12
Currently **I'm using xubuntu** (*newest version*) on my cheapy laptop (*Acer TravelMate 603TER*), I got it for $150 so I can't complain.

**I've tried ubuntu, kubuntu, and xubuntu** on it. **The only thing that works is Windows**, or debian in console mode only. **I can't even run *ubuntu in console mode**, they all do the same.

It starts out as me booting it up fine, then **after about 5 minutes of up time** (*maybe less*) **the CPU usage goes to 100%** and I can't do anything (*froze basically*). I know it's not the best laptop in the world, **700MHz, 128MB of RAM, etc...** but if **it can run Windows flawlessly**... why is it having so much trouble with Linux?

Right now **I'm dual booting the laptop with Windows XP Pro and xubuntu**, so I can still mess with it on the side to see if someone helps me or not.

I'd *really* appreciate it if I could get some form of Linux OS on this P.O.S., **I highly perfer Linux over Windows** (*depending on the situation*) and use it whenever I can.

--
If you need more info or something just ask, I've never really posted before. I hope some *nix guru has had the same problem and knows the answer, :D

-- Thanks, :D
--- Have a nice day, :D
---- Taco

---

### Post by apjone on 2006-10-15
well im no *nix guru, but ill do my best to help, can you post your /var/log/messages and syslog here for us to look at, just need an extract for the time when it shoots to 100% CPU

---

### Post by dmizer on 2006-10-15
try this ... boot.  when grub starts its countdown, hit esc.

select your running kernel and edit the line.  add this to the end:
```
acpi=off
```
boot the edited kernel, and see if that helps.  if not, there's a heck of alot more we can do ... so keep with it.

---

### Post by omghax on 2006-10-15
Eh... I typed out this *whole* reply and then my girlfriend had to close it... *sigh*

Anyway, this version will be shorter due to I'm kinda angry right now. :D

I now have **256MB** of RAM instead of **128MB**, and when I start up xubuntu it loads fine and I get atleast several programs to run before it crash's down. It doesn't say it's 100% CPU anymore, it just... dies.

Now I'm trying the GRUB command, acpi=off -- everything seems to be working fine... so far...

Do you mind if I ask what it did / does?

---

### Post by dmizer on 2006-10-15
it turns off advanced power management.  this is not necessary on most laptops.  acpi is pretty buggy in some situations so as a troubleshooting technique it's one of the first things i do to try to isolate an issue like this.

watch your computer carefully for a while ... make sure the fan comes on when it's working hard (watching a video or some such).

if your fan seems to come on at the appropriate times, then this change hasn't affected anything major.  to make the change perminiant:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
gksudo gedit /boot/grub/menu.lst
add acpi=off to the end of the line and save.  if your computer won't boot after that change, replace your edited copy of grub with your old.

---

### Post by omghax on 2006-10-16
It's been working *great*, thanks so much! I now have a working laptop with (x)ubuntu! \\:D/ 

-- Thanks so much, :D
--- Have a wonderful day, :D
---- Taco

---

