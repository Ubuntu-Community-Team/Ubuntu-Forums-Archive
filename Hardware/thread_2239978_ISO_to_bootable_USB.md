---
title: "ISO to bootable USB"
date: 2014-08-17
forum: Hardware
---

### Post by Richard_Ford on 2014-08-17
Hello,

I have an ISO on my desktop that I want to make into a bootable USB. I am not sure how to do this through the terminal. I read a few things, but none seem to work and I am not sure where the values are from that were used in the commands. Is there anything in the Software I could use or is there a way to do it through the Terminal that might be somewhat easy (I am new to Ubuntu...Noob...I know...)

This is the command I was using. The file is kali-linux-1.0.8-amd64.iso. It is on my desktop.

```
dd if=kali.iso of=/dev/sdb bs=512k
```

---

### Post by kc1di on 2014-08-17
Hi Richard_Ford and welcome to Ubuntu,

install unetbootin it's in the repositories and can be install via the software center or in a terminal with the following commands:
```
sudo apt-get install unetbootin
```

It will burn your ISO to a usb drive for you. 
good Luck.

---

### Post by ian-weisser on 2014-08-17
> **Richard_Ford said:**
> The file is kali-linux-1.0.8-amd64.iso. It is on my desktop.

Then it would be 'if=/home/<your username>/Desktop/kali-linux-1.0.8-amd64.iso' instead of 'if=kali.iso'
'if' means 'input file'. Using complete file paths reduces mistakes.

'of' would be the location of your usb stick. /dev/sdb is normal for most systems that have a single physical hard drive, like laptops.

---

### Post by grahammechanical on 2014-08-17
Are you using Ubuntu? I am and I would open the File Manager select the ISO image and right click and then select Write to Disk. That does every time for me.

---

