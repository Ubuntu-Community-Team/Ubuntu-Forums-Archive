---
title: "Keyboard layout incorrect"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by josephwalter on 2006-08-10
When I connect to Hoary Hedgehog via VNC, my keyboard doesn't type the correct characters. Instead of 'asdf' I get 'abfh'.

System | Preferences | Keyboard shows "US 105-key keyboard (with windows keys)". I tried switching to a US 101-key keyboard, but that didn't fix the problem.  None of the other keyboard layouts were familiar.

The keyboard that's connected to the machine works fine, though. Any suggestions on how to check or set the keyboard keys for when I connect via RealVNC?

---

### Post by tarantoga on 2007-02-22
I have the exact same problem (even the exact same mapping of keys as the original poster) with an Ubuntu Feisty Herd 3. Keys are complete wrongly mapped.
I tried vnc4server, tightvnc, and the old vncserver. They all exhibit the same symptom over VNC. Using a local X display works fine.

The Control Center->Hardware->Keyboard layout is set to US 105 keys.

At one time, I had it set to the german layout, but switched it back to US. This might have caused the problem? Note that the german layout is very close to the US one and not even remotely close to the weird mapping I now get.

---

### Post by tarantoga on 2007-02-22
Some more information about the mapping:
If I type "abcdefg", I get the first letters from the 2nd row on a US kayboard: "asdfgh".

Very strange. :confused:

---

