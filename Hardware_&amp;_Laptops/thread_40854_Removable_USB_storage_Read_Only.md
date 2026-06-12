---
title: "Removable USB storage Read Only"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by rossriley on 2005-06-10
Just thought I'd post this to help anyone who has similar problem. 
When using USB removable storage, in my case a SanDisk Mini SD through a USB adaptor the device will automount but is set to Read Only.

Manually trying to mount produces the error:
mount: block device is write protected mounting read-only
Although there is no write protection on the device. After a bit of searching the solution was to run the following command as root after the device has automounted.


 mount -o rw,remount /path/to/mount

In my case the command was
sudo  mount -o rw,remount /media/sdb1

That fixed the problem and I can now write to the storage space.
Hope this saves some time for anyone with a similar problem.


---
Ross

---

### Post by Mez on 2005-06-11
have a look at ytour /etc/fstab, you can change the mount options for the device in there

---

### Post by zeca_pedra on 2005-07-08
Hi rossriley!
Thanks for this tip - I was really confused why this happened to me but the thruth is that «googleing» was not producing any result in finding a solution! Thanks to you I believe I'll be able to use my pendrive again, fully read and write (as it always should be!)...

 :razz: 

Thanks
Zeca Pedra

---

### Post by pyman on 2006-08-09
Thanks rossriley  
I have been fighting with this issue since I upgraded to Dapper. I have a LYRA mp3 player that mounted fine in Breezy. Now I can't load my music or podcasts. I hope your idea works because changing fstab did nothing for me. I hope this is not a bug.

---

### Post by pyman on 2006-08-09
Ok that did not work. :confused: 
After monkeying around I got this to work and now I am once again happy. :) 
I know 644 would have been better but WTH ](*,) 

sudo mount -o rw,remount,fmask=777  /media/sda

Now I can use my RCA LYRA RD2762A with my Ubuntu Dapper and load my songs and podcasts! 8)

---

### Post by CameronCalver on 2006-08-18
Ok that did not work for me because afetr i add a file on the palm it comes up
```
Error
SlotCardWrite:The card is read only.(exp 2907
```

---

### Post by pyman on 2006-08-23
Did you try running this from the terminal?=; 
I usually let the system bring up the usb then run the command in terminal. That lets me get read write access via konqeror (sp):tongue:

---

