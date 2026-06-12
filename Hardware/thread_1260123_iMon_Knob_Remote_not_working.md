---
title: "iMon Knob Remote not working"
date: 2009-09-07
forum: Hardware
---

### Post by smeck on 2009-09-07
Hi

Running Jaunty AMD64, latest updates.

Just got myself an iMon Knob remote control, I chose that one because I knew there already was a lircd.conf for that remote.

I have the appropriate lircd.conf, both /etc/lirc/lircd.conf and ~/.lircd.conf found in /user/share/lirc/remotes

```
#
# this config file was automatically generated
# using lirc-0.8.0(imon_pad) on Sun Apr  2 20:21:17 2006
#
# contributed by 
#
# brand: iMON Knob SoundGraph 
# model no. of remote control: iMON Knob 
# devices being controlled by this remote: iMON Knob
#

begin remote

  name  IMON_KNOB 
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          119990
  toggle_bit      0


      begin codes
          AppExit                  0x288195B7
          Power                    0x289115B7
          Record                   0x298115B7
          Play                     0x2A8115B7
          Open                     0x29B195B7
          KnobVolUp                0x000100FF
          KnobVolDown              0x010000FF
          KnobMute                 0x000008FF
          Rewind                   0x2A8195B7
          Pause                    0x2A9115B7
          FastForward              0x2B8115B7
          PrevChapter              0x2B9115B7
          Stop                     0x2B9715B7
          NextChapter              0x298195B7
          WindowsKey               0x2B8195B7
          Backspace                0x28A115B7
          MouseKeyboard            0x299115B7
          SelectSpace              0x2A9315B7
          MouseMenu                0x28B715B7
          MouseRightClick          0x688481B7
          Enter                    0x28A195B7
          MouseLeftClick           0x688301B7
          CursorLeft               0x6ABA81B7
          CursorUp                 0x6902F9B7
          CursorRight              0x68A281B7
          CursorDown               0x6882A1B7
          Esc                      0x2BB715B7
          Eject                    0x299395B7
          AppLauncher              0x29B715B7
          MultiMon                 0x2AB195B7
          TaskSwitcher             0x2A9395B7
          Mute                     0x2B9595B7
          VolUp                    0x28A395B7
          VolDown                  0x28A595B7
          ChUp                     0x289395B7
          ChDown                   0x288795B7
          Timer                    0x2B8395B7
          1                        0x28B595B7
          2                        0x2BB195B7
          3                        0x28B195B7
          4                        0x2A8595B7
          5                        0x299595B7
          6                        0x2AA595B7
          7                        0x2B9395B7
          8                        0x2A8515B7
          9                        0x2AA115B7
          ShiftTab                 0x28B515B7
          0                        0x2BA595B7
          Tab                      0x29A115B7
          MyMovie                  0x2B8515B7
          MyMusic                  0x299195B7
          MyPhoto                  0x2BA115B7
          MyTV                     0x28A515B7
          Bookmark                 0x288515B7
          Thumbnail                0x2AB715B7
          AspectRatio              0x29A595B7
          FullScreen               0x2AA395B7
          MyDVD                    0x29A295B7
          Menu                     0x2BA385B7
          Caption                  0x298595B7
          Language                 0x2B8595B7
# these codes may be wrong, but they were included in the first version of
# this config file
          0                        0x2BA595BF
          NextChapter              0x298195BF
          Thumbnail                0x2AB715BF
          FullScreen               0x2AA395BF

      end codes

end remote
```

In Gnome-lirc-properties the Unlock-button is greyed out and every time I have to choose the remote (autodetect lets me choose betwen iMon Knob and Dinovo Edge keyboard), but after doing that the right buttons is reported (in gnome.lirc.properties) when pressing the remote. But I cant get the remote to control anything. I have activated lirc plugins in Rhythmbox and Totem.

irw seems to report button actions from my mouse instead (Logitech MX1000). But if I remove the usb transmitter for the mouse and reinsert it
irw may report imon keys, but I may also have to```
rmmod lirc_imon
lsmod lirc_imon
```to get irw report buttons from the remote.

But I still can't get my iMon Knob to control anything.

Do I need to do something with lircrc and/or hardware.conf? If yes, what should I do?

---

