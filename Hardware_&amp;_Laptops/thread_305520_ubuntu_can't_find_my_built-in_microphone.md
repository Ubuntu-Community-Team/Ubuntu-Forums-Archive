---
title: "ubuntu can't find my built-in microphone"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by myoldryn on 2006-11-23
Hi. I have FS si1520. Everything works just fine, except the built-in microphone. Ubuntu just can't find it. There is no sign of it in dmesg output and device manager. Does anybody have the same problem.

Datasheet: [http://server-uk.imrworldwide.com/cgi-bin/b?cg=COM-complete&ci=siemensfujitsu&tu=http://www.fujitsu-siemens.com/Resources/173/1127099518.pdf]("http://server-uk.imrworldwide.com/cgi-bin/b?cg=COM-complete&ci=siemensfujitsu&tu=http://www.fujitsu-siemens.com/Resources/173/1127099518.pdf")

---

### Post by JayTee on 2006-11-24
Try setting your capture device to line-in in alsamixer from the command line, alsamixer isn't gui but it's kinda graphical in nature. If you don't like using the command line you could download alsamixergui from the repos. Also try switching back to mic input in alsamixer if line-in doesn't work and make sure the volume for MUX is at least 50% or higher. According to the specs for your sound  chip it's sharing line-in and mic. It should show up in Device Manager as Azalia or Intel HDA ICH6 and if a capture device is listed there it means it's recognized. dmesg doesn't list my mic either but it works. NOTE: MUX is not the same as Mic or Line-In volume. It's a separate control setting on the far right side of the alsamixer interface.

---

