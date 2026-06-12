---
title: "LTSP Client Configuration"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by sogotech on 2007-07-31
So I've recently installed Ubuntu (Fiesty) on an HP DL360 G5 to act as terminal server for 5 workstations which need Linux development environments (mainly Eclipse). All 5 of the workstations are HP xw4400 (pretty powerful machines) that have WinXP installed on their respective local HDDs. Following the [LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall") with some slight modifications to /etc/ltsp/dhcp.conf I now have 5 PXE booting thin (i.e. not using their local HDD) clients - whew that was easy! :)

Now, the real problem is I'm not quite sure how I can go about "tweaking" the client machines for X11. All 5 machines have ATI FireGL V3300 cards and I'm not quite sure exactly how to go about configuring the client machines to use the driver from ATI (fglrx) instead of the built-in X11 (ati) driver. Anyone able to point me in the right direction?

PS - I have pretty advanced linux experience and can manage to poke my way around and figure things out (like how /etc/ltsp/dhcp.conf overrides any settings in /etc/dhcp3/dhcp.conf ... that took a minute) but I just can't manage to figure this one out (LTSP is all new to me)

---

### Post by itchy8me on 2007-08-02
Hey there.

Im trying to do exactly the same thing. ei. activate my 3d ati card on the client side. If you have figured it out then i would really appreciate if you let me know how :)

greets wernher

---

### Post by krotaz on 2007-08-05
hi sogotech I'd really apreciate if you can share with me your dhcp, tftp, nfs & init files becuase I followed the same tutorial that you used but I can't boot the thin client it sends me a 

TFTP open timeout

Thanks

---

### Post by markking on 2008-04-02
Edit your /etc/inetd.conf

$ sudo gedit /etc/inetd.conf

then add this line under #BOOT : TFTP service if it's not there.

tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

reagrds

---

