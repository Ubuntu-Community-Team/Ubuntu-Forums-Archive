---
title: "TV on ubuntu (?)"
date: 2008-08-08
forum: General Help
---

### Post by realizee on 2008-08-08
Hi, 

I've got a Emtec S810 that I like to use on Ubuntu, I couldn't make it work on XP Pro. 
Is there anyone who knows how to deal with this? 
Thanks :P

---

### Post by damoxc on 2008-08-08
check to see if it's supported by running:

```
cat /var/log/messages | dvb
```

You should see some output saying it's been registered.

If it is then do the following:
```

sudo -s -H
apt-get install dvb-utils
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > channels.conf
exit
cp channels.conf ~/.gstreamer-0.10/dvb-channels.conf

```

Replace uk-WinterHill with your nearest TV mast, and then you'll be able to watch TV via Totem.

---

### Post by sharma2008 on 2008-08-08
i dnt hv idea..

---

### Post by realizee on 2008-08-08
```
cat /var/log/messages | dvb
```


it says 
```
bash: dvb: command not found
```

---

### Post by damoxc on 2008-08-08
sorry, forgot to put grep in, just run:
```
grep dvb /var/log/messages
```

That'll do the same thing

---

### Post by realizee on 2008-08-08
```
grep dvb /var/log/messages
```

If theres comes up a new line does that mean that it's OK?

---

### Post by damoxc on 2008-08-08
You should get some output stating that your card has been detected, which if there was none, means it wasn't. You should probably do a search to check the support of your card under linux.

---

### Post by Sycron on 2008-08-08
You may try this but I don'k know if will work since I don't tested it...
[http://lists-archives.org/video4linux/21813-support-for-dvb-t-usb-device-emtec-s810.html](http://lists-archives.org/video4linux/21813-support-for-dvb-t-usb-device-emtec-s810.html)

---

