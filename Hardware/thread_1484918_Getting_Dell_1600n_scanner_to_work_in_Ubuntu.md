---
title: "Getting Dell 1600n scanner to work in Ubuntu"
date: 2010-05-16
forum: Hardware
---

### Post by avestboe on 2010-05-16
I am having some problems getting the scanner in my Dell 1600n multi-function printer to work in Ubuntu. I realize that this is a problem that several people have encountered, since I have searched the forums for answers. However, I still cannot get it to work (printing works fine though).

I have read that there is a perl script on [http://www.jon.demon.co.uk/dell1600n-net-scan/](http://www.jon.demon.co.uk/dell1600n-net-scan/), that should work. So I have downloaded it, and attempt to install it, by typing:

perl dell1600n-net-scan.pl --listen localhost

using 'localhost' as the address for my printer. I do not have a network, the printer is just connected through a usb cable. I guess that is the way to specify the printer's address.

It then responds with an error saying a "usleep" sub-routine is missing. In the script this comes from a line that says: "usleep(100)". I then tried to change this to "sleep(0.1)". Anyway, when running it, it just stalls, and nothing happens. I let it stay in the background, and try to scan using 'Simple Scan', but the scanner is not available.

Can anyone help? I am a total newbie to Ubuntu and Linux (installed it yesterday).

---

