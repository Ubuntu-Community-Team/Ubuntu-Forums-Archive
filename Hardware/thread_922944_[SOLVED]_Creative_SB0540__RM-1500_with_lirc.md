---
title: "[SOLVED] Creative SB0540 / RM-1500 with lirc"
date: 2008-09-17
forum: Hardware
---

### Post by Xcerca on 2008-09-17
Hi , I'm trying to get my remote working and I've made some progress but I've been stuck and am looking for some help.   This is where I'm at...

I have a Creative SB0540 USB IR Reciver what is labled as:

ID 041e:3100 Creative Technology, Ltd

and the remote is a Creative RM-1500 , they came with an SB Audigy 4.

I'm pretty sure that the device is
/dev/usb/hiddev1
I can do 'cat /dev/usb/hiddev1' , and when i push buttons on the remote I get an output.

So i tried to set up the lircd.conf with irrecord, i read that i should use the alsa_usb driver but i got an error from irrecord when i try that, so i did

irrecord -H sb0540 -d /dev/usb/hiddev1 lircd.conf

it goes well and i have codes next to the buttons in my the lircd.conf file

i did this to make sure the modules are loaded...
~$ lsmod | grep lirc
lirc_serial            17704  0 
lirc_dev               18248  1 lirc_serial

so i know the kernel modules are loaded, but when i do irw and press buttons i get no output , i can press keys and i get an output, but if i try sudo irw /dev/usb/hiddev1 i get 

$ sudo irw /dev/usb/hiddev1
connect: Connection refused

Here are my conf files,  are these all i need to atleast get an output from irw ?

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="rm-1500"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER="sb0540"
REMOTE_DEVICE="/dev/usb/hiddev1"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

and..

$ cat /etc/lirc/lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Creative USB IR Receiver (SB0540) remote:
#include /usr/share/lirc/remotes/creative/lircd.conf.alsa_usb
begin remote
  name            Creative_SBL
  bits            8
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             315937

  begin codes
       touche1         0x74
       touche2         0x70
       touche3         0x6F
       touche4         0x75
       touche5         0x7B
       touche6         0x87
       touche7         0x76
       touche8         0x7C
       touche9         0x88
       touche0         0x7F
       CMSS            0x8E
       EAX             0x73
       vol-            0x9C
       vol+            0x9D
       up              0x84
       down            0x72
       left            0x78
       right           0x8A
       ok              0x7E
       return          0x71
       start           0x77
       cancel          0x83
       record          0x8C
       options         0x7D
       display         0x89
       previous        0x80
       playpause       0x86
       next            0x85
       slow            0x82
       stop            0x7A
       step            0x81

  end codes

end remote 



i have been doing 

sudo /usr/sbin/lircd -H sb0540 -d /dev/usb/hiddev1 -n  

and then open irw in another console and i get 

lircd-0.8.3pre1[10091]: lircd(userspace) ready
lircd-0.8.3pre1[10091]: accepted new client on /dev/lircd
lircd-0.8.3pre1[10091]: initializing '/dev/usb/hiddev1'
(then i get nothing from irw so I ctrl+z it )
lircd-0.8.3pre1[10091]: removed client
lircd-0.8.3pre1[10091]: closing '/dev/usb/hiddev1'
lircd-0.8.3pre1[10091]: caught signal

does anybody see somthing that sticks out that i can change, or is there anything else that i should check on ?

Thanks,   I love Ubuntu

---

### Post by Xcerca on 2008-09-20
HOLY CRAP !!!!!!!!   

shawn@shawn-desktop:~$ sudo chmod 777 /dev/usb/hiddev1
[sudo] password for shawn: 
shawn@shawn-desktop:~$ irw
000000008322817e 00 Ok Creative_RM-1500
000000008322758a 00 Right Creative_RM-1500
0000000083228d72 00 Down Creative_RM-1500
0000000083228778 00 Left Creative_RM-1500
000000008322758a 00 Right Creative_RM-1500

THATS ALL I HAD TO DO!!!!!!

---

### Post by Xcerca on 2008-09-20
alright so now how do get it to control programs and stuff ?
i need to configure my .lircrc file right ?   

how can i make it control my ALSA for vol up and down , what are the commands to do that so i can put it for irexec ?

heres what i have now  
$ cat .lircrc
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
begin
        remote = Creative_RM-1500
        button = Ok
        prog   = irexec
        repeat = 0
        config = echo "It works!!!"
    end

and this is what my .lircrc/vlc looks like

$ cat /home/shawn/.lirc/vlc
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = Creative_RM-1500
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Creative_RM-1500
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

and this one goes on for the rest of the buttons but i can get irexec to work...    

~$ irexec
It works!!!
It works!!!
It works!!!
It works!!!


so i'm pretty close , just i'm not sure what to do from here ?  are there commands i do to make irexec control ALSA,  what would thry be ?

THanks

---

### Post by Xcerca on 2008-09-21
alright so i got some help from the channel on this one  do this for you're /home/~/.lircrc
add lines like this, then just use irexec to run the amixer commands, and start irexec -d on start

begin
    remote = Creative_RM-1500
    prog = irexec
    button = Vol_Up
    config = amixer sset Master,0 5%+
    repeat = 0
    delay = 0
end
begin
    remote = Creative_RM-1500
    prog = irexec
    button = Vol_Down
    config = amixer sset Master,0 5%-
    repeat = 0
    delay = 0
end


works for me

---

### Post by MeduZa on 2010-09-21
I got my creative SB audigy 4 with the RM 1500, It work out of the box but, there is no volumen control, in other words keys do nothing, only on vlc works.

now, whit this help my volume control works (no screen indicator but the volumen move up and down) 

Now I have and Idea how to use it with other programs.

thanks

---

