---
title: "[SOLVED] lirc problems - remote recognized but programs don't respond"
date: 2008-08-27
forum: Hardware
---

### Post by brohmes on 2008-08-27
Hi,

I think (ok....maybe hope is the better word) I'm close, but I still can't get my applications (vlc, mythtv) to respond to key presses on my remote.

Here's what I've got so far:

- remote is an HP branded MCE remote with a usb IR receiver (says rc6 on the back of the remote - in Vista it showed up as an eHome IR device).

- installed lirc, selected MCE remote ("New, Phillips et all" version)

- this process created /dev/lirc0

- my /etc/lirc/lircd.conf file just says:  
[INDENT]"include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"[/INDENT]

- that file in turn looks like:

```

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
```

- I used the mythbuntu-lirc-generator command to come up with the lircrc file which looks like:

```
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
```

- the vlc file looks like (cut out lots of the key mappings here):

```
begin
    remote = mceusb
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = VolDown
    config = key-vol-down
    repeat = 0
    delay = 0
end
.
.
.
end

```

- the mythtv one looks like:

```
begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

.
.
.
end

```

- I copied the /root/.lircrc file into ~/ and into ~/.mythtv


- "sudo cat /dev/lirc0" will respond to any remote press by outputing a bunch of hex

- "sudo mode2 -d /dev/lirc0" will respond to any remote press with the output of a full screen's worth of alternating lines of "pulse 500" and "space 400"

- "irw " responds to remote presses along the lines of:

[INDENT][INDENT]000000037ff07be0 00 Down mceusb
000000037ff07be1 00 Up mceusb[/INDENT][/INDENT]

It looks like the remote is working fine, but I cannot control either VLC or MythTV.

Have I missed something? I'm new to Linux, so it may be something silly...

Thanks, I appreciate any help.

Ryan

---

### Post by brohmes on 2008-08-29
I solved this problem, thanks to the [lirc mailing list]("https://lists.sourceforge.net/lists/listinfo/lirc-list").

I had a folder  ~/.mythtv/lircrc in addition to the file .lircrc and this caused a conflict.  As soon as I deleted the folder, the remote worked fine.

Ryan

---

