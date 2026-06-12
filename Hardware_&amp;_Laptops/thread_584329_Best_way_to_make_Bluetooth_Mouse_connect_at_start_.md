---
title: "Best way to make Bluetooth Mouse connect at start up?"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by steveneddy on 2007-10-20
It works great, but I am trying to discover the "correct" way to connect my bluetooth mouse at start up.

Sometimes it will start working for about five seconds, and then stop. I have to go to the Bluetooth Manager and browse for the device and then connect.

I haven't been turning it on first and that seems to help a little.

I would rather not have to go to the Bluetooth Manager and connect every time.

Is there a fool proof way that I can do this, a known procedure, for making it hook up right after Gnome starts?

I can't seem to get a system down to make this automatic.

I have done the stuff on this [web site]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") 

and [this site]("https://help.ubuntu.com/community/BluetoothSetup").

It's almost there, I think I just need a little lesson in this new toy.

:popcorn:

---

### Post by steveneddy on 2007-10-21
Sorry about the bump.

---

### Post by fflarex on 2007-10-21
In Bluetooth Preferences, click on the services tab, select input devices and then add device. If this doesn't work I can give you instructions on how to do it by editing a configuration file, because I honestly haven't completely figured out the new bluetooth managers either.

---

### Post by steveneddy on 2007-10-21
Yeah - it's bonded and in input devices, I would just like to get it configured so when I log in the mouse will connect, or when I turn it on it just connects.

---

### Post by fflarex on 2007-10-21
Well that's odd. My bluetooth mouse just connects and I didn't do anything fancy.

However, in Feisty I had to jump through much more elaborate hoops to get it working, so let's try this:

```
gksu gedit /etc/default/bluetooth
```

Then find the line that says HIDD_ENABLED=0 and change it to HIDD_ENABLED=1. Save and close. Should be working now.

Note that if the bluetooth manager is working correctly, there's no reason why you should have to do this. I don't think it even messes with these configuration files at all, because mine is still set to HIDD_ENABLED=0 and it still works perfectly. Still, if you're having trouble this is worth a try.

---

### Post by steveneddy on 2007-10-21
> **fflarex said:**
> Well that's odd. My bluetooth mouse just connects and I didn't do anything fancy.

However, in Feisty I had to jump through much more elaborate hoops to get it working, so let's try this:

```
gksu gedit /etc/default/bluetooth
```

Then find the line that says HIDD_ENABLED=0 and change it to HIDD_ENABLED=1. Save and close. Should be working now.

Note that if the bluetooth manager is working correctly, there's no reason why you should have to do this. I don't think it even messes with these configuration files at all, because mine is still set to HIDD_ENABLED=0 and it still works perfectly. Still, if you're having trouble this is worth a try.

Yeah - I did all of that. These instructions are on both of the referenced websites.

I did notice that there is a patch available for the 2.6.23.1 kernel that should help the Bluetooth stack.

I think I'll wait for that kernel and see if the patch is in there.

---

