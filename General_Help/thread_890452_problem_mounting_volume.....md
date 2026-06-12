---
title: "problem mounting volume...."
date: 2008-08-15
forum: General Help
---

### Post by athreya86 on 2008-08-15
hi guys... i'm new to linux environment and i've been using ubuntu hardy heron for a week..... i've a dual boot system with windows xp and ubuntu... everyday i start my comp and log in to ubuntu i'm unable to open the volumes.... a window pops out and says "unable to mount the volume ... but when i log in to windows xp and come back to ubuntu i'm able to open the volumes.. 
the window shows the following details....


LogFile shows unclean shut down(0,0).failed to mount '/dev/sda5:Operation is not supported Mount is denied because NTFS is marked to be in use. .

so what should i do?

---

### Post by athreya86 on 2008-08-15
guys.... help me.... this is freaking me out....

---

### Post by dexter on 2008-08-15
Could give us the content of /etc/fstab.

---

### Post by athreya86 on 2008-08-15
the result was "permission denied" ??????

---

### Post by john183 on 2008-08-15
> **athreya86 said:**
> hi guys... i'm new to linux environment and i've been using ubuntu hardy heron for a week..... i've a dual boot system with windows xp and ubuntu... everyday i start my comp and log in to ubuntu i'm unable to open the volumes.... a window pops out and says "unable to mount the volume ... but when i log in to windows xp and come back to ubuntu i'm able to open the volumes.. 
the window shows the following details....


LogFile shows unclean shut down(0,0).failed to mount '/dev/sda5:Operation is not supported Mount is denied because NTFS is marked to be in use. .

so what should i do?

I had the same problem once. Reboot the computer into windows and do a proper shutdown. that will get rid of the "unclean shutdown" and should take care of the other problem also. if not then make sure you have the 'ntfs-3g' package installed.

---

### Post by caljohnsmith on 2008-08-16
Athreya86, I used to have to do what john183 describes, namely booting into Windows and making sure it has a "clean" shutdown so that it would mount OK in Ubuntu. But it turns out there is a great program called "ntfsfix" that can fix "unclean" shutdowns of Windows about 99% of the time, at least in my experience. It will save you from having to boot into Windows and doing a proper shutdown. 

First install the program with:
```
sudo apt-get install ntfsprogs
```
Then do the following command to fix your Windows partition:
```
sudo ntfsfix /dev/sdaX
```
Where sdaX should be replaced with your Windows partition. After that you should be able to mount it.

If you need any more specifics, let me know.

---

### Post by athreya86 on 2008-08-16
thank you guys... and thank you john.... that fixed the problem... why does this happen? i always shut down windows properly...

---

### Post by john183 on 2008-11-12
The issue is created when a usb drive is removed from a windows computer without either waiting for a complete shutdown or going through the "Safely remove hardware" routine before removing the drive. Windows is really bad about writing data to usb drives. It does not do the write instantaniously(sp?) when it is told to, it just puts the information into a cache so that if it needs it again quickly it has it right there. It then writes it to the drive when it gets a chance or you tell it that you are going to remove the drive. I jump all over my boss all the time about just yanking out usb drives, he thinks that it has no effect. Unfortunately, he has corrupted many briefings that he has worked on and then "saved" to a usb drive because he just clicked save and yanked out the drive. Long story (and point) short, use the "Safely Remove Hardware" icon in the windows task bar to remove your usb drives and save yourself the headache.

---

### Post by rswoody2000 on 2008-12-13
> **caljohnsmith said:**
> Athreya86, I used to have to do what john183 describes, namely booting into Windows and making sure it has a "clean" shutdown so that it would mount OK in Ubuntu. But it turns out there is a great program called "ntfsfix" that can fix "unclean" shutdowns of Windows about 99% of the time, at least in my experience. It will save you from having to boot into Windows and doing a proper shutdown. 

First install the program with:
```
sudo apt-get install ntfsprogs
```
Then do the following command to fix your Windows partition:
```
sudo ntfsfix /dev/sdaX
```
Where sdaX should be replaced with your Windows partition. After that you should be able to mount it.

If you need any more specifics, let me know.

Sorry stupid question i know, i cant rem how to get the details of the partitions i have. How do i find what my windows partition name is?

---

### Post by caljohnsmith on 2008-12-13
> **rswoody2000 said:**
> Sorry stupid question i know, i cant rem how to get the details of the partitions i have. How do i find what my windows partition name is?
If you open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -l
```
That will show your partitions; look for NTFS/FAT partitions as those could be your Windows.

---

### Post by rswoody2000 on 2008-12-13
> **caljohnsmith said:**
> If you open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -l
```
That will show your partitions; look for NTFS/FAT partitions as those could be your Windows.

Thanks for that, I now have a list of the partitions I have. I followed the directions above but unfortunately i still cant access my windows partition. This is annoying as things arnt running as smoothly since i had fixed the magnify confliction a couple of days ago. Do you thinks that's what caused this problem?

Oh and now it has an error message stating..."Unable to mount the volume. Cannot open /media/.hal-mtab"

Then a few seconds later another window shows with the following..."DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Make sense to anyone?

---

### Post by rswoody2000 on 2008-12-15
Ok i have managed to get it working. So incase anyone else if having the same problem as i just did...here is how i managed to fix it seeing as nothing else worked...

To gain access to /media/.hal-mtab with root permissions i typed the following into terminal

```
gksudo nautilus 
```

That then opened a window with root permissions. I went up a level until i could see a folder by the name of "media", once in there i could see the ".hal-mtab" file. I then deleted it and problem solved. I made a backup of it incase it didnt work. But so far so good.

---

