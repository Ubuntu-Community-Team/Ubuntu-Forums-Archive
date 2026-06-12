---
title: "My wired connection keeps disconnecting randomly even when the cable is plugged-in"
date: 2013-05-31
forum: Hardware
---

### Post by P Maneesha on 2013-05-31
Hi,
      My wired connection keeps disconnecting randomly say in  about an hour or two.And the connection which shows 'connected' shows  'cable unplugged',though the cable is plugged in,without my doing  anything(sometimes due to my very slight disturbing of the cable). I  tried reinstalling the os several times but did not help.To establish the connection again I need to restart the system random number of times(usually 4 to 10 times :( ) and just hope the internet connection is established.It is really annoying to restart my system that many times and for every hour or two.Is this a hardware problem?If so what should I do.Plz help me in this.Thanks in advance :).

---

### Post by sanderj on 2013-05-31
replace the cable with a new, good one?

---

### Post by P Maneesha on 2013-05-31
Thanks but sorry to say i replaced 4 till now and don't think that is the problem.Thanks.

---

### Post by sudodus on 2013-06-04
Reading your description, I would guess it's bad electrical connection (like *sanderj*). If it is the same problem with another cable, maybe one of the connecting strips in the port of the computer or the router is damaged or slightly displaced.

---

### Post by P Maneesha on 2013-06-04
Thanks for your reply.If the problem is with my computer,can i do something about it or i need to change whole motherboard.

---

### Post by sanderj on 2013-06-04
> **P Maneesha said:**
> Thanks for your reply.If the problem is with my computer,can i do something about it or i need to change whole motherboard.

Is it a desktop? If so: put an el-cheapo (5 euro) NIC, and see if that solves it.

Also swap router/switch if the other NIC does not help.

EDIT:
If you only have a USB port, you could try something like: [http://www.edimax.com/en/produce_list.php?pl1_id=5&pl2_id=26](http://www.edimax.com/en/produce_list.php?pl1_id=5&pl2_id=26) or [http://dx.com/p/usb-10-100-rj45-ethernet-network-adapter-dongle-2797](http://dx.com/p/usb-10-100-rj45-ethernet-network-adapter-dongle-2797)

---

### Post by sudodus on 2013-06-04
What computer is it?

- If it is a desktop computer, there are cheap ethernet cards to plug in.

- If it is a laptop, there are usb-to-ethernet adapters (small like usb pendrives) to plug in.

---

### Post by P Maneesha on 2013-06-04
Thanks a lot :D.I did not know about a usb-ethernet adapter before(its best in my case). Thanks sandrej and sudodus for your help.

---

### Post by sudodus on 2013-06-04
You are welcome :-)

Please let us know how it works for you (share the result with the Ubuntu Forums community)

---

### Post by MrBackhand on 2013-06-04
Not very much went into diagnosing the problem with your nic before you were told to get a new one.  Maybe you need a new driver.  What kind of nic is it?  I have a RTL8169 and I had to install the 8188 driver to fix a similar problem.  On the command line type: 
dmesg | grep eth 

Look up the model/type and make sure there's not an easy cheap fix.  :)

Hope this helps!

---

