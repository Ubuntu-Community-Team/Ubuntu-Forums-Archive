---
title: "Bluetooth dongle doesn't work/causes system crashes"
date: 2011-11-23
forum: Hardware
---

### Post by razor7 on 2011-11-23
Hi, i have a USB mini dongle (On chip data ASC AS3620QA C0928CAT). It seem to be Cambridge Silicon Radio (CSR) device.

Im using Ubuntu 11.10 x64

lsusb
> Bus 006 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


The problem is i can not pair my Motorola S10-HD headset (the only bluetooth thing i have)

Simptoms:
[LIST]
[*]Plug USB
[*]Set bluetooth to "Visible"
[*]Click on "Config new device"
[*]Most of the tryes, my headset is not even listed.
[*]When listed, can not pair it
[*]If i have enough luck (20 to 30 tryes), can pair it, but after selecting it as output device in sound settings, no sound at all
[*]When performing any of the above steps, many times Ubuntu just freezes and I have to push the reset burrin os the CPU
[/LIST]

Trying **sudo hciconfig hci0 up** most of the time i get:
> Can't init device hci0: Connection timed out (110)

Thanks lot in advise!

---

### Post by Dr.Faisal on 2011-12-02
Same here any luck ??

---

### Post by razor7 on 2011-12-05
Hi, changed my bluetooth dongle.

Now i get this on pairing

> 
Dec  5 14:55:20 internet bluetoothd[1162]: Stopping discovery
Dec  5 14:55:29 internet bluetoothd[1162]: Badly formated or unrecognized command: AT+CSRSF=0,0,0,0,0,7
Dec  5 14:55:30 internet kernel: [ 2583.244148] input: 00:0D:FD:3F:F5:63 as /devices/virtual/input/input9
Dec  5 14:55:30 internet kernel: [ 2583.244148] input: 00:0D:FD:3F:F5:63 as /devices/virtual/input/input9
Dec  5 17:55:30 internet rtkit-daemon[2301]: Successfully made thread 18110 of process 8197 (n/a) owned by '1000' RT at priority 5.
Dec  5 17:55:30 internet rtkit-daemon[2301]: Supervising 5 threads of 1 processes of 1 users.
Dec  5 14:55:36 internet bluetoothd[1162]: Audio connection got disconnected


And this when trying to enable A2DP from sound config "hardware" tab
> 
Dec  5 18:04:08 internet rtkit-daemon[2301]: Successfully made thread 24786 of process 22977 (n/a) owned by '1000' RT at priority 5.
Dec  5 18:04:08 internet rtkit-daemon[2301]: Supervising 5 threads of 1 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[22977]: [bluetooth] sink.c: Assertion 'pa_frame_aligned(length, &s->sample_spec)' failed at pulsecore/sink.c:1251, function pa_sink_render_full(). Aborting.
Dec  5 15:04:09 internet pulseaudio[24787]: [pulseaudio] main.c: User-configured server at {b54f3777d763aef3b7c2bf3100000009}unix:/home/martin/.pulse/b54f3777d763aef3b7c2bf3100000009-runtime/native, which appears to be local. Probing deeper.
Dec  5 15:04:09 internet pulseaudio[24788]: [pulseaudio] main.c: User-configured server at {b54f3777d763aef3b7c2bf3100000009}unix:/home/martin/.pulse/b54f3777d763aef3b7c2bf3100000009-runtime/native, which appears to be local. Probing deeper.
Dec  5 15:04:09 internet pulseaudio[24789]: [pulseaudio] main.c: User-configured server at {b54f3777d763aef3b7c2bf3100000009}unix:/home/martin/.pulse/b54f3777d763aef3b7c2bf3100000009-runtime/native, which appears to be local. Probing deeper.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24792 of process 24792 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 1 threads of 1 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[24792]: [pulseaudio] pid.c: Stale PID file, overwriting.
Dec  5 15:04:09 internet pulseaudio[24798]: [pulseaudio] main.c: User-configured server at {b54f3777d763aef3b7c2bf3100000009}unix:/home/martin/.pulse/b54f3777d763aef3b7c2bf3100000009-runtime/native, which appears to be local. Probing deeper.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24800 of process 24792 (n/a) owned by '1000' RT at priority 5.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 2 threads of 1 processes of 1 users.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24801 of process 24792 (n/a) owned by '1000' RT at priority 5.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 3 threads of 1 processes of 1 users.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24802 of process 24792 (n/a) owned by '1000' RT at priority 5.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 4 threads of 1 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[24792]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Dec  5 15:04:09  pulseaudio[24792]: last message repeated 2 times
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24803 of process 24792 (n/a) owned by '1000' RT at priority 5.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 5 threads of 1 processes of 1 users.
Dec  5 15:04:09 internet kernel: [ 3101.218058] hci_scodata_packet: hci0 SCO packet for unknown connection handle 41
Dec  5 15:04:09 internet kernel: [ 3101.218068] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218074] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218080] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218086] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218092] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228074] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228081] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228085] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228089] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228093] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228097] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228101] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228104] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228108] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228112] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228116] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228119] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228123] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228127] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228131] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228134] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228138] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228142] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228145] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228149] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228153] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228157] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228161] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228165] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228168] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228172] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228176] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228180] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228184] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228188] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228191] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228195] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228199] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228203] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228207] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228210] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228214] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228218] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228222] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228225] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228229] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228233] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228237] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228241] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228244] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228248] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228252] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228256] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228260] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228263] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228267] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228271] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228274] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228278] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228282] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228286] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228289] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238031] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.238040] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.238046] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238052] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238057] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238061] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238066] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238071] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238077] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238082] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238087] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238092] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238097] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238102] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238108] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238113] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238119] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238125] hci_scodata_packet: hci0 SCO packet for unknown connection handle 5
Dec  5 15:04:09 internet kernel: [ 3101.238131] hci_scodata_packet: hci0 SCO packet for unknown connection handle 2
Dec  5 15:04:09 internet kernel: [ 3101.238137] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238142] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238148] hci_scodata_packet: hci0 SCO packet for unknown connection handle 256
Dec  5 15:04:09 internet kernel: [ 3101.238154] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238159] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238165] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238171] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238177] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238183] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238187] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24806 of process 24806 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 6 threads of 2 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[24806]: [pulseaudio] pid.c: Daemon already running.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24808 of process 24808 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 6 threads of 2 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[24808]: [pulseaudio] pid.c: Daemon already running.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Successfully made thread 24810 of process 24810 (n/a) owned by '1000' high priority at nice level -11.
Dec  5 18:04:09 internet rtkit-daemon[2301]: Supervising 6 threads of 2 processes of 1 users.
Dec  5 15:04:09 internet pulseaudio[24810]: [pulseaudio] pid.c: Daemon already running.
Dec  5 15:04:09 internet kernel: [ 3101.218058] hci_scodata_packet: hci0 SCO packet for unknown connection handle 41
Dec  5 15:04:09 internet kernel: [ 3101.218068] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218074] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218080] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218086] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.218092] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228074] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228081] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228085] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228089] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228093] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228097] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228101] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228104] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228108] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228112] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228116] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228119] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228123] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228127] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228131] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228134] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228138] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228142] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228145] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228149] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228153] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228157] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228161] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228165] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228168] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228172] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228176] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228180] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228184] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228188] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228191] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228195] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228199] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228203] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228207] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228210] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228214] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228218] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228222] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228225] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228229] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.228233] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.228237] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228241] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228244] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228248] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228252] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228256] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228260] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228263] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228267] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228271] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228274] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228278] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228282] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228286] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.228289] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238031] hci_scodata_packet: hci0 SCO packet for unknown connection handle 10752
Dec  5 15:04:09 internet kernel: [ 3101.238040] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48
Dec  5 15:04:09 internet kernel: [ 3101.238046] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238052] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238057] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238061] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238066] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238071] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238077] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238082] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238087] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238092] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238097] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238102] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238108] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238113] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238119] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238125] hci_scodata_packet: hci0 SCO packet for unknown connection handle 5
Dec  5 15:04:09 internet kernel: [ 3101.238131] hci_scodata_packet: hci0 SCO packet for unknown connection handle 2
Dec  5 15:04:09 internet kernel: [ 3101.238137] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Dec  5 15:04:09 internet kernel: [ 3101.238142] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238148] hci_scodata_packet: hci0 SCO packet for unknown connection handle 256
Dec  5 15:04:09 internet kernel: [ 3101.238154] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238159] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238165] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238171] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238177] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238183] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1
Dec  5 15:04:09 internet kernel: [ 3101.238187] hci_scodata_packet: hci0 SCO packet for unknown connection handle 1



Please have in mind that Mono telephony is working, so i can hear mono audio, but A2DP doesn' work at all!

Please advise!

---

### Post by razor7 on 2011-12-05
Well, every time i try to enable A2DP i get this error (among others)
> 
[pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod


---

### Post by razor7 on 2011-12-05
Well, seems that pulseaudio really screwed it up!, but thanks to fedora fellows i have mi headset A2DP working as Ubuntu should make it work!

[http://forums.fedoraforum.org/showpost.php?p=1022695&postcount=1](http://forums.fedoraforum.org/showpost.php?p=1022695&postcount=1)

Ubuntu guys...remember, next release is LTS...how can a fedora forum post of 2008 fix this simple problem?

Best regards!

---

