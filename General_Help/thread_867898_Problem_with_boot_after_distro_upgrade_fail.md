---
title: "Problem with boot after distro upgrade fail"
date: 2008-07-23
forum: General Help
---

### Post by JackTheKnife on 2008-07-23
I tried to upgrade Kubuntu 6.10 to 8.04 with steps to 7.04 then 7.10 and next 8.04. Everything was OK until distro upgrade to 7.10 when power failed (even battery). Right now when I try to boot system it goes only to

```

Checking file systems.... [OK]
fsck 1.40-WIP (14-Nov-2006)

```

and stops.

When I try to boot to the Rescue Mode (even 6.10) it goes to

```

Checking file systems... [OK]
fsck 1.40-WIP (14-Nov-2006)

* Mounting local filesystems.....
* Configuring network interfaces... (moje: wstaje nawet WiFi)
* Setting up console font and keymap...

```

and stops.

Any idea how I can fix that problem? Or how can I backup /home directory

Thanks.

---

### Post by Het Irv on 2008-07-23
If you want to backup your /home, try booting to a LiveCD and moving all of your files to a Jumpdrive or something like that.  This works best if you have an external drive.   If that is not possible, you can also use the LiveCD to create a small data partition on your drive and move your files there, then when you reinstall, be careful not to delete that partition.

---

### Post by JackTheKnife on 2008-07-23
I try to move /home to the pendrive but I got message that I do not have permission for 'sb1' device, or something like that. Even when I try to create archive with ARK. Thanks

PS.
I export /home to Windows XP disk but I'm not sure if all privileges and files settings will stay.

---

### Post by JackTheKnife on 2008-07-23
I try to resize partition to create one for a backup but I can not to do it with qtParted

---

