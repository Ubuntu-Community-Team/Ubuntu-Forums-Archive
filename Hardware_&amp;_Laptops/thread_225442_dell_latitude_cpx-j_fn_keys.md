---
title: "dell latitude cpx-j fn keys"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by chriszf13 on 2006-07-29
Hi guys,

I just got xubuntu going on my latitude cpx, but the fn key combinations don't seem to work. It doesn't even seem like the fn key is being registered as a keypress at all. When I run showkey, pressing fn doesn't generate a code. Any idea what's up? Thanks.

---

### Post by Ziox on 2006-07-29
by "showkey" do you mean the xev command:

xev

and i have the same problem...pressing the fn key doesn't register any keystrokes...i have given up sometime ago on fixing this problem.

---

### Post by K.Mandla on 2006-07-29
I've got a CPx J750GT at home running a straight Xubuntu 6.06 install. If you can tell me the exact combinations you're trying, I'll try them at home and see if they do anything for me.

Of course, chances are if they don't work for you, they're not going to work for me either. :rolleyes:

---

### Post by chriszf13 on 2006-07-30
If you go to the console (it has to be a console, not a term), you can run 'showkey -u' which seems to capture all the codes coming from the keyboard. When I hit fn-anything, like, fn-up or fn-down to change the screen brightness, nothing happens. fn-left or fn-right should change the contrast, but none of that works. In showkey, every key generates both a keydown and a keyup code except for the 'fn' key.

---

### Post by brn on 2006-08-02
Running Dapper,the fn-(arrow) keys on my CPx do seem to have an effect on the screen brightness and contrast but it is very-very miniscule. In fact "Increase Contrast" (left-arrow) and "Increase Brightness" (up-arrow) seem to function identically, as do right and down-arrows.  But there is not enough change to make a real difference.  It's the same with Windows-XP.

As far as I can tell none of the other blue keys (top row) do anything at all.

---

