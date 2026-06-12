---
title: "Asus P7131 Hybrid Remote Control Setup"
date: 2012-01-06
forum: Hardware
---

### Post by hopelessone on 2012-01-06
Hi,

[[IMG]http://img862.imageshack.us/img862/8639/remotep.th.jpg[/IMG]](http://imageshack.us/photo/my-images/862/remotep.jpg/)

This guide is for the Asus P7131 Hybrid TV Card on Ubuntu 11.10 for XBMC

1. Put TV card into computer
2. install firmware:
```
sudo apt-get install linux-firmware-nonfree
```
3. If you cant get all the buttons working do this:
```
sudo apt-get install ir-keytable
``` 
4. ```
sudo ir-keytable
```
> Found /sys/class/rc/rc0/ (/dev/input/event2) with:
	Driver saa7134, table rc-asus-pc39
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Repeat delay = 500 ms, repeat period = 125 ms
5. ```
sudo cp /lib/udev/rc_keymaps/asus_pc39 /etc/rc_keymaps/
```
6. Edit the file:
```
sudo gedit /etc/rc_keymaps/asus_pc39
```
> ==> asus_pc39 <==
# table asus_pc39, type: RC5
0x082a KEY_0
0x0816 KEY_1
0x0812 KEY_2
0x0814 KEY_3
0x0836 KEY_4
0x0832 KEY_5
0x0834 KEY_6
0x080e KEY_7
0x080a KEY_8
0x080c KEY_9
0x0801 KEY_RADIO
0x083c KEY_MENU
0x0815 KEY_VOLUMEUP
0x0826 KEY_VOLUMEDOWN
0x0808 KEY_UP
0x0804 KEY_DOWN
0x0818 KEY_LEFT
0x0810 KEY_RIGHT
0x081a KEY_PAUSE
0x0806 KEY_BLUE
0x081e KEY_TV
0x0822 KEY_BACK
0x0835 KEY_CHANNELUP
0x0824 KEY_CHANNELDOWN
0x0825 KEY_ENTER
0x0839 KEY_PLAY
0x0821 KEY_PREVIOUS
0x0819 KEY_NEXT
0x0831 KEY_REWIND
0x0805 KEY_FASTFORWARD
0x0809 KEY_STOP
0x0811 KEY_RECORD
0x0829 KEY_POWER
0x082e KEY_ZOOM
0x082c KEY_MACRO
0x081c KEY_HOME
0x083a KEY_PVR
0x0802 KEY_MUTE
0x083e KEY_DVD
0X0803 KEY_TEXT
0X080b KEY_RED
0X080d KEY_YELLOW
0X0807 KEY_GREEN
0X0820 KEY_AUDIO
0X0837 KEY_SCREEN
extra buttons can be configured from:
[http://xbmc.exstatic.org/ir_keys.txt](http://xbmc.exstatic.org/ir_keys.txt)
Edit Lircmap.xml if you change any under <altname>devinput</altname>
```
sudo gedit /usr/share/xbmc/system/Lircmap.xml

```7. Test it: 
```
sudo ir-keytable -c
sudo /usr/bin/ir-keytable -p NEC,RC5 -w /etc/rc_keymaps/asus_pc39
sudo ir-keytable -t
```
8. Now you can install LIRC, (Select none,none) 
9. Edit /etc/lirc/hardware.conf so that it looks like:
```
sudo gedit /etc/lirc/hardware.conf
```
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Asus MyCinema P7131"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="saa7134*"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="asus/mycinema.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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
10. Edit /etc/lirc/lircd.conf so that it looks like this:
```
sudo gedit /etc/lirc/lircd.conf
```
> include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"

11. edit the /etc/init.d/lirc so lircd always connects to the right device even if its device number changes after reboot.
```
sudo gedit /etc/init.d/lirc
```
Find the part and change in red:
> #If we have a REMOTE_DEVICE or REMOTE_DRIVER defined (either because no devices
#were defined, OR if we explicitly did), then populate REMOTE_ARGS
if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
if [ -n "$REMOTE_DEVICE" ] && [ "$REMOTE_DEVICE" != "none" ]; then
**[COLOR="Red"]REMOTE_ARGS="--device=name=$REMOTE_DEVICE $REMOTE_ARGS"[/COLOR]**
12. Fire up lirc. 
```
sudo /etc/init.d/lirc start
```
13. Now when you run irw
> blade@oneiric:~$ irw
000000008001018e 00 KEY_RED devinput
0000000080010190 00 KEY_YELLOW devinput
0000000080010191 00 KEY_BLUE devinput
000000008001018f 00 KEY_GREEN devinput


And every things fine..

Credit:
[http://forum.xbmc.org/showthread.php?t=101151](http://forum.xbmc.org/showthread.php?t=101151)
[http://deneb.homedns.org/things/?p=81&replytocom=24](http://deneb.homedns.org/things/?p=81&replytocom=24)

---

