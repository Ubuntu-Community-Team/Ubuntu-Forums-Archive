---
title: "When booting on battery, ndiswrapper hangs?"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Seth on 2005-04-18
Running a Dell Inspiron 600m with Broadcom wireless chipset. Have it working perfectly with bcmwl5 drivers and ndiswrapper. My problem is this: whenever I **boot** while on battery power, the boot process hangs at starting ndiswrapper. I can use my wireless while on battery just fine, but I CANNOT boot. I can't seem to find any error messages about the problem either. I can't CTRL+C past the bootline, nothing; I have to hard reset. The only way to get Ubuntu to boot is to be on AC power.

This is one of the top three problems I have left. But otherwise I'm so giddily happy with Ubuntu :D

---

### Post by rubinstein on 2005-04-18
I had the same problem with ndiswrapper and warty on a Dell Latitude D600. Booting only with battery power ended with opening and reinserting the battery as it froze the laptop.
With hoary, I didn t have this problem - because I couldn t get ndiswrapper to work :-(
So, I decided to buy an Intel 2200BG card - costed me 30 EUR. Now (after an upgrade to a newer driver for this card) it works. You see, not everything is easy.

I can t help you with your problem, but if i remember correctly what I read on the net, it has something to do with the dell hardware not delivering enough battery power to the card - something is a bit broken, but with windows you don t get it because the driver corrects it somehow...

---

### Post by Seth on 2005-04-18
Surely there's a solution... :-|

---

### Post by Seth on 2005-04-19
Is this something I can file a BugZilla bug on? Or does it fall outside the scope of Ubuntu?

---

### Post by Dianoga on 2005-04-19
My laptop (Inspiron 1150) also hangs on ndiswrapper at boot on battery power, but only occasionally. My card is a PCMCIA Motorola card with broadcom chipset. When I pull the card, the machine restarts and then works just fine with the card in it. I don't know why this is the case but...

---

### Post by Seth on 2005-04-20
[QUOTE=Dianoga]My laptop (Inspiron 1150) also hangs on ndiswrapper at boot on battery power, but only occasionally. My card is a PCMCIA Motorola card with broadcom chipset. When I pull the card, the machine restarts and then works just fine with the card in it. I don't know why this is the case but...[/QUOTE]
 That's it, if I'm not the only one...
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9942](https://bugzilla.ubuntu.com/show_bug.cgi?id=9942)

---

### Post by wbeck85 on 2005-04-20
[QUOTE=Seth]That's it, if I'm not the only one...
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9942](https://bugzilla.ubuntu.com/show_bug.cgi?id=9942)[/QUOTE]
 did you try ctrl+c when it got to the ndiswrapper section. That may allow the boot process to skip over that. *May*

---

### Post by Seth on 2005-04-20
[QUOTE=wbeck85]did you try ctrl+c when it got to the ndiswrapper section. That may allow the boot process to skip over that. *May*[/QUOTE]
 You didn't read my initial post, did you. Go on. Read it again ;)

---

### Post by flagg on 2005-04-20
I have a dell latitude D610 and have the same problem. I have played with the bios settings and have had some luck on and off.

The best solution right now for me seems to have the BIOS option to disable wireless on operating system load, and have it toggle-able via Fn-Wireless key.

This seems to let ndiswrapper load, then i can manually turn on the wireless (using the Fn-Wireless keys) without it locking up. 

Good luck.

---

### Post by Seth on 2005-04-20
[QUOTE=flagg]I have a dell latitude D610 and have the same problem. I have played with the bios settings and have had some luck on and off.

The best solution right now for me seems to have the BIOS option to disable wireless on operating system load, and have it toggle-able via Fn-Wireless key.

This seems to let ndiswrapper load, then i can manually turn on the wireless (using the Fn-Wireless keys) without it locking up. 

Good luck.[/QUOTE]
 This is a good workaround. Now if only we'd have decent network auto-configuration. Sometime in Breezy I suppose.

---

### Post by asg on 2005-10-18
[QUOTE=flagg]I have a dell latitude D610 and have the same problem. I have played with the bios settings and have had some luck on and off.

The best solution right now for me seems to have the BIOS option to disable wireless on operating system load, and have it toggle-able via Fn-Wireless key.

This seems to let ndiswrapper load, then i can manually turn on the wireless (using the Fn-Wireless keys) without it locking up. 

Good luck.[/QUOTE]
The solution I used on my D600 is to disable the quick boot bios option. This makes the bios take 10 seconds or so to init but it won't hang ndiswrapper.

---

