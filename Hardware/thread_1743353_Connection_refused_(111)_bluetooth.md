---
title: "Connection refused (111) bluetooth"
date: 2011-04-29
forum: Hardware
---

### Post by ignacio69 on 2011-04-29
Dear all,
I have two hard disks in my computer and 2 ubuntus.
First hard disk main 165 GB has ubuntu 11.04
Second hard disk 80 GB has ubuntu 10.10
+ and one adapter dongle ID 0a12:0001 Cambridge Silicon Radio. specification V.2.0 Compliant.
I want to use my adapter to connect to bluetooth headset Nokia BH-104 which I want to be the output of my computer sound

In First hard disk 165 GB gnome-bluetooth start when logging on and recognizes my bluetooth headset and when trying to connect says: "Connection refused (111)"
```
bluetoothd[1312]: link_key_request (sba=00:15:83:3D:0A:57, dba=00:1C:EF:E1:B2:A9)
bluetoothd[1312]: Connection refused (111)
```

In Second hard disk 80 GB gnome-bluetooth start when loggin on recognizes my bluetooth headset and when trying to connect says: 
```
bluetoothd[1161]: HCI dev 0 up
 bluetoothd[1161]: Starting security manager 0
bluetoothd[1161]: ioctl(HCIUNBLOCKADDR): Invalid argument (22)
[   25.138501] Bluetooth: RFCOMM TTY layer initialized
[   25.138510] Bluetooth: RFCOMM socket layer initialized
[   25.138512] Bluetooth: RFCOMM ver 1.11
bluetoothd[1161]: Adapter /org/bluez/1160/hci0 has been enabled
```

I have tried the instructions in [http://help.ubuntu.com/community/BluetoothHeadset](http://help.ubuntu.com/community/BluetoothHeadset)

with this result and no success:
```
~$ pactl load-module module-alsa-sink device=btheadset
Falla: Falló la inicialización del módulo
~$ pactl load-module module-alsa-source device=btheadset
Falla: Falló la inicialización del módulo
~$ aplay -D btheadset -f s16_le /usr/share/sounds/ubuntu/stereo/dialog-question.wav
/usr/share/sounds/ubuntu/stereo/dialog-question.wav: No existe el fichero o el directorio
~$ aplay -D btheadset -f s16_le /usr/share/sounds/alsa/Front_Center.wav
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
```
My question is what output should give it to you so you can help me to make my bluetooth connect to my headset.

---

