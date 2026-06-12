---
title: "Sony VAIO VPCS136FG Brightness Problem"
date: 2013-10-02
forum: Hardware
---

### Post by XinOxaR on 2013-10-02
I have a sony vaio vpcs136fg laptop. what ever i've done, i was not able to change my laptop brightness. even setpci do not change the laptop brightness. the graphic card is NVIDIA GT218M [GeForce 310M] (rev a2) and it's pci configuration space dump is listed below:

Notes: 
1. the brightness is locked @ maximum. 
2. changing /sys/class/acpi_video0/brightness does not affect the brightness
3. using xbacklight does not change the brightness
4. passing kernel parameters does not change brightness

Probable problem:
Lately before I install Linux, I was using windows 7 with sony care center application on it. sony care center has an option called Auto Brightness. as long as that option was turned on, windows could not change the brightness and everything controlled under that option. When I installed linux, that option was enabled in windows. It might cause of the mess here. I don't want to change the OS to try if it is the problem or not (cause I repartitioned my hard drive and I really don't want to see that Microsoft Logo again)

Note:
I tried vaio forums but there was no answer.
I tried GeForce forum, but there was no answer.

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2)

00: de 10 75 0a 07 00 10 00 a2 00 00 03 00 00 80 00
10: 00 00 00 d2 0c 00 00 c0 00 00 00 00 0c 00 00 d0
20: 00 00 00 00 01 70 00 00 00 00 00 00 4d 10 69 90
30: 00 00 00 00 60 00 00 00 00 00 00 00 07 01 00 00
40: 4d 10 69 90 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 03 00 08 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 b4 02 00 e0 8d 2c 01
80: 10 29 00 00 02 2d 05 00 4b 01 11 10 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 10 00 00 00
a0: 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00
b0: 00 00 00 00 09 00 14 01 00 00 00 00 00 0c 03 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
100: 02 00 81 12 00 00 00 00 00 00 00 00 00 00 00 00
110: 00 00 00 00 01 00 00 80 00 00 00 00 00 00 00 00
120: 00 00 00 00 00 00 00 00 04 00 01 60 00 00 00 00
130: 21 81 07 00 00 00 00 00 00 00 00 20 00 00 ff 33
140: 10 10 00 08 10 00 00 00 ff ff ff ff 1b 00 00 8b
150: 15 fe 00 e0 20 71 00 00 02 0f 00 00 21 81 07 00
160: 21 81 05 00 02 80 03 00 02 80 01 00 06 80 1f 00
170: 06 80 1d 00 00 00 00 00 00 00 00 00 00 00 00 00
180: 00 00 00 00 00 00 00 00 f7 17 45 01 03 00 00 e0
190: 10 10 10 10 00 00 00 00 00 00 00 00 00 00 00 00
1a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1c0: 00 00 00 00 00 00 00 00 e0 be ad de 00 00 00 00
1d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1e0: 74 00 00 00 74 00 00 00 74 00 00 00 00 00 00 00
1f0: 74 00 e0 01 00 00 00 00 00 00 00 00 00 00 00 00
200: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
210: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
220: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
230: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
240: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
250: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
260: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
270: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
280: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
290: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
2f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
300: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
310: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
320: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
330: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
340: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
350: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
360: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
370: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
380: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
390: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
3f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
400: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
410: 00 00 00 00 00 00 00 00 00 00 0e 00 03 84 b6 00
420: 00 00 00 60 00 00 00 00 00 00 00 00 11 20 06 00
430: 00 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00
440: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
450: 00 00 00 00 00 00 00 00 0f 13 28 00 00 00 80 80
460: 20 12 6c b0 c4 09 40 06 00 00 00 00 00 00 00 00
470: 00 00 00 00 69 05 69 05 8f 00 f2 06 15 ad 08 00
480: 00 00 00 00 03 00 00 00 96 05 00 02 8c 00 18 01
490: 70 00 f0 00 d4 a0 b8 06 83 6a df 07 52 17 45 01
4a0: d3 e6 44 01 52 17 45 01 ab 00 00 00 00 00 00 00
4b0: 00 00 00 00 a9 00 00 00 00 00 00 00 00 00 00 00
4c0: 03 03 18 00 01 08 00 00 03 00 00 00 1e 1e a8 00
4d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
4e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
4f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
500: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
510: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
520: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
530: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
540: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
550: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
560: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
570: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
580: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
590: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
5f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
600: 0b 00 01 00 01 00 41 02 02 00 41 01 05 08 00 00
610: 05 00 00 00 01 00 01 00 01 00 00 00 00 00 00 00
620: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
630: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
640: 00 00 00 00 8e 08 3a 04 00 10 00 32 01 15 00 00
650: 90 7e 00 00 3c 00 00 00 0c 00 00 00 00 00 00 00
660: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
670: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
680: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
690: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
6f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
700: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
710: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
720: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
730: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
740: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
750: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
760: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
770: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
780: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
790: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
7f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
800: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
810: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
820: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
830: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
840: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
850: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
860: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
870: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
880: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
890: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
8f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
900: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
910: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
920: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
930: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
940: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
950: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
960: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
970: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
980: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
990: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
9f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
aa0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ab0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ac0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ad0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ae0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
af0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ba0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
bb0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
bc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
bd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
be0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
bf0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ca0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
cb0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
cc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
cd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ce0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
cf0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
da0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
db0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
dc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
dd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
de0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
df0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ea0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
eb0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ec0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ed0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ee0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ef0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
fa0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
fb0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
fc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
fd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
fe0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
ff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

```

thanx in advance
XinOxaR

---

### Post by Toz on 2013-10-02
Hello and welcome to the forums.

Some questions, comments and suggestions:

1. Are you using the opensource nouveau driver or the proprietary nvidia driver?
```
lspci -k | grep -A3 VGA
```
2. How many backlight interfaces do you have? Is it just acpi_video0 or are there other directories at the /sys/class/backlight level?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
3. Which kernel parameters have you tried? And how has each parameter changed the number and type of backlight interfaces available? And are you able to manually echo values into the brightness file of each backlight interface and affect screen brightness?

4. Have you tried the **acpi_osi=\"!Windows 2012\"** kernel parameter?  The relevant lines in /etc/default/grub should look like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
5. Have you tried the ["EnableBrightnessControl=1"]("http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver") xorg setting? This settings seems to help some nvidia cards.

6. Which modules are running (that may be interfering with brightness):
```
lsmod
```
7. Have you had a look at the [nvidiabl]("https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h") module? Looks like the VPCS1* is [supported]("https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h").

Sorry for the laundry list. Let me know if you need more information about any of the points.

---

### Post by XinOxaR on 2013-10-02
> **Toz said:**
> Hello and welcome to the forums.

Thank you



> **Toz said:**
> 1. Are you using the opensource nouveau driver or the proprietary nvidia driver?
```
lspci -k | grep -A3 VGA
```


I'm using nvidia proprietary driver

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2)
    Subsystem: Sony Corporation Device 9069
    Kernel driver in use: nvidia
    Kernel modules: nouveau, nvidia



```


> **Toz said:**
> 2. How many backlight interfaces do you have? Is it just acpi_video0 or are there other directories at the /sys/class/backlight level?


I guess it's just one interface

```

#for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
7
7
8



```


> **Toz said:**
> 
3. Which kernel parameters have you tried? And how has each parameter changed the number and type of backlight interfaces available? And are you able to manually echo values into the brightness file of each backlight interface and affect screen brightness?


I have tried:

1. acpi_osi=Linux acpi_backlight=vendor
Result: the gnome back-light indicator won't appear at all

2. acpi_osi=Linux acpi_backlight=legacy
Result: nothing changes


> **Toz said:**
> 
4. Have you tried the **acpi_osi=\"!Windows 2012\"** kernel parameter? The relevant lines in /etc/default/grub should look like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```


No, I did not tried that one. My boot loader is syslinux. I will try it as soon as "badblocks" finished checking my external H.D.D


> **Toz said:**
> 
5. Have you tried the ["EnableBrightnessControl=1"]("http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver") xorg setting? This settings seems to help some nvidia cards.

Yes, not work. Currently I'm saving my eyes with Nvidia setting which changes the gamma to simulate the brightness control.

> **Toz said:**
> 
6. Which modules are running (that may be interfering with brightness):


```
lsmod
```

```

tun                    19624  2 
hid_generic             1153  0 
usbhid                 41466  0 
hid                    88758  2 hid_generic,usbhid
usb_storage            47847  2 
fuse                   74541  3 
rfcomm                 51153  8 
bnep                   11069  2 
nls_cp437               5953  2 
vfat                   10055  2 
fat                    51827  1 vfat
snd_hda_codec_hdmi     30336  4 
joydev                  9663  0 
snd_hda_codec_realtek    37032  1 
intel_powerclamp        8802  0 
btusb                  18496  0 
coretemp                6326  0 
kvm_intel             129393  0 
uvcvideo               72804  0 
videobuf2_vmalloc       3272  1 uvcvideo
videobuf2_memops        2335  1 videobuf2_vmalloc
videobuf2_core         27797  1 uvcvideo
bluetooth             308340  22 bnep,btusb,rfcomm
videodev              110188  2 uvcvideo,videobuf2_core
kvm                   379223  1 kvm_intel
arc4                    2000  2 
media                  11591  2 uvcvideo,videodev
snd_hda_intel          36520  5 
iwldvm                172354  0 
mac80211              453808  1 iwldvm
crc32_pclmul            3019  0 
crc32c_intel           14249  0 
ghash_clmulni_intel     4501  0 
aesni_intel            46124  0 
aes_x86_64              7399  1 aesni_intel
nvidia              11250487  53 
snd_hda_codec         148129  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
lrw                     3565  1 aesni_intel
snd_hwdep               6332  1 snd_hda_codec
gf128mul                5858  1 lrw
glue_helper             4609  1 aesni_intel
ablk_helper             1972  1 aesni_intel
cryptd                  8473  3 ghash_clmulni_intel,aesni_intel,ablk_helper
sony_laptop            39919  0 
psmouse                85356  0 
snd_pcm                77765  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc          7234  2 snd_pcm,snd_hda_intel
iwlwifi               137145  1 iwldvm
intel_ips              12492  0 
iTCO_wdt                5407  0 
iTCO_vendor_support     1929  1 iTCO_wdt
snd_timer              18718  1 snd_pcm
atl1c                  36898  0 
cfg80211              402729  3 iwlwifi,mac80211,iwldvm
snd                    59141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
microcode              13488  0 
serio_raw               5041  0 
pcspkr                  2027  0 
soundcore               5450  1 snd
rfkill                 15698  6 cfg80211,sony_laptop,bluetooth
thermal                 8620  0 
battery                 6925  0 
evdev                  10693  15 
ac                      3324  0 
acpi_cpufreq           10867  1 
i2c_i801               11269  0 
lpc_ich                13112  0 
intel_agp              10872  0 
i2c_core               23720  3 i2c_i801,nvidia,videodev
intel_gtt              12664  1 intel_agp
shpchp                 25457  0 
mperf                   1267  1 acpi_cpufreq
mei_me                  9296  0 
mei                    61875  1 mei_me
processor              24917  1 acpi_cpufreq
ext4                  470412  3 
crc16                   1359  2 ext4,bluetooth
mbcache                 5866  1 ext4
jbd2                   83376  1 ext4
sr_mod                 14898  0 
cdrom                  34848  1 sr_mod
sd_mod                 30899  8 
mxm_wmi                 1467  0 
ehci_pci                4120  0 
ehci_hcd               48084  1 ehci_pci
ahci                   22888  5 
libahci                21393  1 ahci
sdhci_pci              12138  0 
libata                171318  2 ahci,libahci
scsi_mod              128695  4 usb_storage,libata,sd_mod,sr_mod
usbcore               178049  6 btusb,uvcvideo,usb_storage,ehci_hcd,ehci_pci,usbhid
firewire_ohci          31869  0 
firewire_core          52227  1 firewire_ohci
sdhci                  29076  1 sdhci_pci
crc_itu_t               1363  1 firewire_core
mmc_core               95506  2 sdhci,sdhci_pci
usb_common              1648  1 usbcore
wmi                     8347  1 mxm_wmi
video                  11380  0 
button                  4669  0 

```

> **Toz said:**
> 
7. Have you had a look at the [nvidiabl]("https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h") module? Looks like the VPCS1* is [supported]("https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h").

No, I will try it as soon as my H.D.D recovery got finished.

> **Toz said:**
> 
Sorry for the laundry list. Let me know if you need more information about any of the points.
 It would be great if you can help me solve this problem.

---

### Post by XinOxaR on 2013-10-03
I tried acpi_osi="!windows 2012"
Result: brightness not works

Nvidiabl works!!! Finally.
@Toz: You have saved my eyes. thank you.

Regards,
XinOxaR

---

