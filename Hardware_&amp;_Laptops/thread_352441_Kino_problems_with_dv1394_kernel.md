---
title: "Kino problems with dv1394 kernel"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by Mileeta on 2007-02-03
I have Dapper 6.06 installed.  I have followed the various posts strewn about the forums as far as getting Kino to recognize my DV camcorder over firewire (it does, in preferences, tell me that I have a Canon ZR 500).  When I click over to capture, though, I get the following warning error:

WARNING: dv1394 kernel module not loaded or failure to read/write /dev/raw1394

I'm pretty sure that if Kino knows what kind of camera I have attached, it can read, but I'm completely at a loss for what to do.  Nobody else's problems seem to match what mine are.

Things I have done:

sudo chmod 777 /dev/raw1394
added raw1394 and video1394 to my /etc/modules file

Any help at all would be appreciated.
-M

---

### Post by phansiizwe on 2007-02-03
In a terminal type:

```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```

and search for the KERNEL=="raw1394" entry, make it look like this:

```
KERNEL=="raw1394",		GROUP="plugdev"
KERNEL=="dv1394*",		GROUP="video"
KERNEL=="video1394*",	       GROUP="video"
```

This helps for me, hope it does for you too!

---

### Post by Mileeta on 2007-02-03
That didn't seem to do anything really at all :(

It seems like I'm thisclose to having the problem fixed.  Here's the relevant output from dmesg.

> [17179719.480000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17179719.480000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000085000114ea19]
[17179776.792000] ieee1394: Error parsing configrom for node 0-00:1023
[17179777.472000] ieee1394: Error parsing configrom for node 0-01:1023
[17179777.472000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00601d000000025f]
[17179777.744000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00601d000000025f]
[17179779.752000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000085000114ea19]
[17179779.756000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17179780.316000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17179780.316000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000085000114ea19]
[17185674.444000] ieee1394: Error parsing configrom for node 0-00:1023
[17185675.124000] ieee1394: Error parsing configrom for node 0-01:1023
[17185675.124000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00601d000000025f]
[17185675.396000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00601d000000025f]
[17185677.408000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000085000114ea19]
[17185677.408000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023


That seems a little off, to me.  More possible info, from lsmod

> 
video1394              20300  0
dv1394                 21196  0
raw1394                30956  2
ohci1394               35124  2 video1394,dv1394
ieee1394              299832  5 video1394,sbp2,dv1394,raw1394,ohci1394


I'd post more but I think I'm just grasping at thin air.  Thanks!
-M

---

### Post by meng on 2007-02-03
My solution ("dirty fix") is to do the capture by running kino as root:

gksu kino

then do the editing as a normal user by restarting kino in the usual fashion.

---

### Post by Mileeta on 2007-02-03
Well, it works now.  I did what you suggested, running Kino as root.  Also, I dug around in my /dev/ folder and found the dv1394 file... it was called dv1394-0.  I changed to preferences in Kino to look there for it, and voila!  I'm making movies.  Thanks for your help!!

-M

---

### Post by meng on 2007-02-03
I'm not happy with that solution, but I figure so long as I minimize the time that kino is run as root, there's little potential for harm.

---

### Post by phansiizwe on 2007-02-03
A good source for further info would be [http://www.linux1394.org/faq.php](http://www.linux1394.org/faq.php)
There, they set up the rules I mentioned before as:

```
KERNEL=="raw1394", NAME="%k", GROUP="users"
KERNEL=="dv1394*", NAME="dv1394/%n", GROUP="users"
KERNEL=="video1394*", NAME="video1394/%n", GROUP="users"
```

Good luck making movies!

---

### Post by eggdeng on 2007-02-04
> **Mileeta said:**
>  I dug around in my /dev/ folder and found the dv1394 file... it was called dv1394-0.  I changed to preferences in Kino to look there for it, and voila!  I'm making movies.
-M

This worked for me too. In Kino, Edit->Preferences and on the ieee1394 tab, change dv1394 device to /dev/dv1394-0. Neat piece of work, well done.

---

### Post by igorilla on 2007-04-22
I only had to change DV device in Kino to:

/dev/dv1394/0 (was /dev/dv1394)

---

