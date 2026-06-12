---
title: "NTFS fully supported?"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Robby23 on 2008-03-26
Recently my hard drive has been giving me some problems.  I called up customer support for my drive's manufacturer and they said that ubuntu could be the problem because NTFS is not fully supported.  I did some research and from what I read NTFS is now supported.  My hard drive is an external drive that is connected through firewire.  All I mainly use it for in ubuntu is to watch some movies that I have stored on the drive.  I can't think of many times that I actually put anything on the drive in ubuntu. 

So my question is, is NTFS fully supported now and if not could it cause my drive to become corrupted?  Right now all the old files on my hdd i could access but anything new that I put on it when I try and copy it back the drive's LED turns red and struggles to copy the data.

---

### Post by mssever on 2008-03-27
First, you didn't say whether you're using the ntfs-3g driver. If so, it should work; but keep in mind that all NTFS support in Linux is the result of reverse engineering, and so isn't perfect.

Second, what do you mean by saying that your hadr drive struggles to copy the data? In the absence of further details, I'm guessing that your drive is crashing.

---

### Post by Robby23 on 2008-04-05
Yes i do have ntfs-3g driver.  

And what I mean about copying data, any old files on the drive I'm able to copy to another hard drive but anything new I put on the drive I'm unable to retrieve it.

---

### Post by mssever on 2008-04-06
> **Robby23 said:**
> And what I mean about copying data, any old files on the drive I'm able to copy to another hard drive but anything new I put on the drive I'm unable to retrieve it.

What's the difference between old and new?

---

### Post by Robby23 on 2008-04-06
> **mssever said:**
> What's the difference between old and new?

When I try and copy anything new off the hdd the hdd's LED turns red and make weird noises like its struggling and eventually i'd get an error.

---

### Post by mssever on 2008-04-07
> **Robby23 said:**
> When I try and copy anything new off the hdd the hdd's LED turns red and make weird noises like its struggling and eventually i'd get an error.

You haven't yet given the difference between old and new. Does old mean 2 seconds? 2 days? 500 years?

What error are you getting? It doesn't do a whole lot of good to say that there's an error without saying what the error is.

Weird noises suggest a dying hard drive.

---

### Post by Robby23 on 2008-04-07
> **mssever said:**
> You haven't yet given the difference between old and new. Does old mean 2 seconds? 2 days? 500 years?

What error are you getting? It doesn't do a whole lot of good to say that there's an error without saying what the error is.

Weird noises suggest a dying hard drive.

Old being 1 month old.  Error i get i can't remember because it was about a week ago and I didnt write it down.  Regardless I already RMA'd it

---

### Post by sdennie on 2008-04-07
If at all possible, if you are going to share data between Windows and linux, I would recommend having the shared partition/disk formatted as fat32 (especially if it's just a media drive).  Linux has had great support for fat32 for as long as I can remember (and I remember a long time ago).  I believe that NTFS is supposed to be supported with read/write abilities these days but, frankly, the fat32 support has always been so good that unless you have a dire need to run NTFS on shared media, you are better off going with fat32.

---

