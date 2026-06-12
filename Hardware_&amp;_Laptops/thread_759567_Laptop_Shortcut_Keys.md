---
title: "Laptop Shortcut Keys"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by b3n87 on 2008-04-19
Hello All,

Im usong 8.04 RC (Its awesome btw) and nearly EVERYTHING on my laptop works, expect the infra red remote, but that doesnt really matter.

Anyway on my laptops keyboard I have these touch sensitive buttons that didnt work in gusty, they do now tho! They all work bar one button, which looks like a media button, i want to bind it so that Rythmbox opens up when I press it. When i run dmesg in the terminal I get this error:

```
[    9.212409] atkbd.c: Use 'setkeycodes e02f <keycode>' to make it known.
[    9.227036] atkbd.c: Unknown key pressed (translated set 2, code 0xaf on isa0060/serio0).

```

It looks like its possible to get it working but im not familiar with it, can anyone help me or point me in the right direction?

Many thanks

---

### Post by b3n87 on 2008-04-19
Hello, Ive solved it - not exactly sure what ive done is right but it works
I ran this in the terminal

```

sudo setkeycodes e02f 120

```

Im not sure what the keycode 120 was, but now its my "media launcher" button

Once I ran this, I went into System>Preferences>Keyboard Shortcuts

Then I clicked on Launch Media Player and press my new media button.

Hope this helps anyone whos reading this

---

