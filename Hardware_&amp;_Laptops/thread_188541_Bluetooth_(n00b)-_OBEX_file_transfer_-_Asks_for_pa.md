---
title: "Bluetooth (n00b)- OBEX file transfer - Asks for password on the cellphone."
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-06-04
Hi There,

!!!USING KUBUNTU!!!

First - I'm a complete bluetooth-noob! - Haven't tried it on Windows!

If I wan't to transfer files between the computer and the cellphone, I assume that I should use "OBEX file transfer!"???

I have a standard Bluetooth-dongle, and a cellphone (Sony Ericsson K700i)

Trying to open a "OBEX file transfer" to the phone, asks for a password on the cellphone...

What is that password? (Tried "123", and a lot of other passwords)
...even made my users password "123" - No luck!
...Dongle-specific? - I really have NO clue!

Please HELP!

---

### Post by kwaanens on 2006-06-04
Try 0000 as the password. That was it on my K750i

- Ketil

---

### Post by daller on 2006-06-04
I've tried both "0000" and "1234" as suggested elsewhere... 

So far - No luck!

---

### Post by ToniVR on 2006-09-01
You got to set the pin:

```
sudo vi /etc/bluetooth/pin
```

and enter it on your phone and on your computer when connecting. (Don't know why it is asked twice)

Also, make sure bluez-pin is installed.

---

### Post by daller on 2006-09-01
I'm afraid it's the same over and over again...

The file holds "0000" - and that password doesn't work!

I can send files to the phone, but I can't connect and see the content of the phone...

---

