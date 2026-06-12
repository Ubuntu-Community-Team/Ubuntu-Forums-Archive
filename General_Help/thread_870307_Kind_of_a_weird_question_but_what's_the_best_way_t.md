---
title: "Kind of a weird question but what's the best way to share pictures between users?"
date: 2008-07-25
forum: General Help
---

### Post by S3loth on 2008-07-25
I know you can make folders to share on your account, but is there a "better" place to store pictures that all users will use? Does Ubuntu come installed with a place for users to share files? I know that this isn't a big deal at all, but if there is a pre-made place I think it would turn out better than me trying to remember the folder's I have made shared. :)

---

### Post by ad_267 on 2008-07-25
Don't know if this is really answering your question or is the best thing to do but this is what I've done.

I've got a /home/shared directory with all my shared stuff including /home/shared/photos. I've put all my users in a group called family and have the group set to family. I have the sgid bit set on that directory and subdirectories and all the directories are set to be writeable by the group.

I set the umask in /etc/profile set to 002 so new directories are writeable by the group. There's currently a bug in nautilus that means that this doesn't work for directories created in nautilus though so I have to manually set them to be writeable for the group.

---

### Post by S3loth on 2008-07-25
Yes! That's what I thought would be the way, but wasn't sure if adding folders that weren't profiles in /home was bad. Thanks!

---

### Post by ad_267 on 2008-07-25
Yeah I think it shouldn't be a problem as long as I don't make a user called shared. I might have done it differently but I have two hard drives, /home takes up all of the bigger hard drive and I wanted to keep the shared stuff on that drive.

---

### Post by jflaker on 2008-07-25
You can get a NAS box which I have seen at up to 1TB.  The shared drive can be purchased at office depot or other similar online/brick and mortar store.

The device attaches directly to your network and you mount/map the drives to the device.  I believe that there is a web interface from which you can create users and permissions........The box looks like a book end, so it is unobtrusive to you environment.

Otherwise, you can create a shared folder but that also means the shared box must always be up.

---

