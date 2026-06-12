---
title: "HP Media IR Remote"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by lamalex on 2007-02-12
I was wondering if anyone with an HP laptop has had any luck with their media center remote that came with it? Some of the functions work, scrolling, volume, the OK button works as a 'return' key, but I'd really like the media  control buttons to work with my different applications such as amarok and ogle, at the least have them launch my programs. it might be a little bit much to ask since the remote was really designed for windows media center, but hey, I've got it and I'd like to use it and I'm sure there are others out there who do too.

---

### Post by watson540 on 2007-03-03
Trying to find the same thing right now, probably means configuring lirc. But why do that when it already works...kinda

---

### Post by natman on 2007-03-14
Hi, I am trying for the exact same thing ( dv2278 hp remote control ), it just seems to control volume, scrolling and clicking but not play pause stop.
If anyone has any idea please do reply. I did find this file not sure if its any use but here it is
[HTML]#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

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
[/HTML]
from 

[http://lirc.sourceforge.net/remotes/mceusb/lircd.conf.mceusb](http://lirc.sourceforge.net/remotes/mceusb/lircd.conf.mceusb)

I have no idea whatsoever what to do with the above, ie i need i line by line instructions if anyone has any, thanks.

---

### Post by Sylchat on 2007-12-13
Hi,

I'm trying to make it work on my dv9655ez. The remote is an RC6 IR and I could find the code of a few buttons using XEV, but some are not recognized.

For example, the "I" button is coded :
keysym 0xff67, Menu

But the play button would give:
FocusOut event, serial 31, synthetic NO, window 0x5200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x5200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

I don't know exactly how to handle that yet... but I'll continue investigating.

The strange thing is that the play button would be recognized in Totem but not in VLC... and I'd like to use VLC...

---

