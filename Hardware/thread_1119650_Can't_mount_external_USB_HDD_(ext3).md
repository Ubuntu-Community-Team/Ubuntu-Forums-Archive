---
title: "Can't mount external USB HDD (ext3?)"
date: 2009-04-08
forum: Hardware
---

### Post by BarneyMcgrew on 2009-04-08
Hello
Firstly, I have very little linux and virtually no Ubuntu experience. I'm trying to resolve a specific problem and I'm using Ubuntu 8.10 to (hopefully) do this.

Problem: I have a 300Gb USB2 external HDD that was attached to a Linksys NSLU2 unit. The disk was originally formatted by the NSLU2 (presumably ext3 format?) and had been in operation for about 4 years. Something has happened and now I cannot access the folders or files on the disk. I just need to rescue one folder.

Here's what I've done so far: 
Installed Ubuntu 8.10 to disk on an old laptop. That's all fine. When I plug the errant HDD into the laptop (which BTW only has USB1 ports), it obviously detects it but after about 20 seconds I get 4 error dialogues, as follows:
"Unable to mount 299.9 GB Media.  
DBus error.freedsektop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken"

"Unable to mount 123.4 MB Media" (rest of detail is as above)

"Cannot mount volume. Unable to mount the volume.
Details: 
mount: /dev/sdb1 is not a valid block device"

"Cannot mount volume. Unable to mount the volume.
Details: 
mount: wrong fs type, bad option, bad superblock on /dev/sbd2, missing codepage or helper program, or other error ....."

I've tried the "sudo fdisk -l" command and it returns details only of the on board 40GB HDD. Does this preclude any way of mounting the external HDD volume? Can I manually mount the volume or force a mount somehow?

Any pointers as to how to proceed greatly appreciated. Thanks in advance.

---

