---
title: "check if graphics card is in use"
date: 2011-05-22
forum: Hardware
---

### Post by bro on 2011-05-22
I installed bumblebee to work with my two graphic cards (Nvidia optimus). 

I can find both cards and still have 3d with intel, so that looks good. The lspci | grep VGA shows both. 

With what command can I check which card is in actual use at the moment/for any specific program? 

A second question. How can I check performance? glxgears gives me output, but not for optirun64 glxgears since it just gives the optirun output 'bumblebee on.. ok'

---

### Post by belltown on 2011-05-22
> **bro said:**
> With what command can I check which card is in actual use at the moment/for any specific program? '
```

**egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log**

```

---

### Post by bro on 2011-05-22
Thanks. That is Intel. Does this mean the Nvidia isn't using any battery at the moment either?

---

### Post by belltown on 2011-05-22
> **bro said:**
> Thanks. That is Intel. Does this mean the Nvidia isn't using any battery at the moment either?

No, it just indicates which driver is in use, not whether the unused card is still being powered.

Try this:

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```It should show something like this:

```

$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```IGD refers to the integrated graphics card (intel), in use (+), powered on
DIS refers to the discrete graphics card (radeon in my case), not in use, powered off

To un-power the discrete card type:

```

sudo su
echo OFF>/sys/kernel/debug/vgaswitcheroo/switch
```

---

### Post by bro on 2011-05-22
Ach.. unfortunately that doesn't work. 'no such file or directory'

---

