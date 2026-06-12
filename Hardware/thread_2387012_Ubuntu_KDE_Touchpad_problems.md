---
title: "Ubuntu KDE Touchpad problems"
date: 2018-03-13
forum: Hardware
---

### Post by milosjovanovic96 on 2018-03-13
Hey guys,

I have a laptop 510s 13ikb and while i'm using ubuntu on it, my touchpad acts weird. It's not precise and i'm pretty sure i have to configure driver or somethiing to make it work same as on my windows 10. On windows i have synaptics driver (clickpad v1.6 on SMB port). Can i download a driver for ubuntu that will work the same as the driver on my windows 10 ?

Thanks in advance

---

### Post by thehipho on 2018-03-13
You may be able to configure touchpad with: ```
sudo apt-get install kde-touchpad
```

Are you using Kubuntu? paste the output of: ```
inxi -Fxz
```

---

