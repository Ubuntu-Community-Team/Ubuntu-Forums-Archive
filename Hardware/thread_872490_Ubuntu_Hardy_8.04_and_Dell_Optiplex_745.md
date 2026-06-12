---
title: "Ubuntu Hardy 8.04 and Dell Optiplex 745"
date: 2008-07-28
forum: Hardware
---

### Post by rahmath on 2008-07-28
Dear All,

Problem: 
1. System hangs while booting just before the login prompt (not always but, almost 80% of the time).  
2. System hangs always on reboot, it will hang in the last step where it shows "Restarting" (100% time it hangs at this stage)


I am facing a big problem with ubuntu hardy. Actually i am newbie to Ubuntu, thats also one reason in delaying in finding a solution for this problem. After a lot of googling, i found that, there is different issues for different users with Dell optiplex 745 + Hardy. And this problem gets changed based on the Motherboard series (mine is 0HR330). I tried almost all the work around mentioned in sites (like acpi=force, reboot=b, blacklisting iTCO_wdt module, etc) but no way to get out of this.


Attachment:
===========
I am attaching the output of dmidecode -q, for further information regarding the hardware.


Few Error Messages:

During Reboot: (this is almost the last message in the screen)
=============
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - connection is closed
NetworkManager: nm_hal_deinit(): nm_dbus_signal_device_status_change: assertion 'cb_data->data->
bus_connection' failed
NetworkManager: nm_hal_deinit(): nm_dbus_signal_device_status_change: assertion 'cb_data->data->
bus_connection' failed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init could not get the system bus. Make sure the message bus daemon is running!


During booting:
===============
iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware


Hope there will be someone to help me out...

Thanks in Advance...

---

### Post by SidStudios on 2008-07-28
> **rahmath said:**
> 
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - connection is closed
NetworkManager: nm_hal_deinit(): nm_dbus_signal_device_status_change: assertion 'cb_data->data->
bus_connection' failed
NetworkManager: nm_hal_deinit(): nm_dbus_signal_device_status_change: assertion 'cb_data->data->
bus_connection' failed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init could not get the system bus. Make sure the message bus daemon is running!


I get that too. This is because we use NDISWrapper with the Windows Broadcom Driver, this isn't an issue though. I don't know if there is a "fix" but it doesn't do anything bad. When you use the actual broadcom firmware with a newer distro, like Fedora 9 or OpenSUSE 11, these messages do not show up (as they use 2.6.25 and have no use for the NDISWrapper).

---

### Post by rahmath on 2008-07-28
Thanks for your comments and information. But do u have any idea about my problem??? why it is keeping hanging, is there any workaround for it?

---

### Post by rahmath on 2008-07-28
Now the reboot problem is solved with reboot=b option itself. (before i used it, but it was in the wrong area)

Now Alhamdulillahhh its working...


Really sad to say that i didnt get any workaround even after 8 hours...


This is a problem which is going to effect around 100 PC's which is scheduled to migrate to Ubuntu... and now i am screwing up... it will be great if someone could shed some light...

---

### Post by rahmath on 2008-07-31
Dear All,

I solved the problem. Finally i realized that, there is lot of issues in hardy related to the display drivers. I just plugged in an PCI graphics card MATROX, and things are working fine now.

One bad thing, i had asked almost 3 to 5 questions in the forum. But i didnt get any answer for any of these Q's. i dont know why it is like that. I am actually a newbie to Ubuntu, but working with Linux for almost 9 years. i didnt had this kind of feeling from any of other forums. As its a new stuff for me, i always stuck with many parts of Ubuntu. I thought someone will be here to help me out to speed up the things... but i am really sad in this case...

i dont know why it is like that???

---

### Post by Tex-Twil on 2008-10-06
Hi,
I have the same PC and the same issue.

Could you explain more how you solved the problem ? I'm not sure to understand.

cheers,
Tex

---

### Post by Sef on 2008-10-06
> I have the same PC and the same issue.

Could you explain more how you solved the problem ? I'm not sure to understand.

What is your graphics card?  The OP might have changed the graphics card.

---

