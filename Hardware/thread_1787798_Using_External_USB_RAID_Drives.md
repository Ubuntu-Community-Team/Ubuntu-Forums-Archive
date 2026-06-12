---
title: "Using External USB RAID Drives?"
date: 2011-06-21
forum: Hardware
---

### Post by jonny.milano on 2011-06-21
Hi, 

Simple question here.. I'm thinking of buying a RAID 1 USB enclosure like this one: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16817729030](http://www.newegg.ca/Product/Product.aspx?Item=N82E16817729030) or this one: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16817707174CVF](http://www.newegg.ca/Product/Product.aspx?Item=N82E16817707174CVF)

My question is, does Ubuntu just see this as a standard USB drive? Or, will I need to install RAID software/drivers on installation of Ubuntu or is this handled in the firmware of these units and they just report a "normal" USB drive to the system. 

Manufactures specs say that the are for Windows and Mac. I'm assuming they just forgot to add Linux to that list??

Thanks for the help on this pretty basic question.

---

### Post by Beacon11 on 2011-06-22
I believe these enclosures use a hardware RAID-- it will look like any other USB drive to any computer. I have a similar enclosure. They didn't "forget" to add Linux to the list, the marketing people just figure it would be a waste of words, because "no one uses Linux." :P

---

### Post by psusi on 2011-06-22
What is the point of such a device?

The purpose of raid1 is to maintain 100% uptime, even when a drive fails.  If you are using an external USB enclosure, you presumably don't care about having 100% uptime.

---

### Post by Beacon11 on 2011-06-22
> **psusi said:**
> The purpose of raid1 is to maintain 100% uptime, even when a drive fails.  If you are using an external USB enclosure, you presumably don't care about having 100% uptime.

Oh heavens no. The purpose of a RAID1 is to maintain redundancy. Whether that is used for uptime or used for peace of mind, it's all about redundancy. I've had too many single external hard drives fail (one, to be exact) to NOT use RAID in my enclosures.

---

### Post by jonny.milano on 2011-06-22
Beacon,

Thanks so much! That puts my mind at ease! I will order one! Or, do you have a model recommendation? 

For the other posters,

Thanks for your replies. Yes, I am hoping to use a RAID 1 enclosure for the redundancy but I do have a feeling that RAID 1 may have been invented for 100% uptime.. Anyways, these enclosures offer the redundancy that I'm looking for (and the piece of mind!)

---

### Post by psusi on 2011-06-22
It is a popular misconception that raid1 keeps your data safe.  It does not.  Raid is no substitute for regular backups.  Raid1 might protect you from having a single drive fail, but the other can also fail ( often times people don't notice when the first one goes, and then the second one goes a few weeks/months later ), or you can simply delete a file by accident, or have the filesystem become corrupt.

---

### Post by Beacon11 on 2011-06-22
Haha, I said nothing about keeping my data safe. I want multiple copies of my data on separate devices. Period. Backups are a different matter.

Jonny, I personally use a Sans Digital TowerRAID: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816111143&cm_re=TR4UT-_-16-111-143-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111143&cm_re=TR4UT-_-16-111-143-_-Product) . I find it works perfectly for my purpose, and gives me a bit of room to expand.

---

### Post by psusi on 2011-06-22
> **Beacon11 said:**
> Haha, I said nothing about keeping my data safe. I want multiple copies of my data on separate devices. Period. Backups are a different matter.

Keeping multiple copies of your data on separate devices is a means to an end, not the goal itself.  What you *want* is either to keep your data safe, or to keep it highly available.  *How* you achieve those is by keeping copies on separate devices.

Whether you should use raid or manually copy between the devices depends on which goal you are trying to address.

---

