---
title: "Graphic card temperature"
date: 2012-12-05
forum: Hardware
---

### Post by my.self on 2012-12-05
Hi,

currently I'm using my Dell Vostro 1710 which has a Nvidia GeForce 8600M GS Graphic card.
Installed is a Ubuntu 12.10 64Bit.

Is a graphic card temperature from 65° - 75° normal?

I only use the notebook for Software development. That means, some open text editors (Eclipse, TextEdit...) and one VirtualBox (Win7)...
And youtube ;-)

I have one monitor attached 1650x1080 and the integrated display has a resolution from 1920x1200 pixels.

I'm a bit scared since I already had three Hardware crashes within the last two years (under ubuntu).

Crahsed PC's:
Dell Vostro 1710 -> Mainborad/Graphic
Dell Datitute E6500-> Mainboard/Graphic
Dell Precission T3400 -> Mainboard

Cheers,
Stefan

---

### Post by verzx on 2012-12-05
Install jupiter, this helps power management so your graphics card isn't on constantly. Put it on Power Save mode and see if it makes a difference.
Then when you're playing games put it on the one you think will work best.

```
sudo add-apt-repository ppa:webupd8team/jupiter
```
```
sudo apt-get update
```
```
sudo apt-get install jupiter
```

---

### Post by kazakvasilij on 2012-12-05
Temperature over 65C isn't normal for this type of graphic cards. You have some problems with it. :(

---

### Post by my.self on 2012-12-05
If it isn't normal then there must be something terribly wrong with the entire Ubuntu distribution since all my three PC's have approximately the same graphic card temperature.

But this would be the explanation why I already had three Hardware crashes within the last two years (under ubuntu)

Attached you find a screenshot from the NVIDIA X Server Settings where you can see the temperature of my graphic card.
Personally I also think that it is too hot since I just started the PC 15 minutes ago and everything I've done so far was writing this reply!

---

### Post by Yellow Pasque on 2012-12-06
Yes, it's normal. The 8600 is a high-powered GPU, so it will run a bit hot, but it's made to withstand it. [http://nvidia.custhelp.com/app/answers/detail/a_id/2752/kw/temperature/](http://nvidia.custhelp.com/app/answers/detail/a_id/2752/kw/temperature/)

---

### Post by my.self on 2012-12-06
Thx!
You saved my day :)
As mentioned above I turned a little nervous after my second notebook had the same hardware crash (Mainborad/Graphiccard).

---

### Post by haqking on 2012-12-06
> **kazakvasilij said:**
> Temperature over 65C isn't normal for this type of graphic cards. You have some problems with it. :(

I smell FUD

To the OP, yeah its fine.

---

### Post by my.self on 2012-12-06
So no further crashes for me ?! :)

---

