---
title: "Self Compiling Intel536EP Modem Driver"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by rob_connolly on 2008-02-09
Hi Everyone,

Over the time I have used Ubuntu (and other distros before it) I have been annoyed by my Intel536 modem every time I have reinstalled to upgrade my system. I recently decided to scratch my itch, by creating a self compiling deb file that would therefore work with each new kernel.

I now post it here in the hope that it will be useful for others. It's only dependencies are build-essential and linux-headers-generic, which should be on the install disk. The deb file has so far only been tested on gutsy, but hopefully it should work on anything with a generic kernel.

To install all you need to do is download the file (on another computer if the modem is your only connection to the outside world). Once you have the file click on it to launch the gdebi package installer and click install package in top left corner of the window. The driver will then be extracted, compiled and installed.

You will then need to follow the instructions at [https://help.ubuntu.com/community/DialupModemHowto/Intel536EP#head-65a431db112d3b53e6020f57b22d88c33e4b72d0](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP#head-65a431db112d3b53e6020f57b22d88c33e4b72d0) to configure your connection.

If anyone has any questions feel free to post them below. My next step with this project is to be able to manage the driver through the Restricted Driver Manager, so if anyone has any info on this it would be appreciated.

Hope this is helpful.

Cheers,

Rob

---

