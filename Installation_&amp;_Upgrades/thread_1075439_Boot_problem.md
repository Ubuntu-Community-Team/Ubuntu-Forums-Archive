---
title: "Boot problem"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by ekidd91 on 2009-02-20
Hi, I'm new here and new to Ubuntu also.

After two attempts I finally installed Ubuntu 8.10 successfully (or what i thought was successfully), and now it won't boot. Although I did get the message telling me Ubuntu had been installed and to restart, my screen had gone blank during the installation (from about 83%) and I had to unplug it and after a while I could see the installation again (at 94%). This is probably irrelevant to my problem (likely just a faulty monitor) but I thought I would mention it anyway. I wiped my harddrive and did a clean install using the full harddrive

After the Ubuntu loading screen (orange loading bar), I get a message saying that it gave up loading (or something to that effect) and this error message:

```
ALERT! /dev/disk/by-uuid/44c7b725-2602-4ae2-aa3f-1b0e11d7dc5f  does not exist. Dropping to shell.
```

Following this there are a series of messages which are quite lengthy (hence the fact I didn't copy these down, I can if requested; I thought the initial error message was most important).

I've left the computer for a long time to see if it would eventually load, but alas, it doesn't and just stays at this error screen.

Thanks in advance.

---

### Post by ekidd91 on 2009-02-21
bump

---

### Post by ekidd91 on 2009-02-24
*bump*

Please help me guys.

---

### Post by ekidd91 on 2009-03-02
I am now able to use my computer 100% fine, but it only loads correctly (as opposed to going to the above error) when it hasn't been on for a while (over an hour or an hour and a half). This is fine, at least I can use my computer, but it does mean after updates I can't just restart, I have to shutdown and then wait.

Still nobody with ideas? Sorry to keep going on about this.

---

### Post by caljohnsmith on 2009-03-02
How about trying this: on start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
rootdelay=120
```
Then press enter to save the change, and finally "b" to boot. There have been people in the forums who have received a similar booting error as yours, and that's how they fixed the problem. Let me know if that works for you or not.

---

### Post by ekidd91 on 2009-03-03
OK, I tried that but I may have done it wrong: it didn't fix it, and every time I go back to the Grub menu to try again it doesn't seem to have saved what I've put in. I may have put it in the wrong section.

At the first Grub menu I have the following choices:

[LIST]
[*]Ubuntu 8.10, kernel 2.6.27-11-generic
[*]Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
[*]Ubuntu 8.10, kernel 2.6.27-7-generic
[*]Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
[*]Ubuntu 8.10, memtest86+
[/LIST]

I assumed it was ***Ubuntu 8.10, kernel 2.6.27-11-generic*** I was to edit and so went and pressed "e" on it. I then edited the following line:

```
kernel /boot/vmlinuz -2.6.27-11-generic root=UUID=44c7b725-2602-4ae2-aa3f-1b0e11d7c5f ro quiet splash
```

I tried three different things (I know you had told me to put it at the end but I tried it and for whatever reason it didn't work). I tried booting with the following:

```
kernel /boot/vmlinuz -2.6.27-11-generic root=UUID=44c7b725-2602-4ae2-aa3f-1b0e11d7c5f ro quiet splash rootdelay=120
```

```
kernel /boot/vmlinuz -2.6.27-11-generic root=UUID=44c7b725-2602-4ae2-aa3f-1b0e11d7c5f rootdelay=120 ro quiet splash
```

```
kernel /boot/vmlinuz -2.6.27-11-generic root=UUID=44c7b725-2602-4ae2-aa3f-1b0e11d7c5f rootdelay=120 quiet splash
```

After editing the line each time I pressed "Enter" and then after it was back to the list of options (the one within ***Ubuntu 8.10, kernel 2.6.27-11-generic***) I pressed "b". It would then attempt to boot but the orange loading bar would just go back and forth (for longer than it has ever done it before) and then go to the error in the original post.

Where did I go wrong?

---

### Post by ekidd91 on 2009-03-13
I am now getting the error in the first post all the time now, no matter what I try Ubuntu won't load (tried rootdelay, taking splash out of the kernel line, taking quiet out, taking both quiet out. Everything I know of.)

Please help me fix this once and for all guys.

---

