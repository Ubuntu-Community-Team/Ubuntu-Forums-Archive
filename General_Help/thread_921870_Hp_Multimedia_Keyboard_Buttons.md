---
title: "Hp Multimedia Keyboard Buttons"
date: 2008-09-16
forum: General Help
---

### Post by wisedrunkard on 2008-09-16
I have an hp keyboard 5187-7583. It's a relatively standard keyboard except that it has buttons in the following order on top of the F's and Esc:

(Sleep) (Search|HpClub|Internet|Info|E-mail) (Eject1/Eject2) (Burn Cd/Dvd|<<Prev|Play and Pause|Next>>|Stop) (Volume up|Volume down) (Mute)

The sleep, volume up, volume down, and mute buttons work perfectly. The others don't work at all. Can anyone help me get these other multimedia buttons working?

P.S.- if nothing else I'd like the eject keys to works =D THX ALL

---

### Post by oilchangeguy on 2008-09-16
> **wisedrunkard said:**
> I have an hp keyboard 5187-7583. It's a relatively standard keyboard except that it has buttons in the following order on top of the F's and Esc:

(Sleep) (Search|HpClub|Internet|Info|E-mail) (Eject1/Eject2) (Burn Cd/Dvd|<<Prev|Play and Pause|Next>>|Stop) (Volume up|Volume down) (Mute)

The sleep, volume up, volume down, and mute buttons work perfectly. The others don't work at all. Can anyone help me get these other multimedia buttons working?

P.S.- if nothing else I'd like the eject keys to works =D THX ALL

under system there should be a keyboard link, click on it and from there you can locate your keyboard.

---

### Post by wisedrunkard on 2008-09-16
My keyboard is not listed there, so I tried all the different hp keyboards with no success on getting the new buttons working. Is there possibly a driver download for these types of keyboards?

---

### Post by tgalati4 on 2008-09-16
I have an HP multimedia/internet keyboard (5183-9980).  It's got 23 extra keys.

You may need to modify your keyboard mapping but this works for me:

In .bashrc add the following line at the bottom:

# Needed to define multimedia keys on HP23 keyboard
#!/bin/sh
/usr/bin/xmodmap /home/tgalati4/xmodmap.conf

------------------

Create a file "xmodmap.conf" in your home directory with the following:

keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand
keycode  17 = 8 asterisk
keycode  18 = 9 parenleft
keycode  19 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R
keycode  28 = t T
keycode  29 = y Y
keycode  30 = u U
keycode  31 = i I
keycode  32 = o O
keycode  33 = p P
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A
keycode  39 = s S
keycode  40 = d D
keycode  41 = f F
keycode  42 = g G
keycode  43 = h H
keycode  44 = j J
keycode  45 = k K
keycode  46 = l L
keycode  47 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  49 = grave asciitilde
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M
keycode  59 = comma less
keycode  60 = period greater
keycode  61 = slash question
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
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
keycode  77 = Num_Lock Pointer_EnableKeys
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = less greater bar brokenbar bar brokenbar
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = Alt_R Meta_R
keycode 114 =
keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 129 =
keycode 130 =
keycode 131 =
keycode 132 =
keycode 133 =
keycode 134 =
keycode 135 =
keycode 136 =
keycode 137 =
keycode 138 =
keycode 139 =
keycode 140 =
keycode 141 =
keycode 142 =
keycode 143 =
keycode 144 = XF86MyComputer
keycode 145 =
keycode 146 =
keycode 147 =
keycode 148 =
keycode 149 =
keycode 150 = XF86Calculator
keycode 151 = XF86Favorites
keycode 152 = 
keycode 153 = XF86Search
keycode 154 = 
keycode 155 =
keycode 156 = NoSymbol Meta_L
keycode 157 =
keycode 158 = XF86Mail
keycode 159 = XF86Documents
keycode 160 = XF86AudioMute
keycode 161 = XF86AudioNext
keycode 162 = XF86AudioPlay XF86AudioPause
keycode 163 = 
keycode 164 = XF86AudioStop
keycode 165 = 
keycode 166 =
keycode 167 =
keycode 168 =
keycode 169 =
keycode 170 =
keycode 171 =
keycode 172 =
keycode 173 =
keycode 174 = XF86AudioLowerVolume
keycode 175 =
keycode 176 = XF86AudioRaiseVolume
keycode 177 =
keycode 178 = XF86Finance
keycode 179 =
keycode 180 =
keycode 181 =
keycode 182 =
keycode 183 =
keycode 184 =
keycode 185 =
keycode 186 =
keycode 187 =
keycode 188 =
keycode 189 =
keycode 190 =
keycode 191 =
keycode 192 =
keycode 193 =
keycode 194 =
keycode 195 =
keycode 196 =
keycode 197 =
keycode 198 =
keycode 199 =
keycode 200 =  XF86Video
keycode 201 =
keycode 202 =
keycode 203 =
keycode 204 =
keycode 205 =
keycode 206 =
keycode 207 =
keycode 208 =
keycode 209 =
keycode 210 =
keycode 211 =
keycode 212 =
keycode 213 =
keycode 214 =  XF86Launch2
keycode 215 =
keycode 216 =
keycode 217 =
keycode 218 =
keycode 219 =
keycode 220 =
keycode 221 =
keycode 222 =
keycode 223 =
keycode 224 =
keycode 225 =
keycode 226 =
keycode 227 =
keycode 228 =
keycode 229 =
keycode 230 =
keycode 231 =  XF86Mail
keycode 232 =  XF86Launch3
keycode 233 =  XF86Launch4
keycode 234 =  XF86Shop
keycode 235 =
keycode 236 =
keycode 237 =
keycode 238 =
keycode 239 =
keycode 240 =  XF86WWW
keycode 241 =  XF86Eject XF86Eject
keycode 242 =  XF86AudioPrev
keycode 243 =  XF86Launch1
keycode 244 =  XF86Phone
keycode 245 =
keycode 246 =
keycode 247 =
keycode 248 =
keycode 249 =
keycode 250 =
keycode 251 =
keycode 252 =
keycode 253 =
keycode 254 =
keycode 255 =

--------------------

Then go into preferences-->keyboard shortcuts and start customizing with your new keyboard layout.

It takes some work, but eventually you can get all of those keys to do something useful.

Use XEV in a terminal to get the keycodes of keys that you are unsure of.

You also need to add the following to the bottom of /etc/init.d/bootmisc.sh:

# Added new keycodes for sk2506 HP multimedia 23-key keyboard
setkeycodes e016 235
setkeycodes e01e 158
setkeycodes e012 146
setkeycodes e014 148
setkeycodes e015 149
setkeycodes e02d 173
setkeycodes e018 236
setkeycodes e026 238
setkeycodes e017 227
setkeycodes e01f 159
setkeycodes e025 239
setkeycodes e023 237

-----------------------------

---

### Post by mb_webguy on 2008-09-16
What happens when you go to System->Preferences->Keyboard Shortcuts and try to change use one of the media keys for a shortcut?

---

### Post by wisedrunkard on 2008-09-17
Strangely, only the already working buttons show up, the others act as though they're not being pressed

---

