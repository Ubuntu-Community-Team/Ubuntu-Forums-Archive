---
title: "Failed to find Bluetooth netlink family"
date: 2011-04-17
forum: Hardware
---

### Post by ignacio69 on 2011-04-17
Dear all,
In my PC I have 2 hard disk. In one I have Ubuntu 10.04 and in the other Ubuntu 10.10.
I have a bluetooth adapter ID 0a12:0001 Cambridge Silicon Radio in one USB port.
When I am looged in Ubuntu 10.10 it works perfectly. The adapter pairs and connects to my Headset headseat NOKIA BH-104 and I can listen rythmobx from a diiferent room.

When I logg in Ubuntu 10.04 the bluetooth adapter ID 0a12:0001 Cambridge Silicon Radio is recognized but it is not able to pair to my NOKIA BH-104.

Last night I upgrade my Ubuntu 10.04 to Ubuntu 10.19 with the hope that the  bluetooth adapter ID 0a12:0001 Cambridge Silicon Radio will work well,

However is not pairing.

My question is: if I go to the configuration file of the Ubuntu 10.10 that is nor working correctly and replace it by the other configuration file that is working, would it work?

the second question is how to do this?

The third question where is the configuration file?

I believe that the configuration file is somewhere in /etc/bluetooth/... but which of them is it the correct:?
audio.conf  input.conf	main.conf  network.conf  rfcomm.conf  serial.conf

thank you  in advance for your help

---

### Post by ignacio69 on 2011-04-19
I did this following the instuctions in this howto:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

sudo cp /etc/default/bluetooth.dpkg-bak /etc/default/bluetooth

sudo nano /etc/default/bluetooth

Locate line:

HIDD_ENABLED=0

Change it to:

HIDD_ENABLED=1

Look in the same file for a line close to:

HIDD_OPTIONS="--master --server"

{i} Leave the "--master" command or remove it, it depends on the device. If you have problems with "--master", remove it or vice versa.

Add additional "--connect" arguments for the device you want to connect to at startup:

HIDD_OPTIONS="--connect aa:bb:cc:dd:ee:ff --connect aa:bb:cc:dd:ee:ff --connect aa:bb:cc:dd:ee:ff --server"
I substitute the aa:bb:cc:dd:ee:ff by 00:15:83:3D:0A:57
Save and add HIDP to /etc/modules:

echo hidp | sudo tee -a /etc/modules

Your Bluetooth devices should now connect at startup.

19/04/2011
dmesaage:
20.416340] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 19 21:20:42 ignacio-desktop kernel: [   20.416343] Bluetooth: BNEP filters: protocol multicast
Apr 19 21:20:42 ignacio-desktop kernel: [   20.420781] Bluetooth: SCO (Voice Link) ver 0.6
Apr 19 21:20:42 ignacio-desktop kernel: [   20.420784] Bluetooth: SCO socket layer initialized
Apr 19 21:20:42 ignacio-desktop kernel: [   20.670779] Bluetooth: RFCOMM TTY layer initialized
Apr 19 21:20:42 ignacio-desktop kernel: [   20.670785] Bluetooth: RFCOMM socket layer initialized
Apr 19 21:20:42 ignacio-desktop kernel: [   20.670787] Bluetooth: RFCOMM ver 1.11
syslog:
Apr 19 21:26:31 ignacio-desktop bluetoothd[1232]: link_key_request (sba=00:15:83:3D:0A:57, dba=00:1C:EF:E1:B2:A9)
Apr 19 21:26:31 ignacio-desktop bluetoothd[1232]: Connection refused (111)
daemonlog:
Apr 19 21:26:31 ignacio-desktop bluetoothd[1232]: link_key_request (sba=00:15:83:3D:0A:57, dba=00:1C:EF:E1:B2:A9)
Apr 19 21:26:31 ignacio-desktop bluetoothd[1232]: Connection refused (111)

can anyone help me?

---

### Post by ignacio69 on 2011-04-27
dear all,
trying to follwo the instructions in ubuntu help:[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)
ignacio@ignacio-desktop:~$ dmesg | grep "Blue*"
[   18.456193] Bluetooth: Core ver 2.15
[   18.456238] Bluetooth: HCI device and connection manager initialized
[   18.456240] Bluetooth: HCI socket layer initialized
[   18.521890] Bluetooth: L2CAP ver 2.14
[   18.521894] Bluetooth: L2CAP socket layer initialized
[   18.545131] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
ignacio@ignacio-desktop:~$ hcitool scan
Device is not available: No such device
ignacio@ignacio-desktop:~$ hcitool scan
Device is not available: No such device
ignacio@ignacio-desktop:~$ hcitool scan
Scanning ...
	00:1C:EF:E1:B2:A9	Nokia BH-104
ignacio@ignacio-desktop:~$ sudo gedit ~/.asoundrc
[sudo] password for ignacio: 
ignacio@ignacio-desktop:~$ sudo hciconfig hci0 voice 0x0060
ignacio@ignacio-desktop:~$ pactl load-module module-alsa-sink device=btheadset
Falla: Falló la inicialización del módulo
ignacio@ignacio-desktop:~$ dmesg | grep "Blue*"
[   18.456193] Bluetooth: Core ver 2.15
[   18.456238] Bluetooth: HCI device and connection manager initialized
[   18.456240] Bluetooth: HCI socket layer initialized
[   18.521890] Bluetooth: L2CAP ver 2.14
[   18.521894] Bluetooth: L2CAP socket layer initialized
[   18.545131] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  198.538824] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  198.835115] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  198.835123] Bluetooth: BNEP filters: protocol multicast
[  198.931042] Bluetooth: SCO (Voice Link) ver 0.6
[  198.931049] Bluetooth: SCO socket layer initialized
[  199.203860] Bluetooth: RFCOMM TTY layer initialized
[  199.203872] Bluetooth: RFCOMM socket layer initialized
[  199.203877] Bluetooth: RFCOMM ver 1.11
ignacio@ignacio-desktop:~$ pactl load-module module-alsa-sink device=btheadset
Falla: Falló la inicialización del módulo
ignacio@ignacio-desktop:~$ pactl load-module module-alsa-source device=btheadset
Falla: Falló la inicialización del módulo
ignacio@ignacio-desktop:~$ aplay -D btheadset -f s16_le /usr/share/sounds/ubuntu/stereo/dialog-question.wav
/usr/share/sounds/ubuntu/stereo/dialog-question.wav: No existe el fichero o el directorio
ignacio@ignacio-desktop:~$ aplay -D btheadset -f s16_le /usr/share/sounds/alsa/Front_Center.wav
Sonando WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Ratio 48000 Hz, Mono
Advertencia: tasa inexacta (solicitada = 48000Hz, conseguida = 8000Hz)
         por favor, intente conectar el plugin (-Dplug:btheadset)
ALSA lib audio/pcm_bluetooth.c:1607:(audioservice_expect) BT_START_STREAM failed : Conseguido(0)
ALSA lib audio/pcm_bluetooth.c:1566:(audioservice_recv) Too short (1 bytes) IPC packet from bluetoothd
aplay: set_params:1116: Imposible instalar los parámetros de hw:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: 125000
PERIOD_SIZE: 1000
PERIOD_BYTES: 2000
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 4000
BUFFER_BYTES: 8000
TICK_TIME: [0 0]
ignacio@ignacio-desktop:~$ dmesg | grep "Blue*"[   18.456193] Bluetooth: Core ver 2.15
[   18.456238] Bluetooth: HCI device and connection manager initialized
[   18.456240] Bluetooth: HCI socket layer initialized
[   18.521890] Bluetooth: L2CAP ver 2.14
[   18.521894] Bluetooth: L2CAP socket layer initialized
[   18.545131] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  198.538824] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  198.835115] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  198.835123] Bluetooth: BNEP filters: protocol multicast
[  198.931042] Bluetooth: SCO (Voice Link) ver 0.6
[  198.931049] Bluetooth: SCO socket layer initialized
[  199.203860] Bluetooth: RFCOMM TTY layer initialized
[  199.203872] Bluetooth: RFCOMM socket layer initialized
[  199.203877] Bluetooth: RFCOMM ver 1.11
ignacio@ignacio-desktop:~$ 



I can compare with the output of dmesg of the other adapter working under Ubuntu 10.10:
Apr 17 23:13:10 ignacio-desktop kernel: [   23.697298] Bluetooth: L2CAP ver 2.14
Apr 17 23:13:10 ignacio-desktop kernel: [   23.697302] Bluetooth: L2CAP socket layer initialized
Apr 17 23:13:10 ignacio-desktop kernel: [   23.834858] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
Apr 17 23:13:10 ignacio-desktop kernel: [   23.835112] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
Apr 17 23:13:10 ignacio-desktop kernel: [   24.006919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 17 23:13:10 ignacio-desktop kernel: [   24.006922] Bluetooth: BNEP filters: protocol multicast
Apr 17 23:13:11 ignacio-desktop kernel: [   24.410354] Bluetooth: SCO (Voice Link) ver 0.6
Apr 17 23:13:11 ignacio-desktop kernel: [   24.410357] Bluetooth: SCO socket layer initialized
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138501] Bluetooth: RFCOMM TTY layer initialized
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138510] Bluetooth: RFCOMM socket layer initialized
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138512] Bluetooth: RFCOMM ver 1.11
Apr 17 23:13:25 ignacio-desktop pulseaudio[1448]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-ZznGwB4C02: Conexión rehusada
syslog:
Apr 17 23:13:10 ignacio-desktop kernel: [   23.697298] Bluetooth: L2CAP ver 2.14
Apr 17 23:13:10 ignacio-desktop kernel: [   23.697302] Bluetooth: L2CAP socket layer initialized
Apr 17 23:13:10 ignacio-desktop bluetoothd[1161]: Starting experimental netlink support
Apr 17 23:13:10 ignacio-desktop bluetoothd[1161]: Failed to find Bluetooth netlink family
Apr 17 23:13:10 ignacio-desktop bluetoothd[1161]: Failed to init netlink plugin
Apr 17 23:13:10 ignacio-desktop kernel: [   23.834858] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
Apr 17 23:13:10 ignacio-desktop kernel: [   23.835112] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
Apr 17 23:13:10 ignacio-desktop kernel: [   24.006919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 17 23:13:10 ignacio-desktop kernel: [   24.006922] Bluetooth: BNEP filters: protocol multicast
Apr 17 23:13:11 ignacio-desktop bluetoothd[1161]: HCI dev 0 registered
Apr 17 23:13:11 ignacio-desktop kernel: [   24.410354] Bluetooth: SCO (Voice Link) ver 0.6
Apr 17 23:13:11 ignacio-desktop kernel: [   24.410357] Bluetooth: SCO socket layer initialized
Apr 17 23:13:11 ignacio-desktop bluetoothd[1161]: HCI dev 0 up
Apr 17 23:13:11 ignacio-desktop bluetoothd[1161]: Starting security manager 0
Apr 17 23:13:12 ignacio-desktop bluetoothd[1161]: ioctl(HCIUNBLOCKADDR): Invalid argument (22)
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138501] Bluetooth: RFCOMM TTY layer initialized
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138510] Bluetooth: RFCOMM socket layer initialized
Apr 17 23:13:12 ignacio-desktop kernel: [   25.138512] Bluetooth: RFCOMM ver 1.11
Apr 17 23:13:12 ignacio-desktop bluetoothd[1161]: Adapter /org/bluez/1160/hci0 has been enabled

can anybody tell me what else to set correctly in order to make it work under 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux?

---

### Post by surferX on 2011-05-17
My guess is that you have already paired the device once with something else, perhaps a phone and it wont show up in ubuntu. Delete the pairing by holding the power key and answer key together for 5 seconds and then try and pair it with the pc.

Hope that helps

---

### Post by ignacio69 on 2011-05-25
Dear Surferx,
you were right I delete the device
I searched for the device again
and now they are paired again
however there is a known bug with the last version of gnome-bluetooth that does not allow my device to be set as output.
thank you anyway.

---

