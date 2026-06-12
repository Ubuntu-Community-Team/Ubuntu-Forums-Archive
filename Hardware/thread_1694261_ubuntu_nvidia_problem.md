---
title: "ubuntu nvidia problem"
date: 2011-02-24
forum: Hardware
---

### Post by devuu on 2011-02-24
p { margin-bottom: 0.21cm; }  Hello everyone,
 

 I've recently tried to install ubuntu but having trouble with my nvidia graphic card, so i disabled it and used my on-board graphic card. Ubuntu installed successfully and worked fine.
 

 Then i installed nvidia driver from system>administration > additional drivers (the one which is recommended).
 

 I restarted ubuntu and there was no gui, instead there was tty1 login screen. I've then disabled my on-board graphic card and plugged to nvidia. A black screen with lots of text. Which do not make any sense to me.. some of the lines were:-
 

     > 

ath5k: unknown symbol
     . --some text--.
     Vgaarb:device changed decodes: pci:0000:011:00.0, olddecodes=10+mem, decodes = none:     owns = 10+mem
     --some text--
     nvidia 0000:01:00.0 pci int a->gsi 16 (level, low) -> irq16
     --some text--
     nvrm:loading nvidia unix x86 kernel module 260.19.06
     --some text--
  i then switched back to my onboard graphic card and executed these commands at tty1 screen.
 

>  
     Sudo apt-get install nvidia-glx
     sudo dpkg-reconfigure xserver-xorg
  restarted my pc but no result. I then used recovery mode and in it low graphic mode or something.
 

 Then gui appeared but when tried to open nvidia xserver setting then it says “you do not appear to be using nvidia x driver”.
 

 I want to use my nvidia graphic card. Graphic card itself is fine as it runs ok in XP
 

 My config:
 Pentium 4 1.8Ghz
 nvidia 7300gt
 512ram

---

### Post by zenwalker on 2011-02-24
From terminal (no GUI) run nvidia-xconfig command.

---

### Post by devuu on 2011-02-25
> **zenwalker said:**
> From terminal (no GUI) run nvidia-xconfig command.

I tried.. Got this error msg 

> 
Using X Configuration File: "/etc/x11/xorg.conf"

Validation Error: Data Incomplete in file /etc/x11/xorg.conf.
   Undefined Device "(null)" referenced by screen "default Screen".

Error: Unable to write to directory '/etc/x11'.


Help!!

---

### Post by devuu on 2011-02-25
Ok that’s what I recently done:

Plugged my monitor into my nvidia 7300gt and disabled on-board graphic card. Started ubuntu 10.10 in recovery mode. No GUI but lots text lines, some of them are:- 
> 
50.141297] [<co1659c4] ? kthread +0x74/0*80
    ? kernel_thread_helper + 0*6/0*10

50.141297]EIP: [<co2oed5c>] ext4_handle _error + oX1c/oxbo ss:esp 0068:dde3
50.141297] cr2: 00000000dff4c4c9
50.141297] [end trace acf 300880bfa4ccc]



If you get any clue where the problem is..plzz help

---

### Post by SeijiSensei on 2011-02-25
You need to run nvidia-xconfig as root with sudo like this 

```
sudo nvidia-xconfig
```

The permission denied errors arise because only the "root" user can write to the directory /etc/X11.

---

### Post by devuu on 2011-02-25
> **SeijiSensei said:**
>  
```
sudo nvidia-xconfig
```


It seems that command got executed fine, because I got the msg:

> 
Backed up file ‘/etc/x11/xorg.conf’ as ‘/etc/x11/xorg.conf.backup
New x configuration file written to ‘/etc/x11/xorg.conf’


i then rebooted the system but still no gui..

---

