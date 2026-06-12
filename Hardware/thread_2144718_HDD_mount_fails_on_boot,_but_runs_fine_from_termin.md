---
title: "HDD mount fails on boot, but runs fine from terminal"
date: 2013-05-13
forum: Hardware
---

### Post by Black Hole on 2013-05-13
Upon boot, error message shows up:

[IMG]https://lh3.googleusercontent.com/-y93a5fzKMtw/UZCycv3n96I/AAAAAAAAB_g/3GuqkR_csj8/w727-h545-no/IMG_20130513_112853.jpg[/IMG]

After going into recovery I find that *wd6400aaks* mounts fine, but *wd10eads* and *wd10eads.bck* fail. Manually mounting them works perfectly, so I can't find any error there. 

```

/etc/fstab

UUID=c46acaa9-ed53-4e61-948c-89a8b89d2427 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=51ee3d60-905b-4406-b94b-c8857ba6c34c none            swap    sw              0       0

UUID=a638f3e1-b276-4272-919f-2a0663d37336 /mnt/wd6400aaks 	ext4 	defaults,noatime 	0       2
UUID=fd7afbcc-0b6a-44bf-b2db-c218f87e1881 /mnt/wd10eads.bck 	xfs 	defaults,noatime 	0       2
UUID=d1fc62d3-6c86-4ace-b0af-181ba9acc30f /mnt/wd10eads 	jfs 	defaults,noatime 	0       2
```

```
ls -l /mnt

total 8
drwxrwxrwx  5 dot dot 4096 Mar 19  2012 wd10eads
drwxrwxrwx  4 dot dot   36 Nov 29  2011 wd10eads.bck
drwxr-xr-x 14 dot dot 4096 Apr 12 11:00 wd6400aaks
```

[FIX]
Fixed after installing **xfsprogs** and **jfsutils**

---

