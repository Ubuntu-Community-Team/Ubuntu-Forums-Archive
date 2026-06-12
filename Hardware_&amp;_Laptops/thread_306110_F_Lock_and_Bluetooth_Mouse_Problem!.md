---
title: "F Lock and Bluetooth Mouse Problem!"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by Nush_W on 2006-11-24
Don't know if anyone else has come across this but I have a **Bluetooth Keyboard and Mouse** that work fine together until I press the **F Lock** key.

The mouse functions seem inhibited when this happens as I can move the cursor but I'm restricted in what I can select and click.

If I turn off the **F Lock** everything goes back to normal. I have found if I use a **PS/2 keyboard** then the **Bluetooth Mouse **works fine regardless of the **F Lock** state.

I'm using a **Microsoft Optical Desktop Elite for Bluetooth** keyboard and mouse set in **Ubuntu 6.06**.

I would be much obliged for anyway help given, however limited!

---

### Post by GhettoPuNKkiD on 2006-12-02
I have this problem too!

A bit off topic: Have you got your keyboard and mouse to connect at boot?

---

### Post by Nush_W on 2006-12-05
Yes I have! Though I'm not exactly sure how anymore, I can tell you that it is possible.

If you have Version 2 of the Microsoft Wireless Transceiver for Bluetooth (the USB dongle) then you should be able to access your BIOS. If you have V2 but the keyboard is not working at boot-up then use a wired keyboard to check the CMOS setup options, and see if enabling the USB keyboard or USB legacy support options make a difference.

I was dual-booting Windows XP and Ubuntu using Grub. I had no problem with the mouse, but it was after connecting the keyboard in Ubuntu that it seemed to pick and choose when it could be used at start-up and when entering XP, I would always have to manually reconnect it, though the mouse always worked fine.

Anyway everything sorted itself out, it just took enough staring at forums until the wee hours of the morning. I don't remember updating anything in particular to get it all to work. I did do a lot of tweaking earlier though and updated to a new kernel, followed the info in the Bluez-utils config file and updated to a newer version and installed any other bug fixes available.

All I know is that I can use my Micrsofot Bluetooth Keyboard at startup to access any kernel version of Ubuntu I have in my system, and I can also start Windows XP without having to reconnect the keyboard manually anymore. Bottomline, I could put my PS/2 keyboard back in its box. Not sure exactly what it was that solved the problem, so now I have a "if it's not broke, don't fix it" mentality and have left things well alone.

Sorry I couldn't tell you a specific solution but try rebooting from XP and seeing if you can access your BIOS first. Note: you won't be able to with the original version of the Microsoft Optical Desktop Elite kit...

---

