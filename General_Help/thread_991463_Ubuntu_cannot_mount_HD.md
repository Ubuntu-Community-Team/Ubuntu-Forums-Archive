---
title: "Ubuntu cannot mount HD"
date: 2008-11-23
forum: General Help
---

### Post by Psyphre on 2008-11-23
My windows no longer works, it boots up and logs in but all I see is my wallpaper and nothing else. Ive left it on for an hour and got nothing.

I'm sick of windows dying/failing on me so I want to install ubuntu on my laptop. Before this I need to recover the data on my laptop's HD. I thought I could just pop in the ubuntu CD and access my HD like i've done many times with my desktop, but unfortunately it will not mount my hard drive due to an unclean shut down. 

I couldn't copy and paste the message but I've googled for it:


$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NFTS is marked to be in use. Choose one action:
Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs -3g / dev/sda1 / media/Lokaal station -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 / media/Lokaal station ntfs-3g force 0 0


Of course the details will change a little as that is not my message, but it should be roughly the same. Obviously I cant just boot into windows and shutdown normally so I would have to 'force' the mount.

I am a bit confused as to what this means and what it involves since if it were safe ubuntu would have done that on its own right? What risks do I run, and how do I force mount it? I tried using the suggested command but it didnt work.

Thanks in advance.

---

### Post by geirha on 2008-11-23
I believe there is a slight chance the filesystem may get corrupted, which would be a good reason not to do it by default. Have you tried booting windows in safe mode?

---

### Post by Psyphre on 2008-11-24
ah of course safe mode! I totally forgot, I just tried it and I can boot into windows using safe mode, so I'll be able to back my stuff. Thanks so much.

---

### Post by blazemore on 2008-11-24
There is another way, for people who are having this problem:
```
sudo mount -t ntfs /dev/sda**x** /mnt -o force
```

---

### Post by Psyphre on 2008-11-26
thx blazemore. I'll try that in future.

---

