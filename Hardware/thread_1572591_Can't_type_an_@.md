---
title: "Can't type an @"
date: 2010-09-11
forum: Hardware
---

### Post by The Thunder Chimp on 2010-09-11
Hello everyone,

I know that this isn't an Ubuntu problem, but after googling for 20 minutes, I figured you guys were the only ones that could help me out.

When you have a keyboard layout that doesn't make @s with Shift-2 it's usually made by typing Ctrl-Alt-2 (or so I've understood). However, no matter what I do, it never makes the @ symbol. This is very annoying as copy pasting @s from hotmail isn't fun.

By the way, this happens as much on Windows as Ubuntu, and on every PC I have (four and they all multi-boot).

Can anyone help me out with this?

---

### Post by spjackson on 2010-09-11
> **The Thunder Chimp said:**
> Hello everyone,

I know that this isn't an Ubuntu problem, but after googling for 20 minutes, I figured you guys were the only ones that could help me out.

When you have a keyboard layout that doesn't make @s with Shift-2 it's usually made by typing Ctrl-Alt-2 (or so I've understood). However, no matter what I do, it never makes the @ symbol. This is very annoying as copy pasting @s from hotmail isn't fun.

By the way, this happens as much on Windows as Ubuntu, and on every PC I have (four and they all multi-boot).

Can anyone help me out with this?
It certainly sounds odd that you get this fault on several computers and on Windows too.

One way to enter an @ is with Unicode Composition (see [https://help.ubuntu.com/community/ComposeKey#Unicode%20composition](https://help.ubuntu.com/community/ComposeKey#Unicode%20composition))

Press Ctrl-Shift-U together, release, then type 40 followed by Return. However, that is a lot of keystrokes!

What do you get instead of @ when you press the @ key on your keyboard?
What is your keyboard layout? (System->Preferences->Keyboard)

---

### Post by coffeecat on 2010-09-11
> **spjackson said:**
> 
What is your keyboard layout? (System->Preferences->Keyboard)

Agreed. UK keyboards have the @ symbol two keys to the right of the L key (in the shift position), and shift-2 gives us ". Which is a direct swap of the position of " and @ on US keyboards, which I guess is what you use in Canada.

But if your systems are set up for the UK layout, that must be so on 4 machines in each of Ubuntu and Windows. Whatever - that might be worth checking. 

As an aside - Apple UK keyboards have " and @ in the US positions. All very confusing. :confused:

---

### Post by xarkitu on 2010-09-11
Well i had the same problem (because i was so used to windows) but i realised then in ubuntu it's on "AltGr"+"2".
At least on my pc (Portugal keyboard). Try it, it might work...

---

### Post by The Thunder Chimp on 2010-09-13
> **spjackson said:**
> It certainly sounds odd that you get this fault on several computers and on Windows too.

One way to enter an @ is with Unicode Composition (see [https://help.ubuntu.com/community/ComposeKey#Unicode%20composition](https://help.ubuntu.com/community/ComposeKey#Unicode%20composition))

Press Ctrl-Shift-U together, release, then type 40 followed by Return. However, that is a lot of keystrokes!

What do you get instead of @ when you press the @ key on your keyboard?
What is your keyboard layout? (System->Preferences->Keyboard)

Your unicode composition works and is DEFINETLY faster than going on hotmail.com and copy-pasting the @ off the [email]example@hotmail.com[/email].

When I press Ctrl-Alt-2 I get absolutely nothing.

There must be 10 people in the world who use my layout. It's Canadian French Dvorak.


> **coffeecat said:**
> Agreed. UK keyboards have the @ symbol two keys to the right of the L key (in the shift position), and shift-2 gives us ". Which is a direct swap of the position of " and @ on US keyboards, which I guess is what you use in Canada.

But if your systems are set up for the UK layout, that must be so on 4 machines in each of Ubuntu and Windows. Whatever - that might be worth checking. 

As an aside - Apple UK keyboards have " and @ in the US positions. All very confusing. :confused:

There is no standard Shift-(key) keystroke to get a @. It is Ctrl-Alt-2, and it doesn't work at all.


> **xarkitu said:**
> Well i had the same problem (because i was so used to windows) but i realised then in ubuntu it's on "AltGr"+"2".
At least on my pc (Portugal keyboard). Try it, it might work...

Thanks for trying to help, but my keyboard doesn't even have a AltGr key!

Thanks for your help guys, the unicode thing we'll definetly help me out. But it would be great if we could get this done once and for all. Also, will the unicode thing work on Windows?

Thanks Again

---

### Post by Rhubarb on 2010-09-13
Yay another Dvorak keyboard user :)
I'm somewhat jealous that you use the Canadian French Dvorak layout - as I merely use USA Dvorak.

Anyhow, I switched to your layout and can indeed make the @ symbol by pressing:
> RightAlt 2

Let us know if that doesn't fix the problem for you.

---

### Post by The Thunder Chimp on 2010-09-23
YAY! Thanks man, that solved my problem!

Congrats for using Dvorak, I still hope for the impossible, that someday people will massively change layouts.

 I had no idea that 2nd alternate keys had to be activated by using Right_Alt-(Number)! I always thought it was supposed to be Left_Ctrl-Left_Alt-(Number). Sweet, you have no idea how happy I am right now \\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/

I hope they'll offer some Australian Dvorak layout someday, but I really needed a French Dvorak, because the USA Dvorak doesn't have french accents, and the France Dvorak is optimized for french (somewhat different layout that I don't use).
You are awesome! Thanks for everyone else's great help too!

---

