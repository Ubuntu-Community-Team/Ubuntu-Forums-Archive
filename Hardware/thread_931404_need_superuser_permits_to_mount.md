---
title: "need superuser permits to mount?"
date: 2008-09-27
forum: Hardware
---

### Post by wonkyuk on 2008-09-27
I am trying to mount an SD card on my ASUS eee 1000. I am using the latest version of ubuntu eee. the volume appears on the desktop butt every timee i try to mount it i get the error that only the superuser has permissoion to mount the device. i have gone into the authorizations controls within ubuntu and authorized myself to mount removable storage devices. but it still will not allow me to mount the card. same error regardless. how can i change the authorization level so that i can easily mount sd cards?

thanks for any help,
m

---

### Post by jpeery on 2008-09-27
Is there any messages in your system (auth) log?  Sounds to me if you see it on the desktop it's mounted.  Do you see it in the mount list - if you just type 'mount' ?

---

### Post by wonkyuk on 2008-09-30
I'm sorry, i don't really understand what you mean. the volume is displayed on the right-hand side of the desktop along with the internal volume. but if i try to open the volume i get the error message saying it is unable to mount the volume, saying i need superuser level access to mount the volume. i am not sure how to get that level of access to do this. it is important because i have a relatively small internal volume and will rely on high capacity sd cards, and also need access to my external dvd drive from time to time.

thanks for any help!
mark

---

### Post by iamah on 2008-10-01
> sudo nano /etc/fstab 

comment out the line that contains '/media/cdrom' then restart

---

### Post by wonkyuk on 2008-10-02
thanks so much. the cd rom drive now works perfectly and i do not get the error message of mounting the sd card. unfortunately i still get an error whenever i try to copy data to the sd card. it always says i do not have permission to open the file to be copied. i can copy the same files to another drive but not to the sd. this happens on any file i try to copy to the sd card. any ideas?

---

### Post by protean.star on 2008-11-01
Hi,
I have a similar problem, and would appreciate knowledgeable, accurate help.

I have a Eee PC 1000, with Ubuntu eee 8.4.0.1 (Hardy Heron) installed. 

I am unable to mount the DVD/CD external drive. It is an LG Super Multi DVD Rewriter, model GE20LU10. In the command line, I don't know what the description of the device should be. I also don't know how to write a SUDO command to mount the volume.

When I try to view a DVD, I get a message: Mount: Unable to mount volume. Must be superuser to mount volume.

Please see the screenshot.

Thanks for any help.

---

### Post by protean.star on 2008-12-27
This issue has been SOLVED. see this link:
[http://ubuntuforums.org/showthread.php?t=1023178](http://ubuntuforums.org/showthread.php?t=1023178)

---

