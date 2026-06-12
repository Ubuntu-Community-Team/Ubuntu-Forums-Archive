---
title: "ftp with external drive"
date: 2008-11-28
forum: General Help
---

### Post by sharat87 on 2008-11-28
Hi all, I need help real quick on this one...

I have a collected pictures from all my friends' cameras and put them on my external hard disk. Now all my friends want to access that so that even they can have all the photos.

I have to host an ftp server that would let me allow them to take the photos they want. This is where the problem comes... i could not find a way so that i can put only the folder with all the photos which is in the external to be accessed by ftp.

I mean... if I access ftp with my own account, I can cd to /media/MY-HD/Pictures/allColl and get all the pictures... but I dont want to share my account's credentials... I am sure there a better way than copying all the pictures onto my lappy's small HD.

I am using the vsftpd server. Any suggestions welcome.

Thanks

---

### Post by outofnicks on 2008-11-28
I'm no expert at this but you should be able to specify the location in the config file at /etc/vsftpd.conf where you want guest access to be. 
I think you would only need to add the path to that directory on your external HD, like /hdb1/ftp for example, to the anon_root directive in the config file:
```
# Allow anonymous FTP?
anonymous_enable=YES
...
# The directory which vsftpd will try to change
# into after an anonymous login. (Default = /var/ftp)
anon_root=/data/directory
...
# Uncomment this to allow local users to log in.
local_enable=YES

```

I got that from a howto on linuxhomenetworking.com and you can take a look yourself at:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#The_vsftpd.conf_File](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#The_vsftpd.conf_File)

---

### Post by sharat87 on 2008-11-29
Thanks you very much... I think this might just work. But can a create a user in the ftp group and give the home directory of the user as the folder in the external so I wont expose the folder to anonymous users.

I dont have my HD right now with me... when I get it back I'll test your suggestion... It might just work :)

Thanks a lot

---

