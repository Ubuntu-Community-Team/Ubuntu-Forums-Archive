---
title: "Toshiba Satellite M50: Cannot run toshset!"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by anasofiapaixao on 2006-07-25
[*sigh* WHY have I to be the one having the weird problems NO ONE in the world wide web ever has to talk about?...]

I have (another) problem with Bluetooth (well, toshset actually), this time with a Toshiba Satellite M50.

Everytime I run toshset, I get this fancy message followed by exit:

```
required kernel toshiba support not enabled
```

Whenever I try to configure toshset through the module-assistant (something I somehow think I saw somewhere in a [german site]("http://mail-archive.com/talk@pug.org/msg32197.html") - no I don't know a word of german, yes, the only search result for error message string in google, and yes, total level of desperation) using THIS command:

```
sudo m-a auto-install toshset
```

I get this message:

```
The source tarball could not be found!
Package toshset not installed?
Running "m-a -f get toshset" may help.
```

(No, it doesn't help, in practice looks to me like an apt-get install toshset with a different name)

First it told me it couldn't find /usr/src/modules. Maybe I did sometng stupid, but I copied /lib/modules to that location. Then it told me it couldn't find /usr/src/modules/tosh* with the message above. So I got the source tar.gz, both packed and unpacked to cover any case, to that folder. No avail.

What's wrong?

---

### Post by anasofiapaixao on 2006-07-28
Just putting back on top as I added some important things... (thank god here we're not banned for double posting)

---

### Post by chris_c28 on 2006-07-30
The Satellite M50 is not a true blue Toshiba laptop, hence it doesn't support the Toshiba kernel modules. Basically, all Toshibas with the Phoenix BIOS do not support these modules as they are not developed by Toshiba.

I am using the M50 too and Ubuntu works great except for Bluetooth, which I can't get working either.

If anybody gets their Phoenix BIOS Toshibas working with Bluetooth, I'd like to know. My M50 has a CSR internal USB bluetooth module, but it's not detected even after enabling it under Windows.

---

### Post by anasofiapaixao on 2006-07-30
Oh dear lord... So the M50 DOESN'T have a Toshiba BIOS...


I never got it to work under windows either, if memory is not failing me. The problem is I can't go whine to to Toshiba's support center as they will probably tell me the "you built-in bluetooth device was designed for Microsoft Windows XP" bullshit, or something similar. As that computer isn't even dual-booting, I would have to re-install XP...

---

### Post by chris_c28 on 2006-07-31
> **anasofiapaixao said:**
> Oh dear lord... So the M50 DOESN'T have a Toshiba BIOS...


I never got it to work under windows either, if memory is not failing me. The problem is I can't go whine to to Toshiba's support center as they will probably tell me the "you built-in bluetooth device was designed for Microsoft Windows XP" bullshit, or something similar. As that computer isn't even dual-booting, I would have to re-install XP...

Ubuntu actually works perfectly on mine, except for the Bluetooth. Battery life is really bad though. Might have to try undervolting.

---

### Post by anasofiapaixao on 2006-08-04
Undervolting? You mean the current intensity consumed by the pc? You got me curious, how can that be done?

---

### Post by chris_c28 on 2006-08-18
Breakthrough! I got bluetooth working, but it's still not perfect. It requires you to boot into Windows, turn on bluetooth, then "restart" into Ubuntu. It should then be detected automatically (if you have the bluez tools installed). If you select shut down instead of restarting in Windows, it will not work (the bluetooth dongle switches off). It also will not work after rebooting Ubuntu (switches off again). 
Is there a way we can control this behaviour or at least keep the bluetooth permanently switched on.

---

### Post by anasofiapaixao on 2006-08-22
OMG... I don't have windows installed ](*,) never tought one day I could be sorry for it lol. Plus I culd never get it to work even in windows, how did you do that?

---

