---
title: "Second HARD drive not found"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by John Tumath on 2006-06-18
1st Drive Samsung 2042H with ubunto OK

2nd drive Maxtor  6y080lo  (80 gigs)  FAIL
Diskmanager says it it inaccesible and wont let me enable it.

I have fdisk it
I then used diskmanager to format it and still get the same message

Is Ubuntu able to handle 2 seperate drives :confused: 


John

---

### Post by cotcot on 2006-06-18
Yes ubuntu can handle 2 separate drive.

There might be an issue with 80 GB drive if you have an older computer. Than you have to move the jumper on the HDD so that it is recognised as a 30 GB drive. Ubuntu will install on it using LVM. I have this with my test PC (see signature). This PC is from 1999.

Check your BIOS. It is possible that you have to 'enable' the second HDD in your BIOS settings.

---

### Post by John Tumath on 2006-06-20
Thanks for the info but did not realy help

I got rid of ubunto and replaced it with FC5

It saw both hard disks and the second drive Maxtor 6y080lo (80 gigs) can be seen and is mounted as /data and now has about 10 gigs of test data on it.

Did a live install of ubunto this time, still could not access it
Looking like ubunto was heading for the round filing cabinet by my desk,BUT
had another play with diskmanager and by setting a new access point to
 
file system /data 

all was well.

Now going to install Dapper fully on my PC

Once again 
Thanks for your input

John..:D

---

### Post by John Tumath on 2006-06-20
LATER

We have blast off all systems go

=D> =D> =D> =D> =D> 

John..

---

### Post by John Tumath on 2006-06-25
Now I have another problem

How do I keep /data mounted when i reboot the PC ??????

or do i have to keep using diskmanager

---

### Post by _simon_ on 2006-06-25
I believe you need to add it to /etc/fstab

There's a fair few articles in the wiki on mounting

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=mount&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=mount&titlesearch=Titles)

---

### Post by John Tumath on 2006-06-25
Cheers

---

