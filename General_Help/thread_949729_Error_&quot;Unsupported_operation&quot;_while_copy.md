---
title: "Error &quot;Unsupported operation&quot; while copying &quot;....&quot; opeartion not supported"
date: 2008-10-16
forum: General Help
---

### Post by amit.padhy on 2008-10-16
Hi all....

I get this error while copying/cutting,.etc.. please help...

```
Error "Unsupported operation" while copying "...." opeartion not supported
```

this is a problem with only one partition....
and it has nothing to do with permissions i suppose... 

I had started a thread earlier but it did not help much...
please please help me...

thanks in advance

---

### Post by jocko on 2008-10-16
> **amit.padhy said:**
> Hi all....

I get this error while copying/cutting,.etc.. please help...

```
Error "Unsupported operation" while copying "...." opeartion not supported
```this is a problem with only one partition....
and it has nothing to do with permissions i suppose... 

I had started a thread earlier but it did not help much...
please please help me...

thanks in advance
That error is what you get when you try to move or copy/paste files into a target folder where you don't have write permission, or if the target file system is mounted as read-only.

---

### Post by Tethylis on 2008-10-16
You can check the permissions by left-clicking on the file or folder and selecting properties. Then click on the permission tabs.

---

### Post by Gregory_NZL on 2008-11-22
Hi I get the same error **Operation not supported by backend** when I try to copy files to my newly formatted USB HDD.

I am running Ubuntu 8.04 and have formatted the drive with Ext3.

Why don't I have permission to write to my newly formated drive and how can I change this? :lolflag:

---

### Post by Gregory_NZL on 2008-11-23
Why would only Root be given access to this drive... is there something I have done wrong when using GParted to format the drive?

---

### Post by Gregory_NZL on 2008-11-28
This answer comes from a contributor in another [forum]("http://techreport.com/forums/viewtopic.php?f=7&t=63072"). Thanks JBI.

> By default, the root folder on the new drive will be writable only by root.

There are a number of ways you can deal with this. Assuming you are hot-plugging it, and it is auto-mounting itself as /media/disk, any of the following should work (do this with the drive mounted) --

To make it writable by anyone:

```
sudo chmod go+w /media/disk
```


To change the ownership, making it writable by your account only:

```
sudo chown myaccountname:mygroupname /media/disk
```


To create a subfolder that is writable by your account, while leaving the root folder of the drive writable only by root:

```
sudo mkdir /media/disk/myfolder
sudo chown myaccountname:mygroupname /media/disk/myfolder
```


There's probably a way to do this through the GUI as well, but I've never bothered to figure out how since I'm comfortable with the CLI...

---

