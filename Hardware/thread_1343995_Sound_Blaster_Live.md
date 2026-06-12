---
title: "Sound Blaster Live"
date: 2009-12-02
forum: Hardware
---

### Post by Cpierce on 2009-12-02
I am brand new to Ubuntu, so I need some help. From searching on the web, it looks like my issue is a common problem. I installed Ubuntu on an old desktop which went very smoothly except for no sound. Ubuntu is not recognizing the sound card which is a SB Live. From what I read, that is a good sound card for Ubuntu. I ran some terminal commands like "asoundconfig" and "lspci -v" but nothing is listed. The sound card did work with XP. I also stuck in a SB Audigy SE and it didn't work. I tried different slots, no luck, but the slots do work with other types of cards. This computer is a Dell dim 4100 and has no onboard sound card. I also went to "Users and Groups" to make sure I was listed, which I was, but the " use audio devices" was grayed out and unchecked. 

I sure would appreciate any help.

---

### Post by Cpierce on 2009-12-02
anybody out there ?

---

### Post by Cpierce on 2009-12-03
Hello ????????????

---

### Post by Marran77 on 2009-12-03
I have an audigy SE and it is recognized by Ubuntu and works perfectly. Try lshw and see if it is recognizing the card (although I think it should be recognized by lspci -v). You might install the GTK-version if that make you feel more comfortable. 

```
sudo apt-get install lshw-gtk
```

Then alt+f2
then run the command gksu lshw-gtk

and you'll see information about your system.

To change your rights (or what you call them) you have to click the key-symbol in  "users and groups"-dialog, type in your admin-password and then check the "use audio devices" square. 

Maybe you should check if it is something in the BIOS that is making the card not showing up, unless you have used it under windows on the same computer.

That's the only tip I can give right now... Hope it helpes

---

### Post by Cpierce on 2009-12-03
First of all, thank you for your reply. I will try this. The sound card did work with windows installed. However, I didn't see it in the BIOS. So I flashed the BIOS to the newest version, but still couldn't find the sound card. I have had bluetooth devices that didn't show up in the BIOS until the firmware/driver was installed. I will try your suggestion and get back with you. Really appreciate the help.

---

### Post by Cpierce on 2009-12-04
I tried this and it still does not see the card. I added "use audio devices" to user and groups, rebooted but it made no difference.
From what I read, I believe I need to download the ALSA driver for this card and then modify etc/mod but I don't know how to do this.

---

### Post by Cpierce on 2009-12-07
Does anyone else have any suggestions ?

---

### Post by Cpierce on 2009-12-08
Hello...............anyone out there ?

---

