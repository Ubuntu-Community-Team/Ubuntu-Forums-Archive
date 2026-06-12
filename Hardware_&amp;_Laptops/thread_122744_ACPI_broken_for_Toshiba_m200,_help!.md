---
title: "ACPI broken for Toshiba m200, help!"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by Ninjagecko on 2006-01-28
Would anyone please help?

I've had a Toshiba m200 on which I installed Ubuntu. There seem to be massive ACPI problems.

1) The computer won't shutdown or hibernate. Shutdown makes the screen turn black but it never shuts down. Hib

2) I'm not sure if standby works or not. Every 10 minutes the screen is turning black when I don't want it to. I've disabled standby everywhere I can think of in kcontrol (where can I make 100% sure standby is off?), would someone please tell me how to get rid of standby or whatever is causing the screen to turn black.

I also hear that on Toshiba laptops, one might have to add a line at the end of the resume.sh ACPI script to ensure the backlight comes on? Is this true, and what would the modification be please? Currently when the computer wakes up, I have to ctrl-alt-f1 and then ctrl-alt-f7 in order to see anything on the screen.

Also when I come out of this standby/sleep/whatever, Firefox instantly crashes. Also sometimes, it's impossible to wake from this sleep and I have to make a hard reboot.

3) ctrl-alt-f1 through f6 don't work; they only yield black screens. I think this is nVidia related (and not ACPI related), but if anyone has insight please be so kind as to help

Please, any help is appreciated, this installation of Ubuntu is less usable and stable than the worst Windows/Classic-Mac I've seen yet! -- no offense

---

### Post by Ninjagecko on 2006-01-28
Regarding #2:
Oops... even with the kernel boot option acpi=off, the screen still periodically goes dark... argh, what could the problem be?

[sorry if this content belongs in the KDE forum; there was no appropriate place to post in there]

---

### Post by Ninjagecko on 2006-01-28
4) Additionally, the fan doesn't kick in naturally. I have to force the fan to be on 100% of the time by doing echo "force_on:1" > /proc/acpi/toshiba/fan

---

### Post by Ninjagecko on 2006-02-01
*bump*

Might anyone have any insight into this please?

---

### Post by joejag on 2006-04-05
My nvidia card on my breezy install also does this "blanking" annoyance.

I've disabled XScreensavers power saving stuff but this makes no difference.  The screen can be brought back via a Ctrl+Alt+F1 and then Ctrl+Alt+F7 but this is damned irratating.

I'm thinking this could be a framebuffer problem.

I have a Toshiba Laptop M30 using the nvidia drivers from apt.

---

