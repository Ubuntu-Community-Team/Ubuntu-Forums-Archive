---
title: "IR Remote not working on HP dv4 notebook in 10.04"
date: 2010-06-03
forum: Hardware
---

### Post by ubunt22rock on 2010-06-03
Hi

I have a custom HP dv4t. I got what appears to be called a media centre remote with it, complete with a shiny windows vista button on it. The problem is, the only button which seems to work (only at times) is the "switch displays" button. I have to add I installed lirc sometime back and have been downloading various config files to include in the lircd.conf file. That seemed to be the suggested solution in various forums. This din't work. two important details which may be valuable clues:

1. The "switch displays" button worked before I installed lirc. It does sound odd. But I could have had lirc and been ignorant, not noticing when apt notified me of the fact. 

2. 'irw' command does not register ANY button.

please help me solve this

---

### Post by ubunt22rock on 2010-06-05
anyone out there willing to help me?

---

### Post by Miguel Angel Da Vila on 2010-08-19
I found this solution in the Internet, but I don't have the original author page.

It works for RC model RC1762308701B.

Install lirc

In the /etc/lirc/hardware.conf file configure as in the sample:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="HP_RC172308-01B"
REMOTE="ENE KB3926 B/C/D (ENE0100) CIR port"
REMOTE_MODULES="lirc_dev lirc_ene0100"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lirc.conf"
REMOTE_LIRCD_ARGS="-d /dev/lirc0"

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

```

Then copy the following text in /etc/lircd/lircd.conf

```

#
# this config file was automatically generated
# using lirc-0.8.6(default) on Tue Jun 15 13:43:01 2010
#
# contributed by fogobogo 
#
# brand:                       	HP
# model no. of remote control:  RC1762308/01B
# devices being controlled by this remote: HP Pavillon Entertainment Laptop
#

begin remote

  name  HP_RC172308-01B
  bits            8
  flags RC6
  eps            30
  aeps          100

  header       2780   893
  one           467   412
  zero          467   412
  pre_data_bits   29
  pre_data       0x37FF07B
  gap          72382
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_POWER                0xF3
          KEY_DVD                  0xDB
          KEY_UNKNOWN              0x7F # thats the "check" or "squareroot" button on the top row of the remote
          KEY_SWITCHVIDEOMODE      0x7E
          KEY_MENU                 0xF2 # the "windows" button
          KEY_UP                   0xED
          KEY_DOWN                 0xEC
          KEY_STOP                 0xE6
# these dont work particularly well with most applications. you might want to alter them
          KEY_REWIND               0xEA
          KEY_PLAYPAUSE            0x91
          KEY_FASTFORWARD          0xEB

          KEY_PREVIOUS             0xE4 # the "up" button on the left of the remote
          KEY_NEXT                 0xE5 # the "dn" button on the left of the remote

          KEY_UP                   0xE1
          KEY_LEFT                 0xDF
          KEY_RIGHT                0xDE
          KEY_OK                   0xDD
          KEY_DOWN                 0xE0

          KEY_BACK                 0xDC
          KEY_INFO                 0xF0

          KEY_VOLUMEDOWN           0xEE
          KEY_VOLUMEUP             0xEF
          KEY_MUTE                 0xF1
      end codes

end remote


```

---

### Post by jmatus on 2010-08-22
Works fine for HP dv4 2025la.

---

### Post by saporito on 2010-09-25
I've been looking for this solution for days. Thank you so much! (dv4-2160us)

---

