---
title: "xmodmap - fifth keyboard level doesn't work on some keys"
date: 2008-07-20
forum: General Help
---

### Post by Creshal on 2008-07-20
I created the following xmodmap file:
```
keycode   9 = Escape
keycode  10 = U0031 U0021 U0021 U306C
keycode  11 = U0032 U0026 U0026 U3075
keycode  12 = U0033 U007C U007C U3042
keycode  13 = U0034 U003D U2260 U3046
keycode  14 = U0035 U0022 U0022 U3048
keycode  15 = U0036 U0027 U0027 U304A
keycode  16 = U0037 U003F U003F U3084
keycode  17 = U0038 U0023 U0023 U3086
keycode  18 = U0039 U00A7 U00A7 U3088
keycode  19 = U0030 U00AC U00B0 U308F
keycode  20 = U00DF U1E9E U1E9E U307B
keycode  21 = U0028 U0029 U0029 U3078
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = U0071 U0051 U0040 U305F U0439
keycode  25 = U0077 U0057 U26A0 U3066 U0446
keycode  26 = U0065 U0045 U20AC U3044 U0443
keycode  27 = U0072 U0052 U00AE U3059 U043a
keycode  28 = U0074 U0054 U2122 U304B U0435
keycode  29 = U007A U005A U005A U3093 U043d
keycode  30 = U0075 U0055 U221E U306A U0433
keycode  31 = U0069 U0049 U0049 U306B U0448
keycode  32 = U006F U004F U03A9 U3089 U0449
keycode  33 = U0070 U0050 U003A U308B U0437
keycode  34 = U00FC U00DC U00DC U3080 U0445
keycode  35 = U005B U005D U005D U3002 U044a
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = U0061 U0041 U03B1 U3061 U0444
keycode  39 = U0073 U0053 U221A U3068 U044B
keycode  40 = U0064 U0044 U2205 U3057 U0432
keycode  41 = U0066 U0046 U0024 U306F U0430
keycode  42 = U0067 U0047 U03B3 U304D U043f
keycode  43 = U0068 U0048 U0048 U304F U0440
keycode  44 = U006A U004A U004A U307E U043E
keycode  45 = U006B U004B U004B U306E U043b
keycode  46 = U006C U004C U004C U308A U0434
keycode  47 = U00F6 U00D6 U00F8 U308C U0436
keycode  48 = U00E4 U00C4 U00E6 U3051 U044d
keycode  49 = U005E U007E U00B4 U307D U0060
keycode  50 = Shift_L
keycode  51 = U007B U007D U007D U3001
keycode  52 = U0079 U0059 U00A5 U3055 U044f
keycode  53 = U0078 U0058 U0058 U305D U0447
keycode  54 = U0063 U0043 U00A9 U3072 U0441
keycode  55 = U0076 U0056 U0056 U3073 U043c
keycode  56 = U0062 U0042 U03B2 U307F U0438
keycode  57 = U006E U004E U2622 U3082 U0442
keycode  58 = U006D U004D U00B5 U306D U044c
keycode  59 = U002C U003B U003B U3053 U0431
keycode  60 = U002E U003A U2022 U3081 U044e
keycode  61 = U002D U005F U2013 U308D
keycode  62 = Shift_R
keycode  63 = U002A U002A U3069 U3079
keycode  64 = Alt_L
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
keycode  77 = Num_Lock U307C U3052
keycode  78 = Scroll_Lock
keycode  79 = U0037 U2077 U305B U3092
keycode  80 = U0038 U2078 U304C U3047
keycode  81 = U0039 U2079 U3056 U3045
keycode  82 = U002D U002D U3054 U305E
keycode  83 = U0034 U2074 U3060 U3085
keycode  84 = U0035 U2075 U3070 U3083
keycode  85 = U0036 U2076 U3071 U3049
keycode  86 = U002B U002B U00B1 U307A
keycode  87 = U0031 U00B9 U304E U3063
keycode  88 = U0032 U00B2 U3058 U3043
keycode  89 = U0033 U00B3 U3074 U3087
keycode  90 = U0030 U2070 U305C U3041
keycode  91 = U002C U002C U3077 U3067
keycode  94 = U003C U003E U003E U3064
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
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
keycode 112 = U002F U002F U005C U0025
keycode 113 = Mode_switch
keycode 115 = Multi_key Multi_key
keycode 116 = ISO_Level3_Shift
keycode 117 = Menu
```
Short: First level normal, second via Shift (works), third via AltGr (works), fourth via AltGr+Shift (works)... and the fifth via the right Windows key. But here the keycodes 44 and 57 (j and n) don't work, there I got the first level character instead of the fifth level one (and the secong level if I try the sixth level via RWin+Shift). All other keys work fine with the fifth level, only those two not. I already tried other characters for those levels, same result. I also tried another keyboard, also the same result. Any ideas what the reason for this bug could be?

---

### Post by Creshal on 2008-07-20
What the heck... No key is working with fifth level anymore, except in xev. There the are the correct character shown when pressing the combo (except the two keys mentioned above), but in all other applications there comes simply nothing...

Edit: Ok, whatever this was, it was solved after a reboot. 44 and 57 are still not working, but the rest does.

---

### Post by Creshal on 2008-07-24
*bump*?

---

### Post by Creshal on 2008-08-13
*bump*

---

