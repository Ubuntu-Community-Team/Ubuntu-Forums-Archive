---
title: "Brother MFC-255CW Scanner"
date: 2012-03-26
forum: Hardware
---

### Post by Baldrick_NZ on 2012-03-26
Hi all,

Having successfully installed the Linux drivers from the Brother website, I'm now faced with the onerous honour of installing the scanner drivers. Onerous, because the printer drivers were a breeze by comparison.

I'm installing to the 12.04beta1 release, but my understanding is it should be the same process for any Unity release (11.04 & 11.10).

The are some tutorials for pre-Unity days here on the forums, but none have helped so far.

I have downloaded and installed both 'brscan-skey-0.2.3-0.i386' and 'brscan-0.2.4-0.i386' .deb files from the official Brother website.

Any help to get this going would be very much appreciated..

Thanks in advance.

---

### Post by dandnsmith on 2012-03-27
Are you trying to scan with Xsane/Sane, or even SimpleScan?

Excuse my ignorance, but, so far, I've avoided trying to use Multi-function printers with linux (apart from printing).

---

### Post by Baldrick_NZ on 2012-03-27
Hi, I'd be happy to use either, but neither seem to work.

---

### Post by dandnsmith on 2012-03-28
Have you checked whether the existence of the 'scanner' is recognised - the SANE man page and documentation gives guidance on how to do this?

---

### Post by SheamusPatt on 2012-05-21
You have to do more than just install the driver for these Brother network printers - you need to configure the device as well.

You can test if that's been done by the command:
  brsaneconfig3 -q

You should see your scanner at the end of the list. If it's not there, configure it e.g.

  brsaneconfig3  -a  name=MFC255_SCAN  model=MFC-255CW  ip=xx.xx.xx.xx
or
  brsaneconfig3  -a  name=MFC255_SCAN  model=MFC-255CW  nodename=BRNxxxx

It's better to use a nodename for configuration than ip if you're on DHCP since it won't change. You should be able to find it on the settings of  your printer under TCP/IP (at least, my 295CN works that way). Or  you can run nbtscan:

  nbtscan 192.168.0.0/24 # change to match your network

 The details are on Brother's website, [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html) . 

Once it's set up, I've been pretty happy with my Brother printer. It is a bit of a pain to configure, though; HP does a much better job of getting their support integrated into distributions like Ubuntu.

---

