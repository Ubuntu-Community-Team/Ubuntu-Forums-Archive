---
title: "No sound on my toshiba satellite"
date: 2010-03-17
forum: Hardware
---

### Post by tnimxunil on 2010-03-17
Hi everyone,

I have a Toshiba Satellite R25-S3503 tablet. My brother recently put Linux Mint 8 Helena on it. Now I cannot get the sound to work at all. I've tried searching for previous posts with the same problem, but I haven't found any for my specific laptop. I've tried a few other fixes, but nothing has worked. The sound card is a Realtek ALC262. I don't really know anything about Linux or Coding, so I'm worried I'll screw something up. I'm trying this here because I can't seem to get the Mint forum to let me register. I hope you guys can help. :KS [I hope I posted this correctly.]

---

### Post by n0dix on 2010-03-17
Did you look in alsamixer?
Did you get any sound with the test in System -> Preferences -> Sound?

---

### Post by chaanakya_chiraag on 2010-03-17
Try running the following in the Terminal (not sure how to get there in Mint, but if you have sub-menus, try looking under Accessories):
```
sudo killall pulseaudio
sudo pulseaudio --system --daemon
```Does audio work now??
**Btw, if Mint asks you for the "sudo" password, enter YOUR login password.  IT WILL NOT BE SHOWN (security feature).  Just so you know :D**

---

### Post by radu.c on 2010-03-17
-

---

### Post by tnimxunil on 2010-03-17
When I try your code I get this:

oem@Laptop ~ $ sudo killall pulseaudio
oem@Laptop ~ $ sudo pulseaudio --system --daemon
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
E: main.c: Daemon startup failed.

I still have no sound. Did I do something wrong? I have made sure that nothing is muted in Alsamixer as well. Any other ideas? Thanks for your help. :)

---

### Post by chaanakya_chiraag on 2010-03-18
It seems like pulseaudio doesn't want to start.  Try running ```
sudo killall pulseaudio
pulseaudio &
```
Does pulseaudio startup ok?  I have a feeling it won't, but try it anyway.

---

### Post by willsomebody on 2010-04-06
tnimxunil gave me her laptop to work on because I have some experience with linux, Ubuntu, specifically. I ran "pulseaudio &" as you recommended and it did not work.  Interestingly, lspci claims it has an "Intel 82801G High Definition Audio Controller".  Ubuntu 9.10 running from a USB flash drive said the same thing and did not have working audio either.  Any help would be appreciated as I cannot seem to be able to find anything about sound in linux on this laptop online.

---

### Post by chaanakya_chiraag on 2010-04-08
Go to System->Preferences->Sound and set everything to ALSA.  Does sound work now?

---

### Post by lidex on 2010-04-08
Can you supply some info for us? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

