---
title: "irw dosen't give me any output (lirc)"
date: 2009-11-16
forum: Hardware
---

### Post by eont on 2009-11-16
So I have a thermaltake dh101 case and i found a lircd.conf for it [here]("http://codeka.com/forums/viewtopic.php?f=3&t=60"). Running ```
mode2 --device=/dev/lirc0 --raw
``` appears to give me the same keycodes as are in that lircd.conf for the same buttons however this is where my success ends. If I run 
```
lird -n
```
and
```
irw
```

I get the output
```
lircd-0.8.6[4377]: lircd(default) ready, using /var/run/lirc/lircd
lircd-0.8.6[4377]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[4377]: could not get file information for /dev/lirc
lircd-0.8.6[4377]: default_init(): No such file or directory
lircd-0.8.6[4377]: Failed to initialize hardware
```

if I then create a symlink from /dev/lirc to /dev/lirc0 that error goes away but irw still doesn't give me any output what gives?

Stuff that might help

My lircd.conf
```
begin remote

  name  dh101-IR-Pad_and_Numbers
  bits           64
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  0
  post_data      0x0
  gap          195996
  toggle_bit_mask 0x0000000000

      begin codes
          1                        0x0200001E00000000
          2                        0x0200001F00000000
          3                        0x0200002000000000
          4                        0x0200002100000000
          5                        0x0200002200000000
          6                        0x0200002300000000
          7                        0x0200002400000000
          8                        0x0200002500000000
          9                        0x0200002600000000
          *                        0x0220002500000000
          0                        0x0200002700000000
          #                        0x0220002000000000
          PadUp                    0x0100800000000000
          PadDown                  0x01007F0000000000
          PadRight                 0x0100007F00000000
          PadLeft                  0x0100008000000000
          Backspace                0x0200002A00000000
          Select/Space             0x0200002C00000000
          Menu                     0x0200006500000000
          RightClick               0x0102000000000000
          Enter                    0x0200002800000000
          LeftClick                0x0101000000000000
          Esc                      0x0200002900000000
          StartMenu                0x0280000000000000
      end codes

end remote

# brand:                       Thermaltake DH101
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name          Infra_Red_Remote
  bits           64
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  0
  post_data      0
  gap          195997
  toggle_bit_mask 0x400000000000

      begin codes
          AppExit                  0x288195B700000101
          Power                    0x289115B700000101
          Record                   0x298115B700000101
          Play                     0x2A8115B700000101
          Open                     0x29B195B700000101
          Rew                      0x2A8195B700000101
          Pause                    0x2A9115B700000101
          FFwd                     0x2B8115B700000101
          Prev                     0x2B9115B700000101
          Stop                     0x2B9715B700000101
          Next                     0x298195B700000101
          Eject                    0x299395B700000101
          AppLaunch                0x29B715B700000101
          QuickLaunch              0x2AB195B700000101
          TaskSwitch               0x2A9395B700000101
          Mute                     0x2B9595B700000101
          Vol+                     0x28A395B700000101
          Chn+                     0x289395B700000101
          Timer                    0x2B8395B700000101
          Vol-                     0x28A595B700000101
          Chn-                     0x288795B700000101
          1                        0x28B595B700000101
          2                        0x2BB195B700000101
          3                        0x28B195B700000101
          4                        0x2A8595B700000101
          5                        0x299595B700000101
          6                        0x2AA115B700000101
          7                        0x2B9395B700000101
          8                        0x2A8515B700000101
          9                        0x2AA115B700000101
          ShiftTab                 0x28B515B700000101
          0                        0x2BA595B700000101
          Tab                      0x29A115B700000101
          MyMovie                  0x2B8515B700000101
          MyMusic                  0x299195B700000101
          MyPhoto                  0x2BA115B700000101
          MyTV                     0x28A515B700000101
          Bookmark                 0x288515B700000101
          Thumbnail                0x2AB715B700000101
          AspectRatio              0x29A595B700000101
          FullScreen               0x2AA395B700000101
          MyDVD                    0x29A395B700000101
          Menu                     0x2BA395B700000101
          Caption                  0x298595B700000101
          Language                 0x2B8595B700000101
      end codes
end remote

begin remote

  name  knob-mute
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  24
  post_data      0x1EE
  gap          123997
  min_repeat      84
  toggle_bit_mask 0

      begin codes
          Mute                     0x0000000001
          Vol+                     0x0001000000
          Vol-                     0x0100000000
          iMedian                  0x000000000F
          AppExit                  0x000000002B
          Esc                      0x0000000017
          Up                       0x0000000012
          Enter                    0x0000000016
          Start                    0x000000002C
          Menu                     0x000000002D
          Left                     0x0000000014
          Down                     0x0000000013
          Right                    0x0000000015
      end codes

end remote

```

Output from the command ```
mode2 --device=/dev/lirc0 --raw
``` when pressing the buttons 1-9
```
code: 0x0200001e00000000
code: 0x0200000000000000
code: 0x0200001f00000000
code: 0x0200000000000000
code: 0x0200002000000000
code: 0x0200000000000000
code: 0x0200002100000000
code: 0x0200000000000000
code: 0x0200002200000000
code: 0x0200000000000000
code: 0x0200002300000000
code: 0x0200000000000000
code: 0x0200002400000000
code: 0x0200000000000000
code: 0x0200002500000000
code: 0x0200000000000000
code: 0x0200002600000000
code: 0x0200000000000000

```

---

