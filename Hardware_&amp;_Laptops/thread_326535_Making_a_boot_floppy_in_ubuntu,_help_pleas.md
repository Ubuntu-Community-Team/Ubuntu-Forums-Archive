---
title: "Making a boot floppy in ubuntu, help pleas"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by daniel of sarnia on 2006-12-27
Hello all, what I'm trying to do is install a ubuntu server on a older PC that does not boot from the CD drive.

My work station is running kubuntu 6.10 and I was on the ubuntu web site and I could only find how to make a boot floppy under windows. How do I make a ubuntu boot floppy on my Kubuntu workstation to work with my server that has both a CD drive and a floppy drive, but it can only boot from the floppy.

 Thanks.

---

### Post by louieb on 2006-12-27
I think Smart Boot Manager is on the install CD . To copy it to floppy:
```
dd if=sbootmgr.dsk of=/dev/fd0
```My [SBM]("http://louboldt.com/ilinuxsbm.htm") page contains some more information and links.

---

### Post by daniel of sarnia on 2006-12-27
I figured it out.

I put the ubuntu install CD in my workstation, mounted it. 

Then  I open my command line and ```
 cd /media/cdrom0/ubuntu/install 
```

Put a blank floppy in and
 ```
 sudo dd if=sbm.bin of=/dev/fd0 bs=512 count=2880 
```

I don't really know how that last set of commands work, I just saw it on the GAG wed site and replaced dist.disk with sbm.bin that I found in the windows instructions on the ubuntu wed site. 

It worked and I'm installing my server, although I don't really know completely what the last command  did. Like bs=512 or count=2880??

Oh well at lest It worked!

---

### Post by daniel of sarnia on 2006-12-27
> **louieb said:**
> I think Smart Boot Manager is on the install CD . To copy it to floppy:
```
dd if=sbootmgr.dsk of=/dev/fd0
```My [SBM]("http://louboldt.com/ilinuxsbm.htm") page contains some more information and links.

You got it before me, But on the ubuntu 6.0.6 disk the file is sbm.bin, I don't know if I needed the  bs=512 count=2880 junk at the end but it worked, so I don't know.

Thanks for the help anyways.

---

