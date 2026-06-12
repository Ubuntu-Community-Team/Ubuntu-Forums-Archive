---
title: "Ubuntu and compiling a new kernel.. confused!"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by NinaN on 2009-01-23
Hi people!

Firstly, I have successfully installed Ubuntu 8.04 (Hardy Heron) onto my Thinkpad R50p laptop and everything runs great! :D I also updated the system so that my laptop is running with the newer 2.6.24-23-generic kernel.

However, I need to enable some extra networking features and so I need to make a custom kernel.. this is where my confusion begins :p

[LIST]
[*] I tried to follow the instructions on [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

The first apt-get install says I should install a package called "makedumpfile" but I can't seem to find it. Is this package necessary and where can I find it?


[*] I did "make oldconfig" but the script did not ask me what I wanted. Instead a new .config file was generated. I diff´ed this .config (which is now under /usr/src/linux) with /boot/config-2.6.24-23-generic and they dont appear to be identical? :confused::confused:  Shouldn't they be the same?



[*] Ubuntu tells me that my wireless is using the restricted drivers..I need madwifi for the new custom kernel. Is there a way to install madwifi from the existing 2.6.24-23-generic kernel so that I dont have to compile/install all the restricted drivers again? cos my new kernel is also 2.6.24 and I retrieved the source using "apt-get source linux-image-$(uname -r)"... I don't have too much diskspace left.. :(

[/LIST]


I'm a newbie to this forum so please go easy on me![-o< I hope I'm posting to the right forum area.. 



Nina

---

