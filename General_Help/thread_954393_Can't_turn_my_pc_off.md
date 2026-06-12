---
title: "Can't turn my pc off"
date: 2008-10-21
forum: General Help
---

### Post by dj_ee3 on 2008-10-21
Hi, I have one problem with ubuntu. When I try to turn the pc off it shows me a lot of errors involving networkMManager. The errors are 6 and here are some of them: 
NetworkManager: <info> Deactivating device eth0.
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed 
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus deamon is running.
NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->bus_connection' failed
The last one repeat two more times. 
Can you tel me how to fix the problem so I don't have to turn my pc off from the button because I have heard that turning off the computer from the button can mess it up... thank you in advice..

---

### Post by ronnielsen1 on 2008-10-21
sudo gedit /boot/grub/menu.lst

At the end of the line which begins with "kernel" insert the following "acpi=off" (without the "")

Save the file and reboot.

---

### Post by dj_ee3 on 2008-10-21
> **ronnielsen1 said:**
> sudo gedit /boot/grub/menu.lst

At the end of the line which begins with "kernel" insert the following "acpi=off" (without the "")

Save the file and reboot.
I did it. I went to the console and I typed sudo gedit /boot/grub/menu.lst. A file showed up in which I searched for kernel. I found a line that says    # kernel	/vmlinuz root=/dev/hda2 ro and I added acpi=off so it became # kernel	/vmlinuz root=/dev/hda2 ro acpi=off . I save the faile and turn off the pc and it showed me the same error. Any other thoughts?

---

### Post by ronnielsen1 on 2008-10-22
I guess you need to edit the acpi=off out since it's not doing anything. What kind of computer is this? It would make searching for the problem easier. What's the output of lspci -v and lsagp? Does anything in the following link apply to you?

[http://ubuntuforums.org/showthread.php?t=872490](http://ubuntuforums.org/showthread.php?t=872490)

---

