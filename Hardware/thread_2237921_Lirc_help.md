---
title: "Lirc help"
date: 2014-08-04
forum: Hardware
---

### Post by P_R on 2014-08-04
Hello, 
 I have spent past few days setting up lirc on my computer. I have Avermedia Volar HD nano tuner with remote control. I was keeping step by step next to this video [https://www.youtube.com/watch?v=lsl63mHlcRo](https://www.youtube.com/watch?v=lsl63mHlcRo). Everything worked, also irrecord. But when the video ended I wanted tor try it with irw command, but it didn't worked. 
I also tried this command:
root@5OPC2L:/usr/share/lirc/remotes# lircd -n /etc/lirc/hardware.conf
 lircd-0.9.0[20562]: error in configfile line 3
lircd-0.9.0[20562]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.9.0[20562]: reading of config file failed
lircd-0.9.0[20562]: lircd(default) ready, using /var/run/lirc/lircd
My hardware.conf looks like this:
REMOTE="AverMedia TV card (VDOMATE) (use card=1 3)"
#REMOTE_DRIVER="devinput"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_SOCKET=""
#REMOTE_LIRCD_CONF=""
#REMOTE_LIRCD_ARGS=""
#TRANSMITTER="Custom"
TRANSMITTER_MODULES="None"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
#START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION=""
#REMOTE_LIRCD_CONF="avermedia/lircd.conf.vdomate"
#REMOTE_LIRCD_ARGS=""
#TRANSMITTER="None"

I have also tried to cat /dev/input/event7 , while pressing numbers 1 to 9 each once on RC:(hexadecimal)
0000000    cf7f    53df    0000    0000    ffc9    0008    0000    0000
0000010    0004    0004    0401    800f    cf7f    53df    0000    0000
0000020    ffc9    0008    0000    0000    0000    0000    0000    0000
0000030    cf81    53df    0000    0000    ffc2    0008    0000    0000
0000040    0004    0004    0402    800f    cf81    53df    0000    0000
0000050    ffc2    0008    0000    0000    0000    0000    0000    0000
0000060    cf82    53df    0000    0000    5dd8    0001    0000    0000
0000070    0004    0004    0403    800f    cf82    53df    0000    0000
0000080    5dd8    0001    0000    0000    0000    0000    0000    0000
0000090    cf83    53df    0000    0000    5ece    0001    0000    0000
00000a0    0004    0004    0404    800f    cf83    53df    0000    0000
00000b0    5ece    0001    0000    0000    0000    0000    0000    0000
00000c0    cf83    53df    0000    0000    ffd9    0008    0000    0000
00000d0    0004    0004    0405    800f    cf83    53df    0000    0000
00000e0    ffd9    0008    0000    0000    0000    0000    0000    0000
00000f0    cf84    53df    0000    0000    5eaa    0001    0000    0000
0000100    0004    0004    0406    800f    cf84    53df    0000    0000
0000110    5eaa    0001    0000    0000    0000    0000    0000    0000
0000120    cf84    53df    0000    0000    ffc5    0008    0000    0000
0000130    0004    0004    0407    800f    cf84    53df    0000    0000
0000140    ffc5    0008    0000    0000    0000    0000    0000    0000
0000150    cf85    53df    0000    0000    5ea8    0001    0000    0000
0000160    0004    0004    0408    800f    cf85    53df    0000    0000
0000170    5ea8    0001    0000    0000    0000    0000    0000    0000
0000180    cf86    53df    0000    0000    5ec9    0001    0000    0000
0000190    0004    0004    0409    800f    cf86    53df    0000    0000
00001a0    5ec9    0001    0000    0000    0000    0000    0000    0000
00001b0
Can you guys help me please?
Thanks

---

