---
title: "[solved] Palm T5 synching with Evolution (Breezy) - (USB)"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by robenroute on 2005-10-19
Bloody hell, it took me a while and I must have read every single Internet page about this topic. But finally, I got it working (sort of...)
Okay, here we go:

1. In a terminal window:
[FONT="Courier New"]
rob@ubuntu:~$ ls -al /dev/pilot
crw-rw-rw-  1 root dialout 188, 1 2005-10-19 18:08 /dev/pilot
rob@ubuntu:~$[/FONT]

As you can see, root is the owner, dialout the group.

2. make sure the user wanting to sync, belongs to group dialout
System->Administration->Users and Groups
(just make sure you tick "Show all users and groups") If the sync users doesn't belong to group dialout (or whatever other group name /dev/pilot shows), make sure you add this user to this group. Also make sure everyone has read+write (666) rights.

3. System->Administration->Device Manager
Browse through the device tree and locate your Palm device (in my case "palmOne Handheld"; click on it/select it. In the righthand pane, you'll see 2 (or 3, deending on which branch/leaf in the tree you selected) tabs; select the Advanced one. There should be an "info.udi" key. In my case the key value reads:
/org/freedesktop/Hal/devices/usb_device_830_61_.....

The "830" and "61" values (they might differ in your case) are needed and should be used to configure the following file correctly; type in a terminal window:

[FONT="Courier New"]sudo gedit /usr/share/gnome-pilot/devices.xml[/FONT]

Scroll down the file and locate "your" device. Well, in my case, my device wasn't present at all so I had to insert it:

[FONT="Courier New"]<!-- Palm Tungsten T -->
 <device vendor_id="0830" product_id="0060" />
[COLOR="Red"] <!-- palmOne Handheld -->
 <device vendor_id="0830" product_id="0061" />[/COLOR]
 <!-- Palm Zire -->
 <device vendor_id="0830" product_id="0070" />
 <!-- Palm M100 -->
 <device vendor_id="0830" produ....[/FONT]

Be careful! In my setup, there was a Palm Zire 31 listed with this same product_id="0061". Now, having 2 identical product IDs in this file won't work (I've tried...) So, make sure there's only one and the string between <!-- and --> reads what you've copied from the Device Manager tree.

Save and exit.

One more file to edit (i got this from [http://www.ubuntuforums.org/showpost.php?p=383772&postcount=4](http://www.ubuntuforums.org/showpost.php?p=383772&postcount=4)). Again, in a terminal window:
sudo gedit /etc/udev/rules.d/10-custom.rules

and add the following line.

BUS="usb", SYSFS{product}="palmOne Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Save and close it. As you can see, I applied MY device name here, again. Check your Device Manager's tree for the correct device name of your Palm device!!!

4. Sytem->Preferences->PalmOS Devices
Follow the wizard, but make sure you select a high time-out value (I've got 30 sec.). BTW, there's no need to change the device to something along the lines of /dev/ttyUSB0, or so. /dev/pilot works like a charm, for me.

Also, no need to press the Hotsync key before proceeding with the wizard (as suggested in other threads). In fact, doing that didn't work at all, in my case. Just follow the wizard and when it tells you to press the Hotsync key, press it! On my laptop, it took about 10 sec. before the wizard told me that it had successfully retrieved my ID and username.

Stil in the wizard, press the forward button

5. Now, on the Conduits tab, set the correct behaviour for your conduits and close.

6. Start up Evolution and from the Edit menu, select Synchronization options. Follow the same procedure (somehow, in my case I was guided through the PalmOS Devices wizard again).

7. With your Palm connected, just hit the Hotsync button on the cradle (or the one on the screen).


Everything got synchronized. All appointments, addresses, to-dos, etc. Just one little hiccup: during the rest of the backup (some T5-settings were being synchronized, according to my T5), Breezy popped up a little window telling me that the gpilotd program had crashed. Bother!!! I just need to find out what happened there....

Happy syncing!

Rob


(Edited to correct a few typos)

---

### Post by manicka on 2005-10-19
I believe the crash is caused by the version of pilot-link being used in breezy (0.11.8). Apparently version 0.12 will fix this, but evolution doesn't support it yet

---

### Post by robenroute on 2005-10-19
Thanks for the reply manicka. My last sync, gpilotd didn't crash (at least, there wasn't a notification of it crashing), but my T5 reported a lost connection between it and my laptop. Hmmmmmm..... waiting for 0.12 c.q updated Evolution?

Thanks again,

Rob

---

### Post by franohern on 2005-11-08
Just wanted to say thanks. Finally got my Samsung i500 palm smart phone to sync reliably with Ubuntu after three weeks of trying.

Fran

---

### Post by Japejoop on 2006-01-16
Finally i,m syncing again.
Thank you robenroute!

---

### Post by RezoApio on 2006-07-03
Hello robenroute,

thanks for the posting. Seems to summarize most of the thing I have found on the internet about synching palm. However I am still unable to do it with my Treo 650 !!!

I have the command
william@RezoApio:/dev$ ls -al /dev/pilot
lrwxrwxrwx 1 root root 5 2006-07-03 10:19 /dev/pilot -> pilot

so the dialout group is not used but I am unsure this could have a big impact. Especially that I have added my user to the group root just in case.

I have also the same 0830 and 061 value so I have replaced the Zire 31 with my Palm Handheld value. 
I have also the custom rules with the correct name.

The only thing that may be different is that I have not gotten the wizard to get the user ID from the Tréo 650 with the wizard. And I have not idea on how to force the wizard to run again from scracth. Would you know how to do that ?
I am sure I am very close to a solution but still there is a missing bit to it...

Thanks in advance
William

---

### Post by gdgardnerw on 2006-07-13
z

---

### Post by uboltun on 2006-11-15
Thanks robenroute! It worked for my Tungsten E
I had to put "Palm Tungsten T*" in /etc/udev/rules.d/10-custom.rules

---

