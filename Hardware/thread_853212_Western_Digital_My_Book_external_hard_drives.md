---
title: "Western Digital My Book external hard drives ?"
date: 2008-07-08
forum: Hardware
---

### Post by Physicist on 2008-07-08
My question is simply:

does Ubuntu work with
 
My Book® Mirror Edition™
Dual-Drive Storage System with Mirroring
2 TB, USB 2.0

[http://www.wdc.com/en/products/products.asp?driveid=466](http://www.wdc.com/en/products/products.asp?driveid=466)

and/or

My Book® World Edition™
Home Network Storage with
Remote Access
1 TB, Ethernet

[http://www.wdc.com/en/products/products.asp?driveid=347](http://www.wdc.com/en/products/products.asp?driveid=347)

---

### Post by phidia on 2008-07-08
I have a smaller Mybook drive with usb-it works fine. Mine is formatted to ext3 though if you want to use ntfs you will need to install/configure other things.

---

### Post by kostkon on 2008-07-08
> **Physicist said:**
> 
My Book® World Edition&#8482;
Home Network Storage with
Remote Access
1 TB, Ethernet

[http://www.wdc.com/en/products/products.asp?driveid=347](http://www.wdc.com/en/products/products.asp?driveid=347)
Yes, it works just fine and it is EXT3 formatted. Although, there are many restrictions on what you can share outside your local network (i.e. over the internet). Also, it's not the fastest *NAS* you can find (it does not have very good transfer speeds).

ADDED:
But the perfect thing is that since it runs Linux you can hack it and put anything you like! You can add a torrent capabilities, SSH, FTP, anything!!

Check [here]("http://mybookworld.wikidot.com/") for a start.

Thus, you can make a small server with a very low power consumption. Although, it only has 32MB RAM and slow CPU, so don't expect it to run many many things concurrently.

---

### Post by Mongo5000 on 2008-07-08
I have the 1TB model and it works perfect. I have not hacked mine yet but plan to one day. 

I just mount the PUBLIC folder and put everything in that.

---

### Post by Physicist on 2008-07-09
You mean the World Edition ?

---

### Post by Physicist on 2008-07-09
Just to make sure, the information you gave is for the World Edition ?
What is the default format of the hard drive ? NTFS ? I suppose if I have ntfs-3g, it should be usable ?

> **kostkon said:**
> Yes, it works just fine and it is EXT3 formatted. Although, there are many restrictions on what you can share outside your local network (i.e. over the internet). Also, it's not the fastest *NAS* you can find (it does not have very good transfer speeds).

ADDED:
But the perfect thing is that since it runs Linux you can hack it and put anything you like! You can add a torrent capabilities, SSH, FTP, anything!!

Check [here]("http://mybookworld.wikidot.com/") for a start.

Thus, you can make a small server with a very low power consumption. Although, it only has 32MB RAM and slow CPU, so don't expect it to run many many things concurrently.

---

### Post by kostkon on 2008-07-10
> **Physicist said:**
> Just to make sure, the information you gave is for the World Edition ?
What is the default format of the hard drive ? NTFS ? I suppose if I have ntfs-3g, it should be usable ?
Yes, for the World Edition. Since its a NAS you don't actually care so much about what file system it has. But, just for the info, it is EXT3.

It uses samba, not the best thing. You create shares and then you mount them on your desktop as network drives.

Finally, I want to specify that it only offers a LAN interface, you cannot connect it to your PC using a USB connection.

It has a USB port only in case you want to add an additional drive to it.

---

### Post by Physicist on 2008-07-10
> **kostkon said:**
> Yes, for the World Edition. Since its a NAS you don't actually care so much about what file system it has. But, just for the info, it is EXT3.

It uses samba, not the best thing. You create shares and then you mount them on your desktop as network drives.

Finally, I want to specify that it only offers a LAN interface, you cannot connect it to your PC using a USB connection.

It has a USB port only in case you want to add an additional drive to it.

What is exactly NAS ?

And by "LAN interface" do you mean the connector/plug for an either net card/adapter ? If so, WD My Book World Ed should be connected to a harbor ?

---

### Post by gdoutch on 2008-10-21
> **Mongo5000 said:**
> I have the 1TB model and it works perfect. I have not hacked mine yet but plan to one day. 

I just mount the PUBLIC folder and put everything in that.

I have this too, and I'm trying to mount the PUBLIC folder under kubuntu kde4 8.04.1 and just can't seem to get the right configuration under /etc/fstab. Is this how you did it? Can you post your fstab entry?

---

### Post by Bendihossan on 2009-04-01
> **Mongo5000 said:**
> I have the 1TB model and it works perfect. I have not hacked mine yet but plan to one day. 

I just mount the PUBLIC folder and put everything in that.

I'm having a little difficulty mounting my 1TB WE in 8.04.
Nautilus doesn't complain if I enter the directory "smb://Wdstorage/" but nothing shows. If I enter /public/ etc then I get a directory/file not found error. Any tips? 

Have been trying to access this drive on Ubuntu for a while now. It's a pain rebooting into Windows on a dual-boot just to access a few files ;)

---

### Post by BDNiner on 2009-05-12
Anymore information on this device? I am looking into buying one but I am sure about the consistency of it working under ubuntu. Can you access the other parts of the drive besides the public folder from a linux computer?

---

### Post by Bendihossan on 2009-05-13
> **BDNiner said:**
> Anymore information on this device? I am looking into buying one but I am sure about the consistency of it working under ubuntu. Can you access the other parts of the drive besides the public folder from a linux computer?

I forgot about this thread. I eventually managed to get the drive to mount by using cifs. If I remember correctly I just did an *apt-get install smbfs* and opened nautilus and entered "smb://wdstorage/public/".

To answer the question, yes you can access other folders such as the printer share etc. Just don't specify a folder when you mount. Ie: "//wdstorage/" as the server without a trailing folder. There's also the option of using an SSH hack. Though this is generally discouraged it can be used in emergencies and I'm not sure how WD would react to it if the driver ever became damaged/corrupt :)

---

### Post by davidhill on 2009-07-01
I'd be a little careful with MyBooks - I have two as USB devices - a 640MB and a 500 MB - and have trouble keeping them connected. They seem to go into sleep mode and don't wake up again, leading to the device being offlined, which then can mean loss of data if you were writing at the time.  I've looked around quite a bit (which is how I came upon your message) and I'm not alone in this, but it may be restricted to certain types of MyBook.

---

### Post by 737 on 2009-07-20
Hi all,
I'm new ubuntu user, and I've the WD mybook NAS and I would coonect it to the ubuntu workstation. Which are the actions to follow? 
Thanks in advance for help
737

---

### Post by Andrew_P on 2009-12-02
> **Physicist said:**
> What is exactly NAS ?

And by "LAN interface" do you mean the connector/plug for an either net card/adapter ? If so, WD My Book World Ed should be connected to a harbor ?

"NAS" stands for Network Attached Storage.  That would be storage devices attached to a network, such as file servers, that can be accessed by any computer connected to that network.

As far as "LAN interface" goes, it's an "Ethernet" card/adapter, not "either net".

---

### Post by bayvista on 2012-12-15
I have had a lot of trouble connecting to the WD. It has two types of shared folders: Public and Private. So far I have had no problems connecting to the Public folder from Ubuntu 12.04 following the various snippets in Google. However, I can't seem to write to a private share.

Perhaps I should explain that 'private' shares are created by the WD when you add a User. 

Now I have added myself (David) and now have a private share called David. I can mount this in fstab, copy files to it and rsync to it. Fine. 

I added a second user (my wife) as 'Pam'. I can mount this in fstab BUT there is no way I can write to it. All I get is 'permission denied'.

So, I'm half way there.

---

### Post by howefield on 2012-12-15
Please desist in resurrecting old threads.

Feel free to start a new one, reference this one if it is required.

Old thread back to sleep.

---

