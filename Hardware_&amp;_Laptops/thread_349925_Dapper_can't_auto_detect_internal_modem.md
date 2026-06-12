---
title: "Dapper can't auto detect internal modem"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by eilu on 2007-01-30
it can't autodetect the internal one. eth0 and eth1 (wireless and ethernet, respectively) worked, but the modem cannot be detected. There are 5 ports listed at /dev/ (/modem, /ttyS0, /ttyS1, /ttyS2 and /ttyS3) but it says it can't detect the modem

---

### Post by mandrakethepenguin on 2007-01-30
You probably have a winmodem, or an inexpensive made-for-Windows modem that is not friendly with Linux, I have the kind of modem that came with my HP Desktop PC. Run this command and paste the output in this thread: ```
lspci | grep -i modem
``` Or if nothing shows up, just paste the output of [FONT=Courier New]lspci[FONT=Verdana].[/FONT][/FONT]

---

### Post by eilu on 2007-01-31
$lspci | grep -i modem doesn't return anything, but $lspci returns:
```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
0000:03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```
:confused:

---

### Post by mandrakethepenguin on 2007-01-31
Are you on a laptop or desktop PC?

---

### Post by eilu on 2007-02-03
I'm on a laptop. Sorry about the late response, midterm exams are coming.

---

### Post by eilu on 2007-02-08
*bump bump*
can anyone help? please?

---

