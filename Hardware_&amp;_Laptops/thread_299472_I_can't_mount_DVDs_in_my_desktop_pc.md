---
title: "I can't mount DVDs in my desktop pc"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by jadell on 2006-11-14
Hello all,
I'm using ubuntu 6.06 and now I can't mount DVDs.

When I insert a new DVD it says is a blank DVD.
My fstab says:
/dev/hdc      /media/cdrom0     udf,iso9660     user,noauto     0       0

and if I do:
sudo mount -t udf /dev/hdc /media/cdrom

i says:
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then, the dmesg results are:
[17248665.892000] attempt to access beyond end of device
[17248665.892000] hdc: rw=0, want=1028, limit=4
[17248665.892000] UDF-fs: No partition found (1)


Does anyone have an idea.

Thnx.

Jordi.

---

### Post by taurus on 2006-11-14
What's on the DVD???

---

### Post by jadell on 2006-11-14
It is a data DVD with a couple of directoris with audio files. Nothing special, it is not a comercial DVD, is a backup copy of some audio recordings we did.

The think is that I can mount this DVD and others in a nothe machine containing also ubuntu (don't know which version). 

It is a wired problem for me.

thx.

---

### Post by taurus on 2006-11-14
See if this command works...

```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```

---

### Post by jadell on 2006-11-14
Thanks, I tried it and it didn't work. 
It keeps saying:
> 
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The DVD I try to read is part of a serie of 20 DVDs we recorded. But I tried with another one which contains a similar database, but was recorded in other conditions, and I can read it with no problems.

I do not know how to check diferencies between two DVDs so that I could guess the problem, do you know how.

In case it helps de mtab file for the dvd that works says:
> /dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=jadell 0 0


thnx.

---

### Post by taurus on 2006-11-14
You said that the same DVD that you currently cannot mount mounts fine on another machine running Ubuntu as well!  However, other DVDs mount just fine on the same machine.  There must be something going with that DVD then...

---

### Post by jadell on 2006-11-14
You are right.
People that record the DVD will say it the fault of my machine, because other machines cad read it, and people who built my machine, would say is the fault 
of the DVD because my machine can read other DVDs, :S

But... I just want to read the info inside in order to be able to work with it. 

Since the problem was wired I did something wired:
I did:
```

cd $HOME;
rm -rf .gnome*
rm -rf .nautilus/
sudo rm -rf /tmp/*

```

Then, I inserted the DVD, and .... It Worked!!!
nautilus opens the DVD automatically with no problem, more than I requested.

Does anyone know Why?!!
Which configuration and/or temporal data may affect it.

Thnx. for the help.

Jordi.

---

### Post by jadell on 2006-11-14
oooops!
I restarted my pc, and the DVD is not working again.
I did remove same directories again, ... but now it didn't work....

So it worked once, now It HAS to work, but I do not know why all this happens. Any idea to follow up searching....?

I'm running out of ideas, already.

thx.

---

