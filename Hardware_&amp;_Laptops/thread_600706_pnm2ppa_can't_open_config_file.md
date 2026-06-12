---
title: "pnm2ppa can't open config file"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by Wayne Attwood on 2007-11-02
I have an HP 710C printer, when trying to do a test print nothing happens? I have checked the pnm2ppa.conf file to confirm that the correct version entry "version 710" line is there. Then to the syslog and the lpr log and i find the following entry:

Nov 2 01:27:08 Edgar pnm2ppa[6457]: read_config_file(): couldn't open config file

i have done a "sudo chmod 666 pnm2ppa.conf"

-rw-rw-rw- 1 root root 7648 2007-11-02 01:28 pnm2ppa.conf

seems to make no difference, not sure what to do next? pls help.

Using CUPS if that helps?

Running Kubumtu 7.10

---

