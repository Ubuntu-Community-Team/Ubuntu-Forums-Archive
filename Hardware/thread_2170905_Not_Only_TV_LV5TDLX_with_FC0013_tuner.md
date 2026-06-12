---
title: "Not Only TV LV5TDLX with FC0013 tuner?"
date: 2013-08-28
forum: Hardware
---

### Post by wrzomar on 2013-08-28
I recently bought NOT LV5TDLX and I'm using it on Ubuntu 12.04 with 3.2.0 kernel. I installed dkms driver from PPA ppa:chrisfu/rt2832u-dkms and gqrx from PPA ppa:gqrx/releases, both sdr and rtl2832u driver detects FC0013 tuner but according to many sites ID 1f4d:c803 is FC0012 tuner. In thread [http://ubuntuforums.org/showthread.php?t=1905057](http://ubuntuforums.org/showthread.php?t=1905057) s1hr said:
> This driver depends of particular model of card will open fm radio and DAB radio if your card have support for it.Mine do.
But mine doesn't detect FM and DAB radio in it but DVB-T works perfectly. I can listen to FM radio using gqrx or rtl_fm and play. I can't use gnomeradio due lack of /dev/radio0, I can't use irrecord due lack of /sys/class/rc/rc*. I can make remote control to work but key-mappings are bad. I discovered recently that rc keymap is hard-coded in rtl2832u driver (I found struct rc_map_table rtl2832u_rc_keys_map_table in rtl2832u.c file). Do I need to hack rtl2832u driver to correct key-mapping? How adapter_nr option work? Is this option responsible for device model discovery (will it make FM and DAB radio to work)?

---

### Post by wrzomar on 2013-08-28
I successfully changed key map table for my remote. In file rtl2832u.c I commented out Xgazza's key map and added mine under Xgazza's. I took key names from /lib/udev/rc_keymap/total_media_in_hand and scancodes from ir-keytable output. Two buttons were unknown so I turned ON debugging using debug=7 option of dvb-usb-rtl2832u module and checked /var/log/syslog for unknown scancodes. Now key map for my LV5TDLX (P/N: STLV5TDLXT702) is:
```
static struct rc_map_table rtl2832u_rc_keys_map_table[] = {
    { 0x00ff, KEY_1 },        //1
    { 0x807f, KEY_2 },        //2
    { 0x40bf, KEY_3 },        //3
    { 0xc03f, KEY_4 },        //4
    { 0x20df, KEY_5 },        //5
    { 0xa05f, KEY_6 },        //6
    { 0x609f, KEY_7 },        //7
    { 0xe01f, KEY_8 },        //8
    { 0x10ef, KEY_9 },        //9
    { 0x906f, KEY_0 },        //0
    { 0x50af, KEY_MUTE },        //MUTE
    { 0x28d7, KEY_CYCLEWINDOWS },    //RADIO/TV?
    { 0x30cf, KEY_VIDEO },        //TV/AV
    { 0x708f, KEY_VOLUMEDOWN },    //VOL -
    { 0xf00f, KEY_TIME },        //TIMESHIFT
    { 0x08f7, KEY_RIGHT },        //RIGHT
    { 0x8877, KEY_LEFT },        //LEFT
    { 0x48b7, KEY_UP },        //UP
    { 0xc837, KEY_DOWN },        //DOWN
    { 0xa25d, KEY_POWER },        //POWER
    { 0xa857, KEY_OK },        //OK
    { 0x6897, KEY_STOP },        //STOP
    { 0xe817, KEY_CAMERA },        //SNAPSHOT
    { 0x18e7, KEY_CHANNELUP },    //CH +
    { 0x9867, KEY_RECORD },        //REC
    { 0x58a7, KEY_CHANNELDOWN },    //CH -
    { 0x38c7, KEY_ESC },        //ESC
    { 0x7887, KEY_PLAY },        //PLAY
    { 0xf807, KEY_VOLUMEUP },    //VOL +
    { 0x02fd, KEY_PAUSE },        //PAUSE
    { 0x827d, KEY_FASTFORWARD },    //FASTFORWARD
    { 0x42bd, KEY_REWIND },        //REWIND
    { 0xd02f, KEY_ZOOM },        //min/max
    { 0x22dd, KEY_SHUFFLE },    //SHUFFLE
    { 0xc23d, KEY_INFO }        //key with mouse cursor
};
```
Now I can change the volume, change channels (by writing digits) or change slides in Impress.

---

### Post by wrzomar on 2013-08-30
I made some more changes to some files from rtl2832u-dkms package and I don't want forget what and why I made them so there are patches:
dkms.conf:
```
1c1
< MAKE="make KERNELDIR=/lib/modules/${kernelver}/build"
---
> MAKE="make KDIR=/usr/src/linux-headers-${kernelver}"
8a9
> AUTOINSTALL="yes"
```

I made these changes because driver doesn't update itself after kernel update.

rtl2832u.h
```
226,227c226,227
< #define frt2_bits_mask0            0x00
< #define frt2_bits_mask1            0x00
---
> #define frt2_bits_mask0            0xff
> #define frt2_bits_mask1            0xff
```

rtl2832u.c:
```
88a89
> /*
142c143,181
<
---
> */
> /* wrzomar remote control Ubuntu 12.04 Not Only TV key map */
> static struct rc_map_table rtl2832u_rc_keys_map_table[] = {
>     { 0x40bd00ff, KEY_1 },        //1
>     { 0x40bd807f, KEY_2 },        //2
>     { 0x40bd40bf, KEY_3 },        //3
>     { 0x40bdc03f, KEY_4 },        //4
>     { 0x40bd20df, KEY_5 },        //5
>     { 0x40bda05f, KEY_6 },        //6
>     { 0x40bd609f, KEY_7 },        //7
>     { 0x40bde01f, KEY_8 },        //8
>     { 0x40bd10ef, KEY_9 },        //9
>     { 0x40bd906f, KEY_0 },        //0
>     { 0x40bd50af, KEY_MUTE },        //MUTE
>     { 0x40bd28d7, KEY_CYCLEWINDOWS },    //RADIO/TV?
>     { 0x40bd30cf, KEY_VIDEO },        //TV/AV
>     { 0x40bd708f, KEY_VOLUMEDOWN },    //VOL -
>     { 0x40bdf00f, KEY_TIME },        //TIMESHIFT
>     { 0x40bd08f7, KEY_RIGHT },        //RIGHT
>     { 0x40bd8877, KEY_LEFT },        //LEFT
>     { 0x40bd48b7, KEY_UP },        //UP
>     { 0x40bdc837, KEY_DOWN },        //DOWN
>     { 0x40bda25d, KEY_POWER },        //POWER
>     { 0x40bda857, KEY_OK },        //OK
>     { 0x40bd6897, KEY_STOP },        //STOP
>     { 0x40bde817, KEY_CAMERA },        //SNAPSHOT
>     { 0x40bd18e7, KEY_CHANNELUP },    //CH +
>     { 0x40bd9867, KEY_RECORD },        //REC
>     { 0x40bd58a7, KEY_CHANNELDOWN },    //CH -
>     { 0x40bd38c7, KEY_ESC },        //ESC
>     { 0x40bd7887, KEY_PLAY },        //PLAY
>     { 0x40bdf807, KEY_VOLUMEUP },    //VOL +
>     { 0x40bd02fd, KEY_PAUSE },        //PAUSE
>     { 0x40bd827d, KEY_FASTFORWARD },    //FASTFORWARD
>     { 0x40bd42bd, KEY_REWIND },        //REWIND
>     { 0x40bdd02f, KEY_ZOOM },        //min/max
>     { 0x40bd22dd, KEY_SHUFFLE },    //SHUFFLE
>     { 0x40bdc23d, KEY_INFO }        //key with mouse cursor
> };
540c579
<     u16 scancode=0;
---
>     u32 scancode=0;
624c663
<             scancode=(ucode[2]<<8) | ucode[3] ;
---
>             scancode= (ucode[0]<<24) | (ucode[1]<<16) | (ucode[2]<<8) | ucode[3] ;
```

I added my Not Only TV zapper's scan codes and made them 32 bit so only one zapper control my PC (before my TV zapper interfered with PC).

The patches are outputs from
```
diff original new
```command.

---

### Post by wrzomar on 2013-09-09
I recently changed key mappings for my remote to be more useful, so I'm now publishing it. I changed rtl2832u.c file and made some changes to keyboard.xml from xbmc (I used per user settings, so my "keyboard.xml" is in "~/.xbmc/userdata/keymaps/" and "original" "keyboard.xml" is still in "/usr/share/xbmc/system/keymaps/"). I switched from Kaffeine to xbmc + tvheadend (stable). XBMC is 12.2 version from ppa:team-xbmc/ppa and TvHeadend from "https://tvheadend.org/projects/tvheadend/wiki/AptRepository".
rtl2832u.c/:
```
88a89
> /*
142c143,181
<
---
> */
> /* wrzomar remote control Ubuntu 12.04 Not Only TV key map */
> static struct rc_map_table rtl2832u_rc_keys_map_table[] = {
>     { 0x40bd00ff, KEY_1 },        //1
>     { 0x40bd807f, KEY_2 },        //2
>     { 0x40bd40bf, KEY_3 },        //3
>     { 0x40bdc03f, KEY_4 },        //4
>     { 0x40bd20df, KEY_5 },        //5
>     { 0x40bda05f, KEY_6 },        //6
>     { 0x40bd609f, KEY_7 },        //7
>     { 0x40bde01f, KEY_8 },        //8
>     { 0x40bd10ef, KEY_9 },        //9
>     { 0x40bd906f, KEY_0 },        //0
>     { 0x40bd50af, KEY_MUTE },        //MUTE
>     { 0x40bd28d7, KEY_F11 },    //RADIO/TV?
>     { 0x40bd30cf, KEY_LEFTMETA },        //TV/AV
>     { 0x40bd708f, KEY_VOLUMEDOWN },    //VOL -
>     { 0x40bdf00f, KEY_T },        //TIMESHIFT
>     { 0x40bd08f7, KEY_RIGHT },        //RIGHT
>     { 0x40bd8877, KEY_LEFT },        //LEFT
>     { 0x40bd48b7, KEY_UP },        //UP
>     { 0x40bdc837, KEY_DOWN },        //DOWN
>     { 0x40bda25d, KEY_POWER },        //POWER
>     { 0x40bda857, KEY_ENTER },        //OK
>     { 0x40bd6897, KEY_STOPCD },        //STOP
>     { 0x40bde817, KEY_SYSRQ },        //SNAPSHOT
>     { 0x40bd18e7, KEY_NEXTSONG },    //CH +
>     { 0x40bd9867, KEY_RECORD },        //REC
>     { 0x40bd58a7, KEY_PREVIOUSSONG },    //CH -
>     { 0x40bd38c7, KEY_ESC },        //ESC
>     { 0x40bd7887, KEY_PLAYPAUSE },        //PLAY
>     { 0x40bdf807, KEY_VOLUMEUP },    //VOL +
>     { 0x40bd02fd, KEY_SPACE },        //PAUSE
>     { 0x40bd827d, KEY_FASTFORWARD },    //FASTFORWARD
>     { 0x40bd42bd, KEY_REWIND },        //REWIND
>     { 0x40bdd02f, KEY_F5 },        //min/max
>     { 0x40bd22dd, KEY_Y },    //SHUFFLE
>     { 0x40bdc23d, KEY_COMPOSE }        //key with mouse cursor
> };
540c579
<     u16 scancode=0;
---
>     u32 scancode=0;
624c663
<             scancode=(ucode[2]<<8) | ucode[3] ;
---
>             scancode= (ucode[0]<<24) | (ucode[1]<<16) | (ucode[2]<<8) | ucode[3] ;
```

keyboard.xml (per user (right side) against system (left side)):
```
104a105
>       <KEY_RECORD>XBMC.PlayerControl(Record)</KEY_RECORD>
228a230
>       <y>AudioNextLanguage</y>
```

Now my remote is 100% keyboard, key bindings are as follows:
TV/AV - "Super" key (Windows key) - displays Dash
RADIO/TV - F11 - fullscreen mode in evince
CH + - Next - next song in rhythmbox or audacious, next channel in Live TV (xbmc) and so on
CH - - Previous - previous song in rhythmbox or audacious, previous channel in Live TV (xbmc) and so on
OK - Enter - self explanatory
Play - Play/Pause - works in Rhythmbox, Audacious, xbmc
Pause - Space - works as Play/Pause in most of movie players
Stop - Stop CD - works as Stop in Rhythmbox, Audacious, xbmc
TimeShift - 't' - in xbmc toggle subtitles (standard key binding)
Snapshot - Print Screen
button with something like mouse cursor - Right-click menu
min/max - F5 - presentation mode in evince and Impress
Shuffle - y - cycle through available audio tracks (or streams) in xbmc (my key binding)

That's all Folks! ;)

---

