---
title: "No suspend on lid close, no Fn keys unless running on battery"
date: 2014-01-14
forum: Hardware
---

### Post by katibkitab on 2014-01-14
The title says all
I have a netbook Medion Akoya E1222
I tried U/X/Lubuntu 10.10, 11.10, 12.10
No  suspend on lid close, no Fn keys while running AC power, but  If I  reboot using battery, WITHOUT changing ANY setting, I have suspend on  lid close, and Fn keys working (brightness, volume, external monitor,  suspend...)
This happens even booting a live system on usb !!
The only kernel working regardless power source AC or battery is 2.6.31.14 on ubuntu netbook remix 9.10, Even the next one 2.6.35.22 didnot work
This affects all distros I have tried so far
I tried all combinations of acpi_backlight, acpi_osi... etc No luck! The only fix is to use battery !  

Any idea?
Thanks

---

### Post by Kirboosy on 2014-01-15
Have you tried changing the power settings under System Settings?

By default on AC power the laptop will do nothing when you shut the lid but on battery power it will suspend. I know on Xubuntu I can go under the power options and specify what I want it to do. 

As for the FN keys. Is your laptop setup so it does FN keys by default or do you have to hold the FN key down to access the FN key functions?

Hope that helps!
~Caboose

---

### Post by katibkitab on 2014-01-15
Thanks for reply
On my netbook, I have to hold FN key plus F2, or F3 ..etc
The Power manager is set to suspend on Lid close both on Ac and battery. Furthermore, without changing anything, if I reboot on battery, all FN keys and suspend on lid close works again.

---

### Post by Kirboosy on 2014-01-15
I'm wondering if that isn't somehow related to this bug.

[Arch Linux Bug]("https://bbs.archlinux.org/viewtopic.php?pid=1086769")

The way the guy works around his issue is by suspending the laptop and turning it back on. That seems to clear it up for him.

Also have you tried the most recent version of Ubuntu? The only version still supported in your list is 12.04.

~Caboose
PS Welcome to the forums! :D

---

### Post by katibkitab on 2014-01-15
Thank you again
The story of the other guy is differente from mine
for me: on the same system, same settings Lid events and FN keys are proprely handled when using battery. On AC they are simply ignored

---

### Post by codenine75a on 2014-01-15
I would just eat some soft serve ice cream and wait for April's update.  What do I know I am just a computer operator not a linux movement person.

---

### Post by katibkitab on 2014-01-17
The followings tests may give you more clues about my problem:
I used a live distro: I put the ubuntu 13.04 iso onto usb
After  booting using AC power, there is no suspend on lid close and FN+ F2, F3..  keys dont work for controling btightness, volume.. etc
Then I booted the same iso using battery, suspend on lid close is working alongside FN+ F2, F3.. keys !!!
So is there any scripts ot modules loaded by kernel when using battery and not loaded on AC power ?

---

### Post by katibkitab on 2014-01-20
Any idea please!
Yesterday, I booted a live sytem xubuntu-12.04.2-desktop-i386 from usb
Using battery:  Function keys and suspend on lid close work perfect
Using using AC power: Function keys and suspend on lid close dont  work :(

---

### Post by katibkitab on 2014-01-31
Given modern kernels work good (detect FN keys, lid actions..) provided running battery, 
can someone tell differences between booting on battey and booting on AC power?
In  other words: Is there any additional scripts/modules linux runs (or  doesnot run) while booting on battery? if so is there any log file where  can I track such differences?

---

