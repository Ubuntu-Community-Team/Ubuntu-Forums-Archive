---
title: "Canon Pixma TS3122 scangearmp2 wireless problem"
date: 2019-03-26
forum: Hardware
---

### Post by neilpausa on 2019-03-26
This problem is baffling. Does anyone have any ideas?
I have just purchased a Canon Pixma TS3122 printer.
If I connect it directly to my computer via USB, scangearmp2 will find the scanner and work.
When I disconnect the USB cable, the computer cannot find the scanner wirelessly.
But I can print wirelessly just fine.
Does anyone have any suggestions?
I have downloaded and installed the following files from Canon
cnijfilter2_5.50-1_i386.deb
scangearmp2_3.50-1_i386.deb
My computer's info:
CPU~Dual core Intel Core2 Duo E7200 (-MCP-) speed/max~1725/2534 MHz Kernel~4.15.0-46-generic i686 Up~2:10 Mem~613.2/3015.6MB HDD~640.1GB(23.6% used) Procs~176 Client~Shell inxi~2.2.35
Thank you.
Neil

---

### Post by AnotherBrian on 2019-03-28
canon's pixma literature doesn't mention linux as a supported os.

---

### Post by brian_p on 2019-03-28
> **AnotherBrian said:**
> canon's pixma literature doesn't mention linux as a supported os.

Please give a reference for that.

---

### Post by nlona on 2019-03-29
> **neilpausa said:**
> This problem is baffling. Does anyone have any ideas?
I have just purchased a Canon Pixma TS3122 printer.
If I connect it directly to my computer via USB, scangearmp2 will find the scanner and work.
When I disconnect the USB cable, the computer cannot find the scanner wirelessly.
But I can print wirelessly just fine.
Does anyone have any suggestions?
I have downloaded and installed the following files from Canon
cnijfilter2_5.50-1_i386.deb
scangearmp2_3.50-1_i386.deb
My computer's info:
CPU~Dual core Intel Core2 Duo E7200 (-MCP-) speed/max~1725/2534 MHz Kernel~4.15.0-46-generic i686 Up~2:10 Mem~613.2/3015.6MB HDD~640.1GB(23.6% used) Procs~176 Client~Shell inxi~2.2.35
Thank you.
Neil
Uncomment backend net in /etc/sane.d/ddl.conf

Add scanner IP address in /etc/sane.d/net.conf
Reboot should work

---

