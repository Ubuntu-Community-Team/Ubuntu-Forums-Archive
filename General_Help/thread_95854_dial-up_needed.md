---
title: "dial-up needed"
date: 2005-11-27
forum: General Help
---

### Post by Fittersman on 2005-11-27
in ubuntu's device manager thing it had my modem listed there but when in system > administration > networking when i try and set up a modem connection i press autodetect but it cant find it. Whats up with that?

its an Agere winmodem

im on ubuntu 5.10

if you need more info about my problem tell me plesea

---

### Post by ruffneck on 2005-11-27
Did you try looking in here for help?

[http://www.ubuntuforums.org/showthread.php?t=95176](http://www.ubuntuforums.org/showthread.php?t=95176)

---

### Post by Bachstelze on 2005-11-27
Hey, Fittersman, how many times will you make me repeat this ? 


First, download this tool : [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

copy it onto your Ubuntu system, ru a terminal in the directory with scanmodem.gz and run those three commands

```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

Normally, you will have a Modem directory created with a bunch of files in it. Send an email to [email]discuss@linmodems.org[/email] asking for help with the ModemData.txt file as an attachement. You might have to register on the mailing list before sending, though. (for this send an e-mail with SUBSCRIBE as subject to [email]discuss-subscribe@linmodems.org[/email])

You can also post the content of your modemdata.rxt here, maybe I'll be able to help you

---

### Post by Fittersman on 2005-11-27
and how many times to i have to tell you that gunzip dont work cuz im not qualified enough?:mad:

---

### Post by Bachstelze on 2005-11-27
what does the Terminal tell you when you try to run gunzip ? (I want a copy/paste here !). Did you save the file to your home folder ?

---

### Post by Fittersman on 2005-11-29
no i was trying to run it off of my floppy i will try and take it to my home folder

---

