---
title: "help,Canon CanoScan Lide 110"
date: 2010-11-22
forum: Hardware
---

### Post by nitzdr on 2010-11-22
Hello,
I tried to use this scanner in Ubuntu10.04, but it did not work. 
Can anybody help me.
thanks.
 
1) gedit ~/sane-backends/backend/genesys_devices.c
static Genesys_USB_Device_Entry genesys_usb_device_list[] = {
/* GL847 devices */
{0x04a9, 0x1904, &canon_lide_100_model},
{0x04a9, 0x1909, &canon_lide_110_model},
copy struct data "canon_lide_100_model" as "canon_lide_110_model",and rename some descript,like this
static Genesys_Model canon_lide_110_model = {
"canon-lide-110", /* Name */
"Canon", /* Device vendor string */
"LiDE 110", /* Device model name */
GENESYS_GL847,
NULL,
...
 
2) gedit ~/sane-backends/backend/genesys.conf.in
add the following 2 lines and save:
# Canon LiDE 110
usb 0x04a9 0x1909
 
3) then
cd sane-backends
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
make install
 
4) gedit /lib/udev/rules.d/40-libsane.rules
add the following 2 lines and save:
# Canon CanoScan Lide 110
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1909", ENV{libsane_matched}="yes"
save the file, make, make install, exit terminal, reboot, and...
 
5) Now began to test:
# scanimage -L
device `genesys:libusb:001:002' is a Canon LiDE 110 flatbed scanner
# scanimage >300.pnm
scanimage: open of device genesys:libusb:001:002 failed: Error during device I/O
 
sane-find-scanner give this description:
(vendor=0x04a9 [Canon], product=0x1909 [CanoScan], chip=GL848+) 
nitzdr

---

### Post by nitzdr on 2010-11-22
The following is some debugging information:
# SANE_DEBUG_DLL=255 scanimage >300.pnm
[dll] sane_get_devices: found 1 devices
[dll] sane_open: trying to open `genesys:libusb:001:002'
scanimage: open of device genesys:libusb:001:002 failed: Error 
during device I/O
[dll] sane_exit: exiting
 
 
# SANE_DEBUG_GENESYS_GL847=255 scanimage >300.pnm
[sanei_debug] Setting debug level of genesys_gl847 to 255.
[genesys_gl847] gl847_init start
[genesys_gl847] gl847_init: value=0x00
[genesys_gl847] gl847_init: device is warm
[genesys_gl847] gl847_cold_boot start
[genesys_gl847] gl847_init_registers start
[genesys_gl847] gl847_init_registers completed
[genesys_gl847] gl847_bulk_write_register: wrote 141 registers
[genesys_gl847] write_end_access: 0x10,0x0b
[genesys_gl847] write_end_access: 0x13,0x0e
[genesys_gl847] gl847_init_gpio: start
[genesys_gl847] gl847_init_gpio: completed
[genesys_gl847] gl847_init_memory_layout
[genesys_gl847] gl847_init_memory_layout completed
[genesys_gl847] gl847_cold_boot completed
[genesys_gl847] gl847_set_fe (init)
[genesys_gl847] gl847_set_ad_fe(): start
[genesys_gl847] gl847_set_ad_fe(): setting DAC 11
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_bulk_write_register: wrote 3 registers
[genesys_gl847] gl847_set_ad_fe(): end
[genesys_gl847] gl847_slow_back_home (wait_until_home = 1)
[genesys_gl847] status=
[genesys_gl847] status=
[genesys_gl847] gl847_init_optical_regs_off : start
[genesys_gl847] gl847_init_optical_regs_off : completed. 
[genesys_gl847] gl847_init_motor_regs : feed_steps=65536, action=2, flags=0
[genesys_gl847] gl847_init_motor_regs : fast_exposure=4000 pixels
[genesys_gl847] gl847_init_motor_regs: feedl=65280
[genesys_gl847] gl847_send_slope_table (table_nr = 0, steps = 256)
[genesys_gl847] gl847_send_slope_table: write slope 0 (256)=,3000,2821,2748,2691,2643,2601,2563,2528,2496,2465,2436,2409,2382,2357,2333,2309,2287,2265,2244,2223,2203,2183,2164,2145,2127,2109,2091,2074,2057,2040,2024,2007,1992,1976,1961,1945,1930,1916,1901,1887,1873,1859,1845,1831,1818,1804,1791,1778,1765,1752,1740,1727,1715,1702,1690,1678,1666,1654,1643,1631,1619,1608,1597,1585,1574,1563,1552,1541,1530,1519,1509,1498,1488,1477,1467,1456,1446,1436,1426,1416,1406,1396,1386,1376,1367,1357,1347,1338,1328,1319,1309,1300,1291,1281,1272,1263,1254,1245,1236,1227,1218,1209,1200,1191,1182,1174,1165,1156,1148,1139,1131,1122,1114,1105,1097,1089,1081,1072,1064,1056,1048,1040,1032,1023,1015,1007,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000
[genesys_gl847] write_ahb: write(0x10000000,0x00000200)
[genesys_gl847] write_ahb: AHB= 0x00 0x00 0x00 0x10 0x00 0x02 0x00 0x00
[genesys_gl847] gl847_send_slope_table: completed
[genesys_gl847] gl847_send_slope_table (table_nr = 1, steps = 256)
[genesys_gl847] gl847_send_slope_table: write slope 1 (256)=,3000,2821,2748,2691,2643,2601,2563,2528,2496,2465,2436,2409,2382,2357,2333,2309,2287,2265,2244,2223,2203,2183,2164,2145,2127,2109,2091,2074,2057,2040,2024,2007,1992,1976,1961,1945,1930,1916,1901,1887,1873,1859,1845,1831,1818,1804,1791,1778,1765,1752,1740,1727,1715,1702,1690,1678,1666,1654,1643,1631,1619,1608,1597,1585,1574,1563,1552,1541,1530,1519,1509,1498,1488,1477,1467,1456,1446,1436,1426,1416,1406,1396,1386,1376,1367,1357,1347,1338,1328,1319,1309,1300,1291,1281,1272,1263,1254,1245,1236,1227,1218,1209,1200,1191,1182,1174,1165,1156,1148,1139,1131,1122,1114,1105,1097,1089,1081,1072,1064,1056,1048,1040,1032,1023,1015,1007,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000
[genesys_gl847] write_ahb: write(0x10004000,0x00000200)
[genesys_gl847] write_ahb: AHB= 0x00 0x40 0x00 0x10 0x00 0x02 0x00 0x00
[genesys_gl847] gl847_send_slope_table: completed
[genesys_gl847] gl847_send_slope_table (table_nr = 2, steps = 256)
[genesys_gl847] gl847_send_slope_table: write slope 2 (256)=,3000,2821,2748,2691,2643,2601,2563,2528,2496,2465,2436,2409,2382,2357,2333,2309,2287,2265,2244,2223,2203,2183,2164,2145,2127,2109,2091,2074,2057,2040,2024,2007,1992,1976,1961,1945,1930,1916,1901,1887,1873,1859,1845,1831,1818,1804,1791,1778,1765,1752,1740,1727,1715,1702,1690,1678,1666,1654,1643,1631,1619,1608,1597,1585,1574,1563,1552,1541,1530,1519,1509,1498,1488,1477,1467,1456,1446,1436,1426,1416,1406,1396,1386,1376,1367,1357,1347,1338,1328,1319,1309,1300,1291,1281,1272,1263,1254,1245,1236,1227,1218,1209,1200,1191,1182,1174,1165,1156,1148,1139,1131,1122,1114,1105,1097,1089,1081,1072,1064,1056,1048,1040,1032,1023,1015,1007,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000
[genesys_gl847] write_ahb: write(0x10008000,0x00000200)
[genesys_gl847] write_ahb: AHB= 0x00 0x80 0x00 0x10 0x00 0x02 0x00 0x00
[genesys_gl847] gl847_send_slope_table: completed
[genesys_gl847] gl847_send_slope_table (table_nr = 3, steps = 256)
[genesys_gl847] gl847_send_slope_table: write slope 3 (256)=,3000,2821,2748,2691,2643,2601,2563,2528,2496,2465,2436,2409,2382,2357,2333,2309,2287,2265,2244,2223,2203,2183,2164,2145,2127,2109,2091,2074,2057,2040,2024,2007,1992,1976,1961,1945,1930,1916,1901,1887,1873,1859,1845,1831,1818,1804,1791,1778,1765,1752,1740,1727,1715,1702,1690,1678,1666,1654,1643,1631,1619,1608,1597,1585,1574,1563,1552,1541,1530,1519,1509,1498,1488,1477,1467,1456,1446,1436,1426,1416,1406,1396,1386,1376,1367,1357,1347,1338,1328,1319,1309,1300,1291,1281,1272,1263,1254,1245,1236,1227,1218,1209,1200,1191,1182,1174,1165,1156,1148,1139,1131,1122,1114,1105,1097,1089,1081,1072,1064,1056,1048,1040,1032,1023,1015,1007,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000
[genesys_gl847] write_ahb: write(0x1000c000,0x00000200)
[genesys_gl847] write_ahb: AHB= 0x00 0xc0 0x00 0x10 0x00 0x02 0x00 0x00
[genesys_gl847] gl847_send_slope_table: completed
[genesys_gl847] gl847_send_slope_table (table_nr = 4, steps = 256)
[genesys_gl847] gl847_send_slope_table: write slope 4 (256)=,3000,2821,2748,2691,2643,2601,2563,2528,2496,2465,2436,2409,2382,2357,2333,2309,2287,2265,2244,2223,2203,2183,2164,2145,2127,2109,2091,2074,2057,2040,2024,2007,1992,1976,1961,1945,1930,1916,1901,1887,1873,1859,1845,1831,1818,1804,1791,1778,1765,1752,1740,1727,1715,1702,1690,1678,1666,1654,1643,1631,1619,1608,1597,1585,1574,1563,1552,1541,1530,1519,1509,1498,1488,1477,1467,1456,1446,1436,1426,1416,1406,1396,1386,1376,1367,1357,1347,1338,1328,1319,1309,1300,1291,1281,1272,1263,1254,1245,1236,1227,1218,1209,1200,1191,1182,1174,1165,1156,1148,1139,1131,1122,1114,1105,1097,1089,1081,1072,1064,1056,1048,1040,1032,1023,1015,1007,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000,1000
[genesys_gl847] write_ahb: write(0x10010000,0x00000200)
[genesys_gl847] write_ahb: AHB= 0x00 0x00 0x01 0x10 0x00 0x02 0x00 0x00
[genesys_gl847] gl847_send_slope_table: completed
[genesys_gl847] gl847_init_motor_regs : completed. 
[genesys_gl847] gl847_bulk_write_register: wrote 141 registers
[genesys_gl847] gl847_stop_action
[genesys_gl847] status=
[genesys_gl847] gl847_stop_action: already stopped
[genesys_gl847] gl847_stop_action: completed
[genesys_gl847] gl847_slow_back_home: timeout while waiting for scanhead to go home
scanimage: open of device genesys:libusb:001:002 failed: Error during device I/O

---

### Post by legolas558 on 2010-11-27
Did you ever get this working? I have the same scanner but no luck up to now! :(

---

### Post by pt123 on 2011-01-01
have your tried using the instructions for 100 on this

[http://ubuntuforums.org/showthread.php?p=9462309#post9462309](http://ubuntuforums.org/showthread.php?p=9462309#post9462309)

---

### Post by IcarusR on 2011-01-02
Lide 110 is listed as complete support by the 'SANE Development (git) Version' as per this page

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON")

You can download & install as per the last two posts here

[http://ubuntuforums.org/showthread.php?t=1033181&page=4]("http://ubuntuforums.org/showthread.php?t=1033181&page=4")

```
# Get the sane sources
git clone git://git.debian.org/sane/sane-backends.git sane-backends
# Build sane backends
cd sane-backends
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```

You may need to check that your scanner details are listed in /lib/udev/rules.d/40-libsane.rules

---

### Post by Anna42 on 2011-07-07
[COLOR=#000000][COLOR=#333333][FONT=arial]**[SIZE=3]It DOES transfer it onto Notepad, BUT this is what it looks like:[/SIZE]**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
 
 
**[SIZE=3][FONT=arial][COLOR=#000000]Q X =6 +=. rno r[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]d2 -3H "in i1-; 3 =r +v=.F-[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]{ = -=.r > j.- o- j+;rr'^ =.2 t ,3i.-5f g',f *;f if[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]x'* [ + ; :- I i i a 1 3 i 5 e r : ? i = i ; : : I ] : i E * : c <[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]I 3 € ; s-F i i s E r = I € I ? ;_ = t r 5 = ; : i i i B : ; I ; i[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000], A 7i'4 I-(rS A i. - '-, . * ;1,[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]i c ; F?i, ia.:, "; S=Fi i;+: {Ii q: I ; ai =i;lr[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]E;+ rii:15 rras;ii?+z2qiti€i *:*: 6[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]yr; Ei:Enil EtBg.kt.;'+;iil3f ;f i31= =[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]z.^.<F[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]g€E AsEi:E- ;;+.,: 6 ;i;e:3".r=o- i= -[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000]s Hr'iisifi[ :[['i s *i*= r+iLi o,if I[/COLOR][/FONT][/SIZE]**
 
**[SIZE=3][FONT=arial][COLOR=#000000]Z':7iiza€;Fare= =-4il : i--[ilEiX; i3 =[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=arial][COLOR=#000000];__<i,*+; qiiT<-: *z=? 1 Ii;€iz=_=! =r:[/COLOR][/FONT][/SIZE]**
 
[SIZE=3][FONT=arial][COLOR=#000000]**Can someone tell me how to get this onto word as a document in ENGLISH  so that I can edit it. I am complete dunce I am afraid. Is there a way of making this code readable? I NEED to be able to EDIT is a document in Word. SOB.  **:( [/COLOR][/FONT][/SIZE][/COLOR]

---

