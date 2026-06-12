---
title: "Touchpad disable/enabling problem"
date: 2012-01-24
forum: Hardware
---

### Post by hannnndy on 2012-01-24
Hi all :),
Recently I have a Dell N5110 Laptop,

I have a problem with my touch-pad enable & disabling when I use Fn+F3 which is the shortcut for doing that it does not work only a notification appears at the right-top corner of my display, 

It seems ubuntu 11.10 has not any plan for this 

I googled my problem and just fined a script

disabling my touch pad:

```
$ sudo xinput --set-prop 14 'Device Enabled' 0
```

enabling my touch pad:

```
$ sudo xinput --set-prop 14 'Device Enabled' 1
```

this script solves my problem but the main problem still remains 
1. how can I map this script tp Fn+F3 shortcut?
2. has ubuntu any plan to solve this problem via a patch or something?

Regards,
Moi

---

### Post by hannnndy on 2012-02-03
I used this it works too 

```
xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0
```

but myproblem still remains!

---

### Post by GraeW on 2012-02-03
as I understand it, the Fn+X keys for volume, touchpad, brightness, monitor select, etc - are a proprietary control set up by the OEM. There may be a way to map the keys through your desktop manager/environment (I know XFCE does have optional keyboard shortcuts which can be edited through the system settings).
 
I have a finicky touchpad on my aging laptop, and just added a startup to my session manager to disable it (have to search the threads for "synclient" I think it was).

---

### Post by hannnndy on 2012-02-04
Do you know exactly what should I do?
I mean I should modify something or config somewhere?

---

