---
title: "How do I calibrate my wacom device in Natty"
date: 2011-08-10
forum: Hardware
---

### Post by nego0 on 2011-08-10
I'm using a CTE-430 and tried to re calibrate with some thing i found on another forum.
```
esmania@desmania-MS-7100:~$ sudo apt-get install wacom-tools xserver-xorg-input-wacom
[sudo] password for desmania: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wacom-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xserver-xorg-input-wacom

E: Package 'wacom-tools' has no installation candidate

```

but didn't work 
can anyone help?

Thank you

---

### Post by Favux on 2011-08-10
Hi nego0,

The wacom-tools package hasn't been available since Lucid.  That's because Lucid has Xserver 1.7 and they switched the Wacom X driver from linuxwacom to Xorg's xf86-input-wacom then.  And xf86-input-wacom dropped wacom-tools which used to have wacomcpl (Wacom Control Panel) which included the calibration tool.  With Natty you can use xinput-calibrator instead, which is in the Universe repository.  Information on Calibration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)

The rest of the HOW TOs:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

