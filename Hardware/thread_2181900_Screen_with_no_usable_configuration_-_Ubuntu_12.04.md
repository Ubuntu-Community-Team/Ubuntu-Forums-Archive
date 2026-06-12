---
title: "Screen with no usable configuration - Ubuntu 12.04"
date: 2013-10-19
forum: Hardware
---

### Post by KevinCSE on 2013-10-19
Hi,
I am running Ubuntu 12.04 on my Dell XPS13 L322X (installed onto a flash drive). However, at boot time, the screen just turns off.
I was able to access the Terminal through recovery mode though.  

I have tried several of the most common solutions that I've seen on forums/AskUbuntu, in vain.

Please help me figure this out.  
Thanks!

Here is the content of my xorg.conf:
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208[/TD]
[TD="class: code"][COLOR=#000000]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "record"
    Load  "glx"
    Load  "extmod"
    Load  "dri"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card1"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/COLOR][/TD]
[/TR]
[/TABLE]

and here the contents of my Xorg.0.log
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174[/TD]
[TD="class: code"][COLOR=#000000][    14.380] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    14.380] X Protocol Version 11, Revision 0
[    14.380] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    14.380] Current Operating System: Linux kevinXPSL322X 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64
[    14.380] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic.efi.signed root=UUID=49cb02dd-1ae0-4a3b-9603-3528c55f9ae1 ro recovery nomodeset
[    14.380] Build Date: 16 October 2013  04:41:23PM
[    14.380] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.380] Current version of pixman: 0.24.4
[    14.380]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.380] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.380] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 19 00:10:59 2013
[    14.380] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.380] (==) No Layout section.  Using the first Screen section.
[    14.380] (==) No screen section available. Using defaults.
[    14.380] (**) |-->Screen "Default Screen Section" (0)
[    14.380] (**) |   |-->Monitor "<default monitor>"
[    14.380] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.380] (==) Automatically adding devices
[    14.380] (==) Automatically enabling devices
[    14.380] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.380]     Entry deleted from font path.
[    14.380] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    14.380] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.380] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.380] (II) Loader magic: 0x7fc2ea262b00
[    14.380] (II) Module ABI versions:
[    14.380]     X.Org ANSI C Emulation: 0.4
[    14.380]     X.Org Video Driver: 11.0
[    14.380]     X.Org XInput driver : 16.0
[    14.380]     X.Org Server Extension : 6.0
[    14.381] (--) PCI:*(0:0:2:0) 8086:0166:1028:058b rev 9, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00002000/64
[    14.381] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.381] (II) LoadModule: "extmod"
[    14.381] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.381] (II) Module extmod: vendor="X.Org Foundation"
[    14.381]     compiled for 1.11.3, module version = 1.0.0
[    14.381]     Module class: X.Org Server Extension
[    14.381]     ABI class: X.Org Server Extension, version 6.0
[    14.381] (II) Loading extension MIT-SCREEN-SAVER
[    14.381] (II) Loading extension XFree86-VidModeExtension
[    14.381] (II) Loading extension XFree86-DGA
[    14.381] (II) Loading extension DPMS
[    14.381] (II) Loading extension XVideo
[    14.381] (II) Loading extension XVideo-MotionCompensation
[    14.381] (II) Loading extension X-Resource
[    14.381] (II) LoadModule: "dbe"
[    14.381] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.381] (II) Module dbe: vendor="X.Org Foundation"
[    14.381]     compiled for 1.11.3, module version = 1.0.0
[    14.381]     Module class: X.Org Server Extension
[    14.381]     ABI class: X.Org Server Extension, version 6.0
[    14.381] (II) Loading extension DOUBLE-BUFFER
[    14.381] (II) LoadModule: "glx"
[    14.382] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.382] (II) Module glx: vendor="X.Org Foundation"
[    14.382]     compiled for 1.11.3, module version = 1.0.0
[    14.382]     ABI class: X.Org Server Extension, version 6.0
[    14.382] (==) AIGLX enabled
[    14.382] (II) Loading extension GLX
[    14.382] (II) LoadModule: "record"
[    14.382] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.382] (II) Module record: vendor="X.Org Foundation"
[    14.382]     compiled for 1.11.3, module version = 1.13.0
[    14.382]     Module class: X.Org Server Extension
[    14.382]     ABI class: X.Org Server Extension, version 6.0
[    14.382] (II) Loading extension RECORD
[    14.382] (II) LoadModule: "dri"
[    14.382] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.382] (II) Module dri: vendor="X.Org Foundation"
[    14.382]     compiled for 1.11.3, module version = 1.0.0
[    14.382]     ABI class: X.Org Server Extension, version 6.0
[    14.382] (II) Loading extension XFree86-DRI
[    14.382] (II) LoadModule: "dri2"
[    14.382] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.382] (II) Module dri2: vendor="X.Org Foundation"
[    14.382]     compiled for 1.11.3, module version = 1.2.0
[    14.382]     ABI class: X.Org Server Extension, version 6.0
[    14.382] (II) Loading extension DRI2
[    14.382] (==) Matched intel as autoconfigured driver 0
[    14.382] (==) Matched vesa as autoconfigured driver 1
[    14.382] (==) Matched fbdev as autoconfigured driver 2
[    14.382] (==) Assigned the driver to the xf86ConfigLayout
[    14.382] (II) LoadModule: "intel"
[    14.382] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.383] (II) Module intel: vendor="X.Org Foundation"
[    14.383]     compiled for 1.11.3, module version = 2.19.0
[    14.383]     Module class: X.Org Video Driver
[    14.383]     ABI class: X.Org Video Driver, version 11.0
[    14.383] (II) LoadModule: "vesa"
[    14.383] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.383] (II) Module vesa: vendor="X.Org Foundation"
[    14.383]     compiled for 1.11.3, module version = 2.3.0
[    14.383]     Module class: X.Org Video Driver
[    14.383]     ABI class: X.Org Video Driver, version 11.0
[    14.383] (II) LoadModule: "fbdev"
[    14.383] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.383] (II) Module fbdev: vendor="X.Org Foundation"
[    14.383]     compiled for 1.11.3, module version = 0.4.2
[    14.383]     ABI class: X.Org Video Driver, version 11.0
[    14.383] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[    14.383] (II) VESA: driver for VESA chipsets: vesa
[    14.383] (II) FBDEV: driver for framebuffer: fbdev
[    14.384] (--) using VT number 7

[    14.387] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.387] (WW) Falling back to old probe method for fbdev
[    14.387] (II) Loading sub module "fbdevhw"
[    14.387] (II) LoadModule: "fbdevhw"
[    14.387] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.387] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.387]     compiled for 1.11.3, module version = 0.0.2
[    14.387]     ABI class: X.Org Video Driver, version 11.0
[    14.388] (II) Loading sub module "vbe"
[    14.388] (II) LoadModule: "vbe"
[    14.388] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.388] (II) Module vbe: vendor="X.Org Foundation"
[    14.388]     compiled for 1.11.3, module version = 1.1.0
[    14.388]     ABI class: X.Org Video Driver, version 11.0
[    14.388] (II) Loading sub module "int10"
[    14.388] (II) LoadModule: "int10"
[    14.388] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.388] (II) Module int10: vendor="X.Org Foundation"
[    14.388]     compiled for 1.11.3, module version = 1.0.0
[    14.388]     ABI class: X.Org Video Driver, version 11.0
[    14.388] (II) VESA(0): initializing int10
[    14.388] (EE) VESA(0): V_BIOS address 0xd00 out of range
[    14.388] (II) UnloadModule: "vesa"
[    14.388] (II) Unloading vesa
[    14.388] (II) UnloadModule: "int10"
[    14.388] (II) Unloading int10
[    14.388] (II) UnloadModule: "vbe"
[    14.388] (II) Unloading vbe
[    14.388] (EE) Screen(s) found, but none have a usable configuration.
[    14.388] 
Fatal server error:
[    14.388] no screens found
[    14.388] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.388] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.388] 
[    14.393]  ddxSigGiveUp: Closing log
[    14.393] Server terminated with error (1). Closing log file.[/COLOR][/TD]
[/TR]
[/TABLE]

---

