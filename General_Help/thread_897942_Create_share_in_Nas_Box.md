---
title: "Create share in Nas Box"
date: 2008-08-22
forum: General Help
---

### Post by LynnD1971 on 2008-08-22
I have no idea where to get help with this so please direct me if I'm in the wrong forum or even the wrong website. :)

Basically I'm a techie with Unix (Solaris and HP-UX) and Windows background - I don't know Linux.

I bought a no-brand Gigabit NAS box from a German guy on eBay.  It supports two SATA drives, so I installed a single 1TB drive which ran fine with all the default settings left alone (formatted EXT2).  However, after two months of torrents it's (naturally) full, so I bought another drive, stuck it in, formatted it and... Hmm.  Go to "create new share" in the GUI of the box, and there's no option to specify which of the installed hard drives it is created on. When I actually went looking, I couldn't find anywhere to specify which physical drive the share is created on.  

I telnetted to the box and found that the drives are mounted on /mnt/ide3 and /mnt/ide4.  Fair enough.  Any new share however is created on ide3 which is full.  No idea what the OS etc on the box is - it identified itself as busybox 1.00-rc3.  I did a uname -r and it gave me 2.5.16, and when I googled that number it gave a bunch of Ubuntu links.... so I'm hoping for some help or pointers here.

I need to get a starting point so that I can either set up a share for the new drive, or mount or attach it in some way to the original share /mnt/etc/public.

I'd be very grateful for some ideas... I just don't know the names of any of the packages and tools that are totally basic if you know Linux.  

Many thanks :-D

---

### Post by tamoneya on 2008-08-22
well Im pretty sure your NAS is not running ubuntu.  If anything it would be running debian I think. As for busy box it is a shell that you get dropped to if something fails in ubuntu and I think other linux OSes.  For example if the root partition couldnt be mounted you would get a busy box shell where you could attempt to fix things.  To move forward it would help if we could get any sort of details on the NAS.  Any markings or model numbers so that we can figure out what is running on it and how to fix it.

---

### Post by Loaded.len on 2008-08-22
Here's how adding a drive on my FreeNAS box works.

1st, (after physically adding the drive) Add the drive in FreeNAS
2nd, Format the Drive.  Since FreeNAS is built on FreeBSD, I use UFS Filesystem
3rd, Mount the Drive.
4th, add the share. (I use nfs, since Windows doesn't come anywhere near my network)

My FreeNAS box hostname is "hypogeum", and my drives are "hegmata1", "hegmata2" etc...  All of them mount to /mnt/hegmata(x) so in my fstab file I have:

```
hypogeum:/mnt/hegmata1    /mnt/hegmata1    nfs    defaults    0 0
```

---

