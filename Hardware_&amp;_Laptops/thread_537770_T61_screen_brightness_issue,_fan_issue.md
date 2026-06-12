---
title: "T61 screen brightness issue, fan issue"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by kachofool on 2007-08-29
I've been following the ThinkWiki on settings up Gutsy Gibbon on the Thinkpad T61. I am completely new to Linux, so if you reply please don't give me advanced instructions. The main problems I have right now are adjusting brightness and that the fan is constantly on. Brightness never worked... however after installing updates (I guess it updated the kernel too), the fan has been running constantly. Also when it finished updating everything, the sound and video drivers had to be reinstalled. Anyways,

For brightness control, I tried:

echo "down" >/proc/acpi/ibm/brightness

from terminal and console and I get "Permission Denied". I haven't tried messing with the fan. I should also note that the ibm folder was never in the acpi folder until I typed in
 
"# modprobe thinkpad_acpi"

 I'm guessing this has something to do with the rename of ibm_acpi to thinkpad_acpi... also, I have no idea whether or not I was supposed to type in that modprobe thing in the first place. I don't know what it does, but I saw it on some Gentoo site so I tried it out. I also found a patch on the original ibm_acpi website. I can open it up in a textfile... I don't know what I'm supposed to do with it. Would appreciate some help (and maybe some words on what modprobe is?)

---

### Post by kachofool on 2007-08-29
Okay, if I could ask a more general question, how do I get /proc/acpi/ibm working?
After a restart, the dir is gone...

TiA
Kf

---

