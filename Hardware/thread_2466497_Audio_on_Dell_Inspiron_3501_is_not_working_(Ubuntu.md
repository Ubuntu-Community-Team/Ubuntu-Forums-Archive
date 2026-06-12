---
title: "Audio on Dell Inspiron 3501 is not working (Ubuntu 20.04)"
date: 2021-08-29
forum: Hardware
---

### Post by rahim007 on 2021-08-29
[COLOR=#242729][FONT=-apple-system]I've been using Ubuntu 20.04 for the last few months on my old Dell Inspiron 3558 laptop and it's working like a charm. Recently I bought a new laptop, Dell Inspiron 3501, and it came pre-installed with Windows 10. So I dual-booted Ubuntu 20.04 on it to check if everything is working fine and later I wanted to remove Windows completely and install Ubuntu as my primary OS. After installation, everything is working fine except the audio output. The sound kind of crackles. It works perfectly fine on windows though. I tested inbuild speakers, Bluetooth headset, and output from 3.5 mm audio jack but no difference. I tried youtube videos and local audio and video files but the outcome is the same. I tried many online solutions but without any success. I also installed Ubuntu 21.04, to check if the new kernel brings any improvement but the condition was the same. So I installed Ubuntu 20.04 back since I'm more comfortable with the LTS version.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]
I'm a front-end web developer and I feel comfortable with basic command line but I still consider myself a Linux newbie. Please help me solve this problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]Hardware specs:[/FONT][/COLOR]

[LIST]
[*]Processor: 11th Generation Intel Core i5-1135G7
[*]RAM: 16 GB DDR4
[*]Audio: Cirrus Logic CS8409 (CS42L42 + SN005825)
[*]Storage: 256 GB SSD + 1 TB HDD
[*]Display 15.6 Inch 1920x1080 FHD
[*]GPU: Integrated Intel Iris Xe Graphics
[*]More info: [Dell Inspiron 3501]("https://www.dell.com/support/home/en-in/product-support/product/inspiron-15-3501-laptop/docs")
[/LIST]

---

### Post by Yellow Pasque on 2021-08-29
[https://bugs.launchpad.net/hwe-next/+bug/1916554](https://bugs.launchpad.net/hwe-next/+bug/1916554)

---

### Post by rahim007 on 2021-08-29
So generally how long does it take for Ubuntu LTS to release a fix for this type of bug?

---

### Post by Yellow Pasque on 2021-08-30
So have you tried the oem kernel?

---

### Post by rahim007 on 2021-08-30
Not yet. I don't know how to install a kernel. Currently I'm on 5.11.0-27-generic. I'll do some research and install OEM kernel and let you know.

---

### Post by rahim007 on 2021-08-30
So I installed the OEM kernel using `sudo apt install linux-oem-20.04b` but no improvement in audio. It's still crackling.

---

### Post by vitalyrod on 2021-10-15
In /etc/pulse/daemon.conf , please uncomment following line
; default-sample-format = s16le
**default-sample-rate = 48000**
; alternate-sample-rate = 48000
This should fix an issue with the OEM kernel. Please, note, this issue is fixed in kernel 5.14 in a generic way.

---

### Post by rahim007 on 2021-10-17
Actually I updated to Ubuntu 21.10 and kernel to 5.15 and sound is working fine now. Bass is almost none but at least it's working.

---

### Post by rcastro33 on 2021-11-08
Thank you, that workaround works perfectly for me with Raven/Raven2/FireFlight/Renoir Audio Processor, after that change and reset pulseaudio with `sudo killall pulseaudio` the audio is solved. Kernel: 5.14.12-051412-generic

---

