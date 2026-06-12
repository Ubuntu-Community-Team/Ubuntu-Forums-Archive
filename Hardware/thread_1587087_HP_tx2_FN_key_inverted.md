---
title: "HP tx2 FN key inverted"
date: 2010-10-02
forum: Hardware
---

### Post by dabbish on 2010-10-02
So when Num Lock is off the FN + numerical doesn't give me digits, but system keys such as kp_insert, kp_begin etc.

In System->Preferences->Keyboard I have Generic 105-key (Intl) PC

I'm on a HP touchsmart tx2. And there is no option in BIOS where I can toggle anything like this.

What to do? Please advise.

---

### Post by Ayuthia on 2010-10-05
What you describe is similar to how it is supposed to work.  It matches to the normal HP numeric keypad on their keyboard (at least the US version).  Here is what I see is mapped:
```

. - Delete
0 - Insert
1 - End
2 - Down Arrow
3 - Page Down
4 - Left Arrow
5 - Nothing
6 - Left Arrow
7 - Home
8 - Up Arrow
9 - Page Up

```
Just to be sure, I tested it out on Windows 7 and received the same responses.

If you are looking to change those values, the only thing that I know that might do it is xmodmap and to get the values of the key you would need xev.  I don't recall that there is a graphical version.  To get more information about it you can read it in the manual page from the Terminal:
```

man xmodmap

```

---

### Post by dabbish on 2010-12-26
Actually this has nothing to do with my HP laptop. This seems to be the default behavior with FN keys in Ubuntu. If I for example press FN + shift + U I will get a 4. Without the shift I will get left arrow. I'd like it to be the other way around. So if anyone know how to do that I'll be very grateful for pointers, thanks.
Btw I have tried xkeycaps, but had no clue how to use it.

---

### Post by dabbish on 2010-12-26
Ok finally found it. Go to System->Keyboard->Layout->Options->Miscellaneous compability options->Tick 'Numeric keypad keys work as with Mac'.

---

