---
title: "How can I find out if a USB drive is plugged in?"
date: 2009-01-19
forum: Hardware
---

### Post by j_galt on 2009-01-19
I'm trying to write a script that will run via cron only when an external USB drive is plugged in.  I need to know two things:

1.  How can I determine whether or not the drive is plugged in?
2.  How can I script something that will, if the drive is plugged in but not mounted, determine what the device name is?  (Once I can get the script to id the device, I'll have no problem mounting it...)

As I said, this is to be run via cron, so it has to work without any interaction from me.  If I'm sitting at the keyboard and typing commands, I can easily figure this stuff out, but I have no idea how to automate it.

This is an issue because I sometimes have multiple USB drives plugged in at the same time.  Since they are assigned a device name based on when they are plugged in, and they are plugged in and unplugged as needed, I have no way of predicting which device name will be assigned to which drive...

I've spent the last hour searching Google for an answer but without luck.  Any ideas?

Thanks!

---

### Post by x22 on 2009-01-19
here's some ideas to start:

> determine whether mem stick plugged in

when mem stick in 

"grep USB /proc/bus/usb/devices"

returns "S: Product=USB Flash Memory" but when mem
stick not in, returns nothing

> find name

"dmesg | tail | grep sd | grep ^" " | cut -d: -f2"

returns " sdd1"

---

### Post by j_galt on 2009-01-19
Thanks for the reply but...

Neither command returns anything.

My USB drive is currently plugged in & unmounted.  /proc/bus/usb/devices doesn't exist, and the "dmesg" command returns nothing.

I'm running Kubuntu 8.10, though that shouldn't matter.  Any other ideas?

---

### Post by j_galt on 2009-01-19
OK.  After a whole bunch more searching, I figured some things out.  With the USB drive plugged in and mounted, I ran the following command to determine the device UUID:

ls -l /dev/disk/by-uuid

This gives me the following output:

lrwxrwxrwx 1 root root 10 2009-01-19 22:10 0f733d68-17d1-489e-85d2-23e895354169 -> ../../sdb5

After some testing, I also determined that this entry only exists when the drive is plugged in.  So I can use this entry to accomplish what I want to do.  I can put the UUID into my script & run the above command to determine which device name it has been assigned.

Now I need to figure out how to take that output and assign only the device name - in the above case "sdb5" - to a variable.  This is currently beyond my scripting knowledge to accomplish.  Can anyone help?

Thanks!

---

### Post by j_galt on 2009-01-20
There's gotta be a better way to do it, but the following command gets me what I need:

ls -l /dev/disk/by-uuid | grep 0f733 | sed 's/ //g' | awk -F"/" '{ print $3 }'

The output is simply -- sdb5 -- which is all I need.

Can anyone simplify this for me?  I'd appreciate it...

Thanks

---

### Post by Yashiro on 2009-01-20
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)
Might also be of interest.

---

### Post by j_galt on 2009-01-20
> **Yashiro said:**
> [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)
Might also be of interest.

Thank you very much!

---

