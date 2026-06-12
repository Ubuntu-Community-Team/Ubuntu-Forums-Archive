---
title: "System hangs when entry in  graphical environment"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by adirea on 2009-11-01
[FONT=Verdana][SIZE=1]After installation 9.10, I do login[/SIZE][/FONT] and I enter the graphical environment
[FONT=Verdana][SIZE=1]then the system hangs.

I observe the following, with the command dmesg:

[/SIZE][/FONT]                                        [LEFT][FONT=Verdana][SIZE=1][   31.301725] r8169: eth0: link up[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   31.301735] r8169: eth0: link up[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293544] [drm:edid_is_valid] *ERROR* Raw EDID:[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293553] <3>00 00 00 00 00 00 00 00 00 d9 70 12 11 df 5b 00  ..........p...[.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293557] <3>2b 09 01 02 0e 21 18 96 eb 0c c9 a0 57 47 9b 27  +....!......WG.'[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293561] <3>12 48 4c ff ff 80 31 59 45 59 61 59 71 59 81 99  .HL...1YEYaYqY..[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293565] <3>81 4f a9 4f 01 01 ea 24 00 60 41 00 28 30 30 60  .O.O...$.`A.(00`[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293569] <3>13 00 38 ea 10 00 00 1e 00 00 00 fd 00 30 71 ff  ..8..........0q.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293573] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293577] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293580] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................[/SIZE][/FONT][/LEFT]
    [FONT=Verdana][SIZE=1][   34.293584] [/SIZE][/FONT]
    [LEFT][FONT=Verdana][SIZE=1][   34.293588] i915 0000:00:02.0: VGA-1: EDID invalid.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409664] [drm:edid_is_valid] *ERROR* Raw EDID:[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409673] <3>00 00 00 00 00 00 00 00 00 d9 70 12 11 df 5b 00  ..........p...[.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409677] <3>2b 09 01 02 0e 21 18 96 eb 0c c9 a0 57 47 9b 27  +....!......WG.'[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409681] <3>12 48 4c ff ff 80 31 59 45 59 61 59 71 59 81 99  .HL...1YEYaYqY..[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409684] <3>81 4f a9 4f 01 01 ea 24 00 60 41 00 28 30 30 60  .O.O...$.`A.(00`[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409688] <3>13 00 38 ea 10 00 00 1e 00 00 00 fd 00 30 78 1e  ..8..........0x.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409692] <3>60 1a 00 0a 20 20 20 20 20 20 00 00 00 fc 00 43  `...      .....C[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409696] <3>50 44 2d 47 32 30 30 0a 20 20 20 20 00 00 00 ff  PD-G200.    ....[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409700] <3>00 36 30 32 30 38 38 31 0a 20 20 20 20 20 00 15  .6020881.     ..[/SIZE][/FONT][/LEFT]
    [FONT=Verdana][SIZE=1][   34.409703] [/SIZE][/FONT]
    [LEFT][FONT=Verdana][SIZE=1][   34.409708] i915 0000:00:02.0: VGA-1: EDID invalid.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=1][   34.806801] [drm] DAC-6: set mode 1280x1024 b[/SIZE][/FONT][/LEFT]
[SIZE=1][FONT=Verdana]
[/FONT][/SIZE]I tried with Xubuntu 9.10 and it is working fine, but install compiz and the active, the 
system [FONT=Verdana][SIZE=1] hangs.

Many[/SIZE][/FONT][SIZE=1][FONT=Verdana] [/FONT][/SIZE]thanks,

---

