---
title: "[SOLVED] USB Drive access priviledges magically revoked???"
date: 2008-11-24
forum: General Help
---

### Post by paraplegicpanda on 2008-11-24
So I have been able to access my thumb drives a million times up until I woke up this morning. I popped in one of my 2G jump drives and as normal, it popped up in my nautilus sidebar. When I clicked it to mount it, I was given the error message:
```
**Cannot mount volume.**
You are not privileged to mount the volume 'shad0w'.
```

I also just received (for whatever reason) this message:
```
**Unable to mount shad0w**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

I have tried all 4 of my jump drives with similar results (all 4 are different brands and I have tried all 3 ports on my laptop so I figure it has to be a software issue).

After making a folder titled 'usb' at /media/ I can manually mount the drives with:
```
sudo mount /dev/sdb1 /media/usb
```

Though I still can't copy any of the data or put any new data on it. I have even tried (since I just wanted it to work regardless of security):
```
chmod 777 /dev/sdb1 && chmod 777 /media/usb
```

Thanks in advance for any help!

P.S. - Also tried reformatting all of the drives, still no fix.

---

### Post by ericesque on 2008-11-25
have you tried rebooting?  I think that's actually gotten me around the 
'not privileged to mount' error before.

Also, have you messed with manually configuring fstab recently?

---

### Post by paraplegicpanda on 2008-11-25
I have tried rebooting over and over again and nothing has changed. I'm not really sure what to change in fstab to get the USB to work. I have added the line to allow VirtualBox to use USB but even after commenting it out nothing has changed...

---

### Post by paraplegicpanda on 2008-11-25
P.S. - I have also checked the user privileges for my profile and I am pretty sure that I should have the ability to mount them...

---

### Post by paraplegicpanda on 2008-11-25
Also, I can mount my SD card through the built in card reader in my laptop. Now I really don't think it's anything to do with privileges, it's gotta be related to usbfs somehow...

---

### Post by paraplegicpanda on 2008-11-25
Bump.

---

### Post by ubun_two on 2008-11-25
I had the same issue on my eeePC.  The solution was to comment out the CD-ROM line from fstab, as eeePC don't have the drive.

If it's not eeePC you have, then I have no idea, though I'd imagine it's something similar.

---

### Post by paraplegicpanda on 2008-11-25
Fixed. I just commented /dev/sdb1 out of the fstab and rebooted. Everything's gravy now.

---

