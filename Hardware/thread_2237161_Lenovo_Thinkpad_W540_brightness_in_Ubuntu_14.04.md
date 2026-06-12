---
title: "Lenovo Thinkpad W540 brightness in Ubuntu 14.04"
date: 2014-07-31
forum: Hardware
---

### Post by samer3 on 2014-07-31
Fresh install of 14.04 on new Lenovo Thinkpad W540 with the last bios available nowadays (*). Everything working fine (after standard [installation of Bumblebee for 14.04]("http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04"), with open source nvidia drivers) except the brightness: no brightness slider in Settings=>Brightness & Lock, empty /sys/class/backlight/ , and trying different solutions found online didn't help (adding parameters to /etc/default/grub). Eventually, the whole problem was that I had in grub **GRUB_CMDLINE_LINUX="nomodeset"**, which Ubuntu had inserted automatically (probably because before the installation, when booting from the USB the Ubuntu 14.04, I needed to activate nomodeset in order to see the screen and start the installation). After I left **GRUB_CMDLINE_LINUX=""** along with the default GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", everything worked like a charm. I leave this here in case it can help. 

(*): 
```

aa@aa-Thinkpad-W540:~$ sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date
GNET65WW (2.13 )
06/20/2014

```

---

