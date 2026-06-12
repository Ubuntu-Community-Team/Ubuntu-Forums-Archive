---
title: "Harddisk sound under ubuntu!(IBM laptop)"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by bsbture on 2005-12-12
I am running dual system on my IBM T43 1BH,which are Windows XP and ubuntu.Then,I found that the sound of harddisk when it is working are different under these two systems:
Especially,when ubuntu is working ,the harddisk generate the sound like that of Windows make when windows work hard,namely transferring big files,checking disk.
Is it something to do with my filesystem which is Reisefer?

Thank you for being patient with my English.

---

### Post by CrunchyDoodle on 2005-12-13
I also run a dual system on my notebook with XP and ubuntu. I have ubuntu installed on a USB drive that I plug in when I want to run it. I too have noticed that the hard drive seems to work harder with ubuntu. It is more active, even when it's just sitting idle.

Bye.     :cool:

---

### Post by 23meg on 2005-12-13
Did you try laptop-mode? See if ```
sudo laptop-mode start
``` changes things. If it does, see the manpage for laptop-mode for details and decide if you should be using it.

---

### Post by 23meg on 2005-12-13
[QUOTE=CrunchyDoodle]I also run a dual system on my notebook with XP and ubuntu. I have ubuntu installed on a USB drive that I plug in when I want to run it. I too have noticed that the hard drive seems to work harder with ubuntu. It is more active, even when it's just sitting idle.

Bye.     :cool:[/QUOTE]
It's not really doing a significiant read/write operation, this is a specialty of most *nix filesystems and kernels; they poll the hd every few seconds. Nothing you should be concerned about.

---

### Post by bsbture on 2005-12-13
hello to "23meg"
i will try this command later
it seems like you helped me before,you are very warmhearted

---

### Post by CrunchyDoodle on 2005-12-13
I certainly am not concerned. I was just noticing the difference in disk activity.

I also have a Windows Server 2003 box that handles various tasks, such as print server, weather station server, poopli update server and DVArchive server. The disk is never quiet, even for a second. Not to worry - it's normal.

Bye.     :cool:

[QUOTE=23meg]It's not really doing a significiant read/write operation, this is a specialty of most *nix filesystems and kernels; they poll the hd every few seconds. Nothing you should be concerned about.[/QUOTE]

---

### Post by 23meg on 2005-12-13
[QUOTE=bsbture]hello to "23meg"
i will try this command later
it seems like you helped me before,you are very warmhearted[/QUOTE]
Thanks for the kind words; you should also consider trying hdparm's -M option for acoustic management if you can't get to a solution. Remember that this feature is experimental though, and read the hdparm documentation before trying it.

---

### Post by bsbture on 2005-12-13
Sorry about that the "laptop-mode on" is no use~
I will try the later one

---

### Post by bsbture on 2005-12-13
ooops,I try hdparm -M but it threw me a message : '''HDIO_GET_ACOUSTIC failed:Inappropriate ioctl for device'''

what can i do next?my device file is /dev/sda

---

### Post by 23meg on 2005-12-13
[QUOTE=bsbture]ooops,I try hdparm -M but it threw me a message : '''HDIO_GET_ACOUSTIC failed:Inappropriate ioctl for device'''

what can i do next?my device file is /dev/sda[/QUOTE]
Since it's sda it must be either a SCSI or a SATA device, for which hdparm won't work. Take a look at sdparm, which must be in the repositories.

---

### Post by bsbture on 2005-12-14
still doesn't work on it ,i have check the manpage of the sdparm but the aucousic option was not found

---

### Post by bsbture on 2005-12-16
I used the latest "laptop-mode" ,it seems work on it

---

