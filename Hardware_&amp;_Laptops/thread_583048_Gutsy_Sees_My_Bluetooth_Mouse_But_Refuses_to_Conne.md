---
title: "Gutsy Sees My Bluetooth Mouse But Refuses to Connect"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by guyver on 2007-10-20
I am trying to get my Logitech Bluetooth mouse to connect with Gutsy at bootup and so far the most I can get is the Bluetooth Manager to list it as a Bluetooth Mouse.  When I tell the manager to connect to my mouse I get the following error:

"obex://[xx:xx:xx:xx:xx:xx]" is not a valid location.

The x's being my mouse MAC address which is correct.  What gives?

---

### Post by NilsE on 2007-10-20
Obviously with your BT address in both do the following

To connect:   sudo hidd --connect 00:02:61:82:32:b9

NOTE: You may need to turn it on and off a few times.

Change the HIDD_OPTIONS line (around 19) in /et/default/bluetooth

to

HIDD_OPTIONS="--connect 00:02:61:82:32:b9 --server"

NOTE: You may also have to change HIDD_ENABLED=1 to 0 or 0 to 1 but try options forst

---

### Post by guyver on 2007-10-20
I was able to connect to my mouse as per your instructions.  However, I cannot edit the file you specified because Ubuntu says it's owned by root.

I have tried SUDO chmod 664 bluetooth, and it seems to take, but then when I try to edit the file, I am denied saving it.

---

### Post by guyver on 2007-10-20
Please disregard.  I did a sudo via my preferred editor and I was able to save my changes.  I rebooted and my notebook connects to my mouse automatically without having to have changed the value for HIDD_ENABLED.

Thanks NilsE!

---

### Post by NilsE on 2007-10-20
> **guyver said:**
> Please disregard.  I did a sudo via my preferred editor and I was able to save my changes.  I rebooted and my notebook connects to my mouse automatically without having to have changed the value for HIDD_ENABLED.

Thanks NilsE!
Great...

I didn't think the HIDD_ENABLED had to be changed but early on in Gutsy I had to but the defaukt has now changed.  Thanks for letting me know.

---

### Post by iamm7md on 2008-02-19
Hi every one,

I tried to follow this guide, but it doesn't work for me.
When I type

iamm7md@iamm7md-laptop:~$ sudo hidd --connect 00:12:5a:6a:df:58
Can't get device information: No route to host

even though I changed my bluetooth file as requested.

Can any one tell what is going on.
By the way, the "bluetooth" service is working, but I don't see the "bluetooth icon" on my top bar.

Thanx.
              iamm7md.

---

