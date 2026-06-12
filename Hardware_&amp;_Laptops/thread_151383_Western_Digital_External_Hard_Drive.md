---
title: "Western Digital External Hard Drive"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by TheFaction20 on 2006-03-27
i currently have a western digital mybook essential usb hard drive.  im trying to get it to stay recognized in ubuntu, yet it doesnt seem to want to.  its recognized for a short while then an error seems to occur. me being the linux noob i can't decipher it. i just know its an error.

here is the pastebin file....[http://paste.ubuntu-nl.org/10943](http://paste.ubuntu-nl.org/10943) 

any help in getting this to work would be greatly apprecitated

---

### Post by ubundrew on 2006-04-14
I am also having the same problem...

Any help would be appreciated!

---

### Post by Tom Tiger on 2006-04-15
Does your harddisk get enough power?  

I've got a Mycom external usb harddisk here which won't work on Ubuntu if I just plug it in (sometimes recognized and sometimes not).  

If I plug it in and put it on its adapter, it gets recognized without problems.

---

### Post by grumpymole on 2006-04-17
Had a similar prooblem with power and external USB hard drives.

USB ports are supposed to be limited to 500 mV (0.5V) per connection.  My harddrive was rated at 1.0V.  Therefore, the problem.

I have to use the Y-connector that comes with some external USB cases.  The second thin lead from one end is to provide extra power to the drive.  On some machines, I have to use both to power the external USB HD.  On others, it works with a single connection.  I guess some are more strict in following the USB spec???

Hope this helps.

Cheers

Warren

---

### Post by 89c51 on 2006-04-30
hello
because i am about to purchase a mybook essential can anyone confirm that everything works fine (recognition reading writing shuting down etc)

thanks in advance

---

### Post by TaNeK on 2006-05-23
Got the same problem, no recognition, even with DC adapter plugged in, so its not a power issue.

---

### Post by XXFCTEXX on 2006-09-02
I'm having problems with mine as well, only it's always recognized, but it gets constant read/write errors. I try to back up my music and it gives me a parameter error. So I decided to format it using gparted from fat32 to ext3, but that also failed with an error.

It seems to be a problem with read/write.

---

### Post by TaNeK on 2006-09-03
Im using dapper now, and it automounts fine for me, now errors whatsoever.

---

### Post by zool2005 on 2006-10-13
> **TaNeK said:**
> Im using dapper now, and it automounts fine for me, now errors whatsoever.

Hi,

I am hoping to buy a WD "MY BOOK" (250GB), please can you confirm that this is the External HDD you are referring to in the above quote. Thanks!

Phil

---

### Post by XXFCTEXX on 2006-11-04
I could never get my Western Digital Mybook to backup large files like my music folder, which basically renders it useless to me. Everytime i try to back up my music folder or a large file it backs up like 20 songs or part of the file and then gives me a "parameter error." I could never figure that out. Maybe it's the ext3 to fat32 transfer that is the problem.

Also, Ubuntu is a PITA to rename external drives on, you have to hook it up to a Windows box to rename it. I don't think this was solved in Efty either, which sucks. This is basic functionality which Ubuntu should have by now, it's a great OS, but it lacks some very basic operations.

---

