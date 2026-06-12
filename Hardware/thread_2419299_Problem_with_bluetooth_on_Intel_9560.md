---
title: "Problem with bluetooth on Intel 9560"
date: 2019-05-19
forum: Hardware
---

### Post by collin80 on 2019-05-19
I have a Dell G7 laptop that utilizes the Intel 9560 wireless hardware. I was previously using Linux Mint 19.1 and my Logitech MX 2 Anywhere bluetooth mouse was working fine. But, wifi performance sucked. I would get at most 20 megabits per second on a 150Mb/s cable modem and sometimes it would really lag and sputter and just annoy me. For that and other reasons I switched to Ubuntu 19.04 so I could take better advantage of the fairly new hardware in this laptop. Well, everything works really, really well except bluetooth. Wifi is MUCH improved now. The mouse will never successfully pair with the computer even though the mouse shows up in the list of devices. When the mouse is trying to pair I get many lines like below:

[  584.294335] Bluetooth: hci0: request failed to create LE connection: status 0x0c

Obviously this is super annoying as this hardware worked perfectly fine for bluetooth in Linux Mint 19.1 so obviously someone mucking about in the kernel drivers broke something in the intervening versions. But, what can I do? It seems a bit odd that Ubuntu is sticking with 5.0.0 instead of going to 5.0.17 which may or may not fix the firmware glitch. I thought about going to mainline drivers but this machine has an nVidia Geforce 1060 in it and I'd rather be able to use the nvidia driver if possible. Has anyone run into something like this on 19.04? Should I uninstall the nvidia driver and try a newer mainline kernel?

---

### Post by wildmanne39 on 2019-05-19
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by vicamo on 2019-05-20
> **collin80 said:**
> 
[  584.294335] Bluetooth: hci0: request failed to create LE connection: status 0x0c


Please see [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1829737](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1829737) . Basically you need [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/?id=29a536a02cadb75b84c6c0b5d7af22d34d278563](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/?id=29a536a02cadb75b84c6c0b5d7af22d34d278563) to fix this issue.

---

### Post by collin80 on 2019-05-20
Awesome! Thank you! It worked. Here is what I did:

I went to /usr/lib/firmware/intel and created a directory called backup. I did cp ibt*.* ./backup to save all the ibt files. Then I downloaded the linux_firmware files from the link you provided and extracted all ibt files to a folder. Then I copied all the ibt files from that folder into the proper folder /usr/lib/firmware/intel and powered down. Upon powering back up I was able to connect to the mouse. SUCCESS!

---

