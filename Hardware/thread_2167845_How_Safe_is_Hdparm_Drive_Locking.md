---
title: "How Safe is Hdparm Drive Locking?"
date: 2013-08-15
forum: Hardware
---

### Post by sdpagent on 2013-08-15
I discovered the hdparm drive locking feature on my WD drives. I can enable a password by using the following command:
```
hdparm --user-master u --security-set-pass (your-password-here) /dev/sdx
```
(replace sdx with your drive letter).
When this is enabled, if you turn off your computer, you cannot load your drives. If anything they can be appear 'dead'. To unlock them, you have to run:
```
hdparm --security-unlock (YOUR PASSWORD HERE) /dev/sdx
```
and in order to permanently unlock them, you have to run that command before running:
```
hdparm --security-disable (YOUR PASSWORD HERE) /dev/sdx
```

I would like to know how 'safe' this is, considering that I have not encrypted the data. It's likely to prevent average-joe from accessing your data if he steals your machine, but would it be able to prevent a private security agency if they were **not** unable to brute force your password?

Regards,
Stu

---

### Post by tgalati4 on 2013-08-15
If the password is stored in the firmware of the drive, then one could presumably take the platters out of one tray and place them in another to read the data.  If the password is stored on the drive, then presumably one could hack the firmware of the drive to ignore it.  So one would have to assume that without physical security, your data is at a small risk with a simple password.

A much bigger risk, in my opinion, is simple use of the computer while connected to the internet.  A keylogger would simply capture your hdparm commands, including a hard disk password, which defeats the purpose of this type of security.

---

