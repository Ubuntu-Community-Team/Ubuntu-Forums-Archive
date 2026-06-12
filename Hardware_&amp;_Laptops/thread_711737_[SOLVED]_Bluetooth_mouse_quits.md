---
title: "[SOLVED] Bluetooth mouse quits"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by John Jason Jordan on 2008-02-29
I have two different bluetooth mice and regardless of which one I use it cuts out now and then. Usually I can get it working again with "sudo hidd --search." Today, however, that is not working. It always works again if I reboot.

One is a Logitech V270, and the other is a Razer Pro|Click Mobile. I much prefer the Razer, as the Logitech makes my bluetooth headphones cut out when I move the mouse. Note that the bluetooth headphones work flawlessly, so evidently bluetooth is working reasonably well. The mouse cut-out is unrelated to the headphones. For example, just a little while ago the Razer cut out, but the headphones have not even been turned on since the last time the computer was rebooted.

The error message I get from "sudo hidd --search" is:

jjj@Devil7:~$ sudo hidd --search
[sudo] password for jjj:
Searching ...
        Connecting to device 00:0F:F6:6C:6C:DB
Can't get device information: Operation already in progress

I have googled and found nothing specific. I really need some suggestions. Having to reboot to restore the mouse is not acceptable.

---

### Post by John Jason Jordan on 2008-03-01
I finally found the answer on a French Ubuntu forum (merci!).

The following command has always worked in the past, but last night failed and gave me the "operation already in progress" error message:

sudo hidd --search

However, the above command does find the mouse (assuming I have set it to searchable mode by holding down the connect button for 12 seconds). When it finds the mouse it displays its address. Then, when I tried this command with the address of my mouse it worked:

sudo hidd --connect <address>

I still don't know why it suddenly quits every few days. I can't figure out any special thing that causes it. If I ever find the trigger I'll post a bug report. Meantime, the above keeps me mousing.

---

### Post by supercheetah on 2008-04-17
You're not the only one.  It just started happening to me too right after I rebooted my laptop, and I had put my Bluetooth mouse into discovery mode even though it was already registered.  I was trying to diagnose some other BT problems with that, and it stopped working for some reason.

---

