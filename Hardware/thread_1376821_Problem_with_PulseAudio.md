---
title: "Problem with PulseAudio"
date: 2010-01-09
forum: Hardware
---

### Post by giskar on 2010-01-09
Hi guys, I have connected BT headset (used Blueman) and I try to bring all sounds to it device. I take this instruction [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)
Everything goes fine until the step 16:

```

If not already connected, click on the Connect button to connect to your local PulseAudio server. When connected, you will see details about it listed.

```

As I understand, I need to connect to default server and I do it. Furthermore, I need to go to the Device tab and there I would see my BT headset...but it is not there:sad:


```

cat ~/.asoundrc

pcm.btheadset {
        type bluetooth
        device 00:33:44:DD:EE:FF    # MAC of my BT headset
        profile “auto”
}

```

Who's know what problem?  File .asoundrc must locate in user home directory or in root directory? And why after connection my BT headset I don't see it in cat/proc/asound/cards:

```

$ sudo cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 22

```
 

How can I add my headset???

---

### Post by rsk02 on 2010-01-10
What version of Ubuntu are you using? BT works out-of-the-box on Karmic.

---

### Post by giskar on 2010-01-10
> **rsk02 said:**
> What version of Ubuntu are you using? BT works out-of-the-box on Karmic.


I use Ubuntu 9.4.

$ uname -a
Linux giskar-laptop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux

---

