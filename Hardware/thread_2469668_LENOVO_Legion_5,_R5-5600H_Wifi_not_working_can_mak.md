---
title: "LENOVO Legion 5, R5-5600H Wifi not working can make installation work"
date: 2021-12-06
forum: Hardware
---

### Post by pp1 on 2021-12-06
Hi!

LENOVO Legion 5, R5-5600H Wifi not working can make installation work

i did
[https://github.com/lwfinger/rtw89/issues/74](https://github.com/lwfinger/rtw89/issues/74)

sudo apt-get update
sudo apt-get install make gcc linux-headers-$(uname -r) build-essential git
git clone [https://github.com/lwfinger/rtw89.git](https://github.com/lwfinger/rtw89.git)
[COLOR=#24292F][FONT=-apple-system](or v6)[/FONT][/COLOR]
mkdir ~/mok && cd ~/mok
openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=Custom MOK/"
sudo mokutil --import MOK.der
reboot
[COLOR=#24292F][FONT=-apple-system]blue screen>enroll mok>yes>keep the password you entered in sudo mokutil --import MOK.der>reboot[/FONT][/COLOR]
cd rtw89
make
/usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89core.ko
/usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89pci.ko
sudo make install
reboot

after 

[FONT=-apple-system]====================[/FONT]

[FONT=-apple-system]I make this but after make and this two lines
/usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89core.ko
/usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89pci.ko[/FONT]
[FONT=-apple-system]this happend
root@marlies-Legion-5-15ACH6H:/home/marlies# cd rtw89/
root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89# make
make -C /lib/modules/5.13.0-22-generic/build M=/home/marlies/rtw89 modules
make[1]: Verzeichnis „/usr/src/linux-headers-5.13.0-22-generic“ wird betreten
CC [M] /home/marlies/rtw89/core.o
CC [M] /home/marlies/rtw89/debug.o
CC [M] /home/marlies/rtw89/mac80211.o
CC [M] /home/marlies/rtw89/mac.o
CC [M] /home/marlies/rtw89/phy.o
CC [M] /home/marlies/rtw89/fw.o
CC [M] /home/marlies/rtw89/rtw8852a.o
CC [M] /home/marlies/rtw89/rtw8852a_table.o
CC [M] /home/marlies/rtw89/rtw8852a_rfk.o
CC [M] /home/marlies/rtw89/rtw8852a_rfk_table.o
CC [M] /home/marlies/rtw89/cam.o
CC [M] /home/marlies/rtw89/efuse.o
CC [M] /home/marlies/rtw89/regd.o
CC [M] /home/marlies/rtw89/coex.o
CC [M] /home/marlies/rtw89/ps.o
CC [M] /home/marlies/rtw89/sar.o
CC [M] /home/marlies/rtw89/ser.o
LD [M] /home/marlies/rtw89/rtw89core.o
CC [M] /home/marlies/rtw89/pci.o
LD [M] /home/marlies/rtw89/rtw89pci.o
MODPOST /home/marlies/rtw89/Module.symvers
CC [M] /home/marlies/rtw89/rtw89core.mod.o
LD [M] /home/marlies/rtw89/rtw89core.ko
BTF [M] /home/marlies/rtw89/rtw89core.ko
Skipping BTF generation for /home/marlies/rtw89/rtw89core.ko due to unavailability of vmlinux
CC [M] /home/marlies/rtw89/rtw89pci.mod.o
LD [M] /home/marlies/rtw89/rtw89pci.ko
BTF [M] /home/marlies/rtw89/rtw89pci.ko
Skipping BTF generation for /home/marlies/rtw89/rtw89pci.ko due to unavailability of vmlinux
make[1]: Verzeichnis „/usr/src/linux-headers-5.13.0-22-generic“ wird verlassen
root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89# /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89core.ko
At main.c:160:[/FONT]
[FONT=-apple-system]SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: /home/root/mok/MOK.priv: No such file or directory
root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89# /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 /home/$(echo $USER)/mok/MOK.priv /home/$(echo $USER)/mok/MOK.der rtw89pci.ko
At main.c:160:
SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: /home/root/mok/MOK.priv: No such file or directory
root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89#[/FONT]
[FONT=-apple-system]I try this root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89# sudo make install
make -C /lib/modules/5.13.0-22-generic/build M=/home/marlies/rtw89 modules
make[1]: Verzeichnis „/usr/src/linux-headers-5.13.0-22-generic“ wird betreten
make[1]: Verzeichnis „/usr/src/linux-headers-5.13.0-22-generic“ wird verlassen
Install rtw89 SUCCESS
root@marlies-Legion-5-15ACH6H:/home/marlies/rtw89#

====================

How could i fix this ?

thx
Peter[/FONT]

---

