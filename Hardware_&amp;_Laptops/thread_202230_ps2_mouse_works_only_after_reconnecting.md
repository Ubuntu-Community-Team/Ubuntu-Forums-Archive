---
title: "ps/2 mouse works only after reconnecting"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by mI3O on 2006-06-23
I have this problem:
After Ubuntu start I can see the mouse cursor but I cannot move with it. But when I disconnect the mouse cable and then plug it again in, it works properly. Then it works also after ctrl+alt+backspace but not after restart. After restart it is always the same - I cannot move the cursor.
I'm sure this is not the problem of configurating xorg.conf.
thanks for every reply

---

### Post by mI3O on 2006-06-23
I have old Compaq mouse with 2 buttons and wheel. It works well In Ubuntu 5.10, knoppix, Ubuntu 5.10 Live cd, but it doesn't work in Ubuntu 6.06 Live cd (and of course in Ubuntu Dapper Drake)

---

### Post by sawjew on 2006-06-25
I have the same problem with my Compaq Evo N400c laptop and a 2 button wheel mouse.  I think there is some sort of conflict between the joystick/toucpad and the PS2 mouse.  

This is an improvement over the situation with Windows 2000 on the same laptop though.  In Windows if I boot up with the PS2 mouse in I end up with no mouse at all and even plugging it in again doesn't work and the joystick doesn't work either, only a reboot without the mouse  in gets the joystick back.  

I tried disabling/enabling the use of multiple pointing devices in the Bios but this didn't seem to help either.

Sorry I'm not being very helpful but at least I can sympathise.

---

### Post by mI3O on 2006-06-27
I've been seeking through whole internet but the problem hasn't been solved yet. I think it isn't nice system if I have to reconnect my mouse always after my computer start. I should try another distro...

---

### Post by Dr. Feelgood on 2006-06-28
I'm having problems witrh this too.  My mouse doesn't work at all.  The only thing that works is my laptop touchpad.  Same thing, just a regular old mouse.

---

### Post by fparri on 2006-06-29
I've got the same problem. What kind of mouse do you guys have? Mine is a cheap Trust PS/2 optical mouse. It doesn't work at all under linux. If I try to disconnect it and then reconnect the sensor red light turns on for a while for a few seconds, then it turns off again.

Can you post the related contents of your /var/log/messages when you connect the mouse?

---

### Post by Dr. Feelgood on 2006-06-29
I found a solution that worked for me

```
sudo gedit /etc/rc.local
```

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart - should have your ps/2 mouse back

---

### Post by mI3O on 2006-07-06
to Dr. Feelgood:
your rc.local setting doesn't solve my problem. I've tried it but with no result..
to fparri:
/var/log/messages isn't changed when I connect mouse..

---

### Post by fparri on 2006-07-06
In my case, as soon as I turned off my laptop's touchpad in the bios settings, my PS/2 mouse started working... What could cause this?

---

