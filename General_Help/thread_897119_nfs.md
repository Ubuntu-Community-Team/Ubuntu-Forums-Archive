---
title: "nfs"
date: 2008-08-21
forum: General Help
---

### Post by studentz on 2008-08-21
:confused:
I intend to use a custom application launcher in the panel to mount two folders from the server in my client using NFS4.

these are the commands 
```

sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Pictures  /home/Import/Pictures
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Music  /home/Import/Music 
```

They work OK. But my little problem is that I need two launchers, one for each command. I would like to find a way to use only one launcher changing or join the commands, is this possible? 

Thanks

---

### Post by Unanimated on 2008-08-21
I'm not completely sure, but I think your answer would be:

```
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Pictures  /home/Import/Pictures;sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Music  /home/Import/Music
```

---

### Post by fragos on 2008-08-21
why not write a bash script with the two mounts and launch the bash script?

---

### Post by studentz on 2008-08-22
I tried your modification
```
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Pictures  /home/Import/Pictures;sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Music  /home/Import/Music
```
This did not work in the launcher but it works in a terminal. However; my goal is just click an icon and voila (forgive my French).

Any other suggestions?.

Thanks

---

### Post by fragos on 2008-08-22
Launching a shell script you've stored in /usr/local/bin will work. Do you need help writing it?

---

### Post by studentz on 2008-08-22
Sure, any help is more than welcome.

Thanks

---

### Post by fragos on 2008-08-22
Create a text file "/usr/local/bin/mntmedia" with the following 3 line -- look familiar:

#!/bin/bash
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Pictures  /home/Import/Pictures
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Music  /home/Import/Music

Change permissions to executable. You may now create a launcher for "mntmedia". In Nautilus places you'll now find "Pictures" and "Music". The default Ubuntu install would also place two storage icons for these mounts on your desktop. If these aren't created, open a terminal window and run "mntmdeia". This will show you error messages if the mounting fails.

---

### Post by studentz on 2008-08-23
:)
Thanks
It works. I add one line more to get the windows for the password
```
#!/bin/bash
gksudo -k /bin/echo "got r00t?"
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Pictures /home/Import/Pictures
sudo mount -t nfs4 -o proto=tcp,port=2049 xxx.xxx.x.xxx:/Music /home/Import/Music
```

I do not get the icons in the desktop but I prefer a clean Desktop.

Thanks again

---

