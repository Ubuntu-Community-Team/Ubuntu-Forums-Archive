---
title: "Matebook Touchscreen Wacom? detected but not working"
date: 2018-09-28
forum: Hardware
---

### Post by dooglex2 on 2018-09-28
I have a huawei matebook hz-w19, i got the wifi working by downloading [COLOR=#444444][FONT=Microsoft YaHei][COLOR=#444444] l[inux-firmware_1.157_all.deb [COLOR=#444444][FONT=Microsoft YaHei][/FONT][/COLOR]]("https://mirrors.tuna.tsinghua.edu.cn/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb")[https://mirrors.tuna.tsinghua.edu.cn/ubuntu/pool/main/l/linux-firmware/](https://mirrors.tuna.tsinghua.edu.cn/ubuntu/pool/main/l/linux-firmware/)[COLOR=#444444][/COLOR][/COLOR][/FONT][/COLOR]
I then extracted it, and then copied data/lib/firmware/brcm/[COLOR=#444444][FONT=Microsoft YaHei][COLOR=#444444]brcmfmac4356-pcie.bin from the firmware file and [COLOR=#444444][COLOR=#444444][COLOR=#444444][COLOR=#000000][COLOR=#444444][FONT=Microsoft YaHei]https://fedorapeople.org/~jwrdegoede/brcmfmac4356-pcie.txt into my local /lib/firmware/brcm/ folder, removing all old brcm4356* files first. 

Now I am trying to get the touchscreen to work. when i run xinput i see it, 
[/FONT][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/FONT][/COLOR]nath@nath-MateBook-HZ-W19:~$ xinput
\&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Chicony Huawei Folio keyboard               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Chicony Huawei Folio keyboard Touchpad      id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4834 Pen stylus                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4834 Finger touch                 id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4834 Pen eraser                   id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Chicony Huawei Folio keyboard               id=10    [slave  keyboard (3)]
    &#8627; Intel Virtual Button driver                 id=15    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=16    [slave  keyboard (3)]
    &#8627; Chicony Huawei Folio keyboard               id=17    [slave  keyboard (3)]

I tried to install wacom-dkms but it wasnt in the repos, neither was input-wacom

I tried to install the binary of input-wacom but get a crypto error? 
nath@nath-MateBook-HZ-W19:~/Downloads/input-wacom-0.41.0$ make install
Making install in 4.5
make[1]: Entering directory '/home/nath/Downloads/input-wacom-0.41.0/4.5'
make -C /lib/modules/4.15.0-34-generic/build M=/home/nath/Downloads/input-wacom-0.41.0/4.5 modules_install
make[2]: Entering directory '/usr/src/linux-headers-4.15.0-34-generic'
  INSTALL /home/nath/Downloads/input-wacom-0.41.0/4.5/wacom.ko
cp: cannot create regular file '/lib/modules/4.15.0-34-generic/extra/wacom.ko': Permission denied
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/nath/Downloads/input-wacom-0.41.0/4.5/wacom_w8001.ko
cp: cannot create regular file '/lib/modules/4.15.0-34-generic/extra/wacom_w8001.ko': Permission denied
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  4.15.0-34-generic
make[2]: Leaving directory '/usr/src/linux-headers-4.15.0-34-generic'
mkdir -p /etc/depmod.d
echo "override wacom * extra" > /etc/depmod.d/input-wacom.conf
/bin/sh: 1: cannot create /etc/depmod.d/input-wacom.conf: Permission denied
Makefile:34: recipe for target 'install' failed
make[1]: *** [install] Error 2
make[1]: Leaving directory '/home/nath/Downloads/input-wacom-0.41.0/4.5'
Makefile:371: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1



Many thanks for any help!

---

