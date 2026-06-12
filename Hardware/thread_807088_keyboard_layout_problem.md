---
title: "keyboard layout problem"
date: 2008-05-25
forum: Hardware
---

### Post by datarhythm on 2008-05-25
So i recently purchased the X-gene keyboard, which is made to be a mini keyboard for my htpc. very slick keyboard I think but it has an annoying flaw. It doesn't have a keypad (miniture) so it's sort of like a laptop where it has func keys for the numlock and part of the keyboard serves as the keypad. To turn on the num lock I have to hit the func key and the numlock button up at the top. Problem is, is that I don't think the layout knows that I don't have a keypad.

When I type, I have to hold down the func key to get the letters. If I let off the func key I get numbers on the following keys: 789uiojklm.

When I hit the numlock key it doesn't give me anything when I hit those keys but if I hold down on the func key it gives me the letters.

I'd like to be able to flip what the func key does. So if I don't hit the func key, letters come out and when I hold the func key numbers come out.

I've been looking every where I can search on google for something similar and all I can find is references to:

usr/share/X11/synbols/us

Which is where the layout is but I don't see anything refering to the special keys. Also, the xorg file but I don't know what I have to type. I did find various keyboard apps in mint that talk about the different layouts  (which I've tried a number of them with no luck) as well as a few xorg options... none seem to help me.

frustrating. good keyboard, just holding down the func key when I type is becoming a pain.  

any help would be appreciated.

---

### Post by datarhythm on 2008-05-25
I've tried this thread:
[http://ubuntuforums.org/showthread.php?t=188761&highlight=layout]("http://ubuntuforums.org/showthread.php?t=188761&highlight=layout")

And created the file it specified with the following information with no luck:

```

keycode   9 = Escape Escape
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  95 = F11
keycode  96 = F12
keycode  77 = Num_Lock
keyboard 106 = Insert
keyboard 107 = Delete
keyboard 97 = Home

keycode  49 = grave assciitilde
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign sterling
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  79 = 7 ampersand
keycode  80 = 8 asterisk
keycode  81 = 9 parenleft
keycode  63 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 = BackSpace Terminate_Server

keycode  23 = Tab Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R
keycode  28 = t T
keycode  83 = u U
keycode  84 = i I
keycode  85 = o O
keycode  82 = p P
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright
keycode  51 = backslashp bar
keycode  99 = Prior

keycode  66 = Caps_Lock Caps_Lock
keycode  38 = a A
keycode  39 = s S
keycode  40 = d D
keycode  41 = f F
keycode  42 = g G
keycode  43 = h H
keycode  87 = j J
keycode  88 = k K
keycode  89 = l L
keycode  86 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  36 = Return Return
keycode  105 = Next

keycode  50 = Shift_L
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  90 = m M
keycode  59 = comma less
keycode  91 = period greater
keycode  112 = slash question
keycode  62 = Shift_R
keycode  98 = Up Up
keycode  103 = End

keycode  37 = Control_L
keycode  115 = Super_L
keycode  64 = Alt_L
keycode  65 = space
keycode  113 = Alt_R
keycode  116 = Super_R
keycode  117 = Menu
keycode  109 = Control_R
keycode  100 = Left
keycode  104 = Down
keycode  102 = Right

```

---

