---
title: "automount windows drives"
date: 2008-10-06
forum: General Help
---

### Post by p03t13 on 2008-10-06
i have a windows machine that i already have set up as my main box (as i do not have a pwerful enogh system to fully utuilize my windows apps in ubuntu) but i want to automount my windows harddrives on my linux machine when it boots up, they are separate machines that are always networked together and i am trying to be able to have all my files available to me no matter hich machine im on without manually mounting the drives every time also havent played with linux in some time any help is appreciated

---

### Post by jerome1232 on 2008-10-06
Sound like what you actually want is file sharing.

All you need to do is tell the windows machine you want to share such and such directory, than on Ubuntu you goto Places->Network->browse around you should find your shares.

If you can't find them then it may be due to a bug in gnome, try doing this as a workaround, click places->Network, now hit ctrl+l, type in smb://ip.of.windows.computer/Sharename, you should arrive at the windows share, hit ctrl+d to bookmark it and it'll show up in your places menu now.

note: You can subsitute the windows computer hostname for it's ip.

---

### Post by p03t13 on 2008-10-06
k now that the hard part is done here's the stupid question, is there a way to have all of the icons for the drives automatically appear on the desktop without opening tham all?

---

### Post by jerome1232 on 2008-10-06
I believe this will do it, if this is an authenticated share it involves storing your username and password in a plaintext file though. Make sure you have smbfs installed; sudo apt-get install smbfs

let's say your windows computer is 192.168.1.3, and your share name is Public. You are going to mount this at /media/windowshare (things mounted here show up on your desktop I believe.

We will edit your fstab and add an entry like this:
```
gksu gedit /etc/fstab
# now add this entry to the end
//192.168.1.3/Public  /media/windowshare  cifs exec,credentials=/etc/cifspw 0 0
# if you don't have to login then switch it to this
//192.168.1.3/Public  /media/windowsahre  cifs exec 0 0
```
save that file then make a new file that has your login credentials, if you don't have to login to the share skip this step
```
gksu gedit /etc/cifspw
# add these lines
username=Joe
password=topsecret

# now make it so only root can view this file
sudo chmod 600 /etc/cifspw
```

Now test it
```
sudo mkdir /media/windowshare
sudo mount -a
```

---

